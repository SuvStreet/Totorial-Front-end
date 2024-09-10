<h1>TypeScript</h1>

- [Установка TypeScript](#установка_typescript)
  - `npm install typescript -g`
  - `tsc`
  - [tsconfig.json.txt](#tsconfig.json.txt)
    - `npm install typescript --save-dev`
    - `npx tsc --init`
- [Базовые типы](#базовые_типы)
  - `Число`
  - `Строки. Логический тип. Базовая типизация функций`
  - `Объекты`
  - `Массивы`
  - `Кортежи (Tuples)`
  - `Перечисления (Enums)`
  - `Символ. BigInt`
  - `void vs indefined`
- [Работа с типами](#работа_с_типами)
  - `Объединения (Union Types)`
  - `Литералы (Literal Types)`
  - `Интерфейсы`
  - `unknown`
  - `never`
  - `Защитники типа (Type Guard)`
- [Дженерики](#дженерики)

<h2 name='установка_typescript'>Установка TypeScript</h2>

Команда установки TS `npm install typescript -g`, устанавливаем глобально.

Проверить что он установился, доступна команда `tsc`:
  - `--help` возможности TS

<h3 name='tsconfig.json.txt'>tsconfig.json.txt</h3>

 - `npm install typescript --save-dev` - установить конфиг для настройки компиляции из TS в JS

После этого с помощью CLI мы можем компилировать TS-файлы:

- `npx tsc ./index.ts`

Поведение компилятора можно управлять. Файл `tsconfig.json` — это файл конфигурации, который позволяет управлять поведением компилятора TypeScript. Он помещается в корень проекта, и компилятор автоматически считывает его при компиляции кода. Файл `tsconfig.json` написан в формате JSON и содержит несколько свойств, которые настраивают компилятор TypeScript. TypeScript [документация](https://www.typescriptlang.org/docs/handbook/compiler-options.html).

 - `npx tsc --init` - создание файла `tsconfig.json` со стандартными параметрами. 

Файл со стандартными параметрами:

```json
{
  "compilerOptions": {
    "target": "es2016",
    "module": "commonjs",
    "allowJs": true, 
    "sourceMap": true
    "outDir": "dist",
    "noEmitOnError": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts"]
}
```

`"compilerOptions"` — верхнеуровневое свойство, содержащее параметры для компилятора. Это основная часть конфигурации, которая определяет, как должен работать язык. Рекомендуем ознакомиться с несколькими полезными настройками:

  - `"target"` — указывает версию ECMAScript, в которую будет скомпилирован TypeScript-код. Например, `"es3"`, `"es5"`, `"es6"`, `"es2016"`, `"esnext"` и другие.
  - `"module"` — указывает, какую систему модулей использовать. Можно указать `"commonjs"`, `"amd"`, `"system"`, `"es2015"`, `"es2020"`, `"esnext"` и другие.
  - `"allowJs"` — позволяет использовать JavaScript-файлы в TypeScript-проекте. Эта опция может быть полезна, если у нас уже есть проект на JavaScript, и мы хотим его постепенно перевести на TypeScript.
  - `"sourceMap"` — включает создание source maps для удобства отладки.
  - `"outDir"` — задает каталог, в котором должны сохраняться скомпилированные JavaScript-файлы. Если не указывать, то по умолчанию JS-файлы будут сохраняться там же, где их TS-исходники (например, для файла `/src/foo/bar.ts` создастся `/src/foo/bar.js`).
  - `"noEmitOnError"` — определяет, будет ли TypeScript компилироваться в JavaScript, если в процессе компиляции возникнут ошибки.
  - `"esModuleInterop"` — упрощает работу с импортами CommonJS-модулей.
  - `"forceConsistentCasingInFileNames"` — гарантирует, что при импорте будет указан правильный регистр имени файла. Это может помочь предотвратить ошибки при работе с разными операционными системами (чувствительных и нечувствительных к регистру).
  - `"strict"` — включить все параметры строгой проверки типов (такие как `strictBindCallApply`, `strictFunctionTypes`, `strictNullChecks` и другие). Рекомендуется включить, так как это помогает избежать ошибок в коде, улучшить качество и надежность приложений.

  Далее идет `«include»`. Это верхнеуровневое свойство, которое указывает, что должно быть включено в программу (будет скомпилировано). Оно поддерживает шаблоны поиска, т. е. при указании `[«src/**/*»]` будут искаться TS-файлы внутри папки `src`, а также во всех её дочерних папках.

Затем идет верхнеуровневое свойство `"exclude"`. Здесь ровно наоборот — определяем, что из указанного в `"include"` компилятору нужно проигнорировать. Здесь также поддерживаются шаблоны поиска, т. е. при указании `["**/*.spec.ts"]` все файлы, которые оканчиваются на `.spec.ts` компилироваться не будут.

Полный список параметров, а также их подробные описания можно узнать в [документации](https://www.typescriptlang.org/tsconfig/).


<h3>Запуск с использованием файла конфигурации</h3>

  - `npx tsc` - по умолчанию ищет файл tsconfig.json в текущем каталоге и использует его для настройки компилятора.

<h2 name='базовые_типы'>Базовые типы</h2>

  - `Число` :

```ts
  let a: number // перемменную явно указываем тип
  const b: number // константе явно указываем тип

  // какие значения относятся к number
  const c = 12
  const d = Infinity
  const e = NaN
  const f = 0x1
  const j = 0.1
  const i:24 = 24 // указываем что переменная i будет равна только 24!

  // праметры функции явно указываем тип и явно указываем, что она возвращает
  function sum(a: number, b: number):number {} 
```

  - `Строки. Логический тип. Базовая типизация функций`

```ts
const string = 'Hello TypeScript'

// Указываем что функция принимает строку и булевое значение,
// и отдаёт так же строку. ? - после параметка указывает, что он не
// обязателен и может не передоваться.

function transform(str: string, uppercase?: boolean): string {
    if (uppercase) {
        return str.toUpperCase()
    }
    return str.toLowerCase()
}

let isUppercase = true

// всё тоже самое только с стрелочной функцией.
const arrowTransform = (str: string, uppercase?: boolean): string => {
    if (uppercase) {
        return str.toUpperCase()
    }
    return str.toLowerCase()
}

console.log(transform(string))
console.log(transform(string, isUppercase))
```

  - `Объекты`

```ts
// Явно указываем тип каждому полю объекта
const person: {
    name: string
    age: number
    surname: string
    address: { city: string, street: string }
} = {
    name: 'Vladilen',
    surname: 'Minin',
    age: 29,
    address: {
        city: 'moscow',
        street: 'lenina',
    },
}

// функция принимает объект только поля name и surname
function fullname(obj: { name: string; surname: string }): string {
    return obj.name + ' ' + obj.surname
}

console.log(fullname(person))
```

  - `Массивы`

```ts
// const names: any[] = ['vladilen', 'igor', 'elena', 1] // error

// указываем тип массив строк
const names: string[] = ['vladilen', 'igor', 'elena']
names.push('eva')
// names.push(42) // error

for (let name of names) {
    console.log(name.toUpperCase())
}

const lengths = names
    .filter((n) => n !== 'igor')
    .map((n) => n.length)
    .reduce((acc, cur) => (acc += cur), 0)

console.log(lengths)
```

  - `Кортежи (Tuples)`

Tuples - массивы состоящие из разных типов данных.

```ts
// const tuple: any[] = [42, 'I am string'] // error
// [number, string] - это картеж
// readonly - только для чтения!
const tuple: readonly [number, string] = [42, 'I am string']

// tuple[0] = 'fsdmkl' // error
// const temp = tuple[2] // error

// tuple.push('false') // error

const tuple2: [number, string, ...boolean[]] = [
    42,
    'I am string',
    true,
    true,
    false,
]
```

  - `Перечисления (Enums)`

```ts
// const ROLES = {
//   admin: 'admin',
//   user: 'user',
// }

enum Roles {
    admin = 'admin',
    user = 'user',
}

const person = {
    role: Roles.admin,
}

const person2 = {
    role: Roles.user,
}

function check(person, role: Roles) {
    if (person.role === Roles.admin) {
        console.log('This is admin')
    } else {
        console.log('This is user')
    }
}

check(person, Roles.admin)
check(person2, 'admin') // error
```

  - `Символ. BigInt`

```ts
let a: symbol = Symbol('key')
let b: symbol = Symbol('key2')

a === b // false

// ===

// "target": "ES2020"
const bignum: bigint = 123n
const big2 = BigInt(200)
```

  - `void vs undefined`

```ts
function logInfo(): void { // указываем что функция ничего не возвращает
    console.log(1231)
}

// когда мы не определяем значение перемменной
let temp: undefined
```

<h2 name='работа_с_типами'>Работа с типами</h2>

  - `Объединения (Union Types)`

```ts
function compute(p1: number | string, p2: number | string) {
    if (typeof p1 === 'number' && typeof p2 === 'number') return p1 + p2
    else return p1.toString() + p2.toString()
}

console.log(compute(1, 2))
console.log(compute('hello', 'world'))

function logError(err: string | string[]) {
    if (Array.isArray(err)) {
        console.log(err.reduce((acc, cur) => acc + ' ' + cur, ''))
    } else {
        console.log(err)
    }
}
```

  - `Литералы (Literal Types)`

```ts
// создание кастомного типа
type OutputType = 'string' | 'json'

function convertData(data: object, outputType: OutputType) {
    if (outputType === 'string') {
        return JSON.stringify(data)
    } else if (outputType === 'json') {
        return { ...data }
    }
}

// convertData({ a: 1 }, 'smth')
```

  - `Интерфейсы`

```ts
// type User = {
//   name: string
//   age: number
//   hobbies: string[]
// }

interface Address {
    city: string
    street: string
}

interface User {
    name: string
    age: number
    hobbies: string[]
}

interface FullUser extends User, Address {
    date: Date
}

const person: FullUser = {
    name: 'Vladilen',
    age: 29,
    hobbies: ['a', 'b', 'c'],
    city: 'Moscow',
    street: 'Lenina',
    date: new Date(),
}

// ======

interface UserMap {
    [key: number]: FullUser
}


const userMap = {
    1: person,
    2: person
} as UserMap

// userMap[2].age
```

  - `unknown`

```ts
let a: unknown = 30
let b: boolean = a === 32 // == === || && ? !
// let c = a + 10 // error
// let d = a + 10 // if a: any
if (typeof a === 'number') {
    let d = a + 10
}
```

  - `never`

```ts
// never returns anything (никогда ничего не возвращает)
function throwError(message: string): never {
    throw new Error(message)
}

function loop(): never {
    while (true) {}
}
```

  - `Защитники типа (Type Guard)`

```ts
function isBoolean(value: string | boolean): value is boolean {
    return typeof value === 'boolean'
}

function logFlag(flag: string | boolean) {
    if (isBoolean(flag)) {
        console.log('Hey it is boolean')
    } else {
        console.log('Hey it is string')
    }
}

logFlag(true)
logFlag('lol')
```

<h2 name='дженерики'>Дженерики</h2>



























