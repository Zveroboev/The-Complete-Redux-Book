# Перевод книги [The Complete Redux Book](https://leanpub.com/redux-book) от [Ilya Gelman](https://leanpub.com/u/ilyagelman) и [Boris Dinkevich](https://leanpub.com/u/borisdinkevich)

Перевод книги от 31-01-2017. Переведено и опубликовано с разрешения правообладателей.

## Оглавление
* [Часть 1. Введение в Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%A7%D0%B0%D1%81%D1%82%D1%8C-1-%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B2-redux)
    * [Глава 1. Основные понятия Flux и Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-1-%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%B8%D1%8F-flux-%D0%B8-redux)
        * [Что такое Flux?](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%A7%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-flux)
        * [Redux и Flux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#redux-%D0%B8-flux)
        * [Redux Терминология](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#redux-%D0%A2%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F)
        * [Общие понятия](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%9E%D0%B1%D1%89%D0%B8%D0%B5-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%B8%D1%8F)
        * [Redux и React](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#redux-%D0%B8-react)
        * [Основная реализация Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D0%B0%D1%8F-%D1%80%D0%B5%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F-redux)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part1/charapter-1.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
    * [Глава 2. Ваше первое Redux приложение](#Сharapter-2) 
        * [Стартовый проект](#Starter-Project)
        * [Наше первое приложение](#Our-First-Application)
        * [Настройка Store](#Setting-Up-the-Store)
        * [Добавление рецептов](#Adding-Recipes)
        * [Добавление ингредиентов](#Adding-Ingredients)
        * [Структурирование кода](#Structuring-the-Code)
        * [Подробней о Reducer](#A-Closer-Look-at-Reducers)
        * [Обработка опечаток и дубликатов](#Handling-Typos-and-Duplicates)
        * [Простой пользовательский интерфейс](#Simple-UI)
        * [Логирование](#Logging)
        * [Получение данных с сервера](#Getting-Data-from-the-Server)
        * [Подведем итоги](#Summary-2)
* [Часть 2. Использование в реальном мире](#part-2)       
    * [Глава 3. Управление состоянием](#Сharapter-3)
        * [Общее представление разделения](#The-Concept-of-Separation)
        * [Состояние как база данных](#State-as-a-Database)
        * [Хранение нормализованного состояния](#Keeping-a-Normalized-State)
        * [Сохранение состояния](#Persisting-State)
        * [Состояние в реальном проекте](#Real-World-State)
        * [Подведем итоги](#Summary-3)
    * [Глава 4. Взаимодействие с сервером](#Сharapter-4)
        * [Использование обещаний (promise) в Action Creators](#Using-Promises-in-Action-Creators)
        * [API Middleware](#API-Middleware)
        * [Перемещение кода из Action Creator](#Moving-Code-from-Action-Creators)
        * [Использование API Middleware](#Using-the-API-Middleware)
        * [Обработка ошибок](#Error-Handling)
        * [Индикатор загрузки](#Loading-Indicator)
        * [Динамические типы объекта action](#Dynamic-Action-Types)
        * [Аутентификация](#Authentication)
        * [Дополнительные расширения](#More-Extensions)
        * [Связывания API](#Chaining-APIs)
        * [Отмена API запросов](#Canceling-API-Requests)
        * [Подведем итоги](#Summary-4)
    * [Глава 5. WebSockets](#Charapter-5)
        * [Основная архитектура](#Basic-Architecture)
        * [Redux Link](#Redux-Link)
        * [Реализация кода](#Code-Implementation)
        * [Полный код middleware для работы с WebSocket](#Complete-WebSocket-Middleware-Code)
        * [Аутентификация](#Authentication)
        * [Пример потока](#Sample-Flow)
        * [Примечание](#Notes)
        * [Подведем итоги](#Summary-5)
    * [Глава 6. Тесты](#Сharapter-6)
        * [Тестовые файлы и каталоги](#Test-Files-and-Directories)
        * [Тестирование Action Creators](#Testing-Action-Creators)
        * [Async Action Creators](#Async-Action-Creators)
        * [Тесты для Reducer](#Reducer-Tests)


# <a name="part-2">Использование в реальном мире</a>

## <a name="Сharapter-3">Глава 3. Управление состоянием</a>

Одной из основных преимуществ Redux является разделение состояния (данных) с презентационными и логическими уровнями. Из-за разделения обязанностей разработка схемы состояния может выполняться отдельно от разработки пользовательского интерфейса и любых сложных логических потоков.

### <a name="The-Concept-of-Separation">Общее представление разделения</a>

Чтобы проиллюстрировать эту концепцию, рассмотрим наше приложение для рецептов. Приложение может управлять несколькими книгами рецептов, каждая из которых имеет несколько рецептов. Рецепт, в свою очередь, представляет собой объект, содержащий список ингредиентов, инструкции по приготовлению, изображения и так далее:

_Простая структура состояния приложения_
```javascript
const state = {
  books: [
    {
      id: 21,
      name: 'Breakfast',
      recipes: [
        {
          id: 63,
          name: 'Omelette',
          favorite: true,
          preparation: 'How to prepare...',
          ingredients: [...]
        },
        {...},
        {...}
      ]
    },
    {...},
    {...}
  ]
};
```

Хотя эта схема состояния содержит всю необходимую информацию и точно соответствует описанию нашего приложения, он имеет пару проблем:

* [Вложенный и связанный reducer](#Reducer-Nesting-and-Coupling)
* [Доступ к нескольким вложенных объектов данных](#Access-to-Multiple-Nested-Data-Entities)

#### <a name="Reducer-Nesting-and-Coupling">Вложенный и связанный reducer</a>

Давайте попробуем реализовать reducer, который поддерживает action, добавляющий новый ингредиент в рецепт.

Существуют два основных подхода: первый, где несколько reducer в цепочке знают об одном и том же текущем действии и второй, где каждый reducer передает информацию только своим детям.

Давайте узнаем в чем могут скрываться проблемы и как мы можем с ними справится. Первый подход может быть реализован следующим образом:

_Несколько Reducer знающих об одном action_
```javascript
const booksReducer = (state, action) => {
  switch(action.type) {
    case ADD_INGREDIENT:
      return Object.assign({}, state, {
        books: state.books.map(
          book => book.id !== action.payload.bookId
            ? book
            : recipesReducer(book, action)
        )
      });
  }
};
 
const recipesReducer = (book, action) => {
  switch(action.type) {
    case ADD_INGREDIENT:
      return Object.assign({}, book, {
        recipes: book.recipes.map(
          recipe => recipe.id !== action.payload.recipeId
            ? recipe
            : ingredientsReducer(recipe, action)
        )
      });
  }
};
 
const ingredientsReducer = (recipe, action) => {
  // Обычный reducer
};
```

В этой реализации каждый «родительский» reducer должен знать о любых action, используемых в дочерних. Любые изменения или дополнения потребуют от нас проверки нескольких reducer на изменение кода. Это рушит все преимущества от разделения reducer и значительно усложняет наш код.

Второй вариант заключается в том, что reducer передают все action своим детям:

_Reducer передающий action_

```javascript
const booksReducer = (books, action) => {
  const newBooks = handleBookActions(books, action);
 
  // Обратимся к reducer, который обрабатывает рецепты
  return newBooks.map(book => Object.assign({}, book, {
    recipes: recipesReducer(book.recipes, action)
  }));
};
 
const recipesReducer = (recipes, action) => {
  const newRecipes = handleRecipeActions(book, action);
 
  // Обратимся к reducer, который обрабатывает ингредиенты
  return newRecipes.map(recipe => Object.assign({}, recipe, {
    ingredients: ingredientsReducer(recipe.ingredients, action)
  }));
};
```

В этой реализации мы разделяем логику reducer на две части, одна из которых позволяет запускать любые дочерние reducer, а вторая - обрабатывать action самого reducer. 

Хотя эта реализация не требует, чтобы родитель знал о action, поддерживаемых его детьми, мы вынуждены запускать очень большое количество reducer для каждого рецепта. Один вызов action, не связанного с рецептами, например _UPDATE_PROFILE_, будет запускать _recipesReducer()_ для каждого рецепта и в свою очередь запускать _ingredientsReducer()_ для каждого из ингредиентов.

#### <a name="Access-to-Multiple-Nested-Data-Entities">Доступ к нескольким вложенным объектам данных</a>

Другая проблема с подходом вложенного состояния заключается в извлечении данных. Если мы хотим показать все любимые рецепты пользователя, нам нужно отсканировать все книги, чтобы найти их:

_Получение списка любимых рецептов_
```javascript
const getFavorites = (state) => {
  const recipes = state.books.map(
    book => book.filter(recipe => favorite)
  );
 
  // Удалите все нулевые значения
  return recipes.filter(recipe => recipe);
};    
```

Кроме того, поскольку этот код (или аналогичный) будет использоваться для пользовательского интерфейса, любые изменения в структуре состояния необходимо будет отражать не только в reducer, но и в самом пользовательском интерфейсе. Такой подход рушит преимущества разделение того, что касается модели и может потребовать значительных изменений в уровне пользовательского интерфейса, если изменится структура состояния.

### <a name="State-as-a-Database">Состояние как база данных</a>

Рекомендуемый подход для решения различных вопросов, поднятых выше, заключается в рассмотрении состояния приложения как базы данных объектов. В нашем примере мы сломаем вложенность, чтобы сделать наше состояние как можно более мелким, а свяжем их используя ID:

_Нормализованное состояние_
```javascript
const state = {
  books: {
    21: {
      id: 21,
      name: 'Breakfast',
      recipes: [63, 78, 221]
    }
  },
 
  recipes: {
    63: {
      id: 63,
      book: 21,
      name: 'Omelette',
      favorite: true,
      preparation: 'How to prepare...',
      ingredients: [152, 121]
    },
    78: {},
    221: {}
  },
 
  ingredients: {}
};
```

В этой структуре каждый объект имеет свой собственный ключ в корне нашего состояния. Любые связи между объектами (например, ингредиенты, используемые в рецепте) могут быть выражены с помощью обычного упорядоченного массива идентификаторов (ID).

#### Вложенный и связанный reducer

Давайте рассмотрим реализацию reducer, необходимых для обработки действия (action) _ADD_INGREDIENT_, используя новое состояние:

_Reducer для добавления нового ингредиента_
```javascript
const booksReducer = (books, action) => {
  // Больше не связано с ингредиентами
};
 
const recipeReducer = (recipe, action) => {
  switch (action.type) {
    case ADD_INGREDIENT:
      return Object.assign({}, recipe, {
        ingredients: [...recipe.ingredients, action.payload.id]
      });
  }
 
  return recipe;
};
 
const recipesReducer = (recipes, action) => {
  switch(action.type) {
 
    case ADD_INGREDIENT:
      return recipes.map(recipe =>
        recipe.id !== action.payload.recipeId
          ? recipe
          : recipesReducer(recipe, action));
  }
};
 
const ingredientsReducer = (ingredients, action) => {
  switch (action.type) {
    case ADD_INGREDIENT:
      return [...ingredients, action.payload]
  }
};
```

В этой реализации есть две вещи который нужно отметить, по сравнению с тем, что мы видели с денормализованным состоянием:

* Reducer для обработки книг даже не упоминается. Уровни вложенности влияют только на непосредственных потомков, не ниже. 
* Reducer для рецептов добавляет в массив ингредиентов только ID, а не весь компонент ингредиента.

Что бы воспользоваться этим примером в дальнейшем, реализация _UPDATE_RECIPE_ не потребует никаких изменений в reducer для рецептов, так как он может полностью обрабатываться только лишь одним reducer для ингредиентов.

#### Доступ к нескольким вложенных объектов данных

Получение списка любимых рецептов намного проще в нормализованном состоянии, поскольку нам нужно всего лишь отсканировать "таблицу" рецептов. Это можно сделать в пользовательском интерфейсе, используя функцию, называемую селектором (selector). Если думать о состоянии как базе данных, то можно представить селектор как запрос к базе данных:

_Избранные рецепты_
```javascript
const getFavorites = (state) =>
  state.recipes.filter(recipe => favorite);
```

Основное улучшение заключается в том, что нам не нужно знать структуру или уровни вложенности состояния для доступа к глубоко вложенной информации. Скорее, мы рассматриваем наше состояние как обычную базу данных, из которой извлекается информация для пользовательского интерфейса.

### <a name="Keeping-a-Normalized-State">Хранение нормализованного состояния</a>

Хотя нормализованное состояние может показаться отличной идеей, часто данные, возвращаемые с сервера, структурированы глубоко вложенным образом. Возможный пример полученных данных может выглядеть так:

_Полученные данные_
```javascript
{
  id: 63,
  name: 'Omelette',
  favorite: true,
  preparation: 'How to prepare...',
  ingredients: [
    {
      id: 5123,
      name: 'Egg',
      quantity: 2
    },
    {
      id: 729,
      name: 'Milk',
      quantity: '2 cups'
    }
  ]
};
```

Поскольку единственный способ обновить хранилище (store) Redux - это отправить action в reducer, мы должны создать payload (полезную нагрузку), которую можно легко обработать нашими reducer и найти способ извлечь payload из денормализованных данных, возвращенных сервером.

#### Создание общего action

Потенциально, мы хотели бы, чтобы каждый из наших reducer, работающих с данных, мог обрабатывать специальный action UPDATE_DATA и извлекать нужные ему части:

_Образец действия (action) UPDATE_DATA_
```javascript
const updateData = ({
  type: UPDATE_DATA,
  payload: {
    recipes: {
      63: {
        id: 63,
        name: 'Omelette',
        favorite: true,
        preparation: 'How to prepare...',
        ingredients: [5123, 729]
      }
    },
    ingredients: {
      5123: {
        id: 5123,
        name: 'Egg',
        quantity: 2
      },
      729: {
        id: 729,
        name: 'Milk',
        quantity: '2 cups'
      }
    }
  }
});
```

Используя этот подход, наш reducer рецептов, поддерживающий action UPDATE_DATA, будет выглядеть так:

_Reducer рецептов поддерживающий действие UPDATE_DATA_
```javascript
const recipesReducer = (state, action) => {
  switch(action.type) {
    case UPDATE_DATA:
      if (!('recipes' in action.payload)) return state;

      return Object.assign({}, state, {
        recipes: Object.assign({},
          state.recipes,
          action.payload.recipes
        )
      });
  }
};
```

Наш reducer проверяет, содержит ли payload какие-либо рецепты и объединяет новые данные со старым объектом рецептов (таким образом, добавляя или иным образом модифицируя его по мере необходимости).

#### Нормализация данных

Мы обновили reducer и определили структуру action, однако осталось еще проблема с извлечением payload из денормализованных данных, полученных с сервера.

Прямым подходом может быть создание пользовательской функции, которая знает API всех возвращаемых данных и нормализует возвращенный вложенный JSON в плоскую структуру.

Поскольку это довольно распространенная практика, пользовательский код может быть заменен библиотекой [normalizr](https://github.com/paularmstrong/normalizr). Используя эту библиотеку, мы можем определить схему данных, поступающих с сервера, и получить нормализованную структуру, которую мы можем передать непосредственно в наш action UPDATE_DATA.

### <a name="Persisting-State">Сохранение состояния</a>

Во многих случаях мы хотим сохранить текущее состояние даже во время обновления страницы или закрытия вкладки приложения. Самый простой способ - сохранить его в локальном хранилище браузера (local storage). Чтобы легко синхронизировать наш store с local storage (или любым другим механизмом хранения), мы можем использовать библиотеку [redux-persist](https://github.com/rt2zz/redux-persist). Она будет автоматически сохранить наше состояние после его изменения.

Чтобы использовать библиотеку, просто установите ее с помощью npm и отредактируйте файл создания store, обернув _createStore_ с помощью "усилителя" (enhancer):

_Настройка redux-persist_
```javascript
import { createStore } from 'redux';
import { persistStore, autoRehydrate } from 'redux-persist';
import rootReducer from 'reducers/root';
 
const store = createStore(rootReducer, autoRehydrate());
 
persistStore(store);
```

После вызова _persistStore(store)_ наш store и local storage браузера будут автоматически синхронизироваться, и наш store останется после обновления страницы.

#### Продвинутая синхронизация store

В библиотеке _redux-persist_ есть расширенная функциональность, которая позволит нам сохранять только часть состояния или указывать специальные сериализаторы для части состояния, которая не может быть сериализована с помощью _JSON.stringify()_ (функции, символы и так далее). Мы рекомендуем вам просмотреть документацию библиотеки для получения более подробной информации о более сложных функциях.

### <a name="Real-World-State">Состояние в реальном проекте</a>

В реальном приложении наше состояние обычно содержит несколько разных объектов, включая сами данные приложения (предпочтительно нормализованные) и вспомогательные данные (например, текущий токен доступа, ожидание уведомления и другие).

#### Структура общего состояния

В отличие от данных, поступающих с сервера, некоторая информация будет использоваться исключительно нашим внешним приложением для его внутренних потребностей. Распространенный пример - хранение общего количества активных запросов на на сервер в очереди, для того чтобы знать отображать ли прелоадер. Или у нас может быть свойство _currentUser_, где мы сохраняем информацию о текущем пользователе, такую как имя пользователя и токен доступа:

_Пример состояния_
```javascript
const state = {
  books: { },
  recipes: { },
  ingredients: { },
  ui: {
    activeRequests: 0
  },
  currentUser: {
    name: 'Kipi',
    accessToken: 'topsecrettoken'
  }
};
```

По мере роста нашего приложения, наше состояние будет включать в себя все больше различных объектов. Некоторые из них будут поступать из внешних библиотек, таких как _redux-forms_ и _react-redux-router_. Другим необходимо место непосредственно в state. Они будут появляться в зависимости от бизнес логики нашего приложения.

Например, если нам необходимо поддерживать редактирование профиля пользователя с возможностью отмены, наша реализация может создать новый временный ключ, в котором мы будем хранить копию профиля во время его редактирования. Как только пользователь нажмет «подтвердить» или «отменить», временная копия будет либо скопирована, чтобы стать новым профилем, либо просто удалена.

#### Хранение управляемого состояния

Чтобы сделать эти вещи максимально простыми, лучше всего иметь reducer для каждого ключа в основном состоянии. Это позволит сразу же выяснить кто какие части состояния может модифицировать. Для очень крупного проекта было бы полезно разделить «server data» (данные с сервера) и «auxilary/temp data» (вспомогательные/временные данные) под разными корневыми ключами:

_Состояние с большой вложенностью_
```javascript
const state = {
  db: {
    books: { },
    recipes: { },
    ingredients: { },
  },
  local: {
    ui: {
      activeRequests: 0
    },
    user: {
      name: 'Kipi',
      accessToken: 'topsecrettoken'
    }
  },
  vendor: {
    forms: {},
    router: {}
  }
}; 
```

Такой подход позволяет упростить управление различными частями при принятии решения о том, что необходимо синхронизировать с local storage или при очистке устаревших данных.

В общем, state является некой базой данных для frontend разработчика и его стоит рассматривать как таковое. Важно периодически проверять текущий state и делать какой-либо рефакторинг, чтобы убедиться, что его структура чиста, понятна и проста в расширении.

#### Что помещать в состояние

Общей проблемой при работе с Redux является выбор того, какая информация находится внутри нашего состояния и что осталось за ее пределами - в состоянии React, в сервисах Angular, либо в других методах хранения различных библиотек и фреймворков.

Вот несколько вопросов, которые необходимо учитывать при принятии решения о добавлении чего-либо в состояние:

* Должны ли эти данные сохраняться после обновления страницы?
* Должны ли эти данные сохраняться после изменения маршрута (route)?
* Используются ли эти данные в нескольких местах пользовательского интерфейса?

Если ответ на любой из этих вопросов «да», данные должны хранится в состоянии. Если ответ на все эти вопросы «нет», данные все равно можно разместить в состоянии, но это не обязательно.

Несколько примеров данных, которые могут храниться за пределами state:

* Текущая открытая вкладка на странице (имеется ввиду выбранная вкладка из нескольких внутри страницы, если таковые имеются)
* Открытие/закрытое состояние модального окна
* Текущие отображаемые ошибки

Мы можем считать это похожим на помещение данных в базу данных или временное хранение в памяти. Некоторая информация может быть безопасно потеряна, не искажая пользовательские данные.

### <a name="Summary-3">Подведем итоги</a>

В этой главе мы обсудили структуру нашего состояния Redux и как им следует управлять для упрощения интеграции с reducer и пользовательским интерфейсом. Мы также узнали, что состояние следует рассматривать как базу данных приложения и разрабатывать отдельно от презентационных или логических уровней.

В следующей главе мы поговорим о взаимодействии с сервером, о лучшем методе отправки данных на сервер и получения их с сервера, используя middleware.

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

## <a name="Сharapter-6">Глава 6. Тесты</a>

Одной из ключевых преимуществ Redux является простота тестирования. Чтобы полностью автоматизировать набор тестов, мы можем создавать модульные тесты для каждого из участников (reducer, action creator и middleware) и объединять их для всесторонних интеграционных тестов.

Существует большое количество инструментов для тестирования. Большинство частей нашего Redux приложения будут зависеть от чистых JavaScript функций и объектов без сложных библиотек или асинхронных потоков.

В качестве нашей платформы тестирования мы будем использовать отличную библиотеку [Jest](https://facebook.github.io/jest/) от Facebook, последняя версия которой станет отличным выбором для тестирования Redux. При использовании других фреймворков и инструментов для тестирования, таких как Karma, Mocha и другие, реализация должна выглядеть очень похоже на примеры, разобранные в этой главе.

Что бы доблавить Jest в ваш проект и операционную систему, пройдите [руководство по старту](https://facebook.github.io/jest/docs/en/getting-started.html).

### <a name="Test-Files-and-Directories">Тестовые файлы и каталоги</a>

Для начала нам нужен способ организации наших тестов. Существует два основных подхода: объединение тестов в один каталог с файлами реализации или их размещение в отдельном каталоге. В этом руководстве мы будем использовать последнее. Это вопрос удобства и личных предпочтений, вы можете выбрать то, что вам больше нравится. При этом единственными отличием будут различные конфигурации запуска тестов.

Мы создадим отдельный тестовый файл для каждого файла реализации в нашем проекте. В случае _app/actions/recipes.js_, нашим тестовым файлом будут _test/actions/recipes.test.js_.

#### Структура тестового файла

В наших тестовых файлах мы будем использовать функцию _describe()_ как обертку всех наших тестов. Первый строковый параметр в этой функции позволит нам легко определить, какая группа тестов проваливается или успешно выполняется:

_Пример структуры тестового файла_
```javascript
describe('actions', () => {
  // TODO: Добавить тесты
});
```

Внутри этой функции могут использоваться другие вложенные функции _describe()_, чтобы дополнительно различать разные наборы состояний (например, тестирование неудачных или последующих вызовов API).

Каждый тест в Jest обернут внутри блока _it()_, описывающего, что делает тест. Чтобы тесты были читабельны и понятны, обычно рекомендуется создавать как можно больше коротких тестов (каждый в своем собственном блоке _it()_), а не создавать очень большие одиночные тестовые функции:

_Пример тестового файла с описанием тестов_
```javascript
describe('actions', () => {
  it('должен создать action для добавления рецепта', () => {
    // TODO: Реализовать тест
  });
 
  it('должен создать action для удаления рецепта', () => {
    // TODO: Реализовать тест
  });
});
```

### <a name="Testing-Action-Creators">Тестирование Action Creators</a>

Всюду по этой книге мы пытались хранить асинхронные потоки вне action creator, переместив их в middleware и утилитарные функции. Этот подход позволяет очень легко тестировать action creators, поскольку они представляют собой функции, которые просто возвращают обычные JavaScript объекты:

_Пример action creator_
```javascript
import * as actions from 'constants/action-types';
 
export const setRecipes = (recipes) => ({
 type: actions.SET_RECIPES,
 payload: recipes
});
```

Наш action creator _setRecipes()_ получает единственный параметр и создает в результате простой JavaScript объект. Поскольку здесь нет логики управления потоком или каких-либо побочных эффектов, любой вызов этой функции всегда возвращает одно и то же значение, что делает его очень простым для тестирования:

_Пример теста для setRecipes_
```javascript
import * as actions from 'actions'
 
describe('actions', () => {
 it('должен создать action для добавления рецепта', () => {
   const expected = { type: 'ADD_RECIPE', payload: 'test' };
   const actual = actions.addRecipe('test');
   
   expect(actual).toEqual(expected);
 });
});
```

Этот тест построен в трех частях. Во-первых, мы вычисляем, что должен сделать наш action creator при вызове с _'test'_ в качестве аргумента - в этом случае объект JavaScript, содержащий два ключа, _type_ и _payload_:

_Рассчет ожидаемого результата_
```javascript
const expected = { type: 'ADD_RECIPE', payload: 'test' };
```

Во-вторых, вызывается action creator _actions.addRecipe('test')_, чтобы получить значение, созданное реализацией нашего action creator:

_Рассчет фактического результата_
```javascript
const actual = actions.addRecipe('test');
```

И наконец используются Jest функции  _expect()_ и _toEqual()_ для проверки того, что фактические и ожидаемые результаты одинаковы:

_Проверка соответствия результатов_
```javascript
expect(actual).toEqual(expected);
```

Если ожидаемые и фактические объекты различаются, Jest выдаст ошибку и предоставит информацию, описывающую различия, что позволит нам отловить неправильные реализации.

#### Улучшение кода

Из-за простоты этого кода принято комбинировать несколько этапов в один вызов и переписывать тест следующим образом:

_Более короткая версия теста_
```javascript
it('должен создать action для добавления рецепта', () => {
 const expected = { type: 'ADD_RECIPE', payload: 'test' };
 
 expect(actions.addRecipe('test')).toEqual(expected);
});
```

#### Использование снимков (Snapshot)

Подход вычисления ожидаемого значения, а затем сравнение его с динамически рассчитанными значениями очень распространен в Redux тестах. Что бы сохранить время на набор текста и облегчить чтение кода, мы можем использовать одну из возможностей Jest - [снимков](https://facebook.github.io/jest/docs/en/tutorial-react.html#snapshot-testing) (snapshot).

Вместо того, что бы вручную строить ожидаемый результат, мы можем попросить Jest запустить блок _expect()_ и сохранить результат в специальном файле .snap, генерирующим на ожидаемый объект автоматически: 

_Тест с использованием снимков_
```javascript
it('должен создать action для добавления рецепта', () => {
  expect(actions.addRecipe('test')).toMatchSnapshot();
});
```

Ожидаемый значение рассчиталось и вместо использования _isEqual()_, Jest теперь сравнивает результат выражения внутри _expect()_ с версией, сохраненной на диске. Фактически снимок помещается в каталог __snapshots__ в файл с тем же именем, что и тестовый файл, а также расширением .snap:

_snapshots/action.test.js.snap_
```javascript
exports[`должен создать action для добавления рецепта`] = `
Object {
  "payload": "test",
  "type": "ADD_RECIPE",
}
`;
```

Структура сложнее, чем структура обычного объекта JavaScript, но результат точно такой же, как и наш первоначальный ожидаемый расчет:

_Рассчитанный ожидаемый результат_
```javascript
const expected = { type: 'ADD_RECIPE', payload: 'test' };
```

Что происходит, когда изменяется наш код? В некоторых случаях мы хотим намеренно изменить структуру нашего объекта action. В этих случаях Jest обнаружит, что возвращаемое значение не соответствует тому, что сохраняется в его файле снимков, и выдаст ошибку. Но если мы укажем, что новый результат является правильным, а кешированный снимок уже недействителен, мы можем легко сказать Jest обновить его версию снимка до новой.
 
 #### Динамические Action Creators

В некоторых случаях action creator может содержать логику, которая испускает разные объекты action на основе входных параметров. До тех пор, пока не будет затронут асинхронный код или другие внешние объекты (например, localStorage), мы можем легко протестировать логику, предоставив различные входные параметры для action creator проверив, что он каждый раз создает правильный объект:

_Action creator c изменяемыми входными параметрами_
```javascript
export const addRecipe = (title) => ({
  type: actions.ADD_RECIPE,
  payload: title || "Default"
});
```

Модифицированный action creator _addRecipe()_ установит значение _"Default"_, если пользователь не передаст заголовок. Чтобы проверить это поведение, мы можем создать два теста, один из которых передает параметр (как мы уже делали), и второй, который передает пустую строку. Полностью всеобъемлющий тест может содержать несколько случаев "пустой строки", а именно значение _null_, _undefined_ и ' ':

_Комбинированный тест нескольких входных значений пустой строки_
```javascript
it('должен добавить рецепт с параметром по умолчанию', () => {
  expect(actions.addRecipe(undefined)).toMatchSnapshot();
  expect(actions.addRecipe(null)).toMatchSnapshot();
  expect(actions.addRecipe('')).toMatchSnapshot();
});
```

В отличие от того, что мы обсуждали ранее, здесь мы попытались включить несколько функций _expect()_ в один и тот же тест. Хотя этот подход будет работать, но, в случае ошибки, будет сложно определить, какие из тестовых случаев не удались.
 
Поскольку мы используем JavaScript для написания наших тестов, мы можем легко создавать тестовые случаи для каждого входного значения без значительного увеличения размера нашего кода (создавая _it()_ для каждого случая). Мы можем сделать это, добавив все возможные входные параметры в массив и автоматически создав соответствующие _it()_ блоки:

_Автоматическое создание тестов для каждого тестового случая_
```javascript
[undefined, null, ''].forEach((param) =>
 it(`должен добавить рецепт с параметром по умолчанию ${param}` , () => {
   expect(actions.addRecipe(param)).toMatchSnapshot()
 }));
```

Используя этот подход, мы получаем три разных блока _it()_, автоматически генерируемых JavaScript, сохраняя наши тесты чистыми, а код - коротким.

### <a name="Async-Action-Creators">Async Action Creators</a>

Везде в этой книге мы пытались препятствовать использованию async action creator (создатели асинхронных действий) и функций, которые имеют побочные эффекты. Для этого мы использовали различные библиотеки, такие как [redux-thunk](https://github.com/gaearon/redux-thunk), что бы позволить action creator запланировать асинхронную работу. Одним из основных преимуществ обычных action creators является простота их тестирования - больше информации об этом можно найти в главе [Action Creators](#Charapter-8).

В нашем примере бы создадим простой async action creator, который, используя _redux-thunk_ и метод _fetch()_, получит данные о рецепте с сервера и отправит (dispatch) результат с помощью действия _SET_RECIPE_:

_Async action creator_
```javascript
 export const setRecipe = (id, data) => ({
   type: actions.SET_RECIPE,
   payload: { id, data }
 });
 
 export const fetchRecipe = id => dispatch => {
   return fetch('recipe/' + id)
     .then(response => response.json())
     .then(json  dispatch(setRecipe(id, json)))
 }
```

С помощью _redux-thunk_ наш action creator может вернуть функцию вместо чистого JavaScript объекта. middleware, которую предоставляет _redux-thunk_, может вызвать такие функции и передать им методы _dispatch()_ и _getState()_. Такая реализация позволяет нашему action creator использовать метод fetch() для получение данных с сервера и отправить action, когда эти данные будут получены, используя _dispatch()_.

#### Переопределение fetch()

Прежде чем перейти к тестам, нам нужно определить некоторую инфраструктуру для переопределения метода _fetch()_. Мы создадим фиктивный объект ответа, а затем переопределим _fetch()_ на нашем объекте window:

_Создадим фейковый объект ответа_
```javascript
export const mockResponse = (status, statusText, response) => {
  return new window.Response(response, {
    status: status,
    statusText: statusText,
    headers: {
      'Content-type': 'application/json'
    }
  });
};
```

_Переопределение успешно завершенного метода fetch()_
```javascript
export const mockFetch = (status, data) => {
  window.fetch = jest.fn().mockImplementation(
    () => Promise.resolve(mockResponse(status, null, data)));
};
```

_Переопределение не успешно завершенного метода fetch()_
```javascript
export const mockFetchError = (state, error) => {
  window.fetch = jest.fn().mockImplementation(
    () => Promise.reject(mockResponse(state, error, '{}'))
  );
};
```

Вызов нашего фиктивного _fetch()_ вернет обещание, подобное реальному результату при вызове _fetch()_.

_Пример подмены метода fetch()_
```javascript
mockFetch(200, '{"key":"value"}');
fetch('test.json')
```

Этот код позволит нам вызвать _mockFetch()_ или _mockFetchError()_, в результате чего следующий вызов функции _fetch()_ будет возвращаться с нашим фейковым ответом. Единственная проблема с этой реализацией заключается в том, что она переопределяет все вызовы _fetch()_ в системе, независимо от URL-адреса.

Поскольку первым параметром для _fetch()_ является URL-адрес, мы можем использовать простую функцию _handleResponse()_, чтобы сначала проверить, что URL-адрес, переданный в _fetch()_, является URL-адресом, который мы хотим переопределить:

_Переопределение с проверкой URL-адреса_
```javascript
const handleResponse = (mockedUrl, response) =>
  window.fetch = jest.fn().mockImplementation(url => {
    if (url === mockedUrl) {
      return response;
    }
    throw('Unknown URL: ' + url);
  });
 
export const mockFetch = (mockedUrl, status, data) =>
  handleResponse(
    mockedUrl,
    Promise.resolve(mockResponse(status, null, data)));
 
export const mockFetchError = (mockedUrl, state, error) =>
  handleResponse(
    mockedUrl,
    Promise.reject(mockResponse(state, error, '{}')));
```

#### Создание фейкового Store

В отличии от простых action creators, наш код теперь зависит от использования _dispatch()_, что заставляет нас создавать фейковый экземпляр кода. Для этого мы будем использовать библиотеку [redux-mock-store](https://github.com/arnaudbenard/redux-mock-store):

_Создание фейкового Store_
```javascript
import configureStore from 'redux-mock-store';
import thunk from 'redux-thunk';
 
const mockStore = configureStore([ thunk ]);
```

Здесь мы создаем объект фейкового store с одной middleware. Этот объект можно использовать как обычный Redux store. Он поддерживает отправку действий, которые позже позволят нам определить, что в store был отправлен корректный набор действий.

### Структура теста для Async Action Creator

Поскольку async action creators (создатели асинхронных действий) могут содержать разные потоки на основе результата асинхронного действия, лучше всего включить их в свои собственные блоки _describe()_ в тестах. Это также позволит нам легко создать новый «фейковый store» для каждого из тестовых примеров с использованием Jest's метода _beforeEach()_:

_Структура асинхронного тестового блока_
```javascript
describe('fetch recipe', () => {
  let store;
 
  beforeEach(() => store = mockStore({}));
 
  it('должен получать рецепт, если он существует'), () => {
      ...
  }
});
```

Наш фейковый store автоматически создается заново перед каждой итерацией тестов, очищая любые действия, кэшированные из предыдущего запуска.

#### Базовый тест Async Action Creator

Jest обрабатывает асинхронные тесты, позволяя нам вернуть promise (обещание) в качестве результата теста. Если обещание будет возвращено, Jest будет ждать пока оно не завершится и только потом перейдет к следующему тесту:

_Асинхронный тест_
```javascript
it('должен получать рецепт, если он существует', () => {
  return store.dispatch(actions.fetchRecipe(100));
});
```

Поскольку _store.dispatch()_ в этом случае вернет обещание (помните, наш action creator _fetchRecipe()_ возвращает вызов _fetch()_), мы можем использовать это для создания асинхронного теста.

Чтобы добавить в код блок _expect()_, мы можем использовать тот же promis и запустить наши тесты, как только он будет разрешен:

_Добавление ожидающих вызовов для асинхронных тестов_
```javascript
it('должен получать рецепт, если он существует', () => {
  return store.dispatch(actions.fetchRecipe(100))
    .then(() => expect(store.getActions()).toEqual([]))
});
```

Блок _expect()_ похож на то, что мы использовали в наших предыдущих тестах. Мы используем метод _getActions()_ нашего фейкового stor, что бы получить массив всех действий, отправленных в store. В нашей реализации мы ожидаем успешное завершение вызова _fetch()_ для отправки результата _setRecipe()_ нашего action creator. 

Выполнение этого теста сейчас приведет к неудаче, поскольку мы не подменили метод _fetch()_. Используя небольшую вспомогательную библиотеку, которую мы создали ранее, мы можем подменить его, что приведет к правильной последовательности действий:

_Полный асинхронный тест_
```javascript
it('должен получать рецепт, если он существует', () => {
  mockFetch('recipe/100', 200, '{"title":"hello"}');

  return store.dispatch(actions.fetchRecipe(100))
    .then(() => expect(store.getActions()).toMatchSnapshot())
});
```

Здесь мы подменяем успешным ответом (200) от _fetch()_ и ожидаем, что отправка асинхронного действия, созданного _fetchRecipe(100)_, приведет к последующей отправке действия, созданного _setRecipe()_.

#### Подведем итоги об асинхронных тестах

Как видно из этого минимального примера, тестирование async action creator (создателей асинхронных действий) значительно сложнее, чем тестирование обычных action creator. Если мы добавим надлежащую обработку ошибок и ветвление, тесты быстро станут очень трудными для анализа и построения.

Глава [Middleware](#Charapter-10) предлагает альтернативу async action creator, перемещая асинхронную логику в middleware. Это позволяет нам тестировать и концентрировать весь асинхронный код приложения в одном месте.

### <a name="Reducer-Tests">Тесты для Reducer</a>