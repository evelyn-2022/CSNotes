# Functions

## First-class vs higher-order functions

<img src="https://s2.loli.net/2022/03/01/ElQBuDzbWTPKiek.png" >
 
## Scope

A variable is "alive" (in scope) in between whatever the closest `{` is until that `{` closes its corresponding `}`.

```javascript
function doStuff(B) {
  console.log(B); // works, B parameter is still in scope
  let H = "H";
  if (1 + 1 === 2) {
    const D = "D";
    H = "something else";
  }
  console.log(D); // does not work, D was declared in that if statement block
  console.log(H); // works, H was declared outside the if statement
}
```

However, variables which are declared _without the let or const keywords_ are automatically created in the global scope (unless in strict mode).

It is possible to have both local and global variables with the same name. When you do this, the _local variable takes precedence over the global variable_.

```javascript
const someVar = "Hat";

function myFun() {
  const someVar = "Head";
  return someVar;
}

myFun(); // output: Head
```

## Function expression

In a function expression, the function name is usually omitted. A function with no name is called an _anonymous function_.

```javascript
const calculateArea = function (width, height) {
  const area = width * height;
  return area;
};
```

Declare a variable to make the variable’s name be the name, or identifier, of your function. Since the release of ES6, it is common practice to use `const` as the keyword to declare the variable.

```javascript
variableName(argument1, argument2);
```

To invoke a function expression, write the name of the variable in which the function is stored followed by parentheses enclosing any arguments being passed into the function.

## Arrow function

Arrow functions remove the need to type out the keyword function every time you need to create a function. Instead, you first include the parameters inside the `( )` and then add an arrow `=>` that points to the function body surrounded in `{ }` like this:

```javascript
const rectangleArea = (width, height) => {
  let area = width * height;
  return area;
};
```

### Concise Body Arrow Functions

1. Functions that _take only a single parameter do not need that parameter to be enclosed in parentheses_. However, if a function takes zero or multiple parameters, parentheses are required.

```javascript
// ZERO PARAMETERS
const functionName = () => {};

// ONE PARAMETER
const functionName = (paramOne) => {};

// TWO OR MORE PARAMETERS
const functionName = (paramOne, paramTwo) => {};
```

2. A function body _composed of a single-line block does not need curly braces_. Without the curly braces, whatever that line evaluates will be automatically returned. The contents of the block should immediately follow the arrow `=>` and the `return` keyword can be removed. This is referred to as _implicit return_.

```javascript
// SINGLE-LINE BLOCK
const sumNumbers = (number) => number + number;

// MULTI-LINE BLOCK
const sumNumbers = (number) => {
  const sum = number + number;
  return sum;
};
```

Example:

```javascript
// before
const plantNeedsWater = (day) => {
  return day === "Wednesday" ? true : false;
};

// after
const plantNeedsWater = (day) => (day === "Wednesday" ? true : false);
```

### Default parameters

```javascript
function greeting(name = "stranger") {
  return `Hello, ${name}!`;
}

console.log(greeting("Nick")); // Output: Hello, Nick!
console.log(greeting()); // Output: Hello, stranger!
```

Arrow functions can also take default parameters:

```javascript
const greeting = (name = "stranger") => `Hello, ${name}`;
```

If we need to skip one parameter, we can set the argument to undefined:

```javascript
const createBooking = function (
  flightNum,
  numPassengers = 1,
  price = 199 * numPassengers
) {
  const booking = {
    flightNum,
    numPassengers,
    price,
  };
  console.log(booking);
};

createBooking("LH123", undefined, 1000);

// Prints: {flightNum: 'LH123', numPassengers: 1, price: 1000}
```

## Function objects

JavaScript functions behave like any other data type in the language; we can assign functions to variables, and we can reassign them to new variables.

```javascript
const announceThatIAmDoingImportantWork = () => {
  console.log("I’m doing very important work!");
};

const busy = announceThatIAmDoingImportantWork;

busy(); // This function call barely takes any space!
```

In JavaScript, functions are _first class objects_. This means that, like other objects you’ve encountered, JavaScript functions can have _properties and methods_.

## Functions as parameters

```javascript
const timeFuncRuntime = (funcParameter) => {
  let t1 = Date.now();
  funcParameter();
  let t2 = Date.now();
  return t2 - t1;
};

const addOneToOne = () => 1 + 1;

timeFuncRuntime(addOneToOne);
```

When we pass a function in as an argument to another function, we don’t invoke it. Invoking the function would evaluate to the return value of that function call. With callbacks, we pass in the function itself by typing the function name _without the parentheses_.

```javascript
timeFuncRuntime(() => {
  for (let i = 10; i > 0; i--) {
    console.log(i);
  }
});
```

In this example, we invoked timeFuncRuntime() with an anonymous function that counts backwards from 10.

Another example:

```javascript
function add(num1, num2) {
  return num1 + num2;
}

function multiply(num1, num3) {
  return num1 * num2;
}

function calculator(num1, num2, operator) {
  return operator(num1, num2);
}
```

#### Callback

```javascript
document.addEventListener("keydown", function (event) {
  console.log(event.key);
});
```

Here, the `event` parameter will give back the event that triggered the callback function.

## Immediately invoked function expression (IIFE)

```javascript
(function IIFE() {
  console.log("Hello!");
})();
// "Hello!"
```

The function name can be omitted. By wraping function in parenthesis, we can trick JavaScript into thinking this is an expression:

```javascript
(function () {
  console.log("Hello!");
})();
```

Arrow function：

```javascript
(() => console.log("Hello!"))();
```

IIFEs can also have return values:

```javascript
var x = (function IIFE() {
  return 42;
})();

x; // 42
```

## Functions returning functions

```javascript
const greet = function (greeting) {
  return function (name) {
    console.log(`${greeting} ${name}`);
  };
};

const greeterHey = greet("Hey");
greeterHey("Jonas");
greeterHey("Steven");

// Prints:
// Hey Jonas
// Hey Steven
```

We can also call the function directly:

```javascript
greet("Hello")("Jonas");
```

### With event listener

```javascript
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this);

  this.planes++;
  console.log(this.planes);
};
// lufthansa.buyPlane();

document
  .querySelector(".buy")
  .addEventListener("click", lufthansa.buyPlane.bind(lufthansa));
```

If we don't use bind, `this` keyword will point to the button with class `buy`.

### Partial application

To create a brand new, simply, more specific function based on a more general function:

```javascript
const addTax = (rate, value) => value + value * rate;

const addVAT = addTax.bind(null, 0.23);
// addVAT = value => value + value * 0.23;

console.log(addVAT(100));
// Prints: 123
```

In this case, we don't care about the `this` keyword. So it's a standard practice to use `null`.

## Closure
