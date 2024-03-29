<h1>Введение в основы JavaScript</h1>

 - [Математические операции](#математические_операции)
 - [Сложение/вычитание с присвоением](#сложение/вычитание_с_присвоением)
 - [Инкремент / декремент](#инкремент_/_декремент)
 - [Операторы сравнения](#операторы_сравнения)
 - [Сравнение строк](#сравнение_строк)
 - [Округление](#округление)
 - [Логические конструкции](#логические_конструкции)
   - `if`
   - `if...else`
   - `else...if`
   - `switch`
   - `?:`
 - [Логические операторы](#логические_операторы)
   - `&&`
   - `||`
   - `!`
   - `??`
 - [Циклы](#циклы)
   - `while`
   - `do...while`
   - `for`
   - `break`
   - `continue`

---

<h2><a name="математические_операции">Математические операции</h2>

[Таблица приоритетов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#table)

 - `+` – сложение
 - `–` вычитание
 - `*` – умножение
 - `/` – деление
 - `**` – возведение в степень
 - `%` – остаток от деления. Результатом a % b будет остаток от целочисленного деления a на b

![](https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/41.jpeg "остаток от деления")

<h2><a name="сложение/вычитание_с_присвоением">Сложение/вычитание с присвоением</a></h2>

- сложение (`+=`)
- вычитание (`-=`)
- умножение (`*=`)
- деление (`/=`)
- возводение в степень (`**=`)
- нахождение остатока от деления (`%=`)

<h2><a name="инкремент_/_декремент">Инкремент / декремент</a></h2>

- **`++`** - инкремент
- **`--`** - декремент

Между `a++` и `++a` есть небольшая разница: 

- `a++` возвращает значение a **до** увеличения на 1
- `++a` возвращает значение a **после** увеличения на 1

***Аналогично с декрементом.***

<h2><a name="операторы_сравнения">Операторы сравнения</a></h2>

- `>` - (больше)
- `>=` - (больше или равно ≥)
- `<` - (меньше)
- `<=` - (меньше или равно ≤)
- `==` - (нестрогое сравнение). Сравнивает, пытаясь привести значения к одному типу
- `!=` - (неравенство). Противоположно нестрогому сравнению (==)
- `===` - (строгое сравнение). Сравнивает без приведения типов (чтобы элементы считались равными, их типы также должны совпадать).
- `!==` - (строгое неравенство). Противоположен строгому равенству (===)

<h2><a name="сравнение_строк">Сравнение строк</a></h2>

У каждого символа в строке есть своё числовое значение (от `0` до `65535`). Это значение можно получить при помощи метода `charCodeAt()`. 

```js
console.log('a'.charCodeAt()); // 97
console.log('A'.charCodeAt()); // 65
```

Также можно в обратную сторону получить символ из числа при помощи метода `String.fromCharCode()`.

```js
console.log(String.fromCharCode(97)) // 'a'
console.log(String.fromCharCode(65)) // 'A'
```

Хоть буквы и одинаковые, но от их регистра зависит их числовое значение. При сравнении строк JavaScript будет их сравнивать именно по этим значениям:

```js
console.log('A' < 'a'); // true, т. к. 65 < 97
console.log('Javascript' > 'JAvascript'); // true, т. к. 'a' > 'A'
console.log('123' < '15'); // true, т. к. '2' < '5'
```

<h2><a name="округление">Округление</a></h2>

В JavaScript также содержится объект `Math`, в котором есть множество полезных математических функций / констант.

```js
console.log(Math.PI) // 3.141592653589793
```

Таких констант очень много, поэтому при необходимости их можно [найти в документации](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math#static_properties). 

- **`Math.floor()`** – округление вниз

```js
console.log(Math.floor(41.5)) // 41
console.log(Math.floor(41.9)) // 41
```

- **`Math.round()`** – простое округление

```js
console.log(Math.round(41.5)) // 42
console.log(Math.round(41.4)) // 41
console.log(Math.round(41.8)) // 42
console.log(Math.round(42)) // 42
```

- **`Math.ceil()`** – округление вверх

```js
console.log(Math.ceil(41.5)) // 42
console.log(Math.ceil(41.1)) // 42
console.log(Math.ceil(42)) // 42
```

<h2><a name="логические_конструкции">Логические конструкции</h2>

[Условный оператор](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/if...else) (`if`) – если условие выполнится, то сделать какое-либо действие

```js
if (условие) {
  // Выполнится, если условие будет истинным
}
```

- `if...else` – более расширенная запись предыдущей конструкции.

```js
if (условие) {
  // ...
} else {
  // Выполнится, если условие будет ложным
}
```

- `else if` – дополнительная проверка условия

```js
if (условие1) {
  // ...
} else if (условие2) {
  // Выполнится, если условие 2 было истинным, и условие 1 были ложным
} else if (условие3) {
  // Выполнится, если условие 3 было истинным, и условия 1, 2 были ложными
} else {
  // Выполнится, если все условия выше были ложными
}
```

- [`switch`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/switch) - сравнивает выражение со случаями (кейсами), находит тот, значение которого совпадает с выражением, и затем выполняет инструкции нужного случая.

```js
switch (переменная) {
  case значение1:
    // выполнится, если переменная === значение1
    break // завершение случая
  case значение2:
    // выполнится, если переменная === значение2
    break
  default:
    // выполнится, если ни один другой случай не сработал
    break
}
```

- `?:` – [*Терна́рный оператор*](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) компактная замена `if...else`

```js
условие ? выражение1 : выражение2 // Если условие истинно, то вернется выражение1, а если ложно, то выражение2
```

<h2><a name="логические_операторы">Логические операторы</h2>

- И (`&&`) – логическое И (`a && b`)

Результатом будет `true`, когда все операнды равны `true`. В остальных случаях результатом будет `false`.

![](https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/418.png "логическое И")

Если все значения [truthy](https://developer.mozilla.org/ru/docs/Glossary/Truthy) (приводятся к `true`), то возвращает **последнее из них**.

Если хотя бы одно [falsy](https://developer.mozilla.org/ru/docs/Glossary/Falsy) (приведется к `false`), то возвращает **первое из них**.

```js
// Все truthy
console.log(1 && 'hello' && true); // true
console.log(true && 1 && 'javascript'); // 'javascript'

// Содержится falsy
console.log(false && 0 && 'javascript'); // false
console.log(1 && '' && false); // ''
console.log(0 && '' && false); // 0
```

- ИЛИ (`||`) – логическое ИЛИ (`a || b`)

Результатом будет `true`, когда один или несколько операндов равны `true`. В остальных случаях (только когда все операнды `false`) результатом будет `false`.

![](https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/55.png "логическое ИЛИ")

Если все значения [falsy](https://developer.mozilla.org/ru/docs/Glossary/Falsy) (приводятся к `false`), то возвращает **последнее из них**.

Если хотя бы одно [truthy](https://developer.mozilla.org/ru/docs/Glossary/Truthy) (приведется к `true`), то возвращает **первое из них**.

```js
// Все falsy
console.log('' || 0 || false); // false
console.log(false || 0 || ''); // ''

// Содержится truthy
console.log(false || 'hello' || true); // 'hello'
console.log(1 || false || 'javascript'); // 1
console.log(true || 1 || 'javascript'); // true
```

- НЕ (`!`) – логическое отрицание (`!a`)

Превращает `true` в `false` и наоборот.

- Nullish coalescing (`??`) – [оператор нулевого слияния](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing) (`a ?? b`)

Данный оператор очень похож на ИЛИ (`||`), но он считает за “falsy” только `null` и `undefined`. То есть он возвращает правый операнд, если слева был `null` или `undefined`, и возвращает левый, если их там не было. 

```js
console.log(null ?? '123') // '123'
console.log(undefined ?? '123') // '123'
console.log(false ?? '123') // false
console.log(0 ?? '123') // 0
console.log(true ?? '123') // true
```

<h2><a name="циклы">Циклы</h2>

- `while`

```js
while (условие) {
  // цикл будет повторяться, пока условие истинно
}
```

- `do...while`

```js
do {
  // цикл будет повторяться, пока условие истинно
} while (условие)
```

- `for`

```js
for (инициализация; условие; шаг) {
  // тело цикла
}
```

- `break`

Остановка цикла.

- `continue`

Останавливает работу текущей итерации.






