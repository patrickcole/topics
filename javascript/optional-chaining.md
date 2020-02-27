# Optional Chaining

- consider the following

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

- before optional chaining, if we wanted to check if the `role` property was set we might do something like this:

```js
let myRole = user.job && user.job.role;
```

- now, with optional chaining we can simply do this:

```js
let myRole = user?.job?.role;
```

- this effectively looks for each property and if any of those are undefined, it simply returns `undefined`
- so using the example above, if we were to write:

```js
let myCompany = user?.job?.company;
```

- the example above would return `undefined` because `company` is not defined in the object `user`
- this practice can be done with functions as well:

```js
let myFullName = user?.getFullName?.();
```

- albeit a little strange, the code above looks for the method `getFullName` inside the `user` object, and then, if it exists, it performs the function call.