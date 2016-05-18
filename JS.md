

## Classnames

[classnames](https://npmjs.com/classnames) импортировать только по необходимости. При импорте давать имя `CN`.

```jsx
import CN from 'classnames';

const result = <div className={CN('Loader', { active: activeCondition, wide: global.isWide )} />
```

classnames выполняет роль макроса, то есть разворачивает js-представление в строку.

В мире C-подобных языков макросы пишут в PASCAL_CASE

Также два символа короче и удобнее к чтению/записи, чем дублирование:

```jsx
<div className={CN('class', 'second')} />
// вместо
<div className={classNames('class', 'second')} />
```

При чтении два прописных символа лучше выделяются из кода, чем обычная функция.


## Bind/Autobind

Модуль [autobind](https://npmjs.com/autobind) это декоратор, который можно применить к классу и к методу класса.

Декоратор жестко привязывает контекст метода к объекту класса.

```jsx
import bind from 'autobind';

class SomeCom {
  
  @bind
  handleClick(event) {
    event.preventDefault();
    this.doSomeFunction();
  }
  
  render = () => (
    <div>
      <a onClick={this.handleClick}>Go</a>
      <ul>
        <li><a onClick={this.handleClick}>Real go</a></li>
      </ul>
    </div>
  );
}
```

Во-первых, такой подход убирает необходимость писать явный bind в конструкторе

```js
this.handleClick = this.handleClick.bind(this)
```

Явный bind в конструкторе -- это полный антипаттерн принципу DRY.
Приходится писать название метода дважды, что увеличивает шанс ошибиться.
Также приходится явно описывать в конструкторе вызов `super`, что подвержено ошибкам и опечаткам.

Использование `.bind` или bind-оператора при каждом пробрасывании или вызове метода добавляет лишней работы и не исключает ошибок.

Декоратор `@bind` явно указывает на жестко привязанный контекст метода, что при чтении кода полностью убирает необходимость
отрываться от чтения метода на поиск каждого вызова, чтобы убедиться в наличии `.bind` или bind-оператора.




