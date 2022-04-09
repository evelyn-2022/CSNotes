# Constructor Function vs Factory Functions

## Constructor Function

1. They are named with **capital letter** first.
2. Each statement that creates a new property or method **ends in a semicolon (not a comma, which is used in the literal syntax)**.
3. They should be executed only with "new" operator.

```javascript
const Person = function(firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
}

const jonas = New Person('jonas', 1999);
```

To show the process after `New Person()` is called:

```javascript
// new empty object {} is created;
// this = {};
// {} is linked to prototype (jonas.__proto = Person.prototype);

// add properties to this
this.firstName = "jonas";
this.birthYear = 1999;

// return this;
```
