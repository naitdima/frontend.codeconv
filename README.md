### Нейминг

##### Имена файлов однофайловых компонентов должны быть всегда в PascalCase

PascalCase лучше всего работает с автодополнением в редакторах кода, поскольку он согласуется с тем, как мы ссылаемся на компоненты в JS(X) и шаблонах.

##### Имена компонентов должны состоять из полных слов, а не аббревиатур

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

##### Имена компонентов должны всегда состоять из нескольких слов, за исключением корневого компонента `App`

Это предотвращает конфликты с существующими или будущими HTML-элементами, поскольку все HTML-элементы именуются одним словом.

##### Порядок слов в именах компонентов

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

##### Входные параметры

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

### Структура компонентов

##### Порядок опций компонента/экземпляра

Опции компонента/экземпляра должны быть упорядочены консистентно:

1. **Побочные эффекты** (вызывает эффекты вне компонента)
    - `el`
2. **Глобальная осведомлённость** (требует знаний вне компонента)
    - `name`
    - `parent`
3. **Тип компонента** (изменяет тип компонента)
    - `functional`
4. **Модификаторы шаблона** (изменение способа компиляции шаблонов)
    - `delimiters`
    - `comments`
5. **Зависимости шаблона** (ресурсы, используемые в шаблоне)
    - `components`
    - `directives`
    - `filters`
6. **Композиция** (объединение свойств в опциях)
    - `extends`
    - `mixins`
7. **Интерфейс** (интерфейс компонента)
    - `inheritAttrs`
    - `model`
    - `props`/`propsData`
8. **Хуки жизненного цикла** (коллбэки в процессе жизни компонента, в порядке объявления)
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
9. **Локальное состояние** (локальные реактивные свойства)
    - `data`
    - `computed`
10. **События** (коллбэки вызываемые реактивными событиями)
    - `watch`
11. **Нереактивные свойства** (свойства экземпляра независимые от системы реактивности)
    - `methods`
12. **Отрисовка** (декларативное описание вывода компонента)
    - `template`/`render`
    - `renderError`
    
##### Пустые строки между опций компонента/экземпляра

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

##### Определение входных параметров

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

##### Простые вычисляемые свойства

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

##### Локальные стили компонента

Для приложений стили в корневом компоненте `App` и в компонентах шаблона могут быть глобальными, но во всех остальных компонентах должны быть локальными.

```
<style scoped>
  .kpi-list { 
    background-color: ligthgrey;
  }
</style>
```

### Разметка шаблона

##### Самозакрывающиеся теги компонентов

Компоненты без содержимого должны быть самозакрывающимися тегами в однофайловых компонентах, строковых шаблонах и JSX.

Самозакрывающиеся теги компонентов сообщают, что у них не только нет содержимого, но и сообщает что и не должны иметь содержимого. Это разница между пустой страницей в книге и страницей с надписью: «Эта страница намеренно оставлена пустой». Ваш код также станет более лаконичным без ненужного закрывающего тега.

```
<my-component/>
```

##### Элементы с несколькими атрибутами

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

1. **Определение**
    - `is`
2. **Отображение списка**
    - `v-for`
    - `key`
3. **Условия** (указывается отрисовывается/отображается ли элемент)
    - `v-if`
    - `v-else-if`
    - `v-else`
    - `v-show`
    - `v-cloak`
4. **Модификаторы отрисовки** (изменяют способ отрисовки элемента)
    - `v-pre`
    - `v-once`
5. **Глобальная осведомлённость** (требует знаний вне компонента)
    - `id`
6. **Уникальные атрибуты** (атрибуты, требующие уникальных значений)
    - `ref`
    - `slot`
7. **CSS-классы**
    - `class`
8. **Двусторонняя привязка** (объединение привязки и событий)
    - `v-model`
9. **Другие атрибуты** (все неуказанные связанные или несвязанные атрибуты)
10. **События** (обработчики событий компонента)
    - `@`
11. **Содержимое** (перезаписывает содержимое элемента)
    - `v-html`
    - `v-text`

##### Значения атрибутов в кавычках

Непустые значения HTML-атрибутов должны быть обрамлены двойными кавычками.
```
<input type="radio">
```

##### Сокращённая запись директив

Следует использовать сокращённую запись директив (`:` для `v-bind:`, `@` для `v-on:` и `#` для `v-slot`).

```
<input :value="newTodoText">
<input @focus="onFocus">
<template #header> 
  <h1>Заголовок страницы</h1>
</template>
```

##### Всегда используйте `key` с `v-for`

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

##### Избегайте использования `v-if` с `v-for`

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

##### Простые выражения в шаблонах

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

##### Переводы
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

##### Если одно и то же значение используется несколько раз, необходимо вынести его в переменную:
```
const isGroupSelect = selectedBlocks.length > 0;
const textFormat = isGroupSelect ? getTextFormat(selectedBlocks) : DEFAULT_TEXT_FORMAT;
const blockStyles = isGroupSelect ? getBlockStyles(selectedBlocks) : DEFAULT_BLOCK_STYLES;
```

##### Переносить на новую строку .method массива только при использовании в цепочке:

Плохо:
```
const activeUsers = users
  .filter(user => user.is_active);
```
Хорошо:
```
const activeUsers = users.filter(user => user.is_active);
```

##### Итерируемый элемент массива должен одинаково именоваться в цепочках методов массива:

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

##### Для проверки на несколько совпадений можно использовать `.includes`:

Плохо:
```
const isHeader = block.type === 'header' || block.type === 'header2' || block.type === 'header3';
```
Хорошо:
```
const isHeader = ['header', 'header2', 'header3'].includes(block.type);
```

##### Условия c && и || указывать в одну строку:

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
