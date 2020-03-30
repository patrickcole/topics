# Async / Await

- they are refinements of the `Promise` pattern, which resolves callback hell
- as soon as `async` is prepended to a function, it will return a `Promise`, either resolved or rejected
- `await` is not allowed unless the `async` prefix has been applied to the function
- in order to get the actual return value or data, a `.then()` call is required
- by using `async/await`, values returned from `await`'d functions can be used in others, the scope is the same, unlike promises where each `.then()` has their own local scope
- functions cannot use `await` in the top-level scope, an IIFE is needed

```js
// note the use of underscore _, to indicate no parameters provided
// also valid is just using empty parathesis: async () =>
(async _ => {
  let response = await hi();
  console.log(response);
})();
```

## Error Handling

- it seems like error handling is not standardized on this, there are a few options
  - using `.catch()` on the async functions execution
  - using `try/catch` inside the `async` function, this might reset the call stack? (need verification)
  - **try/catch** provides the ability to catch **both** async and sync errors inside an `async` function
  - can also add event listener to the `window.onrejectionhandled` event
- this [link](https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m#user-profile-example-4) has some interesting ideas for error handling.

## Promise.All

- wait for multiple promises to be resolve before moving on
- any error, will be thrown and caught if catch is available

## Custom Objects

- as long as they have implemented the `.then` method properly, they can be used with `async`

## Classes

- `async` can be added to Class methods and then invoked:

```js
class Order {
  async deliver() {
    return await Promise.resolve('pizza');
  }
}

new Order()
  .delivery()
  .then(v => console.log(v));
```

## Fetch

- being that fetch uses the promise pattern, async/await can be used with fetch
- the following example shows async/await with fetch

```js
const fetchUsers = async () => {
  try {
    const res = await fetch(`https://reqres.in/api/users`);
    if ( !res.ok ) {
      throw new Error(res.status);
    }
    const data = await res.json();
    console.log(data);
  } catch ( err ) {
    console.error(err)
  }
}

fetchUsers();
```

[source](#asyncAwait1)

---

## Sources

- [Introduction to JavaScript Fetch API - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/introduction-to-javascript-fetch-api-4f4c)
- [Async/Await](https://zellwk.com/blog/async-await/)
- [A Beginner's Guide to async/await](https://itnext.io/a-beginners-guide-to-async-await-in-javascript-97750bd09ffa)
- [6 Points You Need to Know about async & await](https://yashints.dev/blog/2019/08/17/js-async-await)
- [JavaScript async and await in loops](https://www.freecodecamp.org/news/javascript-async-and-await-in-loops-30ecc5fb3939/)
- [How To Rock 🤟 Asynchronous Calls By Understanding JavaScript Callbacks, ES6 Promises And ES7 Async/Await](https://dev.to/_marcba/how-to-rock-asynchronous-calls-by-understanding-javascript-callbacks-es6-promises-and-es7-async-await-4nb3)
- [Better error handling with async/await](https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m)
- [7 Reasons Why JavaScript Async/Await Is Better Than Plain Promises (Tutorial)](https://dev.to/gafi/7-reasons-to-always-use-async-await-over-plain-promises-tutorial-4ej9)
- [Async/await without try/catch in JavaScript](https://itnext.io/async-await-without-try-catch-in-javascript-6dcdf705f8b1)
- [JavaScript’s Async/Await versus Promises: The Great Debate](https://itnext.io/javascripts-async-await-versus-promise-the-great-debate-6308cb2e10b3)
