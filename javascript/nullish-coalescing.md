# Nullish Coalescing

- provides a 'default' value for when the variable is `null`

```js
let a = null;
let b = a ?? 42;
console.log(b);  // => 42