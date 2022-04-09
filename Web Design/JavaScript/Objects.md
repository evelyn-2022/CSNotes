 # Objects
 
 [toc]
 
 An object contains a bunch of keys and values. It can also contain functions.
 
 ## Properties
 
 ### Object Literal
 
ES6 provides the syntactic sugar to eliminate the redundancy of having to write x: x. You can simply write x once, and it will be converted tox: x (or something equivalent) under the hood:

```
// Before
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});

// After
const getMousePosition = (x, y) => ({ x, y });
```

### Accessing properties
 
 - dot notation: we write the object’s name, followed by the dot operator and then the property name (key);
 - bracket notation: we pass in the property name (key) **as a string**. We must use bracket notation when accessing keys that have numbers, spaces, or special characters in them.
 
 ```
 let spaceship = {
  'Fuel Type' : 'Turbo Fuel',
  'Active Mission' : true,
  homePlanet : 'Earth', 
  numCrew: 5
 };
 
 spaceship.numCrew;
 spaceship['numCrew'];
```

With bracket notation you can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when working with *functions*:

```
let returnAnyProp = (objectName, propName) => objectName[propName];
 
returnAnyProp(spaceship, 'homePlanet'); // Returns 'Earth'
```

If we tried to write our `returnAnyProp()` function with dot notation (`objectName.propName`) the computer would look for a key of 'propName' on our object and not the value of the `propName` paramete.

### Delete a property

You can delete a property from an object with the delete operator.

```
delete spaceship.numCrew;
```

 ### Testing property existence
 
 `.hasOwnProperty(propname)`:  returns true or false if the object has the specified property as its *own property* .
 
The `in` operator returns true if the specified property is in the specified object or its prototype chain.
 
 ## Methods
 
 We can include methods in our object literals by creating ordinary, comma-separated key-value pairs. 
 
 ```
 const alienShip = {
  invade: function () { 
    console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
  }
};
```

With the new method syntax introduced in ES6 we can omit the colon and the function keyword.

```
const alienShip = {
  invade () { 
    console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
  }
};
```

To call the function: `alienShip.invade()` or 	`alienShip["invade"]()`.

## Nested objects

```
const inner = {
	open: 9,
	close: 7
};

const outer = {
	name: 'jia',
	location: 'asdf',
	inner: inner
};
```

With ES6 enhanced enhanced object literals, we can create a property name *with exactly that variable name*.

```
const outer = {
	name: 'jia',
	location: 'asdf',
	inner,
};
```

## Optional chaining

With optional chaining, if a certain property does not exist, then undefined is returned immediately.

```
console.log(outer.time?.hour);
```

Only when `time` property exists, then the `hour` property will be read from there; if not, `undefined` will immediately be returned.

Optional chaining also works on methods and arrays.

## Pass by reference

Objects are passed by reference. This means when we pass a variable assigned to an object into a function as an argument, the computer interprets the parameter name as *pointing to the space in memory holding that object*. As a result, functions *which change object properties actually mutate the object permanently* (even when the object is assigned to a const variable). However, reassignment of the variable wouldn’t work in the same way:

```
let spaceship = {
  homePlanet : 'Earth',
  color : 'red'
};
let tryReassignment = obj => {
  obj = {
    identified : false, 
    'transport type' : 'flying'
  }
  console.log(obj) // Prints {'identified': false, 'transport type': 'flying'}
 
};
tryReassignment(spaceship) // The attempt at reassignment does not work.
spaceship // Still returns {homePlanet : 'Earth', color : 'red'};
 
spaceship = {
  identified : false, 
  'transport type': 'flying'
}; // Regular reassignment still works.
```
- When we passed spaceship into `tryReassignment` function, obj became a reference to the memory location of the spaceship object, but not to the spaceship variable. This is because the obj parameter of the tryReassignment() function is a variable in its own right. The body of tryReassignment() has no knowledge of the spaceship variable at all!
- When we did the reassignment in the body of tryReassignment(), the obj variable came to refer to the memory location of the object {'identified' : false, 'transport type' : 'flying'}, while the spaceship variable was completely unchanged from its earlier value.

## Looping through objects

```
let spaceship = {
    crew: {
    captain: { 
        name: 'Lily', 
        degree: 'Computer Engineering', 
        cheerTeam() { console.log('You got this!') } 
        },
    'chief officer': { 
        name: 'Dan', 
        degree: 'Aerospace Engineering', 
        agree() { console.log('I agree, captain!') } 
        },
    medic: { 
        name: 'Clementine', 
        degree: 'Physics', 
        announce() { console.log(`Jets on!`) } },
    }
}; 

// Write your code below
for (let crewMember in spaceship.crew) {
  console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`);
}
```

`for...in` will iterate through each element of the `spaceship.crew` object. In each iteration, the variable `crewMember` is set to one of spaceship.crew‘s keys, enabling us to log a list of crew members’ role and name.

```
for (const crew of Object.keys(spaceship.crew)) 
// Returns an array of keys

for (const value of Object.values(spaceship.crew))
// Returns an array of values

for (const [k, v] of Object.entries(spaceship.crew))
// Returns key and value
```

To loop through an *array*:
```
for (const [k, v] of spaceship.crew.entries())
// Here, k is the index number, not a string
```

 ## Context
 
 #### `this` keyword
 
 ```
 const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet() {
    console.log(dietType);
  }
};
goat.diet(); 
// Output will be "ReferenceError: dietType is not defined"
```

Why is dietType not defined even though it’s a property of goat? That’s because inside the scope of the `.diet()` method, we don’t automatically have access to other properties of the goat object.
```
  diet() {
    console.log(this.dietType);
  }
};
```

The `this` keyword references the *calling object* which provides access to the calling object’s properties. In the example above, the calling object is goat and by using `this` we’re accessing the goat object itself, and then the dietType property of goat by using property dot notation.

Anywhere you are in JavaScript you have a **context** you are in. You can reference that context by using `this`. If I just reference `this` from the outtermost layer, it'll be the global object, which in the browser is something called `window`. `window` already has a bunch of stuff on it.

```
console.log(this === window);
console.log(this.scrollY);
console.log(window.scrollY);
```
```
// output
true
0
0
undefined
```

