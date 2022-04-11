# Encapsulation

## Naming convention

```javascript
class Account {
  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.pin = pin;
    this.movements = [];
    this.locale = navigator.language;
    console.log(`Thanks for opening an account, ${owner}!`);
  }

  // Public interface
  deposit(val) {
    this.movements.push(val);
  }

  withdraw(val) {
    this.deposit(-val);
  }
}

const acc1 = new Account("Jonas", "EURO", 1111);
```

> 1. We can create properties that are not based on any input, like `movement` and `locale` here.
> 2. The `Navigator` interface represents the state and the identity of the user agent. It allows scripts to query it and to register themselves to carry on some activities.

It is a convention to add underscore to protected properties and methods:

```javascript
class Account {
  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    // Protected properties
    this._pin = pin;
    this._movements = [];
    this.locale = navigator.language;
    console.log(`Thanks for opening an account, ${owner}!`);
  }

  // Public interface
  deposit(val) {
    this._movements.push(val);
  }

  withdraw(val) {
    this.deposit(-val);
  }

  getMovements() {
    return this._movements;
  }

  requestLoan(val) {
    if (this._approveLoan) {
      console.log("Loan approved!");
    }
  }

  // Protected method
  _approveLoan(val) {
    return true;
  }
}

const acc1 = new Account("Jonas", "EURO", 1111);
```

## Private class fields

```javascript
class Account {
  // Public field (instances)
  locale = navigator.language;

  // Private field
  #movements = [];
  #pin;

  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.#pin = pin;
    console.log(`Thanks for opening an account, ${owner}!`);
  }

  // Public methods
  // Public interface
  deposit(val) {
    this.#movements.push(val);
  }

  withdraw(val) {
    this.deposit(-val);
  }

  getMovements() {
    return this.#movements;
  }

  requestLoan(val) {
    if (this.#approveLoan) {
      console.log("Loan approved!");
    }
  }

  // Private method
  #approveLoan(val) {
    return true;
  }
}

const acc1 = new Account("Jonas", "EURO", 1111);
```

> 1. Public instance fields exist on every created **instance** of a class.
> 2. We cannot define a field in the `constructor`. So we need to define `pin` outside of any method and then redefine it in `constructor`.
> 3. There are also static versions of [public fields and methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields), [private fields and methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_With_Private_Class_Features) to all these four.

## Chaining methods

To enable method chaining, we need to return the object in those methods.

```javascript
class Account {
  // Public field (instances)
  locale = navigator.language;

  // Private field
  #movements = [];
  #pin;

  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.#pin = pin;
    console.log(`Thanks for opening an account, ${owner}!`);
  }

  // Public methods
  // Public interface
  deposit(val) {
    this.#movements.push(val);
    return this;
  }

  withdraw(val) {
    this.deposit(-val);
    return this;
  }

  getMovements() {
    return this.#movements;
  }

  requestLoan(val) {
    if (this.#approveLoan) {
      this.deposit(val);
      console.log("Loan approved!");
      return this;
    }
  }

  // Private method
  #approveLoan(val) {
    return true;
  }
}

const acc1 = new Account("Jonas", "EURO", 1111);

// Chained methods
acc1.deposit(100).withdraw(500).requestLoan(300);
```
