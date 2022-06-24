# Theories about javascript

## Definition

### Multi-paradigm language

Three popular paradigms:- procedural programming: organizing the code in a linear way

- object-oriented programming (OOP)
- functional programming (FP)

We can also classify paradigms as _imperative_ or _declarative_.

Three popular paradigms:

- procedural programming: organizing the code in a linear way
- object-oriented programming (OOP)
- functional programming (FP)

### Prototype-based object-oriented

For example, we can create an array and use the push method on it, because of **prototype inheritance**. We create arrays from an array prototype, and inherits the methods from the prototype.

<img src="https://s2.loli.net/2022/02/26/UOuh6xyYmBKvWrA.png" alt="prototype.png">

### First-class functions

Functions are treated as variables and can be passed into other functions as variables.

### Single-threaded and non-blocking event loop

**Concurrency model**: how the ++JavaScript engine++ handles multiple tasks
happening at the same time

Why do we need that? --
JavaScript runs in **one single thread**, so it can only do one thing at a time.

So what about a long-running task? -- Sounds like it would block the single thread. However, we want non-blocking
behavior!

How do we achieve that? -- By using an **event loop**: takes long running tasks, executes them in the “background”, and puts them back in the main thread once they are finished.

## The JavaScript engine and runtime

**JS engine**: program that executes JavaScript code

Example: Google's V8 Engine

<img src="https://s2.loli.net/2022/02/26/cuW6lEiaUdgLnO3.png" >

JavaScript used to be a purely interpreted language. But because of the low performance, modern JavaScript engine now use a mix between compilation and interpretation which is called **just-in-time compilation**.

_Compilation_: Entire code is converted into machine code at once, and written to a binary file (portable file) that can be executed by a computer.

_Interpretation_: Interpreter runs through the source code and executes it line by line.

_Just-in-time (JIT) compilation_: Entire code is converted into machine code at once (not a portable file), then executed immediately.

Example:

<img src="https://s2.loli.net/2022/02/26/6ZWywxlAtCIRmcr.png" >

When a piece of JavaScript code enters the engine, in the first step, the code is parsed into a data structure called the **abstract syntax tree** or **AST**. (==Note==: this tree has nothing to do with the DOM tree). This works by first splitting up each line of code into pieces that are meaningful to the language like the const or function keywords, and then saving all these pieces into the tree in a structured way. This step also checks if there are any syntax errors and the resulting tree will later be used to generate the _machine code_.

**Runtime**: here we look at a _browser's runtime environment_

<img src="https://s2.loli.net/2022/02/26/XpU8BsubAOW2m9o.png" >

## Execution context

<img src="https://s2.loli.net/2022/02/26/xmPVdhESUvuIO1i.png" >

WHAT’S INSIDE EXECUTION CONTEXT?

1. Variable Environment
   - `let`, `const` and `var` declarations
   - Functions
   - argument object
2. Scope chain
3. `this` keyword

==Note==: argument object and `this` keyword are not in arrow functions!

The content of execution context is generated in a **creation phase**, right before execution.

**Call stack**: “Place” where execution contexts get
stacked on top of each other, to keep
track of where we are in the execution

## Scoping and scope in JavaScript

<kp>coping: </kp>How our program’s variables are organized and accessed. “Where do variables live?” or “Where can we access a certain variable, and where not?”;

<kp>Lexical scoping:</kp> Scoping is controlled by placement of functions and blocks in the code;

<kp>Scope:</kp> Space or environment in which a certain variable is declared (variable environment in case of functions). There is global scope, function scope, and block scope;

<kp>Scope of a variable:</kp> Region of our code where a certain variable can be accessed.

<img src="https://s2.loli.net/2022/02/26/SqIaDTVrFbNB4RO.png" >

`var` is function scoped, `let` and `const` are block scoped.

**Scope chain**

<img src="https://s2.loli.net/2022/02/26/TAJVGoCgLZd2z34.png" >

## Hoisting

Makes some types of variables accessible/usable in the code before they are actually declared. “Variables lifted to the top of their scope”.

<img src="https://s2.loli.net/2022/02/27/MpqfN2vkU1VQsho.png" >

we can use function declarations before they are actually declared in the code, because they are stored in the **variable environment object**, even before the code starts executing;

Unlike functions, when we try to access a `var` variable before it's declared in a code, we don't get the declared value but we get _undefined_;

`let` and `const` variables are technically actually hoisted, but their value is basically set to an initialized. These variables are placed in a so-called **Temporal Dead Zone** or TDZ. If we attempt to use a let or const variable before it's declared, we get an error. _Classes_ are not hoisted.

So, unlike **function declarations**, a **function expression** or **arrow function** created with `var` is hoisted to undefined. But if created with `let` or `const`, it's not usable before it's declared in a code because of the Temporal Dead Zone.

## `argument` keyword

```javascript
const addExpr = function (a, b) {
  console.log(arguments);
  return a + b;
};
addExpr(2, 5, 8, 12); // Output will be an array of 2, 5, 8, 12
```

==Note:== arrow functions do not get arguments keyword.

## Primitives and Objects

<kp>Primitives (primitive types)</kp>including _number, string, boolean, undefined, null, symbol and bigint_ are stored in **call stack**;

<kp>Objects (reference types)</kp>including _object literal, arrays, functions and more_ are stored in **heap**.

<img src="https://s2.loli.net/2022/02/27/Zt7dfpyjB2UEWM3.png" >

### Primitive types

1. `let age = 30;`
   When we declare a variable `let age = 30;`, JavaScript will create a unique **identifier** with the variable name. Then a piece of memory will be allocated with a certain **address** (like `001`) where the **value** is stored. **The identifier points to the address, not the value itself.**

2. `let oldAge = age;`
   `oldAge` will point to the same memory address as the `age` variable.

3. `age = 31;`
   _The value at a certain memory address is immutable,_ so the value at address 001 will not be changed. Instead, a new piece of memory is allocated and the `age` identifier will now point to the new address `002`, will holds the new value `31`.

### Reference types

`const me = {...};`
When a new object is created, it is stored in the heap. The `me` identifier does not directly point to this newly created memory address in the heap. Instead, it will point to a new piece of memory that's created in the stack, and its value will be a reference to memory in heap.

Shallow copy: to copy the properties in the first level but not inner objects, we can use `const friend = Object.assign ({}, me);`. To deep copy, we may need to use a library.

### Pass by value

JavaScript does not have passing by reference, only passing by value. For objects, we do in fact pass in a reference, the memory address of the object. However, that reference itself is still a value. It's simply a value that contains a memory address. So basically we pass a reference to the function, but we do not pass by reference.

[Pass by value vs pass by reference](https://pediaa.com/what-is-the-difference-between-pass-by-value-and-pass-by-reference/#:~:text=The%20main%20difference%20between%20pass,parameter%20passes%20to%20the%20function.)
