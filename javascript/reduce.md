# Reduce

Arrays and Objects can use the `reduce` method.

The syntax is:

`arr.reduce(callback, initialValue)`

- accumulator: the value we end up with
- reducer: the action being performed to obtain one value

Can be used to mutate (add, subtract, multiply, etc..) numbers from an array.

For example:

```js
let numbers = [5,10,15];
let reducer = (accumulator, item) => accumulator + item;
let total = numbers.reduce(reducer, 0);
console.log(total); 
// => 30
```

The example above establishes a reducer function that can be used to add up all the numbers in the `numbers` array. We could create a subtract reducer that would subtrace those numbers from another initial value (ex: 100)

```js
let penalties = [5, 10, 15];
const subtract = (accumulator, item) => accumulator - item;
let total = numbers.reduce(subtract, 100);
console.log(total);
// => 70
```

Can also be useful in modifying objects, if they need to be updated/simplified. The example below moves the `name` property from each object and makes it the key for each object in an array:

```js
const pokemonModified = {
  charmander: { type: "fire" },
  squirtle: { type: "water" },
  bulbasaur: { type: "grass" }
};

// function to handle the reducer:
const getMapFromArray = data =>
  data.reduce((acc, item) => {
    // add object key to our object i.e. charmander: { type: 'water' }
    acc[item.name] = { type: item.type };
    return acc;
  }, {});

// apply the reducer to the array of objects:
getMapFromArray(pokemon);
```

The `reduce` function can be used to create some other high-order functions such as `map`,`some`,`every`, etc.. [This Codepen](https://codepen.io/patrickcole/pen/ZEGJMVj?editors=0012) is an example of those functions implemented with `reduce`.

#### Sources

- [Finally Understand the JavaScript Reduce Method](https://alligator.io/js/finally-understand-reduce/)
- [Learn Reduce in 10 Minutes](https://www.freecodecamp.org/news/learn-reduce-in-10-minutes/)

##### Functional Uses for Reduce
- [10 JavaScript Utility Functions Made with Reduce](https://www.freecodecamp.org/news/10-js-util-functions-in-reduce/)
- [10 More Utility Functions Made with Reduce](https://www.freecodecamp.org/news/10-more-js-utils-using-reduce/)
- [Yet Another 10 Utility Functions Made with Reduce](https://www.freecodecamp.org/news/yet-another-10-utils-using-reduce/)