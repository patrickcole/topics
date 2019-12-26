# JavaScript Optional Values

- `null` & `undefined`
- both of these can cause confusion for every developer
- javascript does not treat these as illegal values
- most of the confusion will come from trying to determine whether a user has properly entered data into a form
- one recommendation is to use a schema validator
- another recommended method is to hydrate input data
  - the idea is that you would never show invalid data, as the data would be also hooked into a "state" that would be updated to true when the input data has actually been set
- avoid creating `null` and `undefined` values
- harness the default values support that is available for functions (for example: provide a default value for a parameter that has not been set)
  - this assumes that you are using functions to handle setting values
  - use state if values cannot be stated up-front, **do not use null or undefined**

## Optional Chaining

- new specification that is starting to arrive on modern browsers
- allows an optional declaration for object queries
- can be used multiple times
- can be used on arrays and/or functions inside objects
- NOTE: This is not a replacement for all references, errors will not be thrown so bugs might leak out
  - without using optional chaining errors would be thrown and bugs would be easier to spot

```js
// for example:
const user = {};

// this will throw an error:
// name is not set inside the user object
try {
  console.log(user.name.first);
} catch ( err ) { console.error(err) }

// with optional chaining, it will return undefined:
console.log( user.name?.first );
```

- to check for a function in the global scope

```js
functionDoesNotExist?.()

// will return undefined instead of an error;
```

## Nullish Coalescing

- new operator to provide a default or "fallback" value if not set
- default values are no longer bound to function parameters

```js
// for example:
let userBalance;
console.log(userBalance); // undefined
console.log(userBalance ?? 0); // 0

// can be combined with optional chaining (section above)
console.log(user.name?.first ?? 'User');
// NOTE: this does not "create" the name object under user
// it just provides the string 'User' back in the console run
```

- NOTE: source1 below has some great ideas to remove `null` and `undefined` results; much derived from functional programming techniques

---

[source1](https://medium.com/javascript-scene/handling-null-and-undefined-in-javascript-1500c65d51ae)
[source2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)
[source3](https://dev.to/laurieontech/optional-chaining-has-arrived-111l)