###Нейминг
##### **[Имена компонентов должны всегда состоять из нескольких слов, за исключением корневого компонента `App`](https://ru.vuejs.org/v2/style-guide/#%D0%98%D0%BC%D0%B5%D0%BD%D0%B0-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%B8%D0%B7-%D0%BD%D0%B5%D1%81%D0%BA%D0%BE%D0%BB%D1%8C%D0%BA%D0%B8%D1%85-%D1%81%D0%BB%D0%BE%D0%B2-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE)**

Это предотвращает конфликты с существующими или будущими HTML-элементами, поскольку все HTML-элементы именуются одним словом.

##### **[Имена компонентов должны состоять из полных слов, а не аббревиатур](https://ru.vuejs.org/v2/style-guide/#%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BF%D0%BE%D0%BB%D0%BD%D1%8B%D1%85-%D1%81%D0%BB%D0%BE%D0%B2-%D0%BF%D1%80%D0%B8-%D0%B8%D0%BC%D0%B5%D0%BD%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Плохо:
```components/
|- SdSettings.vue
|- UProfOpts.vue
```
Хорошо:
```components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

##### **[Имена файлов однофайловых компонентов должны быть всегда в PascalCase](https://ru.vuejs.org/v2/style-guide/#%D0%98%D0%BC%D0%B5%D0%BD%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B4%D0%BD%D0%BE%D1%84%D0%B0%D0%B9%D0%BB%D0%BE%D0%B2%D1%8B%D1%85-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

PascalCase лучше всего работает с автодополнением в редакторах кода, поскольку он согласуется с тем, как мы ссылаемся на компоненты в JS(X) и шаблонах.

##### **[Порядок слов в именах компонентов](https://ru.vuejs.org/v2/style-guide/#%D0%9F%D0%BE%D1%80%D1%8F%D0%B4%D0%BE%D0%BA-%D1%81%D0%BB%D0%BE%D0%B2-%D0%B2-%D0%B8%D0%BC%D0%B5%D0%BD%D0%B0%D1%85-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Компоненты должны именоваться с высшего уровня (часто наиболее общих слов) и заканчиваться описательными дополняющими словами.

Плохо:
```components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue
```

Хорошо:
```components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```

##### **[Стиль именования входных параметров](https://ru.vuejs.org/v2/style-guide/#%D0%A1%D1%82%D0%B8%D0%BB%D1%8C-%D0%B8%D0%BC%D0%B5%D0%BD%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F-%D0%B2%D1%85%D0%BE%D0%B4%D0%BD%D1%8B%D1%85-%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Входные параметры должны всегда использовать camelCase при определении, но kebab-case в шаблонах.
```
props: { 
  greetingText: String,
}

<welcome-message greeting-text="hi"/>
```

### Структура однофайловых компонентов

##### **[Порядок опций компонента/экземпляра](https://ru.vuejs.org/v2/style-guide/#%D0%9F%D0%BE%D1%80%D1%8F%D0%B4%D0%BE%D0%BA-%D0%BE%D0%BF%D1%86%D0%B8%D0%B9-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%B0-%D1%8D%D0%BA%D0%B7%D0%B5%D0%BC%D0%BF%D0%BB%D1%8F%D1%80%D0%B0-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

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
7. **Хуки жизненного цикла** (коллбэки в процессе жизни компонента, в порядке объявления)
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
8. **Локальное состояние** (локальные реактивные свойства)
    - `data`
    - `computed`
9. **События** (коллбэки вызываемые реактивными событиями)
    - `watch`
10. **Нереактивные свойства** (свойства экземпляра независимые от системы реактивности)
    - `methods`
11. **Отрисовка** (декларативное описание вывода компонента)
    - `template`/`render`
    - `renderError`
    
##### **[Пустые строки между опций компонента/экземпляра](https://ru.vuejs.org/v2/style-guide/#%D0%9F%D1%83%D1%81%D1%82%D1%8B%D0%B5-%D1%81%D1%82%D1%80%D0%BE%D0%BA%D0%B8-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%BE%D0%BF%D1%86%D0%B8%D0%B9-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%B0-%D1%8D%D0%BA%D0%B7%D0%B5%D0%BC%D0%BF%D0%BB%D1%8F%D1%80%D0%B0-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Когда компоненты кажутся неразборчивыми и становятся трудными для чтения, то добавление пустых строк между многострочными свойствами может облегчить их беглое изучение просматривая взглядом.

```
props: {
  value: { type: String, required: true }, 
  focused: { type: Boolean, default: false }, 
  label: String, 
  icon: String,
},

computed: { 
  formattedValue: function () { // ... }, 
  inputClasses: function () { // ... }
},
```

##### **[Определение входных параметров](https://ru.vuejs.org/v2/style-guide/#%D0%9E%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B2%D1%85%D0%BE%D0%B4%D0%BD%D1%8B%D1%85-%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE)**

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
      return [ 'syncing', 'synced', 'version-conflict', 'error' ].include(value); 
    },
  },
},
```

##### **[Локальные стили компонента](https://ru.vuejs.org/v2/style-guide/#%D0%9B%D0%BE%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5-%D1%81%D1%82%D0%B8%D0%BB%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%B0-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE)**

Для приложений стили в корневом компоненте `App` и в компонентах шаблона могут быть глобальными, но во всех остальных компонентах должны быть локальными.

```
<style scoped>
  .kpi-list { 
    background-color: ligthgrey;
  }
</style>
```

##### **[Простые вычисляемые свойства](https://ru.vuejs.org/v2/style-guide/#%D0%9F%D1%80%D0%BE%D1%81%D1%82%D1%8B%D0%B5-%D0%B2%D1%8B%D1%87%D0%B8%D1%81%D0%BB%D1%8F%D0%B5%D0%BC%D1%8B%D0%B5-%D1%81%D0%B2%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Комплексные вычисляемые свойства должны быть разделены на максимально простые свойства.

Плохо:
```
computed: {
  price() { 
    const basePrice = this.manufactureCost / (1 - this.profitMargin);
    return (basePrice - basePrice * (this.discountPercent || 0));
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

### Разметка шаблона

##### **[Самозакрывающиеся теги компонентов](https://ru.vuejs.org/v2/style-guide/#%D0%A1%D0%B0%D0%BC%D0%BE%D0%B7%D0%B0%D0%BA%D1%80%D1%8B%D0%B2%D0%B0%D1%8E%D1%89%D0%B8%D0%B5%D1%81%D1%8F-%D1%82%D0%B5%D0%B3%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Компоненты без содержимого должны быть самозакрывающимися тегами в однофайловых компонентах, строковых шаблонах и JSX.

Самозакрывающиеся теги компонентов сообщают, что у них не только нет содержимого, но и сообщает что и не должны иметь содержимого. Это разница между пустой страницей в книге и страницей с надписью: «Эта страница намеренно оставлена пустой». Ваш код также станет более лаконичным без ненужного закрывающего тега.

```
<my-component/>
```

##### **[Всегда используйте `key` с `v-for`](https://ru.vuejs.org/v2/style-guide/#%D0%A3%D0%BD%D0%B8%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5-%D0%BA%D0%BB%D1%8E%D1%87%D0%B8-%D0%B4%D0%BB%D1%8F-v-for-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE)**

`key` с `v-for` всегда обязателен для компонентов, для поддержания внутреннего состояния компонента и его поддерева. Даже для элементов это хорошая практика для поддержания предсказуемого поведения, такого как [консистентности объекта](https://bost.ocks.org/mike/constancy/) в анимации.

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

##### **[Избегайте использования `v-if` с `v-for`](https://ru.vuejs.org/v2/style-guide/#%D0%98%D0%B7%D0%B1%D0%B5%D0%B3%D0%B0%D0%B9%D1%82%D0%B5-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F-v-if-%D1%81-v-for-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE)**

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


##### **[Элементы с несколькими атрибутами](https://ru.vuejs.org/v2/style-guide/#%D0%AD%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D1%81-%D0%BD%D0%B5%D1%81%D0%BA%D0%BE%D0%BB%D1%8C%D0%BA%D0%B8%D0%BC%D0%B8-%D0%B0%D1%82%D1%80%D0%B8%D0%B1%D1%83%D1%82%D0%B0%D0%BC%D0%B8-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Элементы с несколькими атрибутами могут распологаться на одной строке, если колличество символов в строке не превышает 80. Иначе атрибуты должны располагаться на нескольких строках, по одному атрибуту на строку.

```
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">

<input type="number" name="age" min="18" max="130" step="1">

<input
  type="text"
  name="firstname"
  placeholder="Enter your name, John.."
  pattern="/John/"
>
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
8. **CSS-классы**
    - `class`
8. **Двусторонняя привязка** (объединение привязки и событий)
    - `v-model`
9. **Другие атрибуты** (все неуказанные связанные или несвязанные атрибуты)
10. **События** (обработчики событий компонента)
    - `@`
11. **Содержимое** (перезаписывает содержимое элемента)
    - `v-html`
    - `v-text`

##### **[Простые выражения в шаблонах](https://ru.vuejs.org/v2/style-guide/#%D0%9F%D1%80%D0%BE%D1%81%D1%82%D1%8B%D0%B5-%D0%B2%D1%8B%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D1%8F-%D0%B2-%D1%88%D0%B0%D0%B1%D0%BB%D0%BE%D0%BD%D0%B0%D1%85-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Шаблоны компонентов должны содержать только простые выражения, а более комплексные должны быть вынесены в вычисляемые свойства или методы.

Сложные выражения в ваших шаблонах делают их менее декларативными. Мы должны стремиться к описанию *что* должно отобразиться, а не *как* мы вычисляем это значение. Вычисляемые свойства и методы также упрощают переиспользование кода.

```
<span>{{ normalizedFullName }}</span>

computed: { 
  normalizedFullName() { 
    return this.fullName.split(' ').map(function (word) { return word[0].toUpperCase() + word.slice(1) }).join(' ')
  }
}
```

##### **[Значения атрибутов в кавычках](https://ru.vuejs.org/v2/style-guide/#%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F-%D0%B0%D1%82%D1%80%D0%B8%D0%B1%D1%83%D1%82%D0%BE%D0%B2-%D0%B2-%D0%BA%D0%B0%D0%B2%D1%8B%D1%87%D0%BA%D0%B0%D1%85-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Непустые значения HTML-атрибутов должны быть обрамлены двойными кавычками.

Хотя значения атрибутов без каких-либо пробелов не требуют иметь кавычки в HTML, эта практика зачастую приводит к избеганию использования пробелов, делая значения атрибутов менее читабельными.

```
<input type="radio">
```

##### **[Сокращённая запись директив](https://ru.vuejs.org/v2/style-guide/#%D0%A1%D0%BE%D0%BA%D1%80%D0%B0%D1%89%D1%91%D0%BD%D0%BD%D0%B0%D1%8F-%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D1%8C-%D0%B4%D0%B8%D1%80%D0%B5%D0%BA%D1%82%D0%B8%D0%B2-%D0%BD%D0%B0%D1%81%D1%82%D0%BE%D1%8F%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE-%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D1%83%D0%B5%D1%82%D1%81%D1%8F)**

Следует использовать сокращённую запись директив (`:` для `v-bind:`, `@` для `v-on:` и `#` для `v-slot`).

```
<input :value="newTodoText">
<input @focus="onFocus">
<template #header> 
  <h1>Заголовок страницы</h1>
</template>
```

### Структура функционального кода

Если одно и то же значение используется несколько раз, необходимо вынести его в переменную:
```
const isGroupSelect = this.selectedBlocksKeys.length > 0;
const blockRect = isGroupSelect
  ? getElementClientRectangle(this.findBlockElementByKey(this.selectedBlocksKeys[0]).$el)
  : range;
this.textFormat = isGroupSelect
  ? DEFAULT_TEXT_FORMAT
  : textFormat;
this.styledBlockKeys = isGroupSelect
  ? this.selectedBlocksKeys.filter(key => !NON_TEXT_BLOCKS.includes(this.findBlockByKey(key).type))
  : blockKeys;
```

Итерируемый элемент массива должен одинаково именоваться в цепочках методов массива:
```
Плохо:
const answeredQuestionIds = Object.keys(this.value)
  .filter(questionId => Object.values(this.value[questionId]).some(answer => answer))
  .map(id => parseInt(id, 10));

Хорошо:
const answeredQuestionIds = Object.keys(this.value)
  .filter(questionId => Object.values(this.value[questionId]).some(answer => answer))
  .map(questionId => parseInt(id, 10));
```

Проверку на несколько совпадений можно организовать с помощью массива:
```
Плохо:
const isHeader = currentBlock.type === 'header' || currentBlock.type === 'header2';
Хорошо:
['header', 'header2'].includes(currentBlock.type)
```

this.$refs.input.setSelectionRange(0, this.$refs.input.value.length);
для большей наглядности вместо значения в v-model использовать значение самого инпута


Условия c && и || указывать в одну строку: 
```
Плохо:
.filter(entry =>
  entry.userId !== userId &&
  accessKeys.every(key => entry.keys.includes(key)) &&
  entry.keys.every(key => accessKeys.includes(key))
)
Хорошо:
.filter(entry => entry.userId !== userId && this.activeUserIds.include(entry.userId) && accessKeys.every(key => entry.keys.includes(key)) && entry.keys.every(key => accessKeys.includes(key));
)
```

Если условие получается слишком длинным и нечитабельным, необходимо вынести каждый блок условия в константу с понятным именем:
```
.filter(entry => {
  const isActive = entry.userId !== userId && this.activeUserIds.include(entry.userId);
  const userWithAccess = accessKeys.every(key => entry.keys.includes(key)); 
  const blockWithAdminAccess = entry.keys.every(key => accessKeys.includes(key);
  return isActive && userWithAccess && blockWithAdminAccess;
});
```

Переносить на новую строку .method массива только при использовании в цепочке:
```
Плохо:
entries
  .filter(entry => activeEntries.include(entry))

Хорошо:
entries.filter(entry => activeEntries.include(entry))
```
