# JavaScript - Control Flow

## loops

### for

- traditional `for loop` using a initial statement, a condition that will continue the loop's execution and a final expression to perform upon each execution loop

#### Example

- Note: Use of `String - Template Literals` here to render variable inside string

```js
for ( let i = 1; i <= 5; i++ ) {
  console.log(`Statement ${i}`);
}
// => Statement 1
// => Statement 2
// => Statement 3
// => Statement 4
// => Statement 5
```

[Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)

---

### for in loop

- Provides the ability to iterate over enumerable properties
- **Use for looping through objects (not arrays)**
- **Best use case for using this is looping through key/value pairs**

#### Arrays

- You can use `for in` with arrays, but it is not recommended. The caveat is that if you are expecting the index order to always return the same, `for in` will not guarantee that. **It is recommended to use `Array.forEach` or `for of` loop.**

```js
let data = [1,2,3,4,5];
for ( let index in data ) {
  console.log(data[index]);
}

// => 1
// => 2
// => 3
// => 4
// => 5
```

#### Objects

```js
let user = { id: 1, name: 'Patrick Cole' };
for ( let key in user ) {
  console.log( user[key] );
}

// => 1
// => 'Patrick Cole'
```

[source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)

---

### for of loop

- **Use this for iterator objects**
- Loops through iterable objects such as `String`, `Array`, `NodeList`
- For `String`, will expose the `character` only
- For `Array`, will only expose the `value`, not the `index`
- For `NodeList`, will expose the `node` or "element"

#### Array Example

```js
let data = [1,2,3,4,5];
for (let val of data) {
  console.log(val);
}

// => 1
// => 2
// => 3
// => 4
// => 5
```

#### NodeList Example

```js
const pageSections = document.querySelectorAll('section');

for ( let section of pageSections ) {
  section.classList.add('contents-item')
}
```

[source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)

---

## for each in

- **Do not use this, it has been deprecated**

---

## Array.forEach

- see the array/forEach article
- Used mainly for read-only operations with arrays

## Array.map

- see the array/map article
