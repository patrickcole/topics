# Promises

- promises solve the long-standing issue of how to deal with asynchronous code
- being that JavaScript is single-threaded, it can only run code in sequence, not multiple things at once. Promises provide the mechanism to continue to run things in sequence but deal with asynchronous actions and what happens when they resolve or reject
- traditionally this was handled with callback functions, but callback functions can get messy and create what's known as "callback hell" (where one callback calls another callback and so on...)
- promises also deliver a syntax that is more straightforward and easier to read than callback functions
- promises now also can be implemented with `async/await` to make them even easier to read and understand
- promises provide the ability to get the data or response from an async request and then perform some sort of action with the response of the request (the call/then pattern)

## Use of Promises

- promises are used in `fetch` calls
- used in the `Screen Capture API`, `getDisplayMedia`

## States of a Promise

1. pending: waiting for an async action or request to complete
2. resolved: action was completed successfully (or **resolved**)
3. rejected: action was not completed successfully, an issue occured (or **rejected**)

## Syntax of a Promise

- the following example provides basic syntax for a promise:
- **NOTE: the use of `arrow functions`**

```js
let state = true;
const example = new Promise( (resolve, reject) => {
  if ( state ) {
    resolve('success');
  } else {
    reject('failure');
  }
})
```

## Using/Consuming a Promise

- using the call/then/catch pattern to actually consume or execute a promise
- the following example shows how to run a promise:

```js
// promise code from previous example
let state = true;
const example = new Promise( (resolve, reject) => {
  if ( state ) {
    resolve('success');
  } else {
    reject('failure');
  }
})
// now how to execute the promise
example
  .then( response => console.log(response) )
  .catch( error => console.error(error) )
```

## Chaining Promises

- promises can be chained together
- this is a much better pattern than adding promises inside of other promises ("promise nesting")
- here's an example of promise nesting:

```js
const promise1 = new Promise((resolve,reject) => resolve('Promise 1 resolved'));
const promise2 = new Promise((resolve,reject) => resolve('Promise 2 resolved'));
const promise3 = new Promise((resolve,reject) => reject('Promise 3 rejected'));

promise1.then( (response) => {
  console.log(response);
  promise2.then( (response) => {
      console.log(response);
      promise3.then( (response) => {
        console.log(response);
      })
      .catch( (error) => {
        console.error(error);
        })
    })
})
```

- the example above will work, but is difficult to follow and debug

---

- and now here's an example of promise chaining:

```js
// the first two promises are resolving correctly:
const promise1 = new Promise((resolve,reject) => resolve('Promise 1 resolved'));
const promise2 = new Promise((resolve,reject) => resolve('Promise 2 resolved'));
// but maybe we reject the third promise:
const promise3 = new Promise((resolve,reject) => reject('Promise 3 rejected'));

// now to run the promises in sequence:
promise1
  .then( (response) => {
    console.log(response);
    return promise2;
  })
  .then( (response) => {
    console.log(response);
    return promise3;
  })
  .then( (response) => {
    console.log(response);
  })
  .catch( (error) => {
    console.error(error);
  })
```

- note that in the example above, only one catch statement is needed to handle all the chained promises, so the example above does catch because promise3 is rejected
- this is all well and good for sequential execution of promises, but what about concurrent execution of promises

---

## Concurrent Execution via Promise.all()

- `promise.all()` provides a method to run multiple promises concurrently and then waits for all of them to resolve (or any of them to be rejected)
- if they all resolve successfully, a new array will contain the results of each promise with each promise occupying a slot in the array
- if any promise is rejected in the promise.all declaration, any pending promises are stopped and the promise.all returns an error state (that can be caught via the `catch()` block)

- the example below shows two promises running at different at different timeouts and resolving correctly:

```js
const promise1 = new Promise((resolve,reject) => setTimeout( () => resolve('success1'), 2000));
const promise2 = new Promise((resolve,reject) => setTimeout( () => resolve('success2'), 1000));

Promise.all([promise1, promise2])
  .then( responses => console.log(responses[0], responses[1]) )
  .catch( error => console.error(error) );
```

- so after about 3 seconds, the `console.log` inside the `.then()` block will respond with `success1 success2` as both promises were resolved

- now for an example of what happens when one is rejected:

```js
const promise1 = new Promise((resolve,reject) => setTimeout( () => reject('failed!'), 2000));
const promise2 = new Promise((resolve,reject) => setTimeout( () => resolve('success2'), 1000));

Promise.all([promise1, promise2])
  .then( responses => console.log(responses[0], responses[1]) )
  .catch( error => console.error(error) );
```

- now the console will error out and show `failed!` because the first promise rejected

---

## Promise.allSettled()

- coming soon to every modern browser
- provides a result once all promises have either resolved or rejected
- unlike `Promise.all()`, some promises can reject and other promises can still resolve if they are pending, using `Promise.allSettled()` removes the break condition when at least one promise has rejected

[source6](https://v8.dev/features/promise-combinators#promise.allsettled)

---

## Promise.race()

- very similar to `Promise.all()` but instead of waiting for all to resolve or one to reject, the `Promise.race()` returns whichever promise resolved/rejected first. So in essence it is a test to get the first result from any included promises (regardless if they pass or fail)

[source1](https://blog.bitsrc.io/understanding-promises-in-javascript-c5248de9ff8f)
[source2](https://scotch.io/tutorials/javascript-promises-for-dummies)
[source3](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
[source4](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
[source5](https://developers.google.com/web/fundamentals/primers/promises)
