# Sets and Maps

## Sets

A set is a collection of **unique** values. It doesn't have order.

To create a new set, we write `new Set` and pass in an iterable. The most common iterable is an array.

```js
const ordersSet = new Set([
  "Pasta",
  "Pizza",
  "Pizza",
  "Risotto",
  "Pasta",
  "Pizza",
]);
console.log(ordersSet);

// Prints: Set(3) {"Pasta", "Pizza", "Risotto"}
```

We can also pass in a string as an iterable:

```js
console.log(new Set("Jonas"));

// Prints: Set (5) {"J", "o", "n", "a", "s"}
```

The length of a set: `ordersSet.size`;

To check whether a certain element is in the set: `ordersSet.has('Pizza')`;

To add an element: `ordersSet.add('Bread')`, to delete: `ordersSet.delete('Pizza')`. To delete all: `ordersSet.clear()`.

Convert set into array

We can use spread operator (works on iterables) to convert set to array:

```js
const ordersArr = [...ordersSet];
```

## Maps

A map is a data structure that we can use to **map values to keys**. Just like an object, data is stored in key value pairs in maps. The big difference between objects and maps is that in maps, _the keys can have any type_.

We can first create an empty map using `new Map` and then use `set` method to pass in arguments.

```js
const rest = new Map();
rest.set("name", "Classico Italiano");
rest.set(1, "Italy");
rest
  .set(2, "Portugal")
  .set(categories, ["Italian", "Vegetarian", "Organic"])
  .set("open", 11)
  .set("close", 23)
  .set(true, "We are open")
  .set(false, "We are closed");
```

We use `get` method to read data from the map.

```js
const time = 21;
console.log(rest.get(time > rest.get("open") && time < rest.get("close")));

// Prints: We are open
```

To check if a map contains a certain key: `rest.has('categories')`;

To delete a key and value: `rest.delete(2)`;

To count the number of items: `rest.size`;

To remove all elements: `rest.clear()`.

==Note:==

If we use objects as key, we cannot directly use it to retrive value:

```js
rest.set([1, 2], "Test");
console.log(rest.get([1, 2]));

// Prints: undefined (because these two arrays are not the same one in the heap)
```

Instead, we need to create an array and use the same array to read the value out of the map:

```js
const arr = [1, 2];
rest.set(arr, "Test");
```

Another way to create a map without using the `set` method: we can pass in an array and this array itself will contain multiple arrays. In each of these arrays, the first position is gonna be the key, and the second position is gonna be the value.

```js
const question = new Map([
  ["question", "What is the best programming language?"],
  [1, "C"],
  [2, "Java"],
  [3, "JavaScript"],
  ["correct", 3],
  [true, "Correct"],
  [false, "Try again"],
]);
```

The structure we passed in is an array of arrays, which is exactly the structure of `Object.entries()` of an object. So, to convert an object into a map, we can simply use `const newMap = new Map(Object.entries(myObject))`.

We can also use spread operator to convert map to array:

```js
const ordersArr = [...question];
```

`.entries()`, `.keys()` and `.values()` also work on maps.
