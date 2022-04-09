# OOP

[toc]

## Three ways of creating prototypes

<img src="https://s2.loli.net/2022/04/01/xaNWtJDIsLncSfH.png" >

Arrow function cannot work as function constructor because it doesn't have its own `this` keyword.

## Factory functions / Constructor functions

A factory function is a function that returns an object and can be reused to make multiple object instances. It immediately returns the newly-created object.

```javascript
const monsterFactory = (name, age, energySource, catchPhrase) => {
  return {
    name: name,
    age: age,
    energySource: energySource,
    scare() {
      console.log(catchPhrase);
    },
  };
};
```

To make an object that represents a specific monster like a ghost, we can call monsterFactory with the necessary arguments and assign the return value to a variable:

```
const ghost = monsterFactory('Ghouly', 251, 'ectoplasm', 'BOO!');
ghost.scare(); // 'BOO!'
```

==Note:== Angela's version:

The function name should be **capitalized** to show that this is a _constructor function_.

```javascript
function BellBoy (name, age, hasWorkPermit, languages) {
	this.name = name;
	this.age = age;
	this.hasWorkPermit = hasWorkPermit;
	this.languages = languages;
	this.moveSuitcase = function() {
		alert("May I take your suitcase?");
		pickUpSuitcase();
		move();
	}
}

// Or
const BellBoy = function (name, age...) {
 this.name = name;
 ...
}

// To initialise an object
var bellBoy1 = new BellBoy("Timmy", 19, true, ["French", "English"]);
```

Notice here each statement that creates a new property or method for this object **ends in a semicolon (not a comma, which is used in the literal syntax)**.

Without the `new` operator, this inside the constructor would not _point to the newly created object_, giving unexpected results.

!!!attention It's bad practice to create methods inside of a constructor function. Instead, use prototype or protopype inheritance.

### Property Value Shorthand

ES6 introduced some new shortcuts for assigning properties to variables known as destructuring.

```javascript
const monsterFactory = (name, age) => {
  return {
    name: name,
    age: age,
  };
};
```

The example below works exactly like the example above:

```javascript
const monsterFactory = (name, age) => {
  return {
    name,
    age,
  };
};
```

### Verify an object's constructor

`instanceof` allows you to compare an object to a constructor, returning true or false based on whether or not that object was created with the constructor.

```javascript
let Bird = function (name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
};

let crow = new Bird("Alexis", "black");

crow instanceof Bird; // Returns: true
```

### Own properties

```javascript
function Bird(name) {
  this.name = name;
  this.numLegs = 2;
}
```

`name` and `numLegs` are called **own properties**, because they are defined directly on the instance object. That means every instance of Bird will have its own copy of these properties.

To check whether a property is the object's own property, we can use `duck.hasOwnProperty(name)`..

### Prototype properties

Properties in the **prototype** are shared among ALL instances of Bird. Here's how to add numLegs to the Bird prototype:

```javascript
Bird.prototype.numLegs = 2;
```

Now all instances of Bird have the numLegs property.

To set multiple _protoptype_ properties more efficiently:

```javascript
Bird.prototype = {
  numLegs: 2,
  eat: function () {
    console.log("nom nom nom");
  },
};
```

It's good practice to _set methods using prototypes_, for better code performance.

To _print the prototype_ of an object:

```javascript
console.log(duck.__proto__); // The prototype
console.log(duck.__proto__ === Bird.prototype); // True
```

The _prototyte of of duck object_ is actually the _prorotype **property** of the constructor function_. `Bird.prototype` here is actually not the prototype of `Bird`, but instead it's gonna be used as the prototype of all objects created with the `Bird` constructor function.

### Constructor property

The constructor property returns a reference to the Object **constructor function** that created the instance object.

```javascript
let duck = new Bird();

console.log(duck.constructor === Bird); // Output: true
```

==Note:== Since the constructor property can be overwritten (which will be covered in the next two challenges) it’s generally better to use the `instanceof` method to check the type of an object.

### When changing prototype

There is one crucial side effect of manually setting the prototype to a new object. It _erases the constructor property_!

```javascript
duck.constructor === Bird; // false
duck.constructor === Object; // true
duck instanceof Bird; // true
```

To fix this, whenever a prototype is manually set to a new object, remember to _define the constructor property_:

```javascript
Bird.prototype = {
  constructor: Bird,
  numLegs: 2,
  eat: function () {
    console.log("nom nom nom");
  },
};
```

### Prototype inheritance

An object inherits its prototype directly from the constructor function that created it.

```javascript
function Bird(name) {
  this.name = name;
}

let duck = new Bird("Donald");
Bird.prototype.isPrototypeOf(duck); // true
```

#### Prototype chain

Because a prototype is an object, a prototype can have its own prototype! In this case, the prototype of `Bird.prototype` is `Object.prototype`.

```javascript
Object.prototype.isPrototypeOf(Bird.prototype);

// That is: Bird.prototype.__proto__ === Object.prototype
let duck = new Bird("Donald");
duck.hasOwnProperty("name");
```

The `hasOwnProperty` method is defined in `Object.prototype`, which can be accessed by `Bird.prototype`, which can then be accessed by `duck`.

`Object` is a _supertype_ for all objects in JavaScript. Bird is the supertype for duck, while duck is the _subtype_.

## Prototype of arrays

Whenever we create a new array, it is actually created by the Array constructor:

```javascript
const arr = [2, 4, 5]; // Same as: const arr = new Array([2, 4, 5]);
console.log(arr.__proto__ === Array.prototype); // True
console.log(arr.__proto__.constructor); // ƒ Array() { [native code] }
```

Array is actually a constructor function with a `prototype` property. Array.prototype is an object with no key and 36 methods.

The methods contained in Array.prototype (e.g., filter, forEach, slice):

```javascript
console.log(arr.__proto__);
// Output:
[constructor: ƒ, concat: ƒ, copyWithin: ƒ, fill: ƒ, find: ƒ, …]
	at: ƒ at()
	concat: ƒ concat()
	constructor: ƒ Array()
	copyWithin: ƒ copyWithin()
	entries: ƒ entries()
	every: ƒ every()
	fill: ƒ fill()
	filter: ƒ filter()
	find: ƒ find()
	findIndex: ƒ findIndex()
	findLast: ƒ findLast()
```

To list the methods in `Array.prototype`:

```javascript
console.log(Object.getOwnPropertyNames(arr.__proto__));
// Output:
(36)[
  ("length",
  "constructor",
  "concat",
  "copyWithin",
  "fill",
  "find",
  "findIndex",
  "lastIndexOf",
  "pop",
  "push",
  "reverse",
  "shift",
  "unshift",
  "slice",
  "sort",
  "splice",
  "includes",
  "indexOf",
  "join",
  "keys",
  "entries",
  "values",
  "forEach",
  "filter",
  "flat",
  "flatMap",
  "map",
  "every",
  "some",
  "reduce",
  "reduceRight",
  "toLocaleString",
  "toString",
  "at",
  "findLast",
  "findLastIndex")
];
```

We can add our own methods to Array.prototype so that every array can use this method (`this` keyword will be the array on which the method is called):

```javascript
Array.prototype.unique = function () {
  return [...new Set(this)];
};
const newArr = [3, 5, 6, 4, 3, 6, 7];
console.log(newArr.unique()); // Output: (5) [3, 5, 6, 4, 7]
```

The prototype of Array.prototype (an object, a property of Array) is the prototype property of Object.

```javascript
console.log(arr.__proto__.__proto__ === Object.prototype); // true
onsole.log(Object); // ƒ Object() { [native code] }
console.log(arr.__proto__.__proto__.constructor); // ƒ Object() { [native code] }
```

The methods contained in Object.prototype (e.g., hasOwnProperty, isPrototypeOf, toString):

```javascript
console.log(arr.__proto__.__proto__);
// Output:
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}
	constructor: ƒ Object()
	hasOwnProperty: ƒ hasOwnProperty()
	isPrototypeOf: ƒ isPrototypeOf()
	propertyIsEnumerable: ƒ propertyIsEnumerable()
	toLocaleString: ƒ toLocaleString()
	toString: ƒ toString()
	valueOf: ƒ valueOf()
	__defineGetter__: ƒ __defineGetter__()
	__defineSetter__: ƒ __defineSetter__()
```

## Clearing my thoughts

```javascript
const Person = function personFunc(name, birthYear) {
  this.name = name;
  this.birthYear = birthYear;
};

const jonas = new Person("Jonas", 1990);
```

### jonas

**An object with two properties: name and birthYear**

- typeof: object
- content:

```javascript
personFunc {name: 'Jonas', birthYear: 1990}
	birthYear: 1990
	name: "Jonas"
	[[Prototype]]: Object
		constructor: ƒ personFunc(name, birthYear)
		[[Prototype]]: Object
```

- properties:

```javascript
console.log(Object.keys(jonas));

// Output:
(2)[("name", "birthYear")];
```

!!!note Prototype of jonas: an object with the only property `constructor` that points back to the function itself

This method returns the prototype (i.e. the value of the internal `[[Prototype]]` property) of the specified object.

```javascript
console.log(jonas.__proto__); // === prototype property of Person
console.log(typeof jonas.__proto__);
console.log(Object.keys(jonas.__proto__));
console.log(Object.getOwnPropertyNames(jonas.__proto__));
```

Output:

```javascript
{constructor: ƒ}
	constructor: ƒ personFunc(name, birthYear)
	[[Prototype]]: Object
		constructor: ƒ Object()
		hasOwnProperty: ƒ hasOwnProperty()
		isPrototypeOf: ƒ isPrototypeOf()
		--snap--

object

[] // Empty array

['constructor']  // One method
```

!!!note Constructor of jonas: the function `Person`

```javascript
console.log(jonas.constructor);
console.log(typeof jonas.constructor);
```

Output:

```javascript
ƒ personFunc(name, birthYear) {
     this.name = name;
     this.birthYear = birthYear;
}

function
```

### Person

Person is a **function**, it has a `prototype` property which is an object.

- typeof: function
- content:

```javascript
ƒ personFunc(name, birthYear) {
     this.name = name;
     this.birthYear = birthYear;
}
```

==Constructor of `Person.prototype` refers back to itself==

```javascript
Person.prototype.constructor === Person; // true
```

### Person.prototype / `jonas.__proto__`

<kp>prototype</kp>: the prototype property of Object

```javascript
console.log(Person.prototype.__proto__);
```

Output: same as `Object.prototype`

```javascript
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}
	constructor: ƒ Object()
	hasOwnProperty: ƒ hasOwnProperty()
	isPrototypeOf: ƒ isPrototypeOf()
	propertyIsEnumerable: ƒ propertyIsEnumerable()
	toLocaleString: ƒ toLocaleString()
	toString: ƒ toString()
	valueOf: ƒ valueOf()
--snap--
```

!!!note constructor

```javascript
console.log(Person.prototype.__proto__.constructor);
```

Output:

```javascript
ƒ Object() { [native code] }
```

## Privacy

When discussing privacy in objects, we define it as the idea that only certain properties should be mutable or able to change in value.

Certain languages have privacy built-in for objects, but JavaScript does not have this feature. Rather, JavaScript developers follow naming conventions that signal to other developers how to interact with a property. One common convention is to place an underscore `_` before the name of a property to mean that the property should not be altered, such as `_amount: 1000;`.

### Getter method

Getters are methods that get and return the internal properties of an object.

```javascript
const person = {
  _firstName: "John",
  _lastName: "Doe",
  get fullName() {
    if (this._firstName && this._lastName) {
      return `${this._firstName} ${this._lastName}`;
    } else {
      return "Missing a first name or a last name.";
    }
  },
};

// To call the getter method:
person.fullName; // 'John Doe'
```

### Setter method

Along with getter methods, we can also create setter methods which reassign values of existing properties within an object.

```javascript
const person = {
  _age: 37,
  set age(newAge) {
    if (typeof newAge === "number") {
      this._age = newAge;
    } else {
      console.log("You must assign a number to age");
    }
  },
};

// to use the setter method like a property
person.age = 40;
console.log(person._age); // Logs: 40
person.age = "40"; // Logs: You must assign a number to age
```

### Use getter and setter to validate value

```javascript
class PersonCL {
  constructor(fullName, birthYear) {
    this.fullName = fullName;
    this.birthYear = birthYear;
  }

  set fullName(name) {
    if (name.includes(" ")) {
      this._fullName = name;
      // To set a property that aleready exists, add an underscore
    } else {
      alert(`${name} is not a full name!`);
    }
  }

  get fullName() {
    return this._fullName;
  }
}
```

### Static methods

Static methods are not inherited, they are not in the prototype of the object:

```javascript
PersonCL.hey() = {
	console.log('hey');
}
// static method, can only be used in the PersonCL namespace

PersonCL.prototype.newFunction() = {
	// .......
}
// can be inherited
```

To add static methods to classes:

```
// Static method
static hey() {
	// ...
}
```

## ES6 classes

ES6 provides a new syntax to create objects, using the **class** keyword.

It should be noted that the class syntax is just syntax, and **not** a full-fledged class-based implementation of an **object-oriented paradigm**, unlike in languages such as Java, Python, Ruby, etc.

In ES5, we usually define a constructor function and use the new keyword to instantiate an object.

```
var SpaceShuttle = function(targetPlanet){
  this.targetPlanet = targetPlanet;
}
var zeus = new SpaceShuttle('Jupiter');
```

The class syntax simply replaces the constructor function creation:

```javascript
// Class Declaration
class SpaceShuttle {
  constructor(targetPlanet, speed) {
    this.targetPlanet = targetPlanet;
	this.speed = speed;
  }

  // Instance methods: all instances have access to them
  accelerate () {
  	this.speed += 10;
  }

  brake () {
  	this.speed -= 5;
  }
};
const zeus = new SpaceShuttle('Jupiter');

// Class Expression
const SpaceShuttle = class {
	...
};
```

It should be noted that the class keyword _declares a new function_, to which a constructor is added. This constructor is invoked when new is called to create a new object.

**UpperCamelCase** should be used by convention for ES6 class names, as in SpaceShuttle used above.

==Note:== all the methods that we write in the class _outside of the constructor_ will be on the _prototype of the objects_, and not on the objects themselves. Notice that there are **NO COMMAS** between these methods.

> Classes are NOT hoisted.
> Classes are first-class citizens. (can pass them into functions and return them from functions) (because classes are really just a special kind of function behind the scenes)
> Classes are executed in strict mode.

## Object.create

We can manually set the prototype of an object to any other object we want. `Object.create(obj)` creates a new object, and sets `obj` _as the new object's prototype_. :

```javascript
const PersonPro = {
  calcAge() {
    console.log(2030 - this.birthYear);
  },

  init(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  },
};

const jonas = Object.create(PersonPro);
jonas.init("jonas", 1998);
```

## Inheritance

### Using constructor functions

`Person` and `Student` have some duplicate code:

```javascript
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};

const Student = function (firstName, birthYear, course) {
  this.firstName = firstName;
  this.birthYear = birthYear;
  this.course = course;
};
```

We can replace the duplicate code in `Student` with:

```javascript
const Student = function (firstName, birthYear, course) {
  Person.call(this, firstName, birthYear);
  // Person as a function call
  this.course = course;
};
```

prototype property of `Student` inherits from the prototype property of `Person`:

```javascript
Student.prototype = Object.create(Person.prototype);
```

In other words:

```javascript
Student.prototype.__proto__ === Person.prototype; // true
```

==Note:== This should be added **before** all `student.prototype.someMethods`, because `Object.create` will return an empty object. Onto that empty object, we can add methods.

> Why not use `Student.prototype = Person.prototype;`?
> In this way, `Studnet.prototype` and `Person.prototype` would be the exact same object.

#### Clearing my thoughts

```javascript
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
  calcAge = function () {
    console.log(2030 - this.birthYear);
  };
};

const Student = function (firstName, birthYear, course) {
  Person.call(this, firstName, birthYear);
  this.course = course;
  introSelf = function () {
    console.log(`My name is ${firstName}, I'm studying ${course}.`);
  };
};

Student.prototype = Object.create(Person.prototype);
Student.prototype.come = function () {
  console.log("I'm coming!");
};

const mike = new Student("mike", 1999, "math");
```

```javascript
mike.__proto__ === Student.prototype; // true
mike.__proto__.__proto__ === Person.prototype; //true
mike.constructor === Student; // false
mike.constructor === Person; // true
Student.prototype.constructor === Person; // true
```

We need to manually change the constructor:

```javascript
Student.prototype.constructor = Student;
```

Output:

```javascript
Student.prototype.constructor === Student; // true
mike.constructor === Student; // true
```

### Using ES6 classes (`extends` and `super`)

```javascript
class PersonCL {
  constructor(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
  calcAge = function () {
    console.log(2030 - this.birthYear);
  };
}

class StudentCL extends PersonCL {
  // This will link the prototype behind the scenes
  constructor(firstName, birthYear, course) {
    super(firstName, birthYear);
    // Works like the constructor function of parent class
    // Needs to be put before this keyword
    this.course = course;
  }
}
```

==Note:== If we don't need any new parameters in the new class, we don't need to use constructor and super.

```
class StudentCL extends PersonCL {};
const martha = new StudentCL('martha jones', 1999);
```

### Using Object.create()

```javascript
const PersonProto = {
  calcAge() {
    console.log(2030 - this.birthYear);
  },

  init(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  },
};

const StudentProto = Object.create(PersonProto);
StudentProto.init = function (firstName, birthYear, course) {
  PersonProto.init.call(this, firstName, birthYear);
  this.course = course;
};
StudentProto.introduce = function () {
  console.log(`My name is ${this.name}and I'm studying ${this.course}`);
};

const jay = Object.create(StudentProto);
jay.init("jay chow", 1998, "cs");
```

Here, `PersonProto` is the prototype of `StudentProto`, and `StudentProto` is the prototype of `jay`.

## Creating supertype

Notice in the example below that the describe method is shared by Bird and Dog:

```javascript
Bird.prototype = {
  constructor: Bird,
  describe: function () {
    console.log("My name is " + this.name);
  },
};

Dog.prototype = {
  constructor: Dog,
  describe: function () {
    console.log("My name is " + this.name);
  },
};
```

The code can be edited to follow the **DRY principle** by creating a _supertype_ (or parent) called Animal:

```javascript
function Animal() {}

Animal.prototype = {
  constructor: Animal,
  describe: function () {
    console.log("My name is " + this.name);
  },
};

Bird.prototype = {
  constructor: Bird,
};

Dog.prototype = {
  constructor: Dog,
};
```

You already know one way to create an instance of Animal using the new operator:

```javascript
let animal = new Animal();
```

There are some disadvantages when using this syntax for inheritance, which are too complex for the scope of this challenge. Instead, here's an alternative approach without those disadvantages:

```javascript
let animal = Object.create(Animal.prototype);
```

Recall that the prototype is like the "recipe" for creating an object. By setting the prototype of `animal` to be the prototype of `Animal`, you are effectively giving the animal instance the same "recipe" as any other instance of Animal.
