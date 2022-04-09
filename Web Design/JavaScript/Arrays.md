# Arrays

[toc]

## To create an array
Arrays are defined using `[]`. 

To create a new array:

```
const primeNumbers = [1, 2, 3, 5, 7, 11, 13, 17];
// Or
const priNumbers = new Array(1, 2, 3, 5, 7, 11, 13, 17);
```

However, when we only pass in one arguent, it will create an empty argument with that length:

```
const x = new Array(7);
console.log(x);
// Output
[empty × 7]
```
The **only** method we can call on this array is `.fill()`.

```
x.fill(5);
console.log(x);
// Output: [5, 5, 5, 5, 5, 5, 5]

x.fill(5, 3);  // [empty × 3, 5, 5, 5, 5]
x.fill(5, 3, 6);  // [empty × 3, 5, 5, 5, empty]
```
`.fill()` also works on arrays that are not empty.

`.from` method: a function attached to the *Array constructor*, not to the prototype.

<kp>Syntax</kp>
```
Array.from(arrayLike, mapFn, thisArg)
Array.from(arrayLike, (element, index) => { /* ... */ } )
```
`arrayLike`: an array-like or **iterable object** to convert to an array.

Here, `Array` is a function, and we are calling the method `from` on this function object.

```
const y = Array.from({length: 7}, () => 1); // Output: [1, 1, 1, 1, 1, 1, 1]
const z = Array.from({length: 7}, (_, i) => i + 1);  // Output: [1, 2, 3, 4, 5, 6, 7]
```

`.from` can also be used on **nodelists**, which is something like an array and contains all the selected elements, but it's not a real array. To use methods like `map()` or `reduce` on it, we can first convert it into a real array using `.from`.

## Array methods

- To add an element to the end of array, use `.push(item)`. 
- To add items to the beginning, use `.unshift()`. 
- To remove the last item, use `.pop()`. 
- To remove the first item, use `.shift(item)`.
- To test whether it includes an item: `.incluces()`.
- To slice a part of tha array, `.slice(beginning index, optional ending index)` (index can be negative).
- To create a shallow copy of an array: `arr.slice()` or `[...arr]`.
- To actually **mutate the original array**, `.splice(beginning index, the number of elements we want to delete)`. You can use the third index to add more elements to the array.
```
const numbers = [10, 11, 12, 12, 15];
const startIndex = 3;
const amountToDelete = 1;

numbers.splice(startIndex, amountToDelete, 13, 14);
console.log(numbers);  // Output: [ 10, 11, 12, 13, 14, 15 ]
```
- To reverse the array, `arr.reverse()`, mutates the original array.
- To concat two arrays, `arr1.concat(arr2)`, gives the same result as `[...arr1, ...arr2].`
- To join all elements of an array, `arr.join('*')`.
- ES 2022, `at` method: `arr.at[index]`, gives the same result as `arr[index]`.
- To get the last array element: `arr[arr.length - 1]`, `arr.slice(-1)[0]` or `arr.at(-1)`.
- `.includes(item)`: to test if array includes a specific item.
- `.some()`: to test whether at least one element in the array passes the test implemented by the provided function.
- `.every()`: similar to `some`, but only returns true if all elements satisfy the condition.
- `.flat(depth)`: creates a new array with all sub-array elements concatenated into it recursively up to the specified depth. `depth` is optional.
```
const arr2 = [0, 1, 2, [[[3, 4]]]];
console.log(arr2.flat(2));
// expected output: [0, 1, 2, [3, 4]]
```




## Iteration

### `.forEach()` method

<img src="https://content.codecademy.com/courses/learn-javascript-iterators/iterator%20anatomy.svg">

`.forEach()` loops through the array and executes the callback function for each element. During each execution, the current element is passed as an argument to the callback function.
The return value for `.forEach()` will always be *undefined*.

<kp>Syntax</kp>We can also pass in current index as the second argument, entire array as the third argument of the function:

```
array.forEach(function(currentValue, index, arr), thisValue)
```

<kp>With arrow function </kp>
```
groceries.forEach(groceryItem => console.log(groceryItem));
```
- currentValue (Required): The value of the current element.
- index	(Optional): The index of the current element.
- arr (Optional): The array of the current element.
- `this` Value	(Optional, Default undefined): A value passed to the function as its this value.

==Note:== 
1. there is no `break` or `continue` in the `.forEach()` loop, it will always loop over the entire array.
2. `.forEach()` also works on maps and sets.
```
const currencies = new Map([
	['USD', 'United States dollar'],
	['EUR', 'Euro'],
	['GBP', 'Pound sterling'],
]);

currencies.forEach(function (value, key, map) {
	console.log(`${key}: ${value}`);
});
```

We can also define a function beforehand to be used as the callback function.
```
function printGrocery(element){
  console.log(element);
}
 
groceries.forEach(printGrocery);
```

### `.map()` method

When `.map()` is called on an array, it takes an argument of a callback function and returns *a new array*.

```
const numbers = [1, 2, 3, 4, 5]; 
 
const bigNumbers = numbers.map(number => {
  return number * 10;
});
```

`bigNumbers` will store the return value of calling `.map()` on numbers.

### `.flapMap()` method

`flatMap()` method returns a new array formed by applying a given callback function to each element of the array, and then flattening the result by one level. But it only goes *one level deep*.

### `.filter()` method

Like `.map()`, `.filter()` returns a new array. However, `.filter()` returns an array of elements after filtering out certain elements from the original array. The callback function for the `.filter()` method should *return true or false* depending on the element that is passed to it. The elements that cause the callback function to return true are added to the new array.

```
const words = ['chair', 'music', 'pillow', 'brick', 'pen', 'door']; 
 
const shortWords = words.filter(word => {
  return word.length < 6;
});
```

### `.find()` method

<kp>Syntax</kp>

```
find((element, index, array) => { /* ... */ } )
```

The `index` and `array` element are optional.

The `find()` method returns the **first** element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, `undefined` is returned.

### `.findIndex()` method

Calling `.findIndex()` on an array will return the *index of the first element* that evaluates to true in the callback function.

```
const jumbledNums = [123, 25, 78, 5, 9]; 
 
const lessThanTen = jumbledNums.findIndex(num => {
  return num < 10;
});

console.log(lessThanTen); // Output: 3 
```

If there isn’t a single element in the array that satisfies the condition in the callback, then `.findIndex()` will return -1.

### `.reduce()` method

The `.reduce()` method *returns a single value* after iterating through the elements of an array, thereby reducing the array.

<kp>Syntax</kp>

```
const outcome = arr.reduce(function(accumulator, currentElement, index, arr) {
	return accumulator + currentElement;
});
```

The `.reduce()` method can also take an optional second parameter to set an initial value for accumulator (remember, the first argument is the callback function!).

```
const numbers = [1, 2, 4, 10];
 
const summedNums = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 100);  // <- Second argument for .reduce()
 
console.log(summedNums); // Output: 117
```

`.reduce` can also return an object:

```
const account1 = {
  owner: 'Jonas Schmedtmann',
  movements: [200, 450, -400, 3000, -650, -130, 70, 1300],
};
// snap
const accounts = [account1, account2, account3, account4];

const sum = accounts
  .flatMap(acc => acc.movements)
  .reduce(
    (acc, cur) => {
      cur > 0 ? (acc.deposit += cur) : (acc.withdrawal += cur);
      return acc;
    },
    { deposit: 0, withdrawal: 0 }
  );
console.log(sum);
```

Another way to calculate sum:

```
const sum = accounts
  .flatMap(acc => acc.movements)
  .reduce(
    (acc, cur) => {
      acc[cur > 0 ? 'deposit' : 'withdrawal'] += cur;
      return acc;
    },
    { deposit: 0, withdrawal: 0 }
  );
```

### `.sort()` method

The `sort()` method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon *converting the elements into strings*, then comparing their sequences of UTF-16 code units values.

<kp>Syntax</kp>
```
// Arrow function
sort((firstEl, secondEl) => { /* ... */ } )

// Compare function
sort(compareFn)

// Inline compare function
sort(function compareFn(firstEl, secondEl) { /* ... */ })
```

If compareFunction is supplied, all non-undefined array elements are sorted according to the *return value* of the compare function. To compare **numbers** instead of strings, the compare function can subtract b from a.

```
// Function expression
let numbers = [3, 5, 1, 4, 2];
numbers.sort(function (a, b) {
	return a - b;
})

// Arrow function
numbers.sort((a, b) => a - b);
```

## Which method to choose

<img src="https://s2.loli.net/2022/03/05/NrEIpwiuxZBvJhL.png" >

## Example

Flatten a nested array. You must account for varying levels of nesting, and you should not use `.map()`.

```
function steamrollArray(arr) {
  const flattenedArray = [];
  // Loop over array contents
  for (let i = 0; i < arr.length; i++) {
    if (Array.isArray(arr[i])) {
      console.log('array', arr[i]);
      // Recursively flatten entries that are arrays
      //  and push into the flattenedArray
      flattenedArray.push(...steamrollArray(arr[i]));
    } else {
      // Copy contents that are not arrays
      flattenedArray.push(arr[i]);
    }
  }
  console.log(flattenedArray);
  return flattenedArray;

}

steamrollArray([1, [2], [3, [[4]]]]);
```
