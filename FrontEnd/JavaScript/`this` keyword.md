# `this` keyword

`this` is not static. It depends on how the function is called, and the function is only assigned when the function is actually called.

- Method: \<Object that is **calling the method**\> (_not the object in which we wrote the method_)
- Sinple function call: in strict mode, `undefined`; otherwise, `window`
- Arrow functions: do not get its own `this` keyword, but use lexical `this`, which is `this` keyword of its **parent scope**
- Event listener: \<DOM element that the handler is attached to\>

```javascript
const jonas = {
	year: 1991,
	calAge: function() {
		console.log(2047 - this.year);
	}

	// Solution 1
	const self = this;
	const isMillenial = function () {
		console.log(self.year >= 1981 && self.year <= 1996);
	};
	// Solution 2
	const isMillenial = () => {
		console.log(this.year >= 1981 && this.year <= 1996);
	};
	isMillenial();
};
```

## `call` and `apply` method

```javascript
const jonas = {
  year: 1991,
  calAge(title, name) {
    console.log(`${title} ${name} is ${2047 - this.year} years old`);
  },
};

const john = {
  year: 2000,
};
const calAge = jonas.calAge;

calAge("Mr", "john");
/* Undefined, because here calAge is a normal function, not a method.
`this` in simple functions is `undefined` */
```

The first parameter of `call` method can specify `this` keyword, and the following arguments are the argument of the original function.

```javascript
calAge.call(jonas, "Mr", "Jonas");
calAge.call(john, "Mr", "john");

// Prints:
// Mr Jonas is 56 years old
// Mr john is 47 years old
```

`apply` method works in a similar way, but the following arguments should be an array of values:

```javascript
calAge.apply(jonas, ["Mr", "Jonas"]);
```

## `bind` method

The `bind()` method creates _a new function_ that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

```javascript
const calAgeJonas = calAge.bind(jonas);
calAgeJonas("Mr", "Jonas");
```

We can also bind arguments to the method (_partial application_):

```javascript
const calAgeJonasMr = calAge.bind(jonas, "Mr");
calAgeJonasMr("Jonas");
```
