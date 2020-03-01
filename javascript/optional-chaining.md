# Optional Chaining

- Gives the ability to check if a property exists without returning a `ReferenceError`
- If the given statement evaluates to `false` at any point in the chain, it returns `undefined` instead of throwing an error.

## Object Properties (Strings, Numbers, Properties)

```js
return user?.contact?.phone_number
```

This might return the value of `phone_number` if it has been set in the `user` object under the `contact` property. However, if the user does not provide a phone number, the code above will just return `undefined` instead of breaking.

## Arrays

```js
return user?.emails?.[0]
```

This means that if no email is found in the array OR the first index, it will return `undefined`

## Functions

```js
return getUserInfo?.('fake user')
```

Will return `undefined` if `fake user` is not valid in the function.

## Dynamic Properties

```js
let animal = {
  habitat: {
    water: `freshwater`,
    land: `forest`
  }
}
// habitatType can be "water" or "land"
const getHabitatProperty = (type) => {
  return animal?.habitat?.[type]
}
getHabitatType('water')
// returns  ['freshwater']
getHabitatType('land')
// returns ['forest']
```

## In Combination With Nullish Coalescing 

- deal with falsy (`undefined`) values to provide a default:

```js
console.log(person?.profile?.name ?? "Anonymous");
```

If any one of the properties of `person` or `person` is not found, it will console "Anonymous"

## Scenario

Consider the following:

```js
let user = [
  first_name: "Patrick",
  last_name: "Cole",
  job: {
    role: "Software Developer"
  }
  getFullName: function() {
    return `${this.first_name} ${this.last_name}`;
  }
]
```

Before optional chaining, if we wanted to check if the `role` property was set we might do something like this:

```js
let myRole = user.job && user.job.role;
```

Now, with optional chaining we can simply do this:

```js
let myRole = user?.job?.role;
```

This effectively looks for each property and if any of those are `falsy`, it simply returns `undefined` instead of throwing an error.

So using the example above, if we were to write:

```js
let myCompany = user?.job?.company;
```

The example above would return `undefined` because `company` is not defined in the object `user`. This practice can be done with functions as well:

```js
let myFullName = user?.getFullName?.();
```

Albeit a little strange, the code above looks for the method `getFullName` inside the `user` object, and then, if it exists, it performs the function call.

## Sources

- [source1 - Optional Chaining](https://alligator.io/js/v8-optional-chaining-nullish-coalescing/#optional-chaining)
- [source2 - Optional Chaining with Nullish Coalescing](https://alligator.io/js/es2020/#optional-chaining-operator)