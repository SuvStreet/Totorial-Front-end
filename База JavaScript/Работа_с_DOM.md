<h1>Работа с DOM</h1>

- [Что такое DOM-дерево](#что_такое_DOM-дерево)
- [Получение элементов DOM](#получение_элементов_DOM)
  - `getElementById()`
  - `getElementsByClassName()`
  - `getElementsByTagName()`
  - `querySelector()`
  - `querySelectorAll()`
- [Свойства и методы HTML-элементов](свойства_и_методы_HTML-элементов)
  - `id`
  - `className`
  - `innerText`
  - `innerHTML`
  - `children`
- [Data-атрибуты](data-атрибуты)
  - `dataset`
- [Стили](стили)
  - `style`
- [Создание HTML-элементов и добавление их в DOM](создание_HTML-элементов_и_добавление_их_в_DOM)

---

<h2><a name="что_такое_DOM-дерево">Что такое DOM-дерево</a></h2>

`DOM (Document Object Model)` — объектная модель документа. Это технология, позволяющая представить веб-страницу в виде дерева объектов. Каждый тег HTML в этом дереве представлен в виде отдельного объекта.

<h2><a name="получение_элементов_DOM">Получение элементов DOM</a></h2>

Для поиска по всему документу методы вызываются через объект `document`, например `document.getElementById("main")`.

- `getElementById()` - позволяет получить элемент по идентификатору, то есть по значению атрибута `id`.

- `getElementsByClassName()` - позволяет получать элементы по названию класса.

- `getElementsByTagName()` - находит все элементы по названию тега.

- `querySelector()` - более современный и универсальный способ. С помощью этого одного метода можно получать элементы разными способами:

  - Поиск по идентификатору:
    ```js
    const div = document.querySelector("#main");
    ```
    `#` - Это [селектор по идентификатору](https://developer.mozilla.org/ru/docs/Web/CSS/ID_selectors)

  - Поиск по классу:
    ```js
    const paragraph = document.querySelector(".text");
    ```
    `.` - [селектор по классу](https://developer.mozilla.org/ru/docs/Web/CSS/Class_selectors)

  - Поиск по тегу (типу элемента):
    ```js
    const paragraph = document.querySelector("p");
    ```
    [Селектор по типу](https://developer.mozilla.org/ru/docs/Web/CSS/Type_selectors) не требует дополнительных символов перед названием типа

  - Поиск по значению атрибута:
    ```js
    const paragraph = document.querySelector("[data-id='2']");
    ```
    [Селектор по атрибуту](https://developer.mozilla.org/ru/docs/Web/CSS/Attribute_selectors) включает в себя название и значение атрибута, заключенные в квадратные скобки

    Также в селекторе по атрибуту можно не указывать значение атрибута, тогда будут найдены все элементы с этим атрибутом.

  - Комбинированный поиск по селектору:
    ```js
    const elements = document.querySelector("#main p.text");
    ```
    В этом примере осуществляется поиск всех элементов `p` с классом `text`, вложенных внутрь элемента с идентификатором `#main`. Пробел указывает на поиск по потомкам ([селектор потомков](https://developer.mozilla.org/ru/docs/Web/CSS/Descendant_combinator)).
    

- `querySelectorAll()` - Для получения всех элементов по заданному условию. Работает аналогичным образом, как и метод `querySelector()`, разница только в количестве возвращаемых элементов.

<h2><a name='свойства_и_методы_HTML-элементов'>Свойства и методы HTML-элементов</a></h2>

Любой HTML-элемент имеет следующие основные свойства:

- [Свойство `id`](https://developer.mozilla.org/ru/docs/Web/API/Element/id) — идентификатор элемента:

```js
  const div = document.querySelector("#main");
  console.log(div.id); // main
```

 - [Свойство `className`](https://developer.mozilla.org/ru/docs/Web/API/Element/className) — CSS-класс элемента:

```js
  const paragraph = document.querySelector(".text");
  console.log(paragraph.className); // text
```

- Свойство [`innerText`](https://developer.mozilla.org/ru/docs/Web/API/HTMLElement/innerText) и свойство [`textContent`](https://developer.mozilla.org/ru/docs/Web/API/Node/textContent) — текстовое содержимое внутри элемента. 

[Есть небольшие различия в работе этих свойств](https://developer.mozilla.org/ru/docs/Web/API/Node/textContent):

```js
  const paragraph = document.querySelector(".text");
  console.log(paragraph.innerText); // Первый абзац
  console.log(paragraph.textContent); // Первый абзац
```

- Свойство [`innerHTML`](https://developer.mozilla.org/ru/docs/Web/API/Element/innerHTML) — содержит в себе код HTML-разметки внутри элемента:

```js
  const div = document.querySelector("#main");
  console.log(div.innerHTML);
```

- Свойство [`children`](https://developer.mozilla.org/en-US/docs/Web/API/Element/children) — коллекция дочерних элементов:

```js
  const div = document.querySelector("#main");
  console.log(div.children);
```

<h2><a name='data-атрибуты'>Data-атрибуты</a></h2>

[Data-атрибуты](https://developer.mozilla.org/ru/docs/Web/HTML/Global_attributes/data-*) — это атрибуты HTML-элементов, название которых начинается с `data-`.

Data-атрибуты позволяют хранить дополнительную информацию в стандартных элементах HTML, что бывает очень полезно. То есть с их помощью можно создавать свои собственные атрибуты для элементов.

Получить коллекцию data-атрибутов можно с помощью свойства `dataset`:

```js
  const paragraph = document.querySelector(".text");
  console.log(paragraph.dataset);
```

Изменить значение `data-атрибута` можно так же, как и обычное свойство любого объекта:

```js
  paragraph.dataset.id = 123;
```

<h2><a name='стили'>Стили</a></h2>

К коллекции стилей элемента можно обратиться с помощью свойства `style`, например:

```js
  const paragraph = document.querySelector(".text");
  console.log(paragraph.style);
```

В консоль будет выведен длинный список всех возможных стилей элемента.

Задать стиль можно обратившись к конкретному свойству объекта `style`:

```js
  paragraph.style.color = "red";
  paragraph.style.backgroundColor = "gray";
```

<h2><a name='создание_HTML-элементов_и_добавление_их_в_DOM'>Создание HTML-элементов и добавление их в DOM</a></h2>


























