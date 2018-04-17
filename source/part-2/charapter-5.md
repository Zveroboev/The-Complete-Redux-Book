## <a name="Сharapter-5">Глава 5. WebSockets</a>

WebSocket принесли надежный метод связи сокетов прямо в наших браузерах. То, что предназначалось как решение для отслеживания изменений данных на сервере постепенно принимает на себя все больше и больше обязанностей от традиционных запросов на сервер. Основана на action архитектура Redux делает работу с WebSocket исключительно простой и естественной, поскольку она предпологает использование WebSocket в качестве канала для передачи действий на сервер и с сервера.

### <a name="Basic-Architecture">Основная архитектура</a>

WebSockets позволяет нам открывать соединение с сервером и отправлять или получать сообщения полностью асинхронным способом. Нативная реализация в браузерах имеет только четыре метода обратного вызова, которые необходимы для полной поддержки WebSockets:

* onopen – Соединение было открыто.
* onclose – Соединение было закрыто.
* onerror – Возникла ошибка, связанная с соединением WebSocket..
* onmessage – Получено новое сообщение.

Хотя одновременно может использоваться множество WebSockets, большинству приложений потребуется одно или несколько соединений для разных серверов на основании требуемого функционала (сервер чата, сервер уведомлений и так далее).

Для начала мы создадим систему для связи с одним WebSocket, который впоследствии может быть расширен для поддержки множества WebSocket.

### <a name="Redux-Link">Redux Link</a>

Общая архитектура Redux предназначена для отправки четко определенных сообщений в хранилище. Эта же схема может отлично работать для связи с сервером через WebSockets. Та же структура простых объектов с свойством type может быть отправлена на сервер, и мы можем получить аналогично структурированный ответ:

_Пример потока обмена данными
```javascript
> TO-SERVER: { type: 'GET_USER', id: 100 }
< FROM-SERVER: { type: 'USER_INFO', data: { ... }} 
```

Более ясным примером может быть сервер чата, где мы можем отправить в хранилище сообщение, подобное: {id: 'XXX', type: 'ADD_MESSAGE', msg: 'Hello'}. Наш store может обработать это немедленно, добавив сообщение в текущий массив сообщений и отправив его «как есть» по WebSocket на сервер. Сервер, в свою очередь, может передать сообщение всем другим клиентам. Каждый из них получит совершенно стандартный Redux action, который может быть передан непосредственно в их store.

Таким образом, наш frontend может использовать Redux action для передачи информации между окнами браузера и другими компьютерами, используя сервер в качестве общего диспетчера. Наш сервер может выполнить некоторую дополнительную работу, такую как аутентификация и валидация, но по существу он служит посредников для передачи сообщения.

В идеале, реализация WebSocket для Redux позволит нам отправлять (_dispatch()_) действия и, при необходимости, перенаправлять их на сервер, а любые действия, поступающие из WebSocket, отправляются непосредственно в store.

### <a name="Code-Implementation">Реализация кода</a>

Как и любой код, связанный с инфраструктурой, middleware является идеальным местом для нашей реализации WebSocket. Это позволит нам отловить любые действия, которые необходимо отправить по WebSocket и выполнить _dispatch()_ всего, что поступает с сервера.

_Общая структура настройки WebSocket_
```javascript
const WS_ROOT = "ws://echo.websocket.org/";
 
const websocket = new WebSocket(WS_ROOT);
 
websocket.onopen    = () => {};
websocket.onclose   = () => {};
websocket.onerror   = event  => {};
websocket.onmessage = event  => {};
```

Чтобы сделать код более читаемым, мы можем заменить четыре разных gприсвоения одним использованием _Object.assign()_ и использовать код, аналогичный этому:

_Использование Object.assign_
```javascript
Object.assign(websocket, {
  onopen()     { },
  onclose()    { },
  onerror(e)   { },
  onmessage(e) { }
});
```

В нашей middleware мы хотим убедиться, что WebSocket создан только один раз. Таким образом, мы не можем поместить код настройки внутри обработчика действий:

_Неправильный способ инициализации middleware_
```javascript
const wsMiddleware = ({ dispatch, getState }) => next => action => {
  // Инициализация не допускается
};
```

Код в самом внутреннем блоке вызывается каждый раз при отправке действия, поэтому это приведет к тому, что наша настройка и создание соединения по WebSocket будут вызываться несколько раз. Чтобы предотвратить это, мы можем выполнить инициализацию вне блока обратного вызова действия:

_Правильный способ инициализации middleware_
```javascript
const wsMiddleware = ({ dispatch, getState }) => next => {
 
  // TODO: Инициализации
 
  return action => {
    // TODO: код Middleware
  };
};
```

Вернемся к коду инициализации и рассмотрим, как обрабатывать каждый из четырех обратных вызовов: onopen, onclose, onerror и onmessage.

#### onopen

Это в основном информативный этап. Нам нужно указать себе, что сокет готов к отправке и получению данных, а так же уведомить остальную часть Redux приложения об этом (возможно, нужно показать некоторые индикаторы в пользовательском интерфейсе).

Как только сокет открыт, мы отправляем простой action {type: 'WS_CONNECTED'}, чтобы уведомить остальную часть Redux:

_Обработка onopen_
```javascript
websocket.onopen = () => dispatch(wsConnected());
```

Функция _wsConnected()_ - это простой action creator, который должен быть реализован в одном из файлов создателя действия:

_app/actions/ui.js_
```javascript
import { WS_CONNECTED } from 'consts/action-types';
 
const wsConnected = () => ({ type: WS_CONNECTED });
```

#### onclose

Событие закрытия или отключения очень похоже на onopen и может обрабатываться точно так же:

_Обработка onclose_
```javascript
websocket.onclose = () => dispatch(wsDisconnected());
```

#### onerror

Реализация WebSocket в браузере может предоставлять информацию о различных сбоях лежащих в основе связи по сокетам. Обработка этих ошибок аналогична обработке ошибок обычного REST API и может включать отправку действий по обновлению пользовательского интерфейса или закрытию сокета, если это необходимо.

В этом примере мы остановимся на обычном _console.log()_ и оставим читателю возможность самим осуществить более продвинутые методы обработки ошибок:

_Обработка onerror_
```javascript
Websocket.onerror = error => console.error("WS Error", error.data);
```

#### onmessage

Этот обратный вызов вызывается каждый раз, когда новое сообщение принимается через WebSocket. Если мы настроили наш сервер для полной совместимости с Redux действиями, сообщение можно просто отправить в store:

_Обработка onmessage_
```javascript
websocket.onmessage = event => dispatch(JSON.parse(event.data));
```

#### Обработка исходящих сообщений и действий

При обработке всех обратных вызовов WebSocket нам нужно определить, как и когда передавать действия из Redux на сервер:

```javascript
return action => {
  // TODO: Отправить action на сервер
 
  next(action);
};
```

Перед отправкой любых действий нам необходимо убедиться, что WebSocket открыт и готов к передаче. У WebSockets есть свойство _readyState_, которое возвращает текущий статус сокета.

_Проверка что сокет открыт_
```javascript
const SOCKET_STATES = {
  CONNECTING: 0,
  OPEN: 1,
  CLOSING: 2,
  CLOSED: 3
};
 
if (websocket.readyState === SOCKET_STATES.OPEN) {
  // Отправить
}
```

Даже когда сокет открыт не все действия должны быть отправлены (например, действия TAB_SELECTED или REST_API_COMPLETE). Наилучшим подходом будет оставить решение за action creator. Стандартный способ передать специальную информацию об action нашей middleware заключается в использовании мета-ключа внутри action. Таким образом, вместо использования обычного action creator:

_Обычный action creator_
```javascript
export const localAction = (data) => ({
  type: TEST, 
  data 
});
```

мы можем добавить специальную мета-информацию для action:

_Action creator для отправки action на сервер_
```javascript
export const serverAction = (data) => ({ 
  type: TEST, 
  data, 
  meta: { websocket: true }
});
```

Таким образом, наша middleware может использовать поле meta.websocket для принятия решения о том, следует ли отправлять action или нет:

_Отправка action на сервер_
```javascript
return action => {
  if (websocket.readyState === SOCKET_STATES.OPEN && 
      action.meta && 
      action.meta.websocket) {
    websocket.send(JSON.stringify(action));
  }
  
  next(action);
};
```

Однако, обратите внимание, что этот код может вызвать непредсказуемую ошибку. Поскольку мы отправляем все action на сервер, он может, в свою очередь, передавать его всем другим клиентам (даже нам самим). И поскольку мы не удалили метаинформацию о action, middleware других клиентов WebSocket может повторно передавать его снова и снова.

Сервер, знающий о Redux, должен учитывать удаление всей метаинформации для любого действия, которое он получает. В нашей реализации мы удалим это на стороне клиента, хотя сервер все равно должен выполнить проверку:

_Отправка action на сервер (без метаданных)_
```javascript
return next => action => {
  if (websocket.readyState === SOCKET_STATES.OPEN && 
      action.meta && 
      action.meta.websocket) {
 
    // Удалим метаданные action перед отправкой
    const cleanAction = Object.assign({}, action, { meta: undefined });
    websocket.send(JSON.stringify(cleanAction));
  }
 
  next(action);
};
```

Используя этот подход, отправка действий на наш сервер через WebSocket становится такой же простой, как установка поля _meta.websocket_ в значение _true_.

### <a name="Complete-WebSocket-Middleware-Code">Полный код middleware для работы с WebSocket</a>

_middleware/ws.js_
```javascript
import { wsConnected, wsDisconnected } from 'actions';
import { WS_ROOT } from 'const/global';
 
const SOCKET_STATES = {
  CONNECTING: 0,
  OPEN: 1,
  CLOSING: 2,
  CLOSED: 3
};
 
const wsMiddleware = ({ dispatch }) => next => {
 
 const websocket = new WebSocket(WS_ROOT);
 
 Object.assign(websocket, {
   onopen() {
     active = true; 
     dispatch(wsConnected()) 
   },
 
   onclose() {
     active = false; 
     dispatch(wsDisconnected())
   },
 
   onerror(error) {
      console.log(`WS Error: ${ error.data }`);
   },
 
   onmessage(event) {
      dispatch(JSON.parse(event.data));
   }
 });
 
 return action => {
   if (websocket.readyState === SOCKET_STATES.OPEN && 
       action.meta && 
       action.meta.websocket) {
 
     // Удалим метаданные action перед отправкой
     const cleanAction = Object.assign({}, action, { 
       meta: undefined 
     });
     websocket.send(JSON.stringify(cleanAction));
   }
 
   next(action);
}}; 
 
export default wsMiddleware;
```

### <a name="Authentication">Аутентификация</a>

Обработка аутентификации с помощью WebSockets может быть немного сложной, как и во многих приложениях, WebSockets используются наряду с обычными HTTP-запросами. Аутентификация обычно выполняется с помощью обычных вызовов REST или OATH, а интерфейсу предоставляется токен, который сохраняется в cookie или в LocalStorage.

Чтобы разрешить серверу аутентифицировать WebSocket, клиентом должно быть отправлено специальное соглашение. В случае с Redux это может быть специальный объект action, который должен быть отправлен перед выполнением любой другой работы над WebSockets.

### <a name="Sample-Flow">Пример потока</a>

Простым способом реализации аутентификации может быть передача действия API на наш сервер, содержащий адрес электронной почты и пароль:

_Пример action для аутентификации с сервером_
```javascript
dispatch({
  type: API,
  payload: {
    url: 'login',
    method: 'POST',
    success: LOGIN_SUCCEESS,
    data: {
      email: 'info@redux-book.com',
      password: 'top secret'
    }
  }
});
```

В случае успеха наша middleware отправит action _LOGIN_SUCCESS_, содержащий информацию, возвращаемую с сервера:

_Action отправленный при успешном входе в систему_
```javascript
{
  type: LOGIN_SUCCEESS,
  payload: {
    token: 'xxxYYYzzzz'
  }
}
```

Наш пользовательский reducer, в ответ на этот action, добавит токен в state, для передачи его в заголовках будущих API запросов  на сервер.

Чтобы сделать аутентификацию WebSockets с использованием этого токена, мы можем добавить специальный код в наш API WebSocket, который будет проверять _LOGIN_SUCCESS_ (и _LOGOUT_SUCCESS_)

_Код обработки аутентификации WebSocket в middleware_
```javascript
if (action.type === LOGIN_SUCCESS) {
  dispatch({ 
    type: WEBSOCKET_AUTH, 
    payload: action.payload.token, 
    meta: { websocket: true }
  });
}
 
if (action.type === LOGOUT_SUCCESS) {
  dispatch({ 
    type: WEBSOCKET_LOGOUT, 
    meta: { websocket: true }
  });
}
```

Теперь поступление _LOGIN_SUCCESS_ приведет к отправке и обработке нового action с обработкой WebSocket нашей middleware для аутентификации с сервером.

_Поток действий_
```javascript
> Store: 
{ type: API, payload: ... }
 
> Server:
POST http://.../login
 
> Store: 
{ type: LOGIN_SUCCESS, payload: token }
 
> Store: 
{ type: WEBSOCKET_AUTH, payload: token, meta: { websocket: true }}
 
> WebSocket: 
{ type: WEBSOCKET_AUTH, payload: token }
```

### <a name="Notes">Примечание</a>

Для полного потока WebSocket middleware лучше всего отслеживать состояние аутентификации WebSocket и предотвращать отправку или получение действий до того, как WebSocket будет аутентифицирован или после разрыва соединения.

Когда токен уже присутствует в файле cookie, он будет передан в WebSocket, как только откроется сокет. Это может вызвать проблемы, если процесс входа происходит после загрузки приложения. Или еще хуже, когда пользователь выходит, наш WebSocket может оставаться аутентифицированным. Лучше использовать описанный выше подход аутентификации на основе действий, чтобы избежать этих и подобных проблем.

### <a name="Summary-5">Подведем итоги</a>

В этой главе показано, как хорошо WebSockets работают с Redux и практические шаги, необходимые для настройки связи на основе WebSocket.

В следующей главе мы рассмотрим тему тестирования и как каждая часть нашего приложения Redux может тестироваться отдельно и вместе.
