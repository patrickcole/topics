# JavaScript - Control Flow

## loops

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

## Array.forEach

- see the array/forEach article
- Used mainly for read-only operations with arrays

## Array.map

- see the array/map article
