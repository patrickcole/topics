# Context

- JavaScript supports object-oriented approaches
- uses dynamic binding
- dynamic binding allows code to change context at runtime
- accomplished in JavaScript via the `this` keyword and the `prototype chain`

- arrow functions cannot have their own `this`, they bind to the lexical scope
  - NOTE: inside a `Class` an arrow function would then be bound to the `Class` not the global scope (remember a `Class` is block scoped)
- arrow functions also cannot have `this` reassigned with `bind` or `call`

```js
// example
const obj = {
  getThis: () => this
};
console.log(obj.getThis());
// => undefined
```

- `getThis` is returning undefined because the arrow function does not have it's own `this` and therefore moves context up to the global. Once inside the global, there is no `getThis` method found as that method is found inside the `obj` object.

- using a normal function scope, `[function getThis]` would be returned in the `this` context

## Using Call

- now passing another object into a function via `call` can change the context even more:

```js
// setup some objects:
const user = { name: "Patrick" }
const obj = {
  getThis: function() {
    return this;
  }
}
// now we can get the "user" object via "getThis":
console.log(obj.getThis.call(user));
// => { name: "Patrick" }
```

---

[source1](https://medium.com/javascript-scene/what-is-this-the-inner-workings-of-javascript-objects-d397bfa0708a)