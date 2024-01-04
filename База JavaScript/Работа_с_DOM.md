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
  - `createElement()`
- [Добавление элемента на страницу](добавление_элемента_на_страницу)
  - `prepend()`
  - `append()`
  - `before()`
  - `after()`
  - `replaceWith()`
  - `insertAdjacentElement()`
  - `insertAdjacentHTML()`
    - `"beforebegin"`
    - `"afterbegin"`
    - `"beforeend"`
    - `"afterend"`
- [Остальные методы HTML-элементов](остальные_методы_HTML-элементов)
  - `remove()`
  - `closest()`
  - `classList`
    - `add()`
    - `remove()`
    - `toggle()`
    - `replace()`
  - `hasAttribute()`
  - `getAttribute()`
  - `setAttribute()`
  - `removeAttribute()`
- [Обработчики событий. Событие "click"](обработчики_событий._событие_click)
  - `"click"`
    - `addEventListenter()`
    - `event.target`
  - `"submit"`
    - `form.elements`
    - `event.preventDefault()`
  - `"keydown"`
  - `"keyup"`
    - `event.key`
  - `"mouseover"`
  - `"mouseout"`
  - `"contextmenu"`
  - `"change"`
  - `"input"`
- [Всплытие и погружение. Прекращение всплытия](всплытие_и_погружение._прекращение_всплытия)
  - `event.stopPropagation()`
- [Делегирование событий](делегирование_событий)

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

Создать элемент можно с помощью метода [`createElement()`](https://developer.mozilla.org/ru/docs/Web/API/Document/createElement).

```js
  const newParagraph = document.createElement("p");
```

<h2><a name='добавление_элемента_на_страницу'>Добавление элемента на страницу</a></h2>

  - [`prepend()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/prepend) — вставляет элемент `в начало` заданного узла.
  - [`append()`](https://developer.mozilla.org/ru/docs/Web/API/Element/append) — вставляет элемент `в конец` узла. 
  - [`before()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/before) — вставляет элемент `пере` узлом.
  - [`after()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/after) — вставляет элемент `после` узла.

![](https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/350.png)

  - [`replaceWith()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/replaceWith) - позволяет `заменить` один элемент на другой. 

  - [`insertAdjacentElement()`](https://developer.mozilla.org/ru/docs/Web/API/Element/insertAdjacentElement) - позволяет добавить элемент в нужную позицию в зависимости от указанных параметров.

```js
  elem.insertAdjacentElement(where, newElem);
```

где `elem` — существующий элемент, внутрь или рядом с которым нужно вставить новый элемент `newElem`.

  - [`insertAdjacentHTML()`](https://developer.mozilla.org/ru/docs/Web/API/Element/insertAdjacentHTML) - позволяет добавить элемент в нужную позицию в зависимости от указанных параметров.

```js
  elem.insertAdjacentHTML(where, text);
```

где `elem` — существующий элемент, `text` - строка, которая будет проанализирована как HTML и вставлена в DOM дерево документа.

Параметр `where` может принимать следующие значения:

  - `"beforebegin"` – вставить newElem непосредственно `перед` elem,
  - `"afterbegin"` – вставить newElem `в начало` elem,
  - `"beforeend"` – вставить newElem `в конец` elem,
  - `"afterend"` – вставить newElem непосредственно `после` elem.

<h2><a name='остальные_методы_HTML-элементов'>Остальные методы HTML-элементов</a></h2>

- [`remove()`](https://developer.mozilla.org/ru/docs/Web/API/Element/remove) - `удаляет` элемент из DOM-дерева.

- [`closest()`](https://developer.mozilla.org/ru/docs/Web/API/Element/closest) - `находит ближайший родительский элемент` по заданному селектору.

Сам элемент тоже включается в поиск, то есть если сам элемент удовлетворяет условию селектора, то будет возвращен он.

- [`classList`](https://developer.mozilla.org/ru/docs/Web/API/Element/classList) - содержит в себе коллекцию классов элемента
  - [`add()`](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/add) — `добавляет` класс к элементу
  - [`remove()`](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/remove) — `удаляет` класс
  - [`toggle()`](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/toggle) — `добавляет` класс, `если его ещё нет`, иначе удаляет
  - [`replace()`](https://developer.mozilla.org/ru/docs/Web/API/DOMTokenList/replace) — `заменяет` один класс другим

- [`hasAttribute()`](https://developer.mozilla.org/ru/docs/Web/API/Element/hasAttribute) — `имеет ли` элемент указанный атрибут. Возвращает булево значение.
- [`getAttribute()`](https://developer.mozilla.org/ru/docs/Web/API/Element/getAttribute) — `получает` значение атрибута по имени
- [`setAttribute()`](https://developer.mozilla.org/ru/docs/Web/API/Element/setAttribute) — `устанавливает` значение атрибута
- [`removeAttribute()`](https://developer.mozilla.org/ru/docs/Web/API/Element/removeAttribute) — `удаляет` атрибут

<h2><a name='обработчики_событий._событие_click'>Обработчики событий. Событие "click".</a></h2>

`Событие` — это любое действие пользователя, на которое веб-страница может реагировать. Существует множество событий, которые можно обработать.

`Обработчик события` — это код на JavaScript, который срабатывает при запуске события.

- [`"click"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event) - происходит, когда пользователь кликает левой кнопкой мыши по элементу.

Добавление обработчика события делается с помощью метода [`addEventListenter()`](https://developer.mozilla.org/ru/docs/Web/API/EventTarget/addEventListener). Первым параметром он принимает `название события`, вторым — `функцию-обработчик`.

```js
  addEventListener("click", (event) => {});
  onclick = (event) => {};
```

Функция "обработчик событий" принимает один параметр [`event`](https://developer.mozilla.org/ru/docs/Web/API/Event), который содержит различные данные о событии.

  -  - [`event.target`](https://developer.mozilla.org/ru/docs/Web/API/Event/target) - указывает на элемент, который был инициатором события, в данном случае элемент по которому был произведен клик.

  -  - [`Элемент HTML form (<form>)`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/form) — это раздел документа, содержащий интерактивные элементы управления, которые позволяют пользователю отправлять информацию на веб-сервер.

- [`"submit"`](https://developer.mozilla.org/ru/docs/Web/API/HTMLFormElement/submit_event) - обработчик события отправки формы

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  const textToAdd = event.target.elements.text.value;
});
```

  -  - [`event.preventDefault()`](https://developer.mozilla.org/ru/docs/Web/API/Event/preventDefault) - отменяет поведение по умолчанию

Поле ввода мы получили через свойство [`elements`](https://developer.mozilla.org/ru/docs/Web/API/HTMLFormElement/elements) у формы (в `event.target` содержится форма). Через это свойство можно получить любой контролл (поле ввода) из формы. Для этого мы обращаемся к `elements` и через точку пишем название атрибута `name` того поля, которое мы хотим получить. Нашей записью `event.target.elements.text` мы получили из формы `<input name="text">`. Таким образом с `elements` мы можем работать как с объектом, где ключи — значения атрибутов name у полей ввода, а значения — сами поля ввода.

Далее из полученного поля ввода (`<input>`) извлекаем значение через свойство `value`, т. е. полная запись — `event.target.elements.text.value`. 

- [`"keydown"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/keydown_event) - обработка `нажатия` кнопоки клавиатуры
- [`"keyup"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/keyup_event) - обработка `отпускания` кнопоки клавиатуры

  - [`event.key`](https://developer.mozilla.org/ru/docs/Web/API/KeyboardEvent/key) - получим информацию о нажатой кнопке

- [`"mouseover"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseover_event) - срабатывает, когда пользователь `наводит` курсор мыши на элемент.
- [`"mouseout"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseover_event) - срабатывает, когда пользователь `уводит` курсор мыши с элемента.

- [`"contextmenu"`](https://developer.mozilla.org/en-US/docs/Web/API/Element/contextmenu_event) - срабатывает при открытии контекстного меню, то есть когда пользователь кликает правой кнопкой мыши по любой части страницы.

- [`"change"`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/change_event) - срабатывает при изменении значения элемента формы, когда это изменение зафиксировано. Для текстовых элементов событие происходит не при каждом вводе, а при потере фокуса.

- [`"input"`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event) - срабатывает каждый раз при изменении значения текстового поля.

<h2><a name='всплытие_и_погружение._прекращение_всплытия'>Всплытие и погружение. Прекращение всплытия</a></h2>

Распространение события делится на 3 фазы:

- **Фаза погружения** – от `window` к цели (цель – это объект, в котором возникло событие).
- **Фаза цели** – событие на цели.
- **Фаза всплытия** – обратно, от цели к `window`.

![](https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/336.png)

Чтобы "поймать" событие на стадии погружения, нужно добавить обработчик события с помощью метода `addEventListener()` и добавить в нёго третий параметр со значением `true` (предположим, что элементы `<body>`, `<div>` и `<p>` уже найдены):

```js
  body.addEventListener("click", () => alert("body"), true);
  div.addEventListener("click", () => alert("div"), true);
  p.addEventListener("click", () => alert("p"), true);
```

Остановить распространение события можно с помощью метода `event.stopPropagation()`, например:

```js
  div.addEventListener("click", (event) => {
    event.stopPropagation();
  });
```

<h2><a name='делегирование_событий'>Делегирование событий</a></h2>

**Делегирование события** заключается в том, что вместо добавления однотипных обработчиков события для каждого элемента, мы добавляем **один обработчик для родительского элемента**.

Найти элемент, по которому сделан клик можно с помощью `event.target`. Если нужный элемент найден, можно выполнить необходимые действия с ним.
