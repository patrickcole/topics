# Date

## Date.toLocaleString

- given a locale and configuration options, a string is generated accordingly

### Example

```js
const date = new Date();

console.log( date.toLocaleString(`en-US`));
// => 11/16/2019, 4:45:45 PM

console.log( date.toLocaleString(`hi-IN`));
// => 11/16/2019, 4:45:45 pm

// additional properties can be provided:
const options = {
  weekday: 'long',
  era: 'long'
};
console.log(date.toLocaleString(`en-US`, options)); 
// => Sunday Anno Domini

console.log(date.toLocaleString(`hi-IN`, options));
// => ईसवी सन रविवार

console.log(date.toLocaleString(`fr-CH`, options));
// => après Jésus-Christ dimanche
```

[source1](https://alligator.io/js/using-tolocalestring/)
