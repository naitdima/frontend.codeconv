### Нейминг

#### Имена файлов однофайловых компонентов должны быть всегда в PascalCase

PascalCase лучше всего работает с автодополнением в редакторах кода, поскольку он согласуется с тем, как мы ссылаемся на компоненты в JS(X) и шаблонах.

#### Имена компонентов должны состоять из полных слов, а не аббревиатур

Плохо:
```
components/
|- SdSettings.vue
|- UProfOpts.vue
```
Хорошо:
```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

#### Имена компонентов должны всегда состоять из нескольких слов, за исключением корневого компонента `App`

Это предотвращает конфликты с существующими или будущими HTML-элементами, поскольку все HTML-элементы именуются одним словом.

#### Порядок слов в именах компонентов

Компоненты должны именоваться с высшего уровня (часто наиболее общих слов) и заканчиваться описательными дополняющими словами.

Плохо:
```
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue
```
Хорошо:
```
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```

#### Входные параметры

Входные параметры должны всегда использовать camelCase при определении, но kebab-case в шаблонах.
```
props: { 
  greetingText: String,
}

<welcome-message greeting-text="hi"/>
```

#### Значения слежения
Для единообразия следует именовать новое значение: `val`, а старое значение: `oldVal`.
```
watch: {
  type(val, oldVal) {
    ...
  },
}
```

#### Часто упоминаемые объекты именуются одинаково во всем проекте

Плохо:
```
const customer = new User();
const client = new User();
const object = new User();
```
Хорошо:
```
const user = new User();
```

#### Переменные, отражающие свойства объекта, должны включать название объекта

Плохо:
```
const project = new Project();
const name = project.name;
const project = project.name;
```
Хорошо:
```
const project = new Project();
const projectName = project.name;
```

#### Переменные по возможности должны называться на корректном английском

Плохо:
```
const usersStored = [];
```
Хорошо:
```
const storedUsers = [];
```
Исключение: сгруппированные по некому признаку поля или константы. В этом случае можно использовать префикс.
```
STATUS_READY 
STATUS_BLOCKED
 
billingIsPaid
billingPaidDate
billingSum
```

#### В названии переменной не должно быть указания типа

Нельзя писать `projectsArray`, надо писать просто `projects`. Это же касается и форматов (JSON, XML и т.п.), и любой другой не относящейся к предметной области информации.

Плохо:
```
const projectsList = await loadProjects();
const projectsListIds = extractField('id', projectsList);
```
Хорошо:
```
const projects = await loadProjects();
const projectsIds = extractField('id', projects);
```

#### Названия boolean методов и переменных должны содержать глагол `is`, `has` или `can`

Переменные правильно называть, описывая их содержимое, а методы — задавая вопрос. Если переменная содержит свойство объекта, следуем правилу [признак объекта добавляется к названию](https://github.com/roistat/php-code-conventions#-%D0%9F%D1%80%D0%B8%D0%B7%D0%BD%D0%B0%D0%BA-%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%B0-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D1%8F%D0%B5%D1%82%D1%81%D1%8F-%D0%BA-%D0%BD%D0%B0%D0%B7%D0%B2%D0%B0%D0%BD%D0%B8%D1%8E).

Плохо:
```
const isUserValid = user.valid();
const isProjectAnalytics = getProjectAccess(project, 'analytics');
```
Хорошо:
```
const userIsValid = user.isValid();
const projectCanAccessAnalytics = canProjectAccess(project, 'analytics');
```
Геттеры именуются аналогично переменным:
```
class User {
  constructor() {
    this._isEnabled = true;
    this._billingIsPaid = false;
  }
  get isEnabled() { 
    return this._isEnabled;
  } 
  get billingIsPaid() {
    return this._billingIsPaid; 
  }
}
```

Такое именование позволяет легче читать условия:
```
// if user is valid, then do something
if (userIsValid) { 
  // do something
}
```

#### Запрещены отрицательные логические названия

Плохо:
```
if (project.isInvalid()) ...
if (project.isNotValid()) ...
if (accessManager.isAccessDenied()) ...
```
Хорошо:
```
if (!project.isValid()) ...
if (!project.isAccessAllowed()) ...
if (accessManager.canAccess()) ...
```

#### Название метода должно начинаться с глагола и соответствовать правилам именования переменных.

Плохо:
```
async items() { // ...}
convertedDataObject(data) { // ...}
```
Хорошо:
```
async loadItems() { // ...}
convertDataToObject(data) { // ...}
```

#### Нельзя использовать глагол get в геттерах

Например, вместо `getDate()` следует писать `date()`. Геттер — метод, работающий только с полями своего объекта.
```
class User {
  constructor() {
    this._customFields = ...; 
  }

  get customFields() { 
    return this._customFields;
  }
}
```

#### Итерируемый элемент массива должен одинаково именоваться в цепочках методов массива:

Плохо:
```
const answeredQuestions = questionIds
  .filter(questionId => this.value[questionId])
  .map(id => getQuestionById(id));
```
Хорошо:
```
const answeredQuestions = questionIds
  .filter(id => this.value[id])
  .map(id => getQuestionById(id));

// Исключением является преобразованный в теле цепочки элемент (например, после map)
const questionIds = questions
  .map(question => question.id)
  .filter(id => this.value[id]);
```

### Структура компонентов

#### Порядок опций компонента/экземпляра

Опции компонента/экземпляра должны быть упорядочены консистентно:

1. Побочные эффекты (вызывает эффекты вне компонента)
    - `el`
2. Глобальная осведомлённость (требует знаний вне компонента)
    - `name`
    - `parent`
3. Тип компонента (изменяет тип компонента)
    - `functional`
4. Модификаторы шаблона (изменение способа компиляции шаблонов)
    - `delimiters`
    - `comments`
5. Зависимости шаблона (ресурсы, используемые в шаблоне)
    - `components`
    - `directives`
    - `filters`
6. Композиция (объединение свойств в опциях)
    - `extends`
    - `mixins`
7. Интерфейс (интерфейс компонента)
    - `inheritAttrs`
    - `model`
    - `props`/`propsData`
8. Хуки жизненного цикла (коллбэки в процессе жизни компонента, в порядке объявления)
    - `beforeCreate`
    - `created`
    - `beforeMount`
    - `mounted`
    - `beforeUpdate`
    - `updated`
    - `activated`
    - `deactivated`
    - `beforeDestroy`
    - `destroyed`
9. Локальное состояние (локальные реактивные свойства)
    - `data`
    - `computed`
10. События (коллбэки вызываемые реактивными событиями)
    - `watch`
11. Нереактивные свойства (свойства экземпляра независимые от системы реактивности)
    - `methods`
12. Отрисовка (декларативное описание вывода компонента)
    - `template`/`render`
    - `renderError`
    
#### Пустые строки между опций компонента/экземпляра

Когда компоненты кажутся неразборчивыми и становятся трудными для чтения, то добавление пустых строк между многострочными свойствами может облегчить их беглое изучение просматривая взглядом.

```
props: {
  label: String, 
  icon: String,
},

computed: { 
  formattedValue() { ... }, 
  inputClasses() { ... }
},
```

#### Определение входных параметров

Входные параметры должны быть определены как можно более подробно.

```
props: {
  status: String,
}

// Ещё лучше!
props: { 
  status: { 
    type: String, 
    required: true, 
    validator(value) { 
      return [ 'syncing', 'synced', 'version-conflict', 'error' ].includes(value); 
    },
  },
},
```

Входные параметры непримитивного типа должны иметь соответствующее значение по умолчанию.

```
props: { 
  project: {
    type: Object,
    default() {
      return {};
    },
  },
  users: {
    type: Array,
    default() {
      return [];
    },
  },
}
```

#### Простые вычисляемые свойства

Комплексные вычисляемые свойства должны быть разделены на максимально простые свойства.

Плохо:
```
computed: {
  price() { 
    const basePrice = this.manufactureCost / (1 - this.profitMargin);
    return basePrice - basePrice * (this.discountPercent || 0);
  },
}
```
Хорошо:
```
computed: { 
  basePrice() { 
    return this.manufactureCost / (1 - this.profitMargin);
  }, 
  discount() { 
    return this.basePrice * (this.discountPercent || 0);
  }, 
  finalPrice() { 
    return this.basePrice - this.discount;
  },
}
```

#### Локальные стили компонента

Для приложений стили в корневом компоненте `App` и в компонентах шаблона могут быть глобальными, но во всех остальных компонентах должны быть локальными.

```
<style scoped>
  .kpi-list { 
    background-color: ligthgrey;
  }
</style>
```

### Разметка шаблона

#### Самозакрывающиеся теги компонентов

Компоненты без содержимого должны быть самозакрывающимися тегами в однофайловых компонентах, строковых шаблонах и JSX.

Самозакрывающиеся теги компонентов сообщают, что у них не только нет содержимого, но и сообщает что и не должны иметь содержимого. Это разница между пустой страницей в книге и страницей с надписью: «Эта страница намеренно оставлена пустой». Ваш код также станет более лаконичным без ненужного закрывающего тега.

```
<my-component/>
```

#### Элементы с несколькими атрибутами

Элементы с несколькими атрибутами могут распологаться на одной строке, если колличество символов в строке не превышает 80. Иначе атрибуты должны располагаться на нескольких строках, по одному атрибуту на строку.

```
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">

<input type="number" name="age" min="18" max="130" step="1">

<transaction-table
  :type="type"
  :transactions="filteredTransactions"
  @edit-transaction="showEditDialog"
  @clone-transaction="showCloneDialog"
  @remove-transaction="removeTransaction"
/>
```

Атрибуты элементов (в том числе компонентов) должны быть упорядочены консистентно:

1. Определение
    - `is`
2. Отображение списка
    - `v-for`
    - `key`
3. Условия (указывается отрисовывается/отображается ли элемент)
    - `v-if`
    - `v-else-if`
    - `v-else`
    - `v-show`
    - `v-cloak`
4. Модификаторы отрисовки (изменяют способ отрисовки элемента)
    - `v-pre`
    - `v-once`
5. Глобальная осведомлённость (требует знаний вне компонента)
    - `id`
6. Уникальные атрибуты (атрибуты, требующие уникальных значений)
    - `ref`
    - `slot`
7. CSS-классы
    - `class`
8. Двусторонняя привязка (объединение привязки и событий)
    - `v-model`
9. Другие атрибуты (все неуказанные связанные или несвязанные атрибуты)
10. События (обработчики событий компонента)
    - `@`
11. Содержимое (перезаписывает содержимое элемента)
    - `v-html`
    - `v-text`

#### Значения атрибутов в кавычках

Непустые значения HTML-атрибутов должны быть обрамлены двойными кавычками.
```
<input type="radio">
```

#### Сокращённая запись директив

Следует использовать сокращённую запись директив (`:` для `v-bind:`, `@` для `v-on:` и `#` для `v-slot`).

```
<input :value="newTodoText">
<input @focus="onFocus">
<template #header> 
  <h1>Заголовок страницы</h1>
</template>
```

#### Всегда используйте `key` с `v-for`

`key` с `v-for` всегда обязателен для компонентов, для поддержания внутреннего состояния компонента и его поддерева. Даже для элементов это хорошая практика для поддержания предсказуемого поведения, такого как [консистентности объекта

```
<ul> 
  <li 
    v-for="todo in todos" 
    :key="todo.id"
  > 
    {{ todo.text }} 
  </li>
</ul>
```

#### Избегайте использования `v-if` с `v-for`

Никогда не используйте `v-if` на том же элементе, что и `v-for`.

Есть два распространённых случая, когда это может быть заманчиво:

- Чтобы фильтровать элементы списка (например, `v-for="user in users" v-if="user.isActive"`). В этих случаях замените `users` новым вычисляемым свойством, которое возвращает ваш отфильтрованный список (например, `activeUsers`).
- Чтобы избежать отображения списка, если он должен быть скрыт (например, `v-for="user in users" v-if="shouldShowUsers"`). В этих случаях переместите `v-if`выше, в элемент контейнера (например, `ul`, `ol`).

Плохо:
```
<ul> 
  <li 
    v-for="user in users" 
    v-if="user.isActive" 
    :key="user.id"
  > 
    {{ user.name }}</li>
</ul>
<ul>
  <li 
    v-for="user in users" 
    v-if="shouldShowUsers" 
    :key="user.id"
  > 
    {{ user.name }} 
  </li>
</ul>
```
Хорошо:
```
<ul> 
  <li 
    v-for="user in activeUsers" 
    :key="user.id"
  >
    {{ user.name }} 
  </li>
</ul>
<ul v-if="shouldShowUsers"> 
  <li 
    v-for="user in users" 
    :key="user.id"
  > 
    {{ user.name }}
  </li>
</ul>
```

Если элемент имеет динамические CSS-классы, то и статичные, и динамичные должны быть перечислены в одном массиве
Плохо:
```
<div
  class="filter-item"
  :class="{'active': isActive}"
>
```
Хорошо:
```
<div :class="['filter-item', {'active': isActive}]">
```

#### Простые выражения в шаблонах

Шаблоны компонентов должны содержать только простые выражения, а более комплексные должны быть вынесены в вычисляемые свойства или методы.

Сложные выражения в ваших шаблонах делают их менее декларативными. Мы должны стремиться к описанию *что* должно отобразиться, а не *как* мы вычисляем это значение. Вычисляемые свойства и методы также упрощают переиспользование кода.

```
<span>{{ normalizedFullName }}</span>

computed: { 
  normalizedFullName() { 
    return this.fullName
      .split(' ')
      .map(word => `${word[0].toUpperCase()}${word.slice(1)}`)
      .join(' ');
  },
},
```

#### Переводы
Для текстов нужно добавлять переводы и указывать вывод через функцию `t()`

Плохо:
```
<ui-input placeholder="Введите имя" />
```
Хорошо:
```
<ui-input :placeholder="t('Введите имя')" />
```

### Структура функционального кода

#### Если одно и то же значение используется несколько раз, необходимо вынести его в переменную:
```
const isGroupSelect = selectedBlocks.length > 0;
const textFormat = isGroupSelect ? getTextFormat(selectedBlocks) : DEFAULT_TEXT_FORMAT;
const blockStyles = isGroupSelect ? getBlockStyles(selectedBlocks) : DEFAULT_BLOCK_STYLES;
```

#### Переносить на новую строку .method массива только при использовании в цепочке:

Плохо:
```
const activeUsers = users
  .filter(user => user.is_active);
```
Хорошо:
```
const activeUsers = users.filter(user => user.is_active);
```

#### Для проверки на несколько совпадений можно использовать `.includes`:

Плохо:
```
const isHeader = block.type === 'header' || block.type === 'header2' || block.type === 'header3';
```
Хорошо:
```
const isHeader = ['header', 'header2', 'header3'].includes(block.type);
```

#### Передаваемые атрибуты могут распологаться на одной строке
Если колличество символов в строке не превышает 80. Иначе атрибуты должны располагаться на нескольких строках, по одному атрибуту на строку.

```
this._api.requestRoute('wiki.api.course.review-exam', {}, { 
  course_id: courseId, 
  examinee_id: examineeId, 
  answers_results: answerResults,
}); 
```

#### Вместо отсутствующего скалярного значения используется null

0 и пустую строку нельзя использовать в качестве показателя отсутствия значения.

```
sendEmail(title, message, date) {
  ..
}

// сообщение не было передано
this.sendEmail('title', null, date);

// было передано пустое сообщение
this.sendEmail('title', '', date);
```
Однако, это правило не относится к массивам.

Плохо:
```
deleteUsersByIds(ids = [], someOption = false) {
  ...
}

deleteUsersByIds(null, true);
```
Хорошо:
```
deleteUsersByIds([], true);
```

#### Нельзя изменять переменные, которые передаются в метод на вход

Исключение — если эта переменная объект.

Плохо:
```
parseText(text) {
  text = text.trim();
}
```
Хорошо:
```
parseText(text) {
  trimmedText = text.trim();
}
```

#### Каждая переменная должна быть объявлена на новой строке

Плохо:
```
let foo = false, bar = true;
```
Хорошо:
```
let foo = false;
let bar = true;
```

#### Нельзя нескольким переменным присваивать одно и то же значение

Плохо:
```
async loadUsers(ids) {
  const usersIds = ids;
  // ...
}
```

#### Не используйте boolean переменные (флаги) как параметры функции

Флаг в качестве параметра это признак того, что функция делает больше одной вещи, нарушая [принцип единственной ответственности (Single Responsibility Principle или SRP)](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D0%B5%D0%B4%D0%B8%D0%BD%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D0%B9_%D0%BE%D1%82%D0%B2%D0%B5%D1%82%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D1%81%D1%82%D0%B8). Избавляйтесь от них, выделяя код внутри логических блоков в отдельные ветви выполнения.

Плохо:
```
someMethod() {
  // ...
  const projectNotificationIsEnabled = notificationManager.isProjectNotificationEnabled(project); 
  storeUser(user, projectNotificationIsEnabled);
}
storeUser(user, isNotificationEnabled) {
  // ...
  if (isNotificationEnabled) { 
    notify('new user'); 
  }
}
```
Хорошо:
```
someMethod() { 
  storeUser(user);
  if (notificationManager.isProjectNotificationEnabled(project)) {
    notify('new user'); 
  }
}
storeUser(user) { ... }
```

#### В `.js` файлах все параметры, возвращаемое значение и их типы должны быть описаны в JSDoc.

```
/**
 * @param {Object[]} articles
 * @param {Number} spaceId
 * @param {Number} parentId
 * @returns {Number[]}
 */
export function extractSortedIds(articles = [], spaceId = null, parentId = null) {
  // ...
}
```

#### Параметры в методах должны следовать в следующем порядке: обязательные → часто используемые → редко используемые

Нужно соблюдать читаемость при написании вызова.

Плохо:
```
method(required, practicallyUnused = 5, often = [], lessOften = null) { ... }
```
Хорошо:
```
method(required, often = [], lessOften = null, practicallyUnused = 5)  { ... }
```

#### Метод всегда должен возвращать только одну структуру данных (или `null`) или ничего не возвращать

Метод не может в разных ситуациях возвращать разные типы данных.

Плохо:

loadUser() { 
  if (someCondition) { 
    return { id: 1 }; 
  } 
  return new User();
}

Хорошо:

loadUser() { 
  if (someCondition) { 
    const user = new User(); 
    user.id = 1; 
    return user;
  } 
  return new User();
}

#### Если метод возвращает один объект (или скалярный тип), то в случае, если объект не найден, возвращается null
Если же метод возвращает список объектов, то в случае, когда список пуст, возвращает пустой массив. Нельзя возвращать вместо пустого списка null.

Плохо:
```
loadUsers() {
  if (someCondition) {
    return null;
  }
  return [new User()];
}
```
Хорошо:
```
loadUsers() {
  if (someCondition) {
    return [];
  }
  return [new User()];
}
```

Однако, бывают ситуации, когда надо явно указать, что данные отсутвуют, а не содержат пустой список.

Пример: значения полей объекта задаются пользователем. Возможны две ситуации:

- пользователь не знает, каким категориям принадлежит объект — null.
- пользователь знает, что объект не принадлежит ни одной категории — пустой массив ([]).

Тогда для получения категорий объекта будет правильным такой код:
```
getObjectCategories(object) {
  if (object.categories === null) {
    return null;
  }
  return parseCategories(object.categories);
}
```

#### В больших методах возвращаемая переменная должна называться `result`

Если у вас большой метод, возвращаемая переменная должна называться `result`, если с ней могут происходить изменения в середине работы метода. В любом месте в методе должно быть понятно, где вы оперируете результатом, а где локальными переменными.

Плохо:
```
loadUsers() { 
  const users = []; 
  // ... много кода, изменяющего переменную users 
  return users;
}
```
Хорошо:
```
loadUsers() { 
  const result = []; 
  // ... много кода, изменяющего переменную result 
  return result;
}
```

#### Метод должен явно отличать нормальные ситуации от исключительных
Если никакой ошибки не произошло, но отсутствует результат, то это null (или пустой массив), однако если все же произошла исключительная ситуация, которая не заложена системой, то должно кидаться исключение.

Плохо:
```
loadUsers() {
  if (connectionError !== null) {
    return []; // потеряли ошибку, никто не узнает о проблемах с подключением
  }
  // ...
  if (data.length === 0) {
    return [];
  }
    // ...
  return result;
}
```
Хорошо:
```
loadUsers() {
  if (connectionError !== null) {
    throw new Error();
  }
  // ...
  if (data.length === 0) {
    return [];
  }
  // ...
  return result;
}
```

#### Метод должен придерживаться следующей структуры: Проверка параметров → Получение данных → Работа → Результат
Во время проверки параметров и получения необходимых данных метод должен возвращать соответствующее пустое значение или кидать исключение. После того как метод получил все необходимые данные и приступил к работе выход из метода крайне нежелателен. Возможны редкие исключения, облегчающие понимание и читаемость кода.

Плохо:
```
someMethod() {
  const isValid = this._someCheck();
  if (isValid) {
    let tmp = 0;
    let someValue = this._getSomeValue();
    if (someValue > 0) {
      tmp = someValue;
    }
    anotherValue = this._getAnotherValue();
    if (anotherValue > 0) {
      return tmp + anotherValue;
    } else {
      return someValue;
    }
  } else {
    throw new Error();
  }
}
```
Хорошо:
```
someMethod() {
  const isValid = this._someCheck();
  if (!isValid) {
    throw new Error();
  }
  let result = 0;
  
  let someValue = this._getSomeValue();
  if (someValue > 0) {
    result += someValue;
  }
  anotherValue = this._getAnotherValue();
  if (anotherValue > 0) {
    result += anotherValue;
  }
  return result;
}
```

#### В общем случае комментарии запрещены
Желание добавить комментарий — признак плохо читаемого кода. Любой участок кода, который вы хотели бы выделить или прокомментировать, надо выносить в отдельный метод.

Фразу, которую вы хотели написать в комментарии, надо привести в простой вид и сделать ее названием метода.

Плохо:
```
async deleteApprovedUsers() {
  // load users filter them by approval
  const users = await loadUsers();
  users
    .filter(user => user.is_approved)
    .forEach(user => ...);
}
```
Хорошо:
```
async deleteApprovedUsers() {
  const approvedUsers = await loadApprovedUsers();
  approvedUsers.forEach(user => ...);
}

async loadApprovedUsers() {
  const users = await loadUsers();
  return users.filter(user => user.is_approved);
}
```

#### Вынужденные хаки должны быть помечены комментариями
Лучше соблюдать одинаковый формат в рамках проекта

Хорошо:
```
async loadUsers() {
  const result = await repository.loadUsers();
  // hack: status field was removed from storage 
  result.forEach(user => user.status = 'active');
  // hack end
  return result;
}
```

#### Готовые алгоритмы, взятые из внешнего источника, должны быть помечены ссылкой на источник
Хорошо:
```
/**
 * https://en.wikipedia.org/wiki/Quicksort
 */
quickSort(array) {
  // ...
}

/**
 * https://habrahabr.ru/post/320140/
 */
generateRandomMaze() {
  // ...
}
```

#### При разработке прототипа допустимо помечать участки кода `@todo`
Хорошо:
```
async loadUsers() {
  const result = await repository.loadUsers();
  // @todo: delete the hack when field will be restored
  // hack: status field was removed from storage
  result.forEach(user => user.status = 'active');
  // hack end
  return result;
}
```

### Работа с условиями
#### В условном операторе должно проверяться исключительно boolean значение
Плохо:
```
if (userProjects.length) {
  // ...
}
if (project) {
  // ...
}
```
Хорошо:
```
if (isResponseError) { // isResponseError = true
  // ...
}
if (response.isError()) { // isError method returns boolean
  // ...
}
if (userProjects.length > 0) {
  // ...
}
```

#### В сравнении не boolean переменных используется строгое сравнение с приведением типа (===), автоматическое приведение и нестрогое сравнение не используются
Плохо:
```
if (request.sum == 100) {
  // ...
}
if (!request.sum) {
  // ...
}
if (!bill.comment) {
  // ...
}
```
Хорошо:
```
if (Number(request.sum) === 100) {
  // ...
}
if (bill.comment === '') {
  // ...
}
```

#### Автоматическое приведение типов разрешено только, когда один из операндов — литерал с фиксированным типом
При сравнении двух переменных с неизвестными типами для читающего код человека не очевидно, к чему они будут приведены интерпретатором. Если же тип одного из операндов известен, то всё становится очевидно и ручное приведение типов не требуется.

Если вы хотите проверить значение boolean пришедшее извне, то делается это так:

Плохо:
```
if (Number(request.is_something) > 0) {
  // ...
}
if (Number(request.is_something) === 1) {
  // ...
}
if (Number(user.is_registered) === 0) {
  // ...
}
```
Хорошо:
```
if (request.is_something > 0) {
  // ...
}
if (user.is_registered) {
  // ...
}
if (!user.is_registered) {
  // ...
}
```

#### Не надо сравнивать boolean с true/false
Это нарушает запрет на бесполезный код.

Плохо:
```
if (bill.isPaid() == true) {
  // ...
}
if (bill.isPaid() !== false) {
  // ...
}
if (!bill.isPaid() === true) {
  // ...
}
if (!(!bill.isPaid() === true)) {
  // ...
}
if (Boolean(phone.is_external) === true) {
  // ...
}
```
Хорошо:
```
if (bill.isPaid()) {
    // ...
}
```

#### Проверять переменные надо на наличие позитивного вхождения, а не отсутствие негативного
Если вам нужна строка, то проверять надо на то, что переменная является строкой. Не надо проверять на то, что она не является числом или чем-то еще. Перечислять все возможные варианты, чем переменная не должна быть, значит повышать риск ошибки и усложнять поддержку кода.

Плохо:
```
if (!isNumber(value) && !isObject(value)) {
  // ...
}
```
Хорошо:
```
if (isString(value) && value !== '') {
  // ...
}
```

#### При использовании в условном выражении одновременно операторов И и ИЛИ обязательно выделять приоритет скобками
Обратите внимание на различие в значении двух вариантов правильного использования

Плохо:
```
if (isMobile || isSizeTooBig && isAllowedToShrink) {
  // ...
}
```
Хорошо:
```
if ((isMobile || isSizeTooBig) && isAllowedToShrink) {
  // ...
}
if (isMobile || (isSizeTooBig && isAllowedToShrink)) {
  // ...
}
```

#### Условия c && и || указывать в одну строку:

Плохо:
```
.filter(entry =>
  entry.userId !== userId &&
  accessKeys.every(key => entry.keys.includes(key)) &&
  entry.keys.every(key => accessKeys.includes(key))
)
```

Если условие получается слишком длинным и нечитабельным, необходимо вынести каждый блок условия в константу с понятным именем:

Хорошо:
```
.filter(entry => {
  const userIsActive = this.activeUserIds.includes(entry.userId);
  const userHasAccess = entry.accessKeys.includes(accessKey);
  const blockHasAdminAccess = this.adminBlockIds.includes(entry.blockId);
  return userIsActive && userHasAccess && blockHasAdminAccess;
});
```

### Стилизация
#### Цвета
Цвет следует описывать шестизначным hex. Если заливка требует указания непрозрачности - rgba.