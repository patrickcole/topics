# Number

### Number.toLocaleString

- given a locale and configuration options, take any number and format it accordingly

#### Example

```js
const number = 12345.678;
console.log( number.toLocaleString('en-US') );
// => 12,345.678
console.log( number.toLocaleString('fr-FR') );
// => 12 345,678
// can be formatted for currency as well:
console.log( number.toLocaleString('en-US', {
  style: 'currency',
  currency: 'USD'
}));
// => $12,345.68
// can also add how many significate digits to use:
console.log( number.toLocaleString('en-US', {
  style: 'currency',
  currency: 'USD',
  maximumSignificantDigits: 2
}));
// => $12,000
```
