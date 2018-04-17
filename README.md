# Перевод книги [The Complete Redux Book](https://leanpub.com/redux-book) от [Ilya Gelman](https://leanpub.com/u/ilyagelman) и [Boris Dinkevich](https://leanpub.com/u/borisdinkevich)

Перевод книги от 31-01-2017. Переведено и опубликовано с разрешения правообладателей.

## Оглавление
* [Часть 1. Введение в Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%A7%D0%B0%D1%81%D1%82%D1%8C-1-%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B2-redux)
    * [Глава 1. Основные понятия Flux и Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-1-%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%B8%D1%8F-flux-%D0%B8-redux)
        * [Что такое Flux?](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%A7%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-flux)
        * [Redux и Flux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#redux-%D0%B8-flux)
        * [Redux Терминология](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#redux-%D0%A2%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F)
        * [Общие понятия](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%9E%D0%B1%D1%89%D0%B8%D0%B5-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%B8%D1%8F)
        * [Redux и React](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#redux-%D0%B8-react)
        * [Основная реализация Redux](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D0%B0%D1%8F-%D1%80%D0%B5%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F-redux)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-1.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
    * [Глава 2. Ваше первое Redux приложение](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-2-%D0%92%D0%B0%D1%88%D0%B5-%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%B5-redux-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5) 
        * [Стартовый проект](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%A1%D1%82%D0%B0%D1%80%D1%82%D0%BE%D0%B2%D1%8B%D0%B9-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)
        * [Наше первое приложение](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9D%D0%B0%D1%88%D0%B5-%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%B5-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5)
        * [Настройка Store](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-store)
        * [Добавление рецептов](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%94%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D1%80%D0%B5%D1%86%D0%B5%D0%BF%D1%82%D0%BE%D0%B2)
        * [Добавление ингредиентов](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%94%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B8%D0%BD%D0%B3%D1%80%D0%B5%D0%B4%D0%B8%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)
        * [Структурирование кода](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%A1%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D0%B4%D0%B0)
        * [Подробней о Reducer](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9F%D0%BE%D0%B4%D1%80%D0%BE%D0%B1%D0%BD%D0%B5%D0%B9-%D0%BE-reducer)
        * [Обработка опечаток и дубликатов](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9E%D0%B1%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0-%D0%BE%D0%BF%D0%B5%D1%87%D0%B0%D1%82%D0%BE%D0%BA-%D0%B8-%D0%B4%D1%83%D0%B1%D0%BB%D0%B8%D0%BA%D0%B0%D1%82%D0%BE%D0%B2)
        * [Простой пользовательский интерфейс](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9F%D1%80%D0%BE%D1%81%D1%82%D0%BE%D0%B9-%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D1%81%D0%BA%D0%B8%D0%B9-%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D1%84%D0%B5%D0%B9%D1%81)
        * [Логирование](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9B%D0%BE%D0%B3%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)
        * [Получение данных с сервера](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9F%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85-%D1%81-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%D0%B0)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-1/charapter-2.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
* [Часть 2. Использование в реальном мире](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B2-%D1%80%D0%B5%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%BC-%D0%BC%D0%B8%D1%80%D0%B5)       
    * [Глава 3. Управление состоянием](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-3-%D0%A3%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D0%B5%D0%BC)
        * [Общее представление разделения](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%9E%D0%B1%D1%89%D0%B5%D0%B5-%D0%BF%D1%80%D0%B5%D0%B4%D1%81%D1%82%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F)
        * [Состояние как база данных](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%A1%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D0%B5-%D0%BA%D0%B0%D0%BA-%D0%B1%D0%B0%D0%B7%D0%B0-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85)
        * [Хранение нормализованного состояния](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%A5%D1%80%D0%B0%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BD%D0%BE%D1%80%D0%BC%D0%B0%D0%BB%D0%B8%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F)
        * [Сохранение состояния](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%A1%D0%BE%D1%85%D1%80%D0%B0%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F)
        * [Состояние в реальном проекте](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%A1%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D0%B5-%D0%B2-%D1%80%D0%B5%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%BC-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B5)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-3.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
    * [Глава 4. Взаимодействие с сервером](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-4-%D0%92%D0%B7%D0%B0%D0%B8%D0%BC%D0%BE%D0%B4%D0%B5%D0%B9%D1%81%D1%82%D0%B2%D0%B8%D0%B5-%D1%81-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%D0%BE%D0%BC)
        * [Использование обещаний (promise) в Action Creators](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B1%D0%B5%D1%89%D0%B0%D0%BD%D0%B8%D0%B9-promise-%D0%B2-action-creators)
        * [API Middleware](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#api-middleware)
        * [Перемещение кода из Action Creator](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%9F%D0%B5%D1%80%D0%B5%D0%BC%D0%B5%D1%89%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D0%B4%D0%B0-%D0%B8%D0%B7-action-creator)
        * [Использование API Middleware](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-api-middleware)
        * [Обработка ошибок](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%9E%D0%B1%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0-%D0%BE%D1%88%D0%B8%D0%B1%D0%BE%D0%BA)
        * [Индикатор загрузки](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%98%D0%BD%D0%B4%D0%B8%D0%BA%D0%B0%D1%82%D0%BE%D1%80-%D0%B7%D0%B0%D0%B3%D1%80%D1%83%D0%B7%D0%BA%D0%B8)
        * [Динамические типы объекта action](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%94%D0%B8%D0%BD%D0%B0%D0%BC%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B5-%D1%82%D0%B8%D0%BF%D1%8B-%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%B0-action)
        * [Аутентификация](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%90%D1%83%D1%82%D0%B5%D0%BD%D1%82%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F)
        * [Дополнительные расширения](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%94%D0%BE%D0%BF%D0%BE%D0%BB%D0%BD%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5-%D1%80%D0%B0%D1%81%D1%88%D0%B8%D1%80%D0%B5%D0%BD%D0%B8%D1%8F)
        * [Связывания API](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%A1%D0%B2%D1%8F%D0%B7%D1%8B%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-api)
        * [Отмена API запросов](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%9E%D1%82%D0%BC%D0%B5%D0%BD%D0%B0-api-%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%BE%D0%B2)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-4.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
    * [Глава 5. WebSockets](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%93%D0%BB%D0%B0%D0%B2%D0%B0-5-websockets)
        * [Основная архитектура](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D0%B0%D1%8F-%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D0%B0)
        * [Redux Link](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#redux-link)
        * [Реализация кода](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%A0%D0%B5%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F-%D0%BA%D0%BE%D0%B4%D0%B0)
        * [Полный код middleware для работы с WebSocket](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%9F%D0%BE%D0%BB%D0%BD%D1%8B%D0%B9-%D0%BA%D0%BE%D0%B4-middleware-%D0%B4%D0%BB%D1%8F-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B-%D1%81-websocket)
        * [Аутентификация](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%90%D1%83%D1%82%D0%B5%D0%BD%D1%82%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F)
        * [Пример потока](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%9F%D1%80%D0%B8%D0%BC%D0%B5%D1%80-%D0%BF%D0%BE%D1%82%D0%BE%D0%BA%D0%B0)
        * [Примечание](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%9F%D1%80%D0%B8%D0%BC%D0%B5%D1%87%D0%B0%D0%BD%D0%B8%D0%B5)
        * [Подведем итоги](https://github.com/Zveroboev/The-Complete-Redux-Book/blob/master/source/part-2/charapter-5.md#%D0%9F%D0%BE%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%B8%D1%82%D0%BE%D0%B3%D0%B8)
    * [Глава 6. Тесты](#Сharapter-6)
        * [Тестовые файлы и каталоги](#Test-Files-and-Directories)
        * [Тестирование Action Creators](#Testing-Action-Creators)
        * [Async Action Creators](#Async-Action-Creators)
        * [Тесты для Reducer](#Reducer-Tests)


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