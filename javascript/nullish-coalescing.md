# Nullish Coalescing

- provides a `default` value for when the expected value is `falsy`

```js
let a = null;     // could be false, 0, '' or undefined
let b = a ?? 42;  // since a is null, it will assign 42 to b
console.log(b);   // => 42
```

Uses the `??` operator to indicate a default value after a variable if it is set.

For example:

```js
let username = getUserName() ?? "Default User";
```

Traditionally, developers would use the OR operator `||` to indicate a default value if a variable was not set or a function returned null. This new `??` operator handles all crazy cases where the OR operator would return an unexpected result.

The idea behind using the OR operator was to check for a **truthy** value and if it was falsy, it would use the default (to the right of the operator).

Here's an example of where using the OR operator breaks down and necessitates the `??` operator:

```js
let user = {
  isAdmin: false
}
let isAdminRole = user.isAdmin || true;
```

Notice how in the user object, the property `isAdmin` is set to `false` and when it is evaluated by the OR statement, it will actually return `true` for the `isAdminRole` variable. This is because the value being returned is actually **falsy** since it was **false**!!

The `??` would solve this as it would actually use the `false` returned from the object and only use `true` if the `isAdmin` property wasn't explicitly set. Perhaps not a good idea to make the default `true`, but it illustrates the point.

Any falsy values will cause the same problem using the OR operator. Values such as:

- `0`
- `''` (empty string)
- `false`

Nullish coalescing will use `null` or `undefined` to assign values instead of `true` or `false`.

`??` and `||` can be used together to have some great validation:

```js
const name = (getName() ?? 'Name Error') || 'Anonymous User';
```

Let's see what happens with some sample data:

- `getName()` returns `"Patrick"` => `name === "Patrick"`
- `getName()` returns `''` => `name === "Anonymous User"`
- `getName()` returns `null` => `name === "Name Error"`

Finally, nullish coalescing can also be used with optional chaining. Basically, if using optional chaining, any point in the chain fails, it will use what is to the right of the `??` operator. Very useful if expecting a certain object structure from an API, but want to have a default value if the return is not the expected result.

## Sources

- [source1 - v8 Optional Chaining and Nullish Coalescing](https://alligator.io/js/v8-optional-chaining-nullish-coalescing/#nullish-coalescing)
