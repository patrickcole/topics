# Hoisting

- JavaScript's method of handling variables and functions
- declared variables using `var` are hoisted to the top of the script and immediately set to `undefined` until initialized (`var example = "value"`)

- declaration (`var example`)
- initialization (`var example = "value"`)
- function declaration (`function hello() { return "Hello" }`)
- function expression (`var hello = function() { return "Hello"}`)

## Rules

- `var` declarations will be hoisted, but return `undefined` until initialized
- `let` & `const` declarations are not hoisted (will return error) until initialized
- function expressions will return `undefined` if using `var`, will return error if using `let` or `const`
  - for example: `var hello = function(){ return "Hello" }` will return `undefined` if called before initialization
  - `function hello(){ return "Hello" }` will be hoisted and return `Function` as it is a declaration

## Global Scope

- variables declared here will be available to the entire script
- this includes `const` and `let` variables as long as they are not declared inside a block scope using curly braces `{ }`

## Block Scope

- variables declared inside curly braces `{ }` will be block-scoped variables if using `let` or `const`, these will not be available outside the block
- block scoped variables using `var` will not be available if they are inside a `function` block. `if`, `else`, `switch`, etc.. will make them available.

- [source1](https://blog.bitsrc.io/javascript-hoisting-simplified-8090b166005e)
- [source2](https://blog.bitsrc.io/what-is-javascript-hoisting-f0678208eb08)
- [example](https://codepen.io/patrickcole/pen/OJPbQdd?editors=0010)
