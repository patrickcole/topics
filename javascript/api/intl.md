# Intl

- used to format data based on a specific locale
- locales can be short (`en`) or long form (`en-US`)
- strings, numbers, date and time in local-specific formats
- the api is made up of:
  - `Collator`
  - `DateTimeFormat`
  - `ListFormat`
  - `NumberFormat`
  - `PluralRules`
  - `RelativeTimeFormat`
- each constructor is made up of two parameters: the locale and any additional options for that constructor
- by default, the `Intl` API uses the locale set in the runtime (the system setting)

## Collator

- can be used to compare strings that share characters between languages

```js
console.log( new Intl.Collator('de').compare('ä', 'z') );
// => -1
console.log( new Intl.Collator('sv').compare('ä', 'z') );
// => 1
```

## DateTimeFormat

- locale-specific date and time formatting
- can be used to provide a date range as well

```js
const DTF = new Intl.DateTimeFormat(`en`, {
  year: `numeric`,
  month: `short`,
  day: `numeric`
});

const START = new Date(`03-14-2020`);
const END = new Date(`03-27-2020`);
DTF.formatRange(START, END);
// => `Mar 14-27 2020`
```

## ListFormat

- takes a collection of strings and concatenates them together using commas along with `and` for the final option

```js
const OS = [`Windows`,`mac OS`,`Linux`];
const LIST_FORMAT = new Intl.ListFormat(`en`, { type: `conjunction` });
console.log(LIST_FORMAT.format(OS));
// => `Windows, mac OS and Linux`
// can also use `disjunction` to provide `or`
// using `unit` will just place commas
```

## NumberFormat

- can format numbers, especially larger ones with proper locale-specific formatting (ex: commas versus spaces)
- can specify in the options:
  - `style`: decimal, currency or percent (default is decimal)
  - `currency`: for example - USD
  - `currencyDisplay`: symbol, code (default is symbol)

```js
const NUM_FORMAT = new Intl.NumberFormat(`en`);
console.log(NUM_FORMAT.format(1000));
// => `1,000`
// if set to a different locale:
const FR_FORMAT = new Intl.NumberFormat(`fr`);
console.log(FR_FORMAT.format(1000));
// => `1 000`
```

## PluralRules

- calculates the proper plural formatting for an amount

```js
let label = "dog";
let amount = 1;
let pluralize = (amt, phrase) => {
  let pluralTest = new Intl.PluralRules('en-US').select(amt);
  if ( pluralTest == "other" ) {
    phrase += "s";
  }
  return phrase;
};

console.log(`${amount} ${pluralize(amount, label)}`);
// => 1 dog
amount = 10;
console.log(`${amount} ${pluralize(amount, label)}`);
// => 10 dogs
```

## RelativeTimeFormat

- produces a human-readable format; so easier to understand

```js
const TIME_FORMAT = new Intl.RelativeTimeFormat(`en`, { numeric: `auto` });
console.log( TIME_FORMAT.format(-1, `month`) );
// => `last month`
console.log( TIME_FORMAT.format(0, `month`) );
// => `this month`
console.log( TIME_FORMAT.format(-1, `day`) );
// => `yesterday`
console.log( TIME_FORMAT.format(0, `day`) );
// => `today`
console.log( TIME_FORMAT.format(1, `day`) );
// => `tomorrow`
```

## Sources

- [New Intl APIs in JavaScript](https://blog.bitsrc.io/new-intl-apis-in-javascript-c50dc89d2cf3)
- [Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/PluralRules)
- [Internationalization API built into your browser](https://wanago.io/2019/09/02/internationalization-api/)
- [Because Date Time Formatting is Pain & International Formatting is Nearly Impossible](https://itnext.io/javascript-international-methods-b70a2de09d92)
