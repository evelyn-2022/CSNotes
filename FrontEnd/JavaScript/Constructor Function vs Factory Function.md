# Constructor Function vs Factory Functions

## Constructor Function [^1]

1. They are named with **capital letter** first.
2. Each statement that creates a new property or method **ends in a semicolon (not a comma, which is used in the literal syntax)**.
3. They should be executed only with `new` operator.

```javascript
// Function declaration
function Person(firstName, birthYear) {
  --snip--
}

// Or Function expression
const Person = function(firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};

const jonas = new Person('jonas', 1999);
```

What happens after `New Person()` is called:

```javascript
// New empty object {} is created;
this = {}; // Implicit
this.__proto__ = Person.prototype;  // Implicit

// Add properties to this
this.firstName = "jonas";
this.birthYear = 1999;

return this;  // Implicit
```

### Return from constructors

Usually, constructors do not have a `return` statement. Their task is to write all necessary stuff into this, and it automatically becomes the result.

But if there is a `return` statement, then the rule is simple:

If `return` is called with an object, then the object is returned instead of this.
If `return` is called with a primitive, it’s ignored.

==Note:== It's bad practice to create methods inside of a constructor function. Instead, use prototype or protopype inheritance.

## Factory Function

A factory function is a function that returns a new object.

```javascript
const person = function (firstName, birthYear) {
  return {
    firstName: firstName,
    birthYear: birthYear,
  };
};

// Or
const person = function (firstName, birthYear) {
  let person = {};
  person.firstName = firstName;
  person.birthYear = birthYear;
  return person;
};

// To create an object
const jonas = person("jonas", 1999);
```

### Property Value Shorthand

ES6 introduced some new shortcuts for assigning properties to variables known as destructuring. The example below works exactly like the example above:

```javascript
const person = (firstName, birthYear) => {
  return {
    firstName,
    birthYear,
  };
};
```

## Compare them in the console[^2]

#### Factory Function

```javascript
jonas
{firstName: 'jonas', birthYear: 1999}
  birthYear: 1999
  firstName: "jonas"
  [[Prototype]]: Object
    constructor: ƒ Object()
    hasOwnProperty: ƒ hasOwnProperty()
    isPrototypeOf: ƒ isPrototypeOf()
  ......

jonas.constructor
ƒ Object() { [native code] }

jonas.__proto__ === person.prototype
false
jonas.__proto__ === Object.prototype
true
```

#### Constructor Function

```javascript
jonas
Person {firstName: 'jonas', birthYear: 1999}
  birthYear: 1999
  firstName: "jonas"
  [[Prototype]]: Object
    constructor: ƒ (firstName, birthYear)
    [[Prototype]]: Object
      constructor: ƒ Object()
      hasOwnProperty: ƒ hasOwnProperty()
      isPrototypeOf: ƒ isPrototypeOf()
      ...

jonas.constructor
ƒ (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
}

jonas.__proto__ === Person.prototype
true
```

[^1]: [Constructor, operator "new"](https://javascript.info/constructor-new)
[^2]: [JavaScript Factory functions vs Constructor functions](https://chamikakasun.medium.com/javascript-factory-functions-vs-constructor-functions-585919818afe#:~:text=A%20factory%20function%20is%20any,keyword%2C%20it's%20a%20factory%20function.)
