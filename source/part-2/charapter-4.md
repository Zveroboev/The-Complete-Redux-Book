## <a name="Сharapter-4">Глава 4. Взаимодействие с сервером</a>

Взаимодействие с сервером является одной из наиболее важных частей любого приложения. И хотя базовая реализация может быть выполнена в нескольких строках кода, она может быстро вырасти в сложный механизм, способный обрабатывать аутентификацию, кеширование, обработку ошибок, WebSockets и множество другого функционала и краевых случаев.

В онлайн-учебниках обычно уделяется мало времени на эту тему и предлагается использовать обычные обещания (promise) и _redux-thunk_ middleware, чтобы позволить action creator отправить action ( _dispatch()_ ) при получении данных. Однако, когда проект растет, становится ясно, что лучше всего иметь одно место для обработки аутентификации (установки пользовательских заголовков), обработки ошибок и функционала подобного кешированию. Учитывая это, мы должны иметь возможность обращаться к хранилищу (store) и отправлять (dispatch) асинхронные события, что является идеальной задачей для middleware.

Прежде чем читать эту главу, настоятельно рекомендуется прочитать главу [Middleware](#Сharapter-10).

### <a name="Using-Promises-in-Action-Creators">Использование обещаний (promise) в Action Creators</a>

Давайте начнем знакомство с серверным взаимодействием с реализации async action creators (создатели асинхронных действий), используя такие библиотеки как _redux-thunk_, что бы понять основные подводные камни этого подхода:

_Обещание в action creator_
```javascript
const fetchUser = id => (dispatch) =>
  fetch(`user/${id}`)
    .then(response => response.json())
    .then(userData => dispatch(setUserData(userData)))
    .catch(error => dispatch(apiError(error)));
```

Вы заметили, что мы обработали ошибку в _response.json()_ вместо API интерфейса _fetch()_?

С этим кодом есть несколько проблем:

1. Мы не увидим action в наших логах, прежде чем _fetch()_ завершится.
2. Каждый action creator должен иметь повторяющиеся функции для обработки ошибок и установки заголовков.
3. Тестирование становится сложнее, так как добавляются новые асинхронные действия.
4. Если вы хотите изменить стратегию связи с сервером (например, заменить _fetch()_ на WebSockets), вам нужно изменить несколько мест в коде.

Хранение как можно более простого и короткого кода, в духе Redux, проще, когда все action creator являются простыми функциями. Это облегчает их понимание, отладку и тестирование. Сохранность action creators "чистыми" от асинхронного когда означает перемещение их в другую часть стека. К счастью, у нас есть идеальный кандидат - middleware. Как мы увидим, используя этот подход, мы можем упростить action creator и генерировать action, который содержит всю информацию, необходимую для middleware, что бы выполнить запрос.

Здесь мы используем [Fetch API](#https://developer.mozilla.org/ru/docs/Web/API/Fetch_API) для доступа к серверу. Наш итоговый URL-адрес создается из константы, определяющей корень (например, «http://google.com/») и второй части URL-адреса, который мы хотим получить, переданный нам в объекте action.

### <a name="API-Middleware">API Middleware</a>

Наша цель - создать общую middleware, которая может обслуживать любой API запрос и требует только информации, переданной ой в действии. Простейшим решением является определение нового type в action, уникального для событий, связанных с API:

_Простое API middleware_
```javascript
const apiMiddleware = ({ dispatch }) => next => action => {
  if (action.type !== 'API') {
    return next(action);
  }
 
  // Обработка API кода
};
```

Наша middleware будет слушать все action c type 'API' и использовать информацию переданную ей в поле payload, что бы отправить запрос на сервер.

### <a name="Moving-Code-from-Action-Creators">Перемещение кода из action creator</a>

В исходном асинхронном примере для связи с сервером использовался следующий код:

_Обещание в action creator_
```javascript
const fetchUser = id => (dispatch) =>
  fetch(`user/${id}`)
    .then(response => response.json())
    .then(userData => dispatch(setUserData(userData)))
    .catch(error => dispatch(apiError(error)))
```

В этом коде есть несколько проблем, которые нам необходимо будет решить в нашем общем API:

* Как создать URL-адрес
* Какой HTTP запрос использовать (GET/POST или другие)
* Какой action отправится в случае успеха и в случае ошибки

Поскольку мы планируем передать всю эту информацию внутри нашего объекта action, мы можем ожидать, что соответствующий action creator передаст ему все эти необходимые параметры.

Проблема с построением URL адресов решается просто передав требуемый URL адрес в объект action (мы начнем только с GET запросов):

_Итоговый URL адрес_
```javascript
fetch(BASE_URL + action.url)
```
 
Чтобы сделать эти вещи более универсальными, action будет содержать только относительную часть полного URL адреса сервера. Это позволит нам легко установить различный _BASE_URL_ в процессе разработки и тестирования.

Обработка возвращаемого значения из вызова немного сложнее, так как нашей middleware необходимо выяснить, какой action нужно отправить (dispatch). Самое простое решение - передать следующий action внутри текущего. В нашем случае мы будем использовать соглашение Flux Standard Action (FSA) и поместим идентификатор следующего действия в ключ _success_ (а точнее - action.payload.success):

_Обработка результата_
```javascript
dispatch({ type: action.payload.success, response });
```

Объединение этих двух идей приводит к следующему базовому API middleware:

_Базовый API middleware_
```javascript
const apiMiddleware = ({ dispatch }) => next => action => {
  if (action.type !== 'API') {
    return next(action);
  }
 
  const { payload } = action; 
   
  fetch(BASE_URL + action.url)
     .then(response => response.json())
     .then(response => dispatch({ type: payload.success, response }));
};
```

### <a name="Using-the-API-Middleware">Использование API Middleware</a>

Чтобы использовать нашу middleware, нам нужно создать для него специальный объект действия:

_Пример action creator_
```javascript
import { API, SET_RECIPES } from 'constants/action-types';
 
const fetchRecipes = () => ({
  type: API,
  payload: {
    url: 'recipes.json',
    success: SET_RECIPES
  }
})
```

Наша middleware должна связаться с сервером и продолжить обычный поток приложения. Позднее, как только общение с сервером завершится, она должна отправить новый action в store:

_Конечный action отправленный после успешно завершенного вызова_
```javascript
{
  type: SET_RECIPES,
  payload: [ .. массив рецептов с сервера ..]
};
```

### <a name="Error-Handling">Обработка ошибок</a>

Наш текущий пример игнорирует любую обработку ошибок. Чтобы решить эту проблему, нам нужно расширить нашу middleware, чтобы отловить ошибки сервера и отправить необходимые события, когда они произойдут.

Обработка ошибок может быть выполнена несколькими способами:

* Отправить собственное сообщение об ошибке (основанное на данных в объекте action)
* Отправить общий action ошибки, который должен обрабатываться специальным reducer или другой middleware.
* Объединить оба подхода. Использовать №2, если №1 не было предоставлено.

Например, здесь мы используем FSA-совместимый action creator для отправки общего сообщения _apiError()_ при любом неудавшемся запросе сервера:

_Обработка API ошибок с общим обратным вызовом_
```javascript
const handleError = error => dispatch(apiError(error));
 
fetch(BASE_URL + action.url)
  .then(response => {
    if (response.status >= 300) {
      handleError(response.status);
    } else {
      response.json()
        .then(data => dispatch({ type: action.next, data }))
    }
  })
  .catch(handleError);
```

В качестве упражнения предлагаем вам самим добавить поддержку для action собственных сообщений об ошибке (способ для action creator указать, что ему нужно отправить другую ошибку, а не объект ошибки по умолчанию).

### <a name="Loading-Indicator">Индикатор загрузки</a>

Частый вопрос при использовании Redux заключается в том, как показать индикатор загрузки, когда выполняются запросы на сервер. Подход с использованием middleware решает этот вопрос использованием дополнительных вызовов _dispatch()_. Перед началом запроса или после его завершения мы можем отправить специальный action, которое должно быть пойман в reducer, ответственный за состояние пользовательского интерфейса. Здесь мы отправляем action _apiStart()_ перед началом любой связи с сервером и отправляем _apiDone()_ как на успешные, так и на неудавшиеся ответы сервера:

_Показываем и прячем индикатор загрузки_
```javascript
dispatch(apiStart());
 
fetch(BASE_URL + action.payload.url)
  .then(response => {
    dispatch(apiDone());
    // ...
  })
  .catch(error => {
    dispatch(apiDone());
    // ...
  })
}
```

Чтобы отслеживать выполняющиеся запросы, мы можем хранить счетчик в состоянии внутри контейнера _serverStatus_ или _ui_. Счетчик может использоваться пользовательским интерфейсом для отображения индикатора загрузки, если количество выполняющихся запросов больше нуля:

_Reducer пользовательского интерфейса для обработки счетчика запросов_
```javascript
const uiReducer = (state, action) => {
  switch (action.type) {
    case API_START:
      return Object.assign({}, state, { 
        requests: state.requests + 1 
      });
 
    case API_DONE:
      return Object.assign({}, state, { 
        requests: state.requests - 1 
      });
    }
};
```

### <a name="Dynamic-Action-Types">Динамические типы объекта action</a>

Основываясь на примере индикатора загрузки, мы можем обрабатывать несколько индикаторов для разных частей нашего приложения, используя множественные поддеревья в под-дереве состояния _ui_. К сожалению, это не работает с общими actions успеха/ошибки. 

Один из способов обработки множества ожидающих, успешных и неуспешных action - передать их в отправленном action:

_Action creator с пользовательским ожидаемым действием_
```javascript
const fetchRecipes = () => ({
  type: 'API',
  payload: { 
    url: 'recipes.json',
    pending: 'FETCH_RECIPES_PENDING',
    success: 'FETCH_RECIPES_SUCCEESS',
    error:   'FETCH_RECIPES_FAILURE'
  }
});
```

Этот метод позволяет нам обрабатывать различные типы action в разных reducer. Однако этот подход не гибок, принуждает к повторению кода и заставляет нас иметь несколько типов action, определенных для каждого отдельного action API.

Другой подход призывает указывать статус ответа сервера в отправленном action:

```javascript
dispatch({ type: FETCH_RECIPES, status: 'SUCCESS', response });
```

Это может выглядеть просто, поскольку вы можете повторно использовать одно действие в middleware, но этот подход приводит к тому, что reducer содержит больше информации и логики, что очень сильно затрудняет отладку и логирование (потому что мы получаем одни и те же типы action и правильно определить, какой из них имел определенный статус).

Третий подход заключается в создании динамических типов объекта action, которые будут следовать единому соглашению:

_constants/action-types.js_
```javascript
const asyncActionType = (type) => ({
  PENDING: `${type}_PENDING`,
  SUCCESS: `${type}_SUCCESS`,
  ERROR: `${type}_ERROR`,
});
 
export const LOGIN = asyncActionType('LOGIN');
export const FETCH_RECIPES = asyncActionType('FETCH_RECIPES');
```

При таком подходе мы можем использовать одну и ту же константу типа action для обработки трех случаев для асинхронных действий:

_reducers/recipes.js_
```javascript
import { FETCH_RECIPES } from 'constants/action-types';

const recipesReducer = (state, action) => {
  
  switch (action.type) {
    case FETCH_RECIPES_SUCCESS:
	  // Обработка успешного ответа
  
    case FETCH_RECIPES_ERROR:
	  // Обработка ошибки
    ...
  }
}
```

Поскольку наш API middleware уже проверяет _success_ и _panding_ в _action.payload_, action creators могут просто объединить все эти асинхронные action внутри payload: 

_API action creator с пользовательской обработкой статуса_
```javascript
const fetchRecipes = () => ({
  type: API,
  payload: Object.assign({ url: 'recipes' }, FETCH_RECIPES)
});
```

Результатом этого action creator будет следующий action:

_Action с пользовательской обработкой статуса_
```javascript
{
  type: 'API',
  payload: {
    url: 'recipes',
    PEDNING: 'RECIPES_PENDING',
    SUCCESS: 'RECIPES_SUCCESS',
    ERROR: 'RECIPES_ERROR'
  }
};
```

### <a name="Authentication">Аутентификация</a>

Распространенное место для хранения информации о текущем пользователе (например, токен доступа) находится в хранилище (store) Redux. Поскольку вся наша API логика теперь находится в одном месте, а middleware имеет полный доступ к хранилищу благодаря методу _getState()_, мы можем извлечь _accessToke_ из состояния и установить его как заголовок для наших запросов на сервер:

_Установка токена доступа_
```javascript
const { accessToken } = getState().currentUser;

if (accessToken) {
  // Устанавливаем заголовки
}
```

Все наши запросы на серверов теперь автоматически получат правильные заголовки, и мы не будем беспокоиться об этом в других частях нашего приложения.

### <a name="More-Extensions">Дополнительные расширения</a>

По-прежнему существует несколько вещей, которых не хватает в нашей middleware, что бы сделать её пригодной для использования в реальных приложениях. Нам нужна поддержка большего количества типов запросов (а не только GET), установка пользовательских заголовков, таймауты, кеширование и многое другое. Большинство из этого можно реализовать путем получения данных из объекта action или из самого хранилища. Надежное решение для этого уже реализовано в [redux-api-middleware](https://github.com/agraboso/redux-api-middleware).

### <a name="Chaining-APIs">Связывание API</a>

Иногда получение данных с сервера требует нескольких разных вызовов - например, когда возвращаемые данные из одного необходимы для других вызовов. Как пример можно привести получение данных о текущем пользователе, а затем, используя эти данные, получаем профиля этого пользователя. Если бы мы использовали обещания action creator, решение оказалось бы довольно простым:

_Связывание обещаний_
```javascript
const fetchCurrentUser = () => (dispatch) => fetch(`user`)
  .then(response => response.json())
  .then(userData => {
      dispatch(setUserData(userData));
 
      // Получаем профиль пользователя
      fetch(`profile/${userData.profileId}`)
        .then(response => response.json())
        .then(profileData => dispatch(setProfileData(profileData)));
    }
  );
};
```

С этим кодом есть несколько проблем:

* Обработка ошибок - отлов ошибок не очевиден и может сильно усложнится по мере роста цепочки.
* Отладка - трудно отлаживать и понимать, на каком шаге мы находимся.
* Отмена - почти невозможно отменить или прервать цепочку вызовов, если пользователь переходит к другой части пользовательского интерфейса, и текущая цепочка запросов больше не нужна.

Как мы видим, цепочка обещаний не является идеальным решением. При работе с Redux у нас есть еще две альтернативы для использования, middleware и saga.

#### Использование middleware

В рамках подхода использования middleware мы разделили код обработки сервера и логику потока. Наш API middleware останется таким же, и нам необходимо найти другое место, что бы внедрить туда логику потока вызовов. Один из подходов, обсуждаемый в главе [Middleware](#Сharapter-10), заключается в создании дополнительной middleware для управления потоком:

_Пример middleware для обработки потока пользователей_
```javascript
const userFlowMiddleware = ({ dispatch }) => next => action => {
  switch (action.type) {
    case FETCH_CURRENT_USER:
      dispatch(fetchCurrentUser());
      break;
    case SET_CURRENT_USER:
      dispatch(fetchProfile(action.payload.userId));
      break;
  };

  next(action);
}
```

К сожалению, этот подход также имеет свои проблемы. Он приведет к тому, что action _fetchProfile()_ будет отправляться каждый раз, когда кто-то отправляет _SET_CURRENT_USER_. Там может быть поток, в котором не нужно получать данные о профиле пользователя, но мы не можем это предотвратить.

Мы можем решить эту проблему, создав специальный поток действий, который имеет аналогичное поведение с _fetchCurrentUser()_, но также запускает действие _fetchProfile()_. Это можно осуществить создав новый action creator и action:

_Обработка потока с особым action_
```javascript
const fetchCurrentUser = (next = SET_CURRENT_USER) => ({
  type: API,
  url: 'user',
  next
});

const userFlowMiddleware = ({ dispatch }) => next => action => {
  switch (action.type) {
    case FETCH_CURRENT_USER:
      dispatch(fetchCurrentUser(SPECIAL_SET_CURRENT_USER));
      break;

    case SPECIAL_SET_CURRENT_USER:
     dispatch(setCurrentUser(action.payload)); 
     dispatch(fetchProfile(action.payload.userId));
     break;
  };

  next(action);
}
```

Такой подход требует изменения нашего action creator весьма неявным способом. Хотя он будет работать, он может вызвать ошибки, если мы забудем выпустить обычный вызов _getCurrentUser()_ из нашего специального обработчика действий. С другой стороны, это будет намного легче отлаживать, поскольку ясно, какой тип запроса мы выполняем.

Более чистый подход состоял бы в том, чтобы позволить нашим async action creator (создателям синхронных действий) передать массив действий, на которые middleware должна выполнить _dispatch()_, когда запрос завершен успешно:

_Action creator, который позволяет выполнить множество обратных вызовов_
```javascript
const fetchCurrentUser = (extraActions = []) => ({
  type: API,
  payload: {
    url: 'user',
    success: extraActions.concat(SET_CURRENT_USER)   
  }
});
```

_API middleware с поддержкой множества обратных вызовов_
```javascript
const notify = (data) => {
  action.next.each(type => dispatch({ type, data });
};

fetch(`user/${id}`)
  .then(response => response.json())
  .then(notify)
  .catch(error => dispatch(apiError(error)));
```

Эта новая реализация позволит нам остановить поток middleware:

_Обработка потока с множеством action_
```javascript
const userFlowMiddleware = ({ dispatch }) => next => action => {
  switch (action.type) {
    case FETCH_CURRENT_USER:
      dispatch(fetchCurrentUser(FETCH_PROFILE));
      break;
  
    case FETCH_PROFILE:
     dispatch(fetchProfile(action.payload.userId));
     break;
  };
  
  next(action);
}
```

Этот подход позволяет нам получить текущего пользователя с обновлением профиля или без обновления:

```javascript
// Получить данные о пользователе
dispatch(fetchCurrentUser());
 
// Получить данные о пользователе и обновить профиль
dispatch(fetchCurrentUser(FETCH_PROFILE));
```

Существует ряд предложений по обработке потока в главе [Middleware](#Сharapter-10), которая может упростить управление этим потоком, например, с помощью sagas.

#### Использование Sagas для управления потоком

Более чистый подход к управлению потоком - использование [redux-saga](https://github.com/redux-saga/redux-saga). Эта библиотека позволяет нам создавать сложные асинхронные решения для управления потоками, используя саги и эффекты. По сути, он использует специальную middleware, для добавления нового элемента в мир Redux.

Хотя Redux-saga подробно не рассматриваются в этой книге, мы приведем простой пример использования sagas для управления потоком:

_Использование redux saga для контроля потока_
```javascript
import { call, put } from 'redux-saga/effects'

export function *fetchCurrentUser() {
  while (true) {
    yield take(FETCH_CURRENT_USER);
  
    const action = yield take(SET_CURRENT_USER);
  
    yield put(fetchProfile(action.payload.userId));
  }
};
```

В этом примере у нас есть бесконечный цикл, ожидающий отправки действия _FETCH_CURRENT_USER_. Когда это происходит, код начинает ожидание соответствующего действия _SET_CURRENT_USER_. Payload может использоваться для отправки действия из _fetchProfile()_ для получения соответствующего профиля с сервера.

Это очень простой пример использования саги, он не обрабатывает ошибки и не позволяет отменить запросы потоков. Для получения дополнительной информации о сагах, проконсультируйтесь с обширной документацией на [официальном сайте документации по redux-saga](https://redux-saga.js.org/index.html).

### <a name="Canceling-API-Requests">Отмена API запросов</a>

Во время обработки потока приложения мы можем открыть несколько долгих запросов, которые нам нужно отменить (например, когда пользователь переходит на другую страницу приложения). Некоторые реализации обещаний поддерживают эту функцию, но она также вполне реализуема с помощью подхода API middleware.

Чтобы разрешить отмену, нам нужно предоставить уникальный идентификатор каждому отправляемому запросу и сохранить его для фазы отмены. Для этого нам необходимом добавить поддержку добавления ID к нашим action creator.

_Action creator с поддержкой ID_
```javascript
const fetchUser = (id, cancelable) => ({
  type: API,
  url: `user/${id}`,
  next: SET_USER,
  cancelable
});
 
const actionId = uuid.generate();
dispatch(fetchUser(100, actionId));
```

В этом коде мы использовали несуществующую функцию _uuid.generate()_. Существует множество реализаций подобной функции, самая простая из них - обычный глобальный счетчик.

Если позднее нам понадобится отменить конкретный API запрос, нам нужно будет отправить специальный action нашей middleware с указанием ID этого API запроса:

_Action для отмены API запроса_
```javascript
const cancelAPI = (id) => ({
  type: CANCEL_API,
  id
});
```

Что бы обработать этот action в нашей middleware, мы должны либо отменить общение (при использовании реализаций, поддерживающих эту возможность), либо позволить этому запросу завершиться и проигнорировать ответ:

_API middleware с поддержкой отмены запроса_
```javascript
const canceled = {};
 
const apiMiddleware = ({ dispatch }) => next => action => {
 
  const handleResponse = (data) => {
    if (action.cancelable && canceled[action.cancelable]) {
      return;
    }
   
    dispatch({ type: action.next, data });
  };
 
  switch (action.type) {
    case API: 
      fetch(BASE_URL + action.url)
        .then(response => response.json())
        .then(handleResponse);
    return;
   
   case CANCEL_API:
     canceled[action.id] = true;
     setTimeout(() => delete canceled[action.id], 5000);
 }
 
 return next(action);
};
```

Чтобы реализовать эту функциональность, мы просто добавили объект с ключами, соответствующими отмененным запросам. Функция _setTimeout()_ удялаяет ID ненужных запросов через 5 секунд, чтобы предотвратить ненужное заполнение объекта.

С помощью этой функции мы можем в любое время отменить запросы и не нужно беспокоиться о завершении запроса после ухода пользователя на другую страницу или после завершения более долгого запроса (например, два последовательных запроса фильтра для отправки данных и первый возвращается позднее второго).

### <a name="Summary-4">Подведем итоги</a>

В этой главе мы узнали, как создать всеобъемлющий механизм для связи с сервером. Мы использовали Redux концепцию middleware для перемещения большей части сложной и асинхронной логики из наших action creator и создали единое место, где можно сконфигурировать обработку ошибок, кеширование и другие аспекты запросов сервера.

В следующей главе мы рассмотрим коммуникацию с сервером на основе WebSocket и узнаем как с этим работать на архитектурой Redux.
