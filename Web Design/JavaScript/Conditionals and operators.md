
# Conditionals and operators

[toc]

## Loops

```
for (var key in object)
{
	// use object[key] in here
}
```

To loop through all elements:

```
var students = [/*..*/];

for (let i = 0; i < students.length; i++) {
	greetStudent(students[i]);
}

for (let student of students) {
	greetStudent(student);
}
```

This will give you the current element of the loop.
If we need the current index, we can use `for (let student of students.entries())`, which will give us an array of the current index and element, and we can use destructuring to log them seperately.

==Note:== differences between `for...in` and `for...of`

`for..in` iterates over all enumerable property **keys** of an object;
`for..of` iterates over the **values** of an iterable object. The values which an iterable data structure will return using `for..of` is dependent on the type of iterable object.

[Read more about the differences](https://stackoverflow.com/questions/29285897/what-is-the-difference-between-for-in-and-for-of-statements)

## Operators

- binary operators: `+`, `-`...
- unary operators: `!`, *a single operand* involved in the operation, such as `!true`

### Short-circuit evaluation

```
// OR OPERATOR
console.log('jonas' || 3);  
// Prints: jonas
console.log('' || 3); 
// Prints: 3
console.log(undefined, null);
// Prints: null (even though null is also a falsy value)

// AND OPERATOR
console.log(0 && 3);
// Prints: 0 (return the first falsy value without evaluating the second operand)
console.log(3 && "jonas")
// Prints: jonas
```

### Nullish Coalescing Operator `??`

Problem with value 0 when using `||`:

```
const guestNum = 0;
console.log(guestNum || 10);
// Prints: 10 (but  guestNum is actually defined)
```

This operator was introduced in ES 2000:

```
const guestNum = 0;
console.log(guestNum ?? 10);
// Prints: 0
``` 

nullish: null and undefined, so 0 and empty string will not be falsy values

### Logical Assignment Operators

Introduced in 2021

```
const rest1 = {
	name: 'Carp',
	numGuests: 20
};

const rest2 = {
	name: 'La Piazza',
	owner: 'Jack'
};

rest1.numGuests ||= 10;
rest2.numGuests ||= 10;

console.log(rest1);
// Prints: {name: 'Carp',numGuests: 20}
console.log(rest2);
// Prints: {name: 'La Piazza',owner: 'Jack',numGuests: 10}
```

The OR assignment operator assigns a variable to a variable if that variable is currently falsy (don't work fine if the value is 0).

We can use the logical nullish assignment operator `??=` if the value is 0.

The AND assignment operator assigns a value to a variable if the variable is currently truthy.

```
rest1.owner &&= '<ANONYMOUS>';
rest2.owner &&= '<ANONYMOUS>';
console.log(rest1);
// Prints: {name: 'Carp',numGuests: 20}
console.log(rest2);
// Prints: {name: 'La Piazza',owner: <ANONYMOUS>,numGuests: 10}
```

### Ternary Operator

```
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

It has the same effect as 

```
if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

#### Multiple Conditional (Ternary) Operators

```
function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" 
    : (a > b) ? "a is greater" 
    : "b is greater";
}
```

#### Optional Chaining

The `?.` operator is like the `.` chaining operator, except that instead of causing an error if a reference is *nullish* (null or undefined), the expression short-circuits with a return value of `undefined`. 

### Difference between `i++` and `++i`

`++i` will increment the value of i, and then return the incremented value.

```
 i = 1;
 j = ++i;
 (i is 2, j is 2)
 ```
 
` i++` will increment the value of i, but return the original value that i held before being incremented.

```
 i = 1;
 j = i++;
 (i is 2, j is 1)
 ```
 