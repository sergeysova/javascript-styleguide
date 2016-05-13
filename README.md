# Code Style Guide

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Example eslint config](#example-eslint-config)
- [Linter Rules](#linter-rules)
	- [Comma dangle](#comma-dangle)
	- [No cond assign](#no-cond-assign)
	- [No console](#no-console)
	- [No debugger](#no-debugger)
	- [No dupe args](#no-dupe-args)
	- [No dupe keys](#no-dupe-keys)
	- [No empty](#no-empty)
	- [No extra boolean cast](#no-extra-boolean-cast)
	- [No unreachable](#no-unreachable)
	- [Use isNan](#use-isnan)
	- [Valid typeof](#valid-typeof)
	- [Dot location](#dot-location)
	- [No empty function](#no-empty-function)
	- [No implicit coercion](#no-implicit-coercion)
	- [No lone blocks](#no-lone-blocks)
	- [No loop function](#no-loop-function)
	- [No multi spaces](#no-multi-spaces)
	- [No return assing](#no-return-assing)
	- [Radix](#radix)
	- [Yoda](#yoda)
	- [No unused vars](#no-unused-vars)
	- [Global require](#global-require)
- [Stylistic Rules](#stylistic-rules)
	- [Array bracket spacing](#array-bracket-spacing)
	- [Block spacing](#block-spacing)
	- [Brace style](#brace-style)
	- [Comma spacing](#comma-spacing)
	- [Comma style](#comma-style)
	- [Computed property spacing](#computed-property-spacing)
	- [EOL last](#eol-last)
	- [ID length](#id-length)
	- [Indent](#indent)
	- [JSX quotes](#jsx-quotes)
	- [Key spacing](#key-spacing)
	- [Keyword spacing](#keyword-spacing)
	- [New cap](#new-cap)
	- [New parens](#new-parens)
	- [Newline after var](#newline-after-var)
	- [No array constructor](#no-array-constructor)
	- [No continue](#no-continue)
	- [No lonely if](#no-lonely-if)
	- [Multiple empty line](#multiple-empty-line)
	- [No negated conditions](#no-negated-conditions)
	- [No spaced func](#no-spaced-func)
	- [No trailing spaces](#no-trailing-spaces)
	- [No unneeded ternary](#no-unneeded-ternary)
	- [No whitespace before property](#no-whitespace-before-property)
	- [Object curly spacing](#object-curly-spacing)
	- [Operator assignment](#operator-assignment)
	- [Operator linebreak](#operator-linebreak)
	- [Padded blocks](#padded-blocks)
	- [Quoted props](#quoted-props)
	- [Semi](#semi)
	- [Space before function paren](#space-before-function-paren)
	- [Space in parens](#space-in-parens)
	- [Space comment](#space-comment)
	- [Arrow body style](#arrow-body-style)
	- [Arrow parens](#arrow-parens)
	- [Arrow spacing](#arrow-spacing)
	- [No dupe class members](#no-dupe-class-members)
	- [No duplicate imports](#no-duplicate-imports)
	- [No this before super](#no-this-before-super)
	- [No var](#no-var)
	- [Object shorthand](#object-shorthand)
	- [Prefer rest params](#prefer-rest-params)
	- [Prefer spread](#prefer-spread)
	- [Prefer template](#prefer-template)
- [On Discussion](#on-discussion)

<!-- /TOC -->

## Example eslint config

```json
{
  "comma-dangle": ["error", "always-multiline"],
  "no-cond-assing": ["error", "always"],
  "no-console": ["error", { "allow": ["warn", "error"] }],
  "no-debugger": "error",
  "no-dupe-args": "error",
  "no-dupe-keys": "error",
  "no-empty": ["error", { "allowEmptyCatch": true }],
  "no-extra-boolean-cast": "error",
  "no-unreachable": "error",
  "use-isnan": "error",
  "valid-typeof": "error",
  "dot-location": ["error", "property"],
  "no-empty-function": ["error", { "allow": ["arrowFunctions"] }],
  "no-implicit-coercion": "error",
  "no-lone-blocks": "error",
  "no-loop-func": "error",
  "no-multi-spaces": "error",
  "no-return-assign": "error",
  "radix": "error",
  "yoda": "error",
  "no-unused-vars": "warning",
  "global-require": "error",

  "array-bracket-spacing": ["error", "never"],
  "block-spacing": ["error", "never"],
  "brace-style": ["error", "stroustrup", { "allowSingleLine": true }],
  "comma-spacing": ["error", { "before": false, "after": true }],
  "comma-style": ["error", "last"],
  "computed-property-spacing": ["error", "never"],
  "eol-last": "error",
  "id-length": ["error", { "min": 2 }],
  "indent": ["error", 2, { "SwitchCase": 1 }],
  "jsx-quotes": ["error", "prefer-double"],
  "key-spacing": ["error", { "beforeColon": false, "afterColon": true }],
  "keyword-spacing": ["error", { "before": true, "after": true, "overrides": { "catch": { "after": true } } }],
  "lines-around-comment": ["warning", { "afterLineComment": false, "beforeLineComment": true }],
  "new-cap": ["error", { "newIsCap": true }],
  "new-parens": "error",
  "newline-after-var": ["error", "always"],
  "no-array-constructor": "error",
  "no-continue": "error",
  "no-lonely-if": "error",
  "no-multiple-empty-lines": ["error", { "max": 3 }],
  "no-negated-condition": "error",
  "no-spaced-func": "error",
  "no-trailing-spaces": ["error", { "skipBlankLines": false }],
  "no-unneeded-ternary": "warning",
  "no-whitespace-before-property": "error",
  "object-curly-spacing": ["error", "always"],
  "operator-assignment": ["warning", "always"],
  "operator-linebreak": ["error", "before"],
  "padded-blocks": ["error", "never"],
  "quoted-props": ["error", "as-needed"],
  "semi": ["error", "always"],
  "semi-spacing": ["error", { "before": false, "after": true }],
  "space-before-function-paren": ["error", "never"],
  "space-in-parens": ["error", "never"],
  "spaced-comment": ["error", "always"],
  "arrow-body-style": ["error", "as-needed"],
  "arrow-parens": ["error", "as-needed"],
  "arrow-spacing": ["error", { "before": true, "after": true }],
  "no-dupe-class-members": "error",
  "no-duplicate-imports": "error",
  "no-this-before-super": "error",
  "no-var": "error",
  "object-shorthand": ["error", "always"],
  "prefer-rest-params": "error",
  "prefer-spread": "warning",
  "prefer-template": "warning",
  "template-curly-spacing": ["error", "never"]
}
```

## Linter Rules

### Comma dangle

Добавлять запятую после последнего элемента массива или объекта, только в многострочном определении.
Упрощает дописывание элементов в конец, git diff получается однострочный, не затрагивая вышестоящую строку.

### No cond assign

Установка значений переменным в условиях влечет за собой сложнообнаруживаемые ошибки.
В случае включенной проверки, опечатки сводятся к нулю, код проще для понимания.

### No console

Не нужно оставлять в коде ваши отладочные принты в консоль.
Если уж необходимо отладить код на dev (например), то добавляйте строчное исключение и пишите об этом к коммите.

```js
// eslint-disable-next-line no-console
console.log("Some data")

console.log('Wow Bad'); // eslint-disable-line no-console
```

### No debugger

Здесь вроде всё очевидно.
Но при острой необходимости: также `// eslint-disable-line no-debugger` и пояснения в коммите.
Желательно, добавлять `debugger` отдельным коммитом, чтобы можно было сделать `git revert`, а не выискивать по коду, есть человеческий фактор и забывчивость.


### No dupe args

Дубликаты имен аргументов это fatal!

### No dupe keys

Также fatal! проверяйте свой код.


### No empty

Запрет создания пустых блоков кода, вроде `if (some >= 20) {}`.
Так как в таких блоках кода нет смысла. Блоки кода с комментариями не считаются пустыми.
А также `catch (e) {}` не считается пустым блоком.


### No extra boolean cast

Запрещает дополнительное приведение в boolean в случае условий:

```js
let foo0 = !!!bar;

let foo1 = !!bar ? baz : bat;

let foo2 = Boolean(!!bar);

let foo3 = new Boolean(!!bar);

if (!!foo) {}

if (Boolean(foo)) {}

while (!!foo) {}

do {} while (Boolean(foo))

for (; !!foo; ) {}
```

### No unreachable

Запрещает написание кода, который никогда не выполнится. Например:

```js
function fn() {
    x = 1;
    return x;
    x = 3; // Этот код никогда не выполнится
}
```

### Use isNan

Запрет сравнивания с `NaN`. Например: `if (foo === NaN) {}`
Решает некоторые потенциальные ошибки возникающие при сравнении со специальным значением `NaN`
Принуждает использовать `isNan()` для проверок.


### Valid typeof

Просто дополнительная проверка на опечатку.

### Dot location

Обязывает в многострочных обращениях к свойствам и методам объекта ставить точку в начале новой строки.
Пример правильного расположения точки:

```js
const data = Plant
  .select('some')
  .filter(a => a < 1)
  .unwrap();
```

Такое расположение точки, явно указывает на вызов метода/свойства объекта выше строчками.

### No empty function

Запрещает описывать пустые функции.
Разрешены только пустые arrow-функции: `{ defaultHandler: () => {} }`


### No implicit coercion

Вносит запрет на неявное приведение типов, вроде:

```js
const b = !!foo;
const b = ~foo.indexOf(".");
const n = +foo;
const n = 1 * foo;
const s = "" + foo;
foo += "";
```
Вместо этого, необходимо явно приводить к необходимому типу:

```js
let b = Boolean(foo);
let b = foo.indexOf(".") !== -1;
let n = Number(foo);
let n = Number(foo);
let s = String(foo);
foo = String(foo);
```

### No lone blocks

Запрещает писать блоки кода без условий, циклов и других определений.
Пример неправильного использования блоков кода:

```js
// Wrong!

{
  callSomeFunction();

  function someDefinition() {}
}
```

### No loop function

Запрещает описание функций с замыканиями внутри циклов.


### No multi spaces

Запрет написания нескольких пробелов между инструкциями


### No return assing

Запрещает присваивать значение в теле оператора `return`


### Radix

Обязывает при использовании `parseInt()` указывать систему счисления вторым параметром.
Чтобы избежать неправильного парсинга строки в число.

### Yoda

Запрещает писать "обратные" условия, вроде: `if (1 == foo) {}` или `if (true === flag) {}`


### No unused vars

Неиспользованные переменные загрязняют код, ухудшают понимание.
Данное правило вызывает предупреждение, когда в коде встречается неиспользованная переменная.


### Global require

Все импорты должны быть на верхнем уровне. Правило запрещает заносить импорт в скобки условий или циклов.


## Stylistic Rules

### Array bracket spacing

Не должно быть пробелов внутри квадратных скобок массива.

```js
let arr = [];
let arr = ['foo', 'bar', 'baz'];
let arr = [['foo'], 'bar', 'baz'];
let arr = [
  'foo',
  'bar',
  'baz'
];
let [x, y] = z;
let [x,y] = z;
let [x, ...y] = z;
let [,,x,] = z;
```

### Block spacing

Обязательны пробелы внутри однострочного блока кода.

```js
function foo() { return true; }
if (foo) { bar = 0; }
```

### Brace style

Использовать стиль Страуструпа.

```js
function foo() {
  return true;
}

if (foo) {
  bar();
}

if (foo) {
  bar();
}
else {
  baz();
}

try {
  somethingRisky();
}
catch (e) {
  handleError();
}

// без скобок однострочные
if (foo) bar();
else if (baz) boom();

// со скобками однострочные
function nop() { return; }

if (foo) { bar(); }

if (foo) { bar(); }
else { baz(); }

try { somethingRisky(); }
catch (e) { handleError(); }
```

### Comma spacing

Пробел ставится **только после** запятой

```js
let foo = 1, bar = 2, baz = 3;
let arr = [1, 2];
let arr = [1,, 3]
let obj = {"foo": "bar", "baz": "qur"};
foo(a, b);
new Foo(a, b);
function foo (a, b) {}
a, b
```

### Comma style

Запятая ставится **после** элемента, а не перед ним.

```js
var foo = 1, bar = 2;

var foo = 1,
    bar = 2;

var foo = ["apples",
           "oranges"];

function bar() {
    return {
        "a": 1,
        "b:": 2,
    };
}
```

### Computed property spacing

Внутри скобок определениях вычисляемых свойств пробелы не нужны:

```js
obj[foo];
let x = { [b]: a };

obj[foo[bar]] = x;
```

### EOL last

Каждый файл исходного кода должен заканчиваться переносом строки


### ID length

Все идентификаторы должны быть не короче 2 символов

### Indent

Отступы должны быть в 2 пробельных символа.
Определения `case/default` должны быть на 1 уровень глубже `switch`.
Тело `case/default` должно быть глубже его определения.
Тело не может быть на одной строке с определением.

```js
if (a > 20) {
  switch (a) {
    case 22:
      some.func(a, true);
      break;
    case 24:
      some.func(a + 1, false);
      notif.ok(a + 1, 'ok');
      break;
    default:
      notif.err(a, 'no one');
  }
}
```


### JSX quotes

В JSX-тегах необходимо использовать двойные кавычки.

```js
<Component title="Example title">
  <div className="description-line" />
</Component>
```


### Key spacing

В определении объекта, пробел должен стоять только **после** символа двоеточия.

```js
let object = { user: "Name" };
let some = {
  key: "Value",
  foo: "Bar",
  zoo: "Zoo",
}
```

### Keyword spacing

Ключевые слова должны быть окружены пробелами.

```js
if (foo) {
  // ...
}
else if (bar) {
  // ...
}
else {
  // ...
}

class A {}

function* foo(a) {
  return yield + a;
}

try {
  throw new Error('Wow');
}
catch (err) {
  console.error(err.message);
}

for (let b = 0; b <= 1000; b++) {
  some.caller(b, b + 1, true);
}

while (a < 5) {
  fnc(a, String(a));
}

do {
  connection();
  load();
}
while (retry());
```

### New cap

Все классы и объекты создаваемые через `new` должны начинаться с прописной буквы.

```js

let obj = new DefaultObject();
let dmn = new DomainKnowledge();

let boo = new fooBar(); // ошибка
```

### New parens

При вызове конструктора через `new` скобки обязательны.

```js
let obj = new ClassDefinition();

let def = new DefaultParams; // ошибка!
```

### Newline after var

После определения переменных необходимо оставить пустую строку. Для увеличения читабельности.

```js
let a = 1;
let b = 2;
let commoncc = new CommonCC();

commoncc.init(a, b);
commoncc.pub(b);
```

### No array constructor

Нельзя создавать массив через конструктор `Array`.

```js
let a = Array(500); // 500 элементов
let b = new Array(5); // 5 элементов
```

### No continue

Необходимо писать код не используя `continue`

### No lonely if

Нельзя помещать дополнительный `if` в тело `else`.
Например так нельзя:

```js
if (foo) {
  // ...1
}
else {
  if (bar) {
    // ...2.
  }
}
```

Код должен быть переписан:

```js
if (foo) {
  // ...1
}
else if (bar) {
  // ...2
}
```


### Multiple empty line

Максимум 3 пустые строки между методами и определениями.


### No negated conditions

В коде не должно быть `if/else` в котором есть условие с отрицанием.
Такой код должен быть переписан:

```js
if (!a) {
  // 1 some
}
else {
  // 2 code
}
```

В такой:

```js
if (a) {
  // 2 code
}
else {
  // 1 code
}
```

### No spaced func

При вызове функции после идентификатора не должно быть пробела:

```js
someFunc();

// Неправильно!
fn ();
```

### No trailing spaces

Строки не должны оканчиваться пробелами.
Пустые строки также не могут содержать пробелы.

> Рекомендуется включить отображение пробельных символов в Вашем редакторе или IDE

### No unneeded ternary

Не нужно описывать тернарную операцию лишний раз.

```js
// Неправильно
let isYes = answer === 1 ? true : false;
let isNo = answer === 1 ? false : true;
let foo = bar ? bar : 1;

// Правильно
let isYes = answer === 1;
let isNo = answer !== 1;
let foo = bar || 1;
```

### No whitespace before property

При обращении к свойству объекта запрещено ставить пробел перед и после точки.

```js
// правильно
foo
  .bar()
  .baz()
  .qux();

foo.bar().baz().qux();

// неправильно
foo .bar();
foo. baz();
foo . qux();
foo
  .bar(). baz();
```

### Object curly spacing

Пробелы должны быть внутри фигурных скобок объекта и destructing-присваивания.

```js
let obj = {};
let oob = { foo: 'bar' };
let ojj = { foo: { bar: 'baz', qux: 'guz' } };
const { foo, bar } = guz;
import { foo } from 'bar';
```

### Operator assignment

Операторы изменения переменной с присваиванием должны быть сокращены.

```js
// вместо
x = x + 1;
y = y / 2;
a[0] = a[0] + a[1];
d = d ** c;

// должно быть
x += 1;
y /= 2;
a[0] += a[1];
d **= c; // d = Math.pow(d, c)
```

### Operator linebreak

При переносе длинного условия операторы необходимо ставить в начале строки.

```js
foo = 1
  + 2
  + 3
  + 4;

if (someLongConditionPartOfManyConditionsArray
  || wowThatsAnotherLongConditionButThatIsOneNotPart) {
    // ... some code
  }

let result = someLongCondition
  ? operationTruthy()
  : conditionFalsy();
```

Данный выбор объясняется безусловной видимостью операторов в начале строки.
Отсутствует необходимость визуально отыскивать их в конце строк разной длины.


### Padded blocks

Внутри блоков кода не должно быть пустых строк в начале и конце блока

```js
// неправильно
if (a) {

  b();

}

// правильно
if (a) {
  b();
}
```


### Quoted props

В определении объекта кавычки для имен свойств использовать только в случае совпадения с ключевым именем:

```js
let obj = {
  hello: 'world',
  0: 12,
  true: 1,
  'qux-lorem': true,
  'null': 'wow'
};
```

### Semi

Так как JavaScript неявно дополняет каждую строку `;` и иногда это совсем не очевидно, двоеточия необходимы.
В случае `for` после `;` необходим пробел. Но разрешено писать `for (;;) {}`


### Space before function paren

В определении именованной или метода класса перед круглыми скобками не должно быть пробелов.


```js
function foo() {}
const d = function() {};

class Foo {
  constructor() {
    // ...
  }
}

go(function() {
  // ... go callback
});
```

### Space in parens

Внутри круглых скобок пробелы не должно быть

```js
foo();

foo('bar');

let foo = (1 + 2) + 3;
(function() { return 'bar'; })();
```


### Space comment

Комментарии должны начинаться с пробела

```js
// Some comment

//Bad comment
```


### Arrow body style

В стрелочной функции необходимо обрамлять тело скобками только:

- Если тело в несколько строк
- Когда необходимо выполнить несколько операторов разделенных `;`
- Не нужно возвращать значение

```js
let foo = () => 0;
let foo = (retv, name) => {
    retv[name] = true;
    return retv;
};
let foo = () => { bar(); };
let foo = () => {};
let foo = () => { /* ничего */ };
let foo = () => {
    // ничего не делает
};
```

### Arrow parens

В стрелочной функции скобки вокруг аргументов ставятся **только** в случаях:

- если нет аргументов
- если аргументов больше одного
- если используется деструкция (`([a, b]) => {}`, `({a, b}) => {}`)
- если есть значение по умолчанию для аргумента (`(a = 2) => {}`)

```js
() => {};
a => {};
a => a;
a => {'\n'};
a.then(foo => {});
a.then(foo => { if (true) {}; });
(a, b, c) => a;
(a = 10) => a;
([a, b]) => a;
({a, b}) => a;
let b = parameter => {
  let c = a + parameter;
  return c / 2;
}
```

### Arrow spacing

В стрелочной функции должны быть пробелы вокруг круглых скобок списка аргументов.

```js
() => {};
(a) => {};
let b = a => a;
let c = () => {'\n'};
```

### No dupe class members

Запрещает определить в классе свойства и методы с одинаковыми именами.


### No duplicate imports

Необходимо группировать импорты из одного модуля.

Правило запрещает дублирующиеся импорты.
Такой код должен быть исправлен.

```js
import { name } from 'mod';
import { second } from 'mod';
```


### No this before super

В конструкторе класса-наследника запрещает использовать `this` до вызова `super()`.
Необходимо сначала вызвать родительский конструктор


### No var

Вместо `var` необходимо использовать `let`/`const`.



### Object shorthand

Необходимо использовать коротку форму в объектах.

```js
let b = 1;
let foo = {
  w() {},
  [y]() {},
  b,
  j: (a) => ++a,
};
```

### Prefer rest params

Вместо `arguments` необходимо использовать rest-параметр

```js
function foo(bar, ...args) {
  bar(...args);
}
```


### Prefer spread

Вместо `.apply()` лучше использовать spread.

```js
const max = Math.max(...[1, 2, 3, 4]);
```


### Prefer template

Вместо конкатенации строк и переменных лучше использовать шаблонные строки.
Внутри фигурных скобок шаблона не должно быть пробелов.

```js
const ex = `Hello ${name}. You balance: $${balance.value}`;
```



## On Discussion

- [Vars on top](http://eslint.org/docs/rules/vars-on-top)
- [Disallow nested ternaries](http://eslint.org/docs/rules/no-nested-ternary)
- [Disallow new Object](http://eslint.org/docs/rules/no-new-object)
- [JSDoc required](http://eslint.org/docs/rules/require-jsdoc)
- [Arrow confusing](http://eslint.org/docs/rules/no-confusing-arrow)
