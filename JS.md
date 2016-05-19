

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

Бритва Оккама в программировании: если что-то можно написать разными способами и результат при этом не меняется,
следует выбрать тот способ, в котором наименьшее количество кода и одновременно наибольшая читабельность.


## Ternary

Использование тернарных выражений само по себе усложняет чтение кода.
В некоторых случаях тернарное выражение сократит количество кода.

Тернарное выражение должно быть однострочным, если общая длина не превышает 100 символов.

При написании 3 строчного тернарного выражения символы `?` `:` необходимо ставить в начале строки, а также необходим одинарный отступ.

В случае многострочного тернарного выражения, выравнивание кода должно быть в 2 отступа.

```js

const fund = fundingType === 'temporary' ? fundingValue.demo() : fundingValue.abs();

const conf = {
  amount: fundingValue.amount,
  error: null,
  accountID: account.present()
    ? account.models.filter(acc => acc.type == 'funding').reduce((prev, curr) => curr.id ? curr.id : prev.id)
    : ROM.defined.load(fundingValue.referrerId).model.id
  multiplier: fund / fundingValue.total.reduce((prev, curr) => prev + curr)
};
```

В многострочных тернарных выражениях JSX отступ перед символами `?` `:` ставить не нужно.

Условие и символы тернарного выражения находящие на одном уровне отступов, позволяют с первого взгляда определить начало и конец блоков кода.

```jsx
<div>
  <h2>Account info</h2>
  <section>
  {
    account.activated
    ? <AccountInfo present account={account} style="wide">
        <ButtonGroup wide>
          <Button primary onClick={this.handleEdit}>Edit</Button>
          <Button rounded onClick={this.handleFrustrate}>Frustrate</Button>
        </ButtonGroup>
      </AccountInfo>
    : <div className="info disabled">Your account is disabled!</div>
  }
  </section>
  <section className="primary">
    {
      account.activated
      ? <div className="info success">Your account active!</div>
      : null
    }
    {
      account.access.can('funds.add')
      ? <FundsAddWidget account={account} small />
      : <AccountRequestAccess account={account} funct="funds.add">
          Please, activate funding in account settings
        </AccountRequestAccess>
    }
    {System.upgrades.has() ? <SystemUpgrades has={true} /> : null}
    {account.settings.get('upgradable') ? <AccountUpgradable widget account={account} /> : null}
  </section>
</div>
```

Сравнить с:

```jsx
<div>
  <h2>Account info</h2>
  <section>
  {
    account.activated ?
      <AccountInfo present account={account} style="wide">
        <ButtonGroup wide>
          <Button primary onClick={this.handleEdit}>Edit</Button>
          <Button rounded onClick={this.handleFrustrate}>Frustrate</Button>
        </ButtonGroup>
      </AccountInfo> :
      <div className="info disabled">Your account is disabled!</div>
  }
  </section>
  <section className="primary">
    {
      !account.activated ? null :
        <div className="info success">Your account active!</div>
    }
    {
      account.access.can('funds.add') ?
        <FundsAddWidget account={account} small /> :
        <AccountRequestAccess account={account} funct="funds.add">
          Please, activate funding in account settings
        </AccountRequestAccess>
    }
    {
      System.upgrades.has() ? <SystemUpgrades has={true} /> : null
    }
    {
      account.settings.get('upgradable') ? <AccountUpgradable widget account={account} /> : null
    }
  </section>
</div>
```


## Props, Context, State

Определение Properties в React-компоненте это по сути спецификация и внешний интерфейс.

Любой человек, читающий код компонента, должен в первую очередь изучить интерфейс прежде, чем изучать содержимое.

- `propTypes` должны быть на видном месте, то есть в начале определения класса
- У каждого параметра `propTypes` можно выставить `.isRequired` необходимость его заполнения,
соответственно, если компонент имеет необязательные параметра, *необходимо* заполнить для них параметры по умолчанию (`defaultProps`).
- Все обязательные поля должны быть в начале определения `propTypes`.
- Все `bool` поля обязаны быть `false` по умолчанию, чтобы их можно было применять без указания значения (`<Ex boolProp />`).


Также компонент, может иметь доступ к React-контексту, соостветственно также должен быть описан объект `contextTypes`.

Определение начального состояния компонента есть часть компонента.
Так как внутренняя структура JavaScript рекомендует создавать объекты с заранее предустановленными полями
и не добавлять поля в ходе выполнения, **объект описывающий состояние `this.state` должен быть описан** со всеми используемыми полями со значениями по умолчанию.

- У каждого элемента может быть только одно место в порядке определения спецификации компонента.
- Каждое определение должно заканчиваться `;` и соответствовать правилам определения объектов.
- Между определениями должна быть пустая строка.
- Объект состояния компонента должен быть описан вне конструктора.
- Конструктор должен лишь обновлять необходимые поля напрямую.

Порядок определения: `propTypes`, `defaultProps`, `contextTypes`, `state`

```js

class Demo extends Component {
  static propTypes = {
    children: PropTypes.node.isRequired,
    userId: PropTypes.number.isRequired,
    className: PropTypes.string,
    onClick: PropTypes.func,
    wide: PropTypes.bool,
  };
  
  static defaultProps = {
    className: '',
    onClick: () => {},
    wide: false,
  };
  
  static contextTypes = {
    globalStore: GlobalStore.PropTypes.store,
  };
  
  state = {
    loaded: false,
    currentItem: null,
    currentId: -1,
    switcher: '',
  };
  
  constructor(props) {
    super(props);
    
    this.state.currentId = props.userId;
  }
}
```


