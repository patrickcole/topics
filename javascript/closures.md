# Closures

The classic example:

```js
function getCounter() {
  let counter = 0;
  return function() {
    return counter++;
  }
}
let count = getCounter(); // count is the closure
// it has access to the `counter` variable
console.log(count());  // 0
console.log(count());  // 1
console.log(count());  // 2
```

Another classic example. Here's the problem:

```js
let fns =[]

for(var i = 0; i < 5; i++) {
 var c = i * 2;
 fns.push( _ => console.log(c))
}

fns.forEach( f => f() )
```

> The result of this would be, `8, 8, 8, 8` because `c` has been updated without creating a new scope.

The solution is to use an IIFE (immediately-invoked function expression).

```js
for(var i = 0; i <5; i++) {
 ( _ => {
   var c = i * 2;
   fns.push( __ => console.log(c) )
 })()
}

fns.forEach( f => f() )
```

> Now the result would be: `2,4,6,8` because each time the function is run, it creates a new scope and `c` can be assigned to whatever value `i` has been set to.

**Closures are paramount to Functional Composition (ie using a function to create another function**

> The closure is storing the current definitions and scope information in a function to pass it to outer scopes. Normally inner scope can not be accessible from outer scopes in the Lexical Scope environment.

#### Sources

- [Good example of IIFE and Module Pattern](https://codeburst.io/how-does-javascript-closure-work-7eb79dde722d)
- [Excellent source on Closures / Scope](https://blog.bitsrc.io/a-beginners-guide-to-closures-in-javascript-97d372284dda)
- [Another Excellent source on Closures](https://blog.bitsrc.io/closures-in-javascript-why-do-we-need-them-2097f5317daf#85b9)
- [Good explanation of Closures](https://dmitripavlutin.com/simple-explanation-of-javascript-closures/)
