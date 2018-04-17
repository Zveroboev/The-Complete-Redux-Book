## <a name="Сharapter-2">Глава 2. Ваше первое Redux приложение</a>

В прошлой главе мы узнали что такое Redux и как он работает. В этой главе мы узнаем как использовать его с небольшим проектом. База кода, созданная в этой главе, будет использоваться в качестве основы для всех примеров в остальной части этой книги. Настоятельно рекомендуется полностью понять и разобрать эту главу, прежде чем перейти к более продвинутым темам.

### <a name="Starter-Project">Стартовый проект</a>

Современные клиентские приложения часто требуют набора так называемых шаблонов, чтобы упростить разработку. В состав шаблона могут входить такие элементы, как структура каталогов, инструменты преобразования кода (такие как компиляторы SCSS и ES2016), инфраструктура тестирования и средства для создания автоматизации таких задач, как минимизация, сжатие и конкатенация.

Чтобы облегчить работу по созданию нового проекта, open-source сообщество создало десятки различных стартовых проектов. Самые большие из них, например [react-redux-starter-kit](https://github.com/davezuko/react-redux-starter-kit), состоят из более чем ста файлов. Мы будем использовать гораздо более простой шаблон, но его будет достаточно для того, чтобы охватить все концепции, описанные в данной книге.

Поскольку наш проект будет на чистом Redux, нам не потребуется React и другие библиотеки. Мы будем использовать [Webpack](https://webpack.js.org/) в качестве нашего основного инструмента для обработки всех задач преобразования кода.

#### Обзор шаблона

Чтобы начать работу, давайте клонируем стартовый шаблон, установим необходимые пакеты и убедимся, что наша среда разработки готова:

_Настройка стартового шаблона_
```bash
git clone http://github.com/redux-book/starter
cd starter
npm install
npm start
```

Если все прошло успешно, вы должны получить доступ к [http://localhost:8080](http://localhost:8080), увидеть там страницу “A simple Redux starter” и запущенный счетчик. Если вы откроете JavaScript консоль в инструментах разработчика, вы также увидите вывод «Redux start». Наш проект готов!

Настало время открыть редактор кода и пройтись по пяти файлам, которые, в настоящее время, составляют проект:

1. _.gitignore_ - Список шаблонов имен файлов, которые будет игнорировать Git при управлении нашим репозиторием.
2. _package.json_ - Список используемых пакетов и общая информация о проекте.
3. _webpack.config.js_ - Настройки Webpack.
4. _app/index.html_ - Главный HTML файл, входная точка нашего проекта.
5. _app/app.js_ - Входная точка нашего JavaScript кода.
6. _app/assets/stylesheets/main.css_ - Некоторые базовые CSS стили для проекта.

**.gitignore**

Это специальный файл конфигурации для системы контроля версий Git, этот файл указывает Git, какие файлы и каталоги не им управляться не должны (например, node_modules).

**package.json**

Хотя большинство полей в этом файле не имеют значения в данный момент, важно отметить два раздела: _devDependencies_ и _dependencies_. Первый - это список всех инструментов, необходимых для создания проекта. В настоящее время он включает в себя только _webpack-tools_ и Babel transpiler, необходимый для преобразования ES2016. В разделе _dependencies_ перечислены все пакеты, которые будут связаны с нашим приложением. Он включает только сам Redux.

**webpack.config.js**

Это основной файл конфигурации Webpack. Этот файл настроек указывает Webpack, как связать инструменты разработки, как выстраивать зависимости и содержит большую часть конфигурации нашего проекта. В нашем простом проекте есть только один файл настроек (более крупные проекты могут иметь более подробные файлы для тестирования, разработки, сборки и так далее). Наш файл webpack.config.js настраивает Babel для перевода ES2016 в ES5 и определяет точку входа нашего приложения.

**index.html / app.js**

Одностраничные приложения, в отличие от своих двоюродных братьев, имеют одну точку входа. В нашем проекте, каждая часть и страница приложения будут отображаться начиная с _index.html_, а весь код связанный с JavaScript бдует находится в _app.js_.

### <a name="Our-First-Application">Наше первое приложение</a>

Чтобы узнать, как использовать разные части Redux, мы создадим приложение "Книга рецептов". Оно сможет добавлять рецепты и ингредиенты для каждого рецепта, а так же будет получать первоначальный список рецептов с удаленного сервера. В соответствии с принципами Redux, приложение будет хранить все свое состояние в нашем глобальном store, включая некоторые части пользовательского интерфейса.

Первым шагом для любого приложением на основе Redux является планирование того, как данные будут храниться в store. Наш объект рецепта для начала будет содержать только имя рецепта (при необходимости мы добавим больше полей). Чтобы сохранить текущий список, мы можем использовать обычный массив:

_Простое состояние_
```javascript
recipes = [
  { name: 'Omelette' },
  ...
];
```

Ингредиенты для каждого рецепта будут содержать _название (name)_ и _количество (quantity)_. Добавление их в состояние (state) нашего приложения станет более сложной задачей. Для этого есть три общих подхода.

Подход _вложенные объекты (nested objects)_ заключается в том, чтобы удерживать ингредиенты в виде массива внутри самого рецепта:

_Состояние со вложенными объектами (Nested objects state)_
```javascript
state = {
  recipes: [
    {
      name: 'omelette',
      ingredients: [
        {
          name: 'eggs',
          quantity: 2
        }
      ]
    },
    ...
  ]
};
```

Подход _вложенные ссылки (nested reference)_ заключается в том, чтобы хранить информацию о ингредиенте рецепта непосредственно в state, а каждом из рецептов хранить массив с ID нужных ингредиентов:

_Состояние со вложенными ссылками (Nested reference state)_
```javascript
state = {
  recipes: [
    {
      name: 'omelette',
      ingredients: [2, 3]
    }
  ],
  ingredients: {
    2: {
      name: 'eggs',
      quantity: 2
    },
    3: {
      name: 'milk',
      quantity: 1
    }
  }
};
```

Подход _Отдельные объекты (separate object)_ заключается в том, чтобы хранить ингредиенты в состоянии (state) в виде отдельного массива, а внутри него поместить ID рецепта, который на него ссылается.

_Состояние с отдельными объектами (Separate objects state)_
```javascript
state = {
  recipes: [
    {
      id: 10,
      name: 'omelette'
    }
  ],
  ingredients: [
    {
      recipe_id: 10,
      name: 'eggs',
      quantity: 2
    },
    {
      recipe_id: 10,
      name: 'milk',
      quantity: 1
    }
  ]
};    
```

Хотя все подходы имеют свои преимущества и недостатки, мы быстро обнаружим, что в Redux, сохранение структуры в более "плоском" виде (как во втором и третьем примерах), сделает код более чистым и простым. Структура state подразумевает использование двух отдельных reducers для рецептов и ингредиентов. Мы можем обрабатывать их независимо.

Самая большая разница между вторым и третьим способом заключается в том, как определяется ссылка (кто на какой ID ссылается). Во втором примере добавление ингредиента потребует обновления в двух разных частях состояния (state) - как в рецептах, так и поддеревах ингредиентов - в то время как в третьем подходе мы всегда можем обновить только одну часть дерева. В нашем примере мы будем использовать этот метод.

Тема управления состоянием подробно разбирается в главе «[Управление состоянием](#Сharapter-3)» в Части 2.

### <a name="Setting-Up-the-Store">Настройка Store</a>

Мы начнем с создания хранилища (store). В Redux существует только одно хранилище, которое создается и инициализируется методом _createStore()_. Давайте откроем наш файл _index.js_ и создадим его:

_Создание хранилища (store) Redux_
```javascript
import { createStore } from 'redux';
 
const reducer = (state, action) => state;
const store = createStore(reducer);
```

Функция _createStore()_ может принимать ряд параметров, но обязательный только один - reducer. В нашем примере reducer просто возвращает одно и то же состояние независимо от действия.

Мы можем сделать и более "интересные" вещи - передадим начальное состояние (state) в наше хранилище (store). Это полезно для обучения, но в реальном приложении использование этой функции, в основном, связано с рендерингом сервера. Вы предварительно рассчитываете состояние приложения на сервере, а затем можете создать store на клиенте c этим предварительно рассчитанным состоянием.

_Создание хранилища с изначальным состоянием_
```javascript
const initialState = {
  recipes: [
    {
      name: 'Omelette'
    }
  ],
  ingredients: [
    {
      recipe: 'Omelette',
      name: 'Egg',
      quantity: 2
    }
  ]
};
 
const reducer = (state, action) => state;
const store = createStore(reducer, initialState);
 
window.store = store;
```

В последней строке мы делаем наше хранилище (store) доступным везде, помещая его в глобальный объект _window_. Если мы перейдем к консоли JavaScript, мы можем попробовать поиграться с этим:

_Попытка использования API в консоли_
```javascript
store.getState()
// Object {recipes: Array[1], ingredients: Array[1]}
  
store.subscribe(() => console.log("Store changed"));
  
store.dispatch({ type: 'ACTION' });
// Store изменен
```

Как вы можете видеть, мы можем использовать объект store для доступа к текущему состоянию (state) с помощью _getState()_, подписаться на получение уведомлений о изменениях в хранилище (store) с помощью _subscribe()_ и отправлять действия (actions) с помощью _dispatch()_.

### <a name="Adding-Recipes">Добавление рецептов</a>

Чтобы реализовать добавление рецептов, нам нужно найти способ изменить наш store. Как мы узнали в предыдущей главе, изменять store могут только reducer в ответ на action. Это означает, что нам нужно определить структуру действия (action) и изменить наш (очень скудный) reducer, чтобы поддержать это действие (action).

Действия (actions) в Redux - это не что иное, как простые объекты, обладающие обязательным свойством _type_. Мы будем использовать строки, чтобы дать имя нашему action, причем наиболее подходящим в этом случае будет 'ADD_RECIPE'. Поскольку у рецепта есть название, мы добавим его к данным action:

_Отправка объекта Redux_
```javascript
store.dispatch({ type: 'ADD_RECIPE', name: 'Pancake' });
```

Давайте изменим наш reducer, чтобы поддержать новое действие (action). Самый простой подход может оказаться следующим:

_Reducer, который поддерживает ADD_RECIPE_
```javascript
const reducer = (state, action) => {
  switch (action.type) {
    case 'ADD_RECIPE':
      state.recipes.push({ name: action.name });
  }
 
  return state;
};
```

Хотя это и выглядит верно (и даже работает), этот код нарушает основной принцип Redux - _store неизменяемый (immutability)_. Наш reducer _никогда не должен менять_ state, он должен создавать его новую копию с нужными изменениями. Таким образом, код нашего reducer необходимо изменить:

_Правильный способ создания reducer_
```javascript
const reducer = (state, action) => {
  switch (action.type) {
    case 'ADD_RECIPE':
      return Object.assign({}, state, {
        recipes: state.recipes.concat({ name: action.name })
      });
  }
 
  return state;
};
```

case 'ADD_RECIPE' стал более сложный, но работает в точности так, как мы хотим. Мы используем метод _Object.assign()_ для создания нового объекта, который не только будет иметь все ключи/значения из нашего прошлого состояния (state), но и  перезапишет ключ _recipes_ с новым значением. Чтобы вычислить список новых рецептов, мы используем _concat()_ вместо _push()_, так как _push()_ изменяет исходный массив, в то время как _concat()_ создает новый массив, содержащий все исходные значения и одно новое.

Больше информации о методе _Object.assign()_ доступно в главе [Reducers](#Сharapter-5).

### <a name="Adding-Ingredients">Добавление ингредиентов</a>

Подобно добавлению рецептов, этот шаг потребует, чтобы мы снова модифицировали reducer. Добавим ему возможность добавления ингредиентов:

_Добавляем ADD_INGREDIENT в reducer_
```javascript
const reducer = (state, action) => {
  switch (action.type) {
    case 'ADD_RECIPE':
      return Object.assign({}, state, {
        recipes: state.recipes.concat({ name: action.name })
      });
 
    case 'ADD_INGREDIENT':
      const newIngredient = {
        name: action.name,
        recipe: action.recipe,
        quantity: action.quantity
      };
      return Object.assign({}, state, {
        ingredients: state.ingredients.concat(newIngredient)
      });
   }
 
  return state;
};
```

Одна из проблем, с которой вы можете столкнуться при отправке действий из консоли для тестирования store, заключается в том, что трудно запомнить свойства, которые необходимо передать в объекте действия (action). Это одна из причин почему в Redux мы используем идею _action creators_: функции, которые создают для нас объект действия.

_Функция создания объекта action_
```javascript
const addIngredient = (recipe, name, quantity) => ({
  type: 'ADD_INGREDIENT', recipe, name, quantity
});
 
store.dispatch(addIngredient('Omelette', 'Eggs', 3));
```

Эта функция скрывает структуру action от пользователя и позволяет нам изменять action, устанавливать значения по умолчанию для свойств, обрезать имена и многое другое.

Для получения более подробной информации о action creators обратитесь к главе [Actions и Action Creators](#Сharapter-8)

### <a name="Structuring-the-Code">Структурирование кода</a>

Очевидно, что весь наш код в одном файле - плохая идея. Обычно в Redux структура каталогов соответствует именам его сущностей. Reducers помещаются в каталог _reducers_, а основной reducer (обычно называемый корневым) помещается в файл _root.js_. Action creators находятся в директории _actions_, разделенные по типу объекта или данных, которые они обрабатывают - в нашем случае _actions/recipes.js_ и _actions/ingredients.js_. Поскольку у нас есть только один store, мы можем поместить весь его код в один файл: _store/store.js_.

После всех изменений файл index.js должен выглядеть следующим образом:

_index.js_
```javascript
import store from './store/store';
import { addRecipe } from './actions/recipes';
import { addIngredient } from './actions/ingredients';

store.dispatch(addRecipe('Pancake'));
store.dispatch(addIngredient('Pancake', 'Eggs', 3));

window.store = store;
```

### <a name="A-Closer-Look-at-Reducers">Подробней о Reducer</a>

Если вы откроете _reducers/root.js_, вы увидите что этот reducer обрабатывает разные части нашего дерева состояния. По мере того как наше приложение будет расти, к рецептам и поддеревам ингредиентов добавятся больше свойств. Поскольку код в обоих обработчиках не зависит друг от друга, мы можем разделить его на три редуктора, каждый из которых отвечает за другую часть состояния:

_Многофункциональный reducer_
```javascript
const recipesReducer = (recipes, action) => {
  switch (action.type) {
    case 'ADD_RECIPE':
      return recipes.concat({name: action.name});
  }
 
  return recipes;
};
 
const ingredientsReducer = (ingredients, action) => { … }
 
const rootReducer = (state, action) => {
  return Object.assign({}, state, {
    recipes: recipesReducer(state.recipes, action),
    ingredients: ingredientsReducer(state.ingredients, action)
  });
};
```

В таком подходе есть три основных преимущества. Во-первых, наш корневой reducer теперь очень простой. Все что он делает, это создает новый объект состояния (state), комбинируя старое состояние и результат каждого reducer. Во-вторых, наш reducer по обработке рецептов стал намного проще, поскольку он должен обрабатывать только часть нашего state. И самое главное, наш корневой reducer. Reducer ингредиентов, рецептов и любой другой, который мы можем создать в дальнейшем не должны ничего знать заботиться о внутренней структуре друг друга. Таким образом, изменение какого-то рецепта будет влиять только на часть этого поддерева состояния. Побочным эффектом этого является то, что мы можем сказать каждому reducer, как инициализировать его собственное поддерево, используя параметры по умолчанию из ES2016:

_Reducer для рецептов_
```javascript
const recipesReducer = (recipes = [], action) => { ... };
```

Обратите внимание на значение по умолчанию `[]` для _рецептов (recipes)_.

Поскольку объединение нескольких reducer является очень распространенной схемой, Redux имеет специальную функцию _combineReducers()_, которая занимается именно тем, что и делает наш корневой reducer:

_Объединение нескольких reducer_
```javascript
export default combineReducers({
  recipes: recipesReducer,
  ingredients: ingredientsReducer
});
```

Здесь мы создали корневой reducer, в котором используются два других reducer, один из которых находится в поддереве рецептов, а другой - в поддереве ингредиентов. Настало время разделить наши reducer на два отдельных файла _reducers/recipes.js_ и _reducers/ingredients.js_.

### <a name="Handling-Typos-and-Duplicates">Обработка опечаток и дубликатов</a>

Прежде чем двигаться дальше, нам нужно внести последнее изменение в наш код, чтобы исправить что-то, что может быть не очевидной проблемой прямо сейчас. Мы использовали такие строки, как `'ADD_RECIPE'` в наших actions и reducers, но нигде не проверяли, что они совпадают. В больших приложениях это часто приводит к ошибкам, которые очень трудно отлаживать, поскольку опечатка в action creator заставит reducer игнорировать action. Или, что еще хуже, два разработчика могут ошибочно использовать одну и ту же строку, что приведет к очень странным побочным эффектам, поскольку reducer будут непреднамеренно обрабатывать отправленные action.

Чтобы исправить эти проблемы, мы можем использовать встроенную поддержку _констант (const)_ ES2016, которая гарантирует, что мы не сможем определить одну и ту же константу дважды в одном файле. Это отловит дублирование имен еще на этапе компиляции, даже до того, как наш код достигнет браузера.

Давайте создадим новый файл _constants/action-types.js_, который будет содержать все константы для ключа type у action в нашем приложении:

_constants/action-types.js_
```javascript
export const ADD_RECIPE = 'ADD_RECIPE';
export const ADD_INGREDIENT = 'ADD_INGREDIENT';
```

Теперь в наших reducers и action creators мы будем использовать константы вместо строк:

_Использование констант_
```javascript
import { ADD_RECIPE } from 'constants/action-types';
 
const recipesReducer = (recipes = [], action) => {
  switch (action.type) {
    case ADD_RECIPE:
      …
```

### <a name="Simple-UI">Простой пользовательский интерфейс</a>

Что бы разобрать как можно связать пользовательский интерфейс и Redux мы будем использовать немного магии jQuery. Обратите внимание, что этот пример очень прост и никогда не должен использоваться в реальном приложении. Он должен дать общее представление о том, как «реальные» приложения взаимодействуют с Redux.

Давайте сохраним нам текущий пользовательский интерфейс в _ui/jquery/index.js_. Он создаст простое отображение текущих рецептов из хранилища (store):

_ui/jquery/index.js_
```javascript
import $ from 'jquery';
import store from 'store/store';
 
function updateUI() {
  const { recipes } = store.getState();
  const renderRecipe = (recipe) => `<li>${ recipe.name }</li>`;
 
  $('.recipes > ul').html(recipes.map(renderRecipe));
}
 
export default function loadUI() {
  $('#app').append(`
    <div class="recipes">
      <h2>Recipes:</h2>
      <ul></ul>
    </div>
  `);
  
  updateUI();
}
```

Мы используем jQuery метод _append()_ для добавления нового div в контейнер нашего приложения и используем функцию _updateUI()_, чтобы вытащить список рецептов из нашего store и отобразить их как список неупорядоченных элементов.

Чтобы наш пользовательский интерфейс отвечал на обновления, мы можем просто зарегистрировать функцию _updateUI()_ в нашем store, внутри _loadUI()_:

_Зарегистрировать updateUI в store_
```javascript
store.subscribe(updateUI);
```

Чтобы поддерживать добавление рецептов, мы добавим простой `input` и `button`, используем метод _dispatch()_ нашего store вместе с action creator _addRecipe()_, чтобы отправить action в store:

_Добавим поддержку событий click_
```javascript
import $ from 'jquery';
import store from 'store/store';
import { addRecipe } from 'actions/recipes';
 
function updateUI() {
  const { recipes } = store.getState();
  const renderRecipe = (recipe) => `<li>${ recipe.name }</li>`;
 
  $('.recipes > ul').html(recipes.map(renderRecipe));
}
 
function handleAdd() {
  const $recipeName = $('.recipes > input');
 
  store.dispatch(addRecipe($recipeName.val()));
 
  $recipeName.val('');
}
 
export default function loadUI() {
  $('#app').append(`
    <div class="recipes">
      <h2>Recipes:</h2>
      <ul></ul>
      <input type="text" />
      <button>Add</button>
    </div>
  `);
 
  store.subscribe(updateUI);
 
  $(document).on('click', '.recipes > button', handleAdd);
 
  updateUI();
}
```

### <a name="Logging">Логирование</a>

Теперь, когда наш пользовательский интерфейс позволяет нам добавлять новые рецепты, мы обнаружили, что нам трудно понять какие actions отправляются в store. Как вариант можно логировать логировать actions из корневого reducer, но, как мы вскоре увидим, это может быть проблематично. Другим вариантом является использование _middleware_, о которой мы говорили в предыдущей главе.

В store содержится подключение ко всем middleware и они получают action раньше чем reducer. Это означает, что они имеют доступ к любым action, отправленным в store. Чтобы проверить это, давайте создадим простую логирующую middleware, которая будет выводить в консоль любые действия, отправленные в store:

_Простая логирующая middleware_
```javascript
const logMiddleware = ({ getState, dispatch }) => (next) => (action) => {
  console.log(`Action: ${ action.type }`);
 
  next(action);
};
 
export default logMiddleware;
```

По началу эта структура может показаться странной, так как мы создаем функцию, которая возвращает функцию, которая возвращает функцию. Хотя это может немного сбивать с толку, но это необходимо для того, чтобы Redux мог объединить все middleware. На практике, внутри самой функции, мы имеем доступ к методам хранилища (store) _dispatch()_ и _getState()_, текущему обрабатываемому action и методу _next()_, который позволяет нам вызвать следующую по порядку middleware.

Наш логер выводит в консль текущий action, а затем вызывает _next(action)_, чтобы передать action следующей middleware. В некоторых случаях middleware может подавлять action или изменять его. Поэтому внедрение логера в reducer не является жизнеспособным решением - некоторые из action могут не дойти до него.

Для подключения middleware к нашему store, нам необходимо изменить файл _store/store.js_. Используем встроенную в Redux функцию _applyMiddleware()_:

_Подключение middleware к store_
```javascript
import { createStore, applyMiddleware } from 'redux';
import rootReducers from 'reducers/root';
import logMiddleware from 'middleware/log';

const initialState = { ... };

export default createStore(
  rootReducers,
  initialState,
  applyMiddleware(logMiddleware)
);
```

### <a name="Getting-Data-from-the-Server">Получение данных с сервера</a>

Получение данных с сервера, как и все в Redux, происходит в результате отправленного action. В нашем случае пользовательский интерфейс должен отправить action когда он загружается, чтобы попросить Redux запросить данные в store. Для этого мы должны добавить новую константу в _constants/action-types.js_ и новый  action creator в _actions/recipes.js_. Наш action будет называться `'FETCH_RECIPES'`.

К сожалению, мы не можем обработать action внутри reducer, посколько action требует ответа от сервера, а это может занять некоторое время. Наш reducer не сможет обработать ответ, он должен сразу же вернуть модифицированное состояние.

К счастью, у нас есть middleware, которые имеют доступ к store и , следовательно, к его методу _dispatch()_. Это значит, что мы можем поймать action в middleware, отправить Ajax запрос и затем отправить новый action в reducer, c полученными данными внутри.

Вот простое API для middleware, которое слушает `'FETCH_RECIPES'` и отправляет `'SET_RECIPES'`, когда получает данные:

_API middleware_
```javascript
import { FETCH_RECIPES } from 'constants/action-types';
import { setRecipes } from 'actions/recipes';
 
const URL = 'https://s3.amazonaws.com/500tech-shared/db.json';
 
function fetchData(url, callback) {
  fetch(url)
    .then((response) => {
      if (response.status !== 200) {
        console.log(`Error fetching recipes: ${ response.status }`);
      } else {
        response.json().then(callback);
      }
    })
    .catch((err) => console.log(`Error fetching recipes: ${ err }`))
}
 
const apiMiddleware = ({ dispatch }) => next => action => {
  if (action.type === FETCH_RECIPES) {
    fetchData(URL, data => dispatch(setRecipes(data)));
  }
 
  next(action);
};
 
export default apiMiddleware;
```

Главное в коде нашей middleware - это простой оператор _if_, который вызывает функцию _fetchData()_ и передает ему обратный вызов (callback). Этот callback вызывает функцию _dispatch_, в которую передает _setRecipes()_ с возвращенными данными:

_Ловим API запроса_
```javascript
if (action.type === FETCH_RECIPES) {
  fetchData(URL, data => store.dispatch(setRecipes(data)));
}
```

Функция _fetchData()_ является универсальной для всех действий, где необходим запрос на сервер.

Что бы заставить эту middleware работать, нам необходимо добавить её в наш store.

_Добавляем middleware в store_
```javascript
import { createStore, applyMiddleware } from 'redux';
import rootReducers from 'reducers/root';
import logMiddleware from 'middleware/log';
import apiMiddleware from 'middleware/api';
 
const initialState = { … };
 
export default createStore(
  rootReducers,
  initialState,
  applyMiddleware(logMiddleware, apiMiddleware)
);
```

Нам так же нужно изменить файл _reducers/recipes.js_ для поддержки нового action `'SET_RECIPES'`:

_Добавляем поддержку SET_RECIPES в reducer_
```javascript
import { ADD_RECIPE, SET_RECIPES } from 'constants/action-types';
 
const recipesReducer = (recipes = [], action) => {
  switch (action.type) {
    case ADD_RECIPE:
      return recipes.concat({name: action.name});
 
    case SET_RECIPES:
      return action.data.recipes;
  }
 
  return recipes;
};
 
export default recipesReducer;
```

Код в reducer на удивление прост. Поскольку мы получаем новый список рецептов с сервера, мы можем просто вернуть его:

_Простая реализация SET_RECIPES_
```javascript
case SET_RECIPES:
  return action.data.recipes;
```

Наконец, мы можем удалить _начальное состояние (initialState)_, которое мы передали в наш store, так как мы будем получать эти данные с сервера. Каждый reducer имеет значения по умолчанию для своих поддеревьев (помните `recipes = []` выше?) и они будут автоматически создавать начальное состояние. Эта магия объясняется в главе [Reducers](#Сharapter-9).

Это наш новый _store/store.js_:

_store/store.js_
```javascript
import { createStore, applyMiddleware } from 'redux';
import rootReducers from 'reducers/root';
import logMiddleware from 'middleware/log';
import apiMiddleware from 'middleware/api';
 
export default createStore(
  rootReducers,
  applyMiddleware(logMiddleware, apiMiddleware)
);
```

В реальном приложении API middleware будет более общим и надежным. Более подробно рассмотрим в главе [Middleware](#Сharapter-10).

### <a name="Summary-2">Подведем итоги</a>

В этой главе мы создали простое Redux приложение, которое поддерживает множественные reducer, middleware и action creators. Мы установили доступ к серверу и создали минимальный пользовательский интерфейс, используя jQuery. В [Git репозитории](https://github.com/redux-book) этой книги вы можете найти полный исходный код для этого примера, включая отсутствующие части (например, пользовательский интерфейс ингредиентов).