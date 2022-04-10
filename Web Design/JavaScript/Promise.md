# Promise

Promise is a constructor function, so you need to use the `new` keyword to create one. It takes a function, as its argument, with two parameters - `resolve` and `reject`.

```javascript
const myPromise = new Promise((resolve, reject) => {});
```

A promise has three states: `pending`, `fulfilled`, and `rejected`. If you didn't add a way to complete the promise, it's forever stuck in the `pending` state.

```javascript
const myPromise = new Promise((resolve, reject) => {
  if(condition here) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});
```

## then

Promises are most useful when you have a process that takes an unknown amount of time in your code. After it completes you usually want to do something with the response from the server. This can be achieved by using the `then` method. The then method is _executed immediately after your promise is fulfilled with resolve_.

```javascript
myPromise.then((result) => {});
```

`result` comes from the argument given to the resolve method.

## catch

catch is the method used when your promise has been rejected. It is executed immediately after a promise's _reject_ method is called.

```javascript
myPromise.catch((error) => {});
```

`error` is the argument passed in to the reject method.
