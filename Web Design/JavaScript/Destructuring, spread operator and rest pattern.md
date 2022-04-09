# Destructuring, spread operator and rest pattern

[toc]

## Destructuring

### Destructuring objects

```
const vampire = {
  name: 'Dracula',
  residence: 'Transylvania',
  preferences: {
    day: 'stay inside',
    night: 'satisfy appetite'
  },
  functionality: {
    beep() {
      console.log('Beep Boop');
    },
    fireLaser() {
      console.log('Pew Pew');
    },
  }
};
```

We can take advantage of a destructuring technique called *destructured assignment* to save ourselves some keystrokes. In destructured assignment we create *a variable with the name of an object’s key* that is wrapped in curly braces { } and assign to it the object.

```
const { name, residence } = vampire; 
console.log(name); // Prints 'Dracula'
console.log(residence); // Prints 'Transylvania'
```

Here's how you can give new variable names in the assignment:

```
const { 
	name: userName, 
	residence: placeToGo 
} = vampire; 
```

Here, vampire.name is assigned to a new variable name userName, and vampire.residence is assigned to placeToGo.

We can also use default values in case it's not defined:

```
const { 
	name: userName = 'John', 
	residence: placeToGo = 'Castle'
} = vampire; 
```

#### Mutating variables

```
let a = 111;
let b = 999;
const obj = {a: 23, b: 7, c: 14};
({a, b} = obj); // Take special notice of parenthesis
console.log(a, b);  // Prints 23 7
```

Here we cannot use `const` or `let` because a and b have been defined before. Instead, we need to wrap things up in parenthesis when destructuring, because if a line starts with curly braces, JavaScript will interpret it as a code block.

#### nested properties 

```
const { day } = vampire.preferences; 
console.log(day); // Prints 'stay inside'
```
Or:

```
const { preferences: { day: activity1, night: activity2}} = vampire;
```

Since functionality is referencing robot.functionality we can call the methods available to robot.functionality simply through functionality.

```
functionality.beep();
```


### Destructuring arrays

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

Destructuring an array lets us do exactly that:

```
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b);
```

The console will display the values of a and b as 1, 2.

We can also access the value at any index in an array with destructuring by using commas to reach the desired index:

```
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
```
The console will display the values of a, b, and c as 1, 2, 5.

We can also assign default value to thses variables:

```
const [p = 1, q = 1, r = 1] = [2, 3];
console.log(p, q);
// Output: 2 3 1
```

### Destructuring assignment

Use Destructuring Assignment to Pass an Object as a Function's Parameters:

```
const stats = {
  max: 56.78,
  standard_deviation: 4.34,
  median: 34.54,
  mode: 23.87,
  min: -0.75,
  average: 35.85
};

// Without destructuring
const half = (stats) => (stats.max + stats.min) / 2.0;

// Use destructuring
const half = ({max, min}) => (max + min) / 2.0;
```

## Spread Operator

*Spread operator* allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

The ES5 code below uses `apply()` to compute the maximum value in an array:

```
var arr = [6, 89, 3, 45];
var maximus = Math.max.apply(null, arr);  // output: 89
```

We had to use `Math.max.apply(null, arr)` because `Math.max(arr)` returns `NaN`. `Math.max()` expects comma-separated arguments, but not an array. 

Since ES6, the spread operator makes this syntax much better to read and maintain.

```
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
```
`...arr` returns an **unpacked array**. In other words, it's like taking all the elements out of the array and writing them manually. However, the spread operator only works in-place, like in an argument to a function or in an array literal. The following code will not work:

```
const spreaded = ...arr;
```
Correct way:
```
const spreaded = [...arr];  
// Prints '6 89 3 45'
```
As spread operator takes *all* the elements from the array and doesn't create new variables, as a consequence, we can only use it in places where we would otherwise write *multiple values separated by commas* (usually to pass arguments to a function or build a new array).

Spread operators work on all iterables (including arrays, strings, maps, or sets, but NOT objects).

However, since ES 2018, it also works on objects, and we can use it to copy all properties of the old object into new ones.

## Rest pattern and parameters

==Note:== Comparing spread and rest

```
//  SPREAD, because on RIGHT side of =
const arr = [1, 2, ...[3, 4]];

// REST, because on LEFT side of =
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others);  // Output: 1 2 [3, 4, 5]
```

ES6 introduces the *rest parameter*. It takes multiple numbers of values and then packs them *all into one array*.

Rest parameter also works on object properties.

With the rest parameter, you can create functions that take a variable number of arguments. These arguments are stored in an *array* that can be accessed later from inside the function.

```
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));  
// You have passed 3 arguments.
console.log(howMany("string", null, [1, 2, 3], { }));  
// You have passed 4 arguments.
```

The rest parameter eliminates the need to check the `args` array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.

Take any number of arguments and return their sum:
```
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}
```
