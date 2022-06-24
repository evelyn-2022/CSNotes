# Data types

if we declare a variable without initializing it, the variable will be automatically initialized with a value of `undefined`. `const` cannot be defined without initializing.

Difference between `var` and `let`:

- Unlike `var`, when you use `let`, a variable with the same name can only be declared once (will not be overwritten because of being declared more than once).

```javascript
var numArray = [];
for (var i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
console.log(i);
```

Here the console will display the values [0, 1, 2] and 3 because with the `var` keyword, i is declared globally.
This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function will always refer to the _value of the updated global i variable_.

```javascript
var printNumTwo;
for (var i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function () {
      return i;
    };
  }
}
console.log(printNumTwo()); // output: 3
```

## Strings

- Length of string: `'abcd1234'.length`;

- Find the index of a certain character: `'abcd1234'.indexOf('c')`; to find the last index of a certain character: `'abcd1234'.lastIndexOf('c')`. We can also search for a certain word using `indexOf()`.

- To slice a substring:

```javascript
const myString = "abcd1234";
console.log(myString.slice(myString.indexOf(1)));
// Prints: 1234
```

- Convert to uppercase / lowercase: `.toUpperCase()`, `.toLowerCase()`
- `.trim()`: remove whitespace. You can also use `.trimStart()` or `.trimEnd()` to remove the left or right whitespace.
- To replace a part of the string:

```javascript
const priceGB = "288,97£";
const priceUS = priceGB.replace("£", "$").replace(",", ".");
// Prints: 288.97$
```

But the `.replace` method only replace the first appearance of an element. To replace all, we need to use regular expression:

```javascript
const test = "abbjklabbcgb";
console.log(test.replace(/abb/g, "***"));

// Prints: ***jkl***cgb
```

- To test if the string includes an element: `.includes(elm)`
- To test if the string starts with an element `.startsWith('elm')`
- To test if ends with: `.endsWith('elm')`
- To split the string, `.split()`:
- To join the string, `.join()` :

```javascript
const [firstName, lastName] = "Jonas Schmedtmann".split(" ");
const newName = ["Mr", firstName, lastName.toUpperCase()].join("-");
console.log(newName);

// Prints: Mr-Jonas-SCHMEDTMANN
```

- `.padStart()` and `.padEnd()`: padding a string (to add a number of characters to the string until the string has a certain desired length)

```javascript
console.log("jonas".padStart(12, "*"));

// Prints: *******jonas
```

- To repeat the same string multiple times:

### Boxing

Methods only be available on objects. But strings are primitives. Why do strings have methods?

<kp>Boxing</kp>Whenever we call a method on a string, JavaScript will automatically behind the scenes take that string primitive and put it into a box which is a string object.

What happened behind the scene: `new String(myString)`.

### Template strings

If you use `backticks`, around your strings, you get template strings. It was updated in 2015. Using template strings, everything inside `${}` will be substituted as variables.

```javascript
const firstName = "Brian";
const lastName = "Holt";

const sentenceWithTemplate = `Hello ${firstName} ${lastName}! How are you!?`;
```

We can also use template strings to span multiple lines:

```javascript
console.log(`String
multiple
lines`);
```

## Numbers

JavaScript don't seperate integers and floats, only one type, `number`. All numbers are presented internally as floating point numbers. Numbers are in a 64 base 2 format, so they are always stored in a binary format.

### Numeric seperator

We can use '\_' to seperate long numbers.

```javascript
const diameter = 187_000_000;
```

## Type coercion

- "+" sign: number will be converted to string
- "-" sign: string will be converted to number
- When used as unary operator, '+' and '-' refer to positive or negative numbers, so it will always be converted to a number: `Number('5')` produces the same result as `+'5'`.

```javascript
console.log("23" - "10" - 3); // 10
console.log("23" + "10" + 3); // '23103'
console.log("23" * "2"); // 46
console.log(2 + 3 + 4 + "5"); // '95'
console.log("10" - "4" - "3" - 2 + "5"); // 15
```

### Make use of type coercion

```javascript
const num = +inp.value; // convert string to number
const newStr = Date.now() + ""; // convert number to string
```

### `parceInt` and `parceFloat`

`parseInt()` function parses a string and returns an integer. If the first character in the string can't be converted into a number, then it returns `NaN`. It takes a second argument for the **radix**, which specifies the base of the number in the string. The radix can be an integer between 2 and 36.

```javascript
const a = Number.parseInt("11", 2); // output: 3
```

Similarly, `parseFloat` will decimal number from our string:

```javascript
console.log(Number.parseFloat("2.5rem")); // 2.5
```

### `isFinite` and `isNaN`

`isNaN` checks if is _NaN_:

```javascript
Number.isNaN(20); // false
Number.isNaN("20"); // false
Number.isNaN(+"20X"); // true
```

Comparison with `.isNaN`: only values of the type _number_, that are also NaN, return true.

```javascript
isNaN(undefined); // true
Number.isNaN(undefined); // false
```

But when dealing with infinity, it also returns false:

```javascript
Number.isNaN(23 / 0); // false
```

`isFinite` checks if value _is a number_:

```javascript
Number.isFinite(23 / 0); // false
Number.isFinite(+"20X"); // false
```

`isInteger` checks if value _is integer_.

## `math` namespace

- `Math.sqrt()`
- `Math.max()`
- `Math.PI`
- `Math.trunc()`: remove decimal part

## Other methods

- `.tiFixed()`: specify decimal numbers, returns a _string_
- `.toPrecision()` method formats a number to a specified length.

## BigInt

We can add a `n` to the end of a number in order to create a BigInt: `792635037250n`. We can also use construction functions `BigInt(937593)`, but this only works well on smaller numbers.

## Dates and time

```javascript
const now = new Date(); // Outputs current date and time
```

We can also pass in string about time, and JavaScript will automatically turn it into standard time.

```javascript
console.log(new Date("December 24 1998"));
// Output： Thu Dec 24 1998 00:00:00 GMT+0800 (Singapore Standard Time)
```

<kp>Timestamp</kp>
The amount of milliseconds passed since the beginning of the Unix time, which is _January 1, 1970_. To create a date three days later after Unix time:

```javascript
console.log(new Date(3 * 24 * 60 * 60 * 1000));

// Convert a date to number
let a = new Date("2034 april 5");
console.log(+a); // Output: 2027779200000
```

To get the amount of miniseconds passed after Unix time, use `.getTime()`. We can then create the date using the miniseconds:

```javascript
let a = new Date("2034 april 5");
console.log(a);
// Output: Wed Apr 05 2034 00:00:00 GMT+0800 (Singapore Standard Time)

console.log(a.getTime());
// Output: 2027779200000

console.log(new Date(2027779200000));
// Output: Wed Apr 05 2034 00:00:00 GMT+0800 (Singapore Standard Time)
```

Methods of date object:

- `.getFullYear()`: get the year
- `.getMonth()`: because it is _zero based_, 10 is actually the month number 11
- `.getDate()`: get the date
- `.getDay()`: get the day of the week, e.g. sunday
- `.getHours()`, `gerMinutes()` and `getSeconds()`
- `.toISOString()`: get a nicely formatted string
- `.setFulYear()` and the like can be used to set time.

==Note== `.get...` methods cannot work on ISOString, so ISOString needs to be converted to date using `new Date(string)` before getting date, month, year, etc.

## Internationalization API

[language code](https://www.andiamo.co.uk/resources/iso-language-codes/)

<kp>Syntax</kp>

```javascript
new Intl.DateTimeFormat(locale, options).format(time);
```

`Intl`: the namespace for the Internationalization API

`.DateTimeFormat()`: we need to pass in a locale string, which is languange-country.

`.format()`: here we pass in the date to be formatted

options: an object with properties that vary between constructors and functions.

```javascript
const options = {
  hour: "numeric",
  minute: "numeric",
  day: "2-digit",
  month: "long",
  year: "numeric",
  weekday: "short",
};
const now = new Date();
labelDate.textContent = Intl.DateTimeFormat("en-US", options).format(now);

// Output: Mon, March 07, 2022, 4:14 PM
```

To get locale from user's browser without setting it manually:

```javascript
const locale = navigator.language;
```

`.NumberFormat()`: language-sensitive number formatting

## Timer

### setTimeOut

<kp>Syntax</kp>

```javascript
var timeoutID = setTimeout(function[, delay]);
```

```javascript
const ingredients = ["olives", "spinach"];
const pizzaTimer = setTimeOut(
  (ing1, ing2) => console.log(`Here is your pizza with ${ing1} and ${ing2}`),
  3000,
  ...ingredients
);

if (ingredients.includes("spinach")) clearTimer(pizzaTimer);
```

### setInterval

`setInterval()` will be executed over and over again with interval.
