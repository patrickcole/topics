# JavaScript - Array

## Methods

- many of the methods below are considered "high-order functions" as they accept or return a function to perform their task

### Array.every

- performs a callback function and conditional statement on each item in the array
- returns true if every item in the array evaluate to true

#### Example

```js
let ages = [23,49,29,21];
let canEveryoneDrink = ages.every(val => val >= 21);
console.log(canEveryoneDrink);
// => true
```

```js
let scores = [89,92,48,75,88,79];
let didEveryonePass = scores.every(val => val >= 70);
console.log(didEveryonePass);
// => false
```

---

### Array.filter

- executes a callback function on each item within the provided array
- evaluates if each item passes or fails the conditional statement provided
- returns a new array of items that pass conditional statement

#### Example

- NOTE: The callback function here is using an `Arrow Function`

```js
let likes = [
  { id: 1, type: 'sports', name: 'Washington Nationals' },
  { id: 2, type: 'food', name: 'Five Guys' },
  { id: 3, type: 'electronics', name: 'iPhone' },
  { id: 4, type: 'food', name: 'Coca-Cola' },
  { id: 5, type: 'food', name: 'M&Ms' }
];
let foodLikes = likes.filter(item => item.type === 'food' );
console.log(foodLikes);
/*
=> [
  { id: 2, type: 'food', name: 'Five Guys' },
  { id: 4, type: 'food', name: 'Coca-Cola' },
  { id: 5, type: 'food', name: 'M&Ms' }
];
*/
```

- can also filter by value type:

```js
let responses = [1,9,4,5,10, 'good', 'excellent', 'not bad', 'good'];
// obtain the numeric responses:
let scoresNum = responses.filter((val) => typeof val === 'number');
console.log(scoresNum);
// => [1,9,4,5,10]
let scoresTxt = responses.filter((val) => typeof val === 'string');
// => ['good', 'excellent', 'not bad', 'good']
```

---

### Array.find

- executes a callback function on each item within the provided array
- returns **the first** object or value that evaluates to true

#### Example

- NOTE: The callback function here is using an `Arrow Function`

```js
let likes = [
  { id: 1, type: 'sports', name: 'Washington Nationals' },
  { id: 2, type: 'food', name: 'Five Guys' },
  { id: 3, type: 'electronics', name: 'iPhone' },
  { id: 4, type: 'food', name: 'Coca-Cola' },
  { id: 5, type: 'food', name: 'M&Ms' }
];
let iPhoneObject = likes.find( item => item.name === "iPhone" );
console.log(iPhoneObject);
```

---

### Array.findIndex

- returns the index of an included value, if it exists in the array

```js
let data = [94,180,7492,9207,297,2900,'a','c',9720];
console.log(data.findIndex( (val) => val === 2900) );
console.log(data.findIndex( (val) => val === "b") );
// => 5
// => -1
```

---

### Array.fill

- will set the provided value along with a start and end position

```js
// setup an array of binary values for summer months
let summerMonths = new Array(12);
// fill in all slots with 0
summerMonths = summerMonths.fill(0);
// assign a 1 to slots 5-8 for June, July, August
summerMonths = summerMonths.fill(1,5,8);
console.log(summerMonths);
// => [0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0]
```

---

### Array.forEach

- executes a callback function on each item within the provided array
- does not return anything
- operations that are executed inside the `forEach` can be immutable or perform mutations, depending on how the operations have been assigned to the array
- useful when looping through elements from a `querySelectorAll` execution

#### Example

- NOTE: The callback function here is using an `Arrow Function`

```js
let data = [4,9,49];
data.forEach( (value, index) => {
  console.log(value);
});

// => 4
// => 9
// => 49
```

[source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

---

- creates and returns a new array from a provided `Iterator`

```js
let phrase = "hello";
console.log(Array.from(phrase));
// => ['h','e','l','l','o'];
```


[source](https://blog.alexdevero.com/javascript-arrays/)

---

### Array.includes

- returns a boolean whether the array contains the indicated value

```js
let data = [84,92,100];
console.log(data.includes(100));
// => true
```

[source](https://blog.alexdevero.com/javascript-arrays/)

---

### Array.keys

- very similar to `Array.values` as it will create an `Array Iterator` with the keys

---

### Array.map

- transforms an existing array into a new array
- executes a callback function on each item
- returns a new array

#### Examples

- NOTE: The callback functions here are using `Arrow Function`s

```js
let data = [4,9,49];
let newData = data.map( (val) => {
  return val += 1;
});
console.log(newData);
// => [5,10,50];
```

```js
let products = [
  { id: '3948-29481', name: 'Phone' },
  { id: '2848-28840', name: 'Laptop' },
  { id: '9087-29281', name: 'Badge' }
];
let employeeProductIds = products.map(val => val.id);
console.log(employeeProductIds);
// => ['3948-29481', '2848-28840', '9087-29281']
```

---

### Array.of

- creates an array with values provided in the constructor

```js
console.log(Array.of('alpha','beta','charlie'));
// => ['alpha', 'beta', 'charlie']
```

---

### Array.reduce

- Run a callback function on each item in the array to manipulate an existing value
- Useful for adding up values inside arrays or arrays of objects

#### Examples

- NOTE: The callback functions here are using `Arrow Function`s
- NOTE 2: The second parameter of the `reduce` call is the initial value of 0

```js
let data = [1,2,3,4,5];
let total = data.reduce((accumulator, currentValue) => {
  return (accumulator + currentValue)
}, 0);
console.log(total);
// => 15
```

```js
let products = [
  { id: 1, cost: 20 },
  { id: 2, cost: 55 },
  { id: 3, cost: 5 },
  { id: 4, cost: 200 },
  { id: 5, cost: 10 }
];
let expenses = products.reduce((accumulator, currentValue) => {
  return (accumulator + currentValue.cost)
}, 0);
console.log(expenses);
// => 290
```

---

### Array.some

- Runs a callback function on each item in the array to evaluate whether the item returns true based on the provided conditional statement
- Returns true if at least one item evaluates to true

#### Example

```js
let ages = [13,15,16,18,30];
let anyAdults = ages.some(val => val >= 18);
console.log(anyAdults);
// => true
```

---

### Array.toLocaleString

- Depending on the included `locale` options, the data inside an array can be formatted accordingly

#### Example

```js
const arr = [12345678, new Date(), "alligators"];
const formatted = arr.toLocaleString(`fr-FR`, {
  style: 'currency',
  currency: 'EUR',
  era: 'long'
});
console.log(formatted);
// => 12 345 678,00 €,10 11 2019 après Jésus-Christ à 18:30:03,alligators
```

### Array.values

- returns an `Array Iterator` with all the values of a provided array

```js
let names = ["Patrick", "Elizabeth", "Mark", "Steve", "Lisa", "Greta"];
let namesIterator = names.values();
for ( let name of namesIterator ) {
  console.log(name);
}
// => "Patrick"
// => "Elizabeth"
// => "Mark"
// => "Steve"
// => "Lisa"
// => "Greta"

// the Iterator object can actually be re-used and started again
// since it is a Generator
console.log(namesIterator.next().value); // => "Patrick"
console.log(namesIterator.next().value); // => "Elizabeth"
```

## Sources

- [Better loops in JavaScript - DEV Community 👩‍💻👨‍💻](https://dev.to/kartik2406/better-loops-in-javascript-2716)
- [source2](https://blog.alexdevero.com/javascript-arrays/)
