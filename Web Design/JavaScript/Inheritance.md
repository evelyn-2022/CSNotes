# Inheritance

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

When manually setting the prototype to a new object, it erases the constructor property, and we should remember to define the constructor property:

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
