# Prototype

- JavaScript objects can be declared in multiple ways:
  - declarative form (also known as "object literal")

  ```js
  const user = {
    first_name: "Patrick",
    last_name: "Cole",
    age: 33
  }
  ```

  - deconstructed form

  ```js
  const user = new Object();
  user.first_name = "Patrick";
  user.last_name = "Cole";
  user.age = 33;
  ```

- each object has a base set of properties and methods from the `Object.prototype`
- can check for a property of an object by using the `obj.hasOwnProperty("prop")` method
- another method is `Object.prototype.toString()` or just `.toString()`
- methods that are established in the prototype do not have to be re-established each time the object is created, they are stored in the prototype
- each new instantiation (creation) of an object can use the built-in methods along with whatever values have been configured

```js
// for example:
// using object literal declaration:
const User = {
  printName: function() {
    return this.name
  }
};
// now instantiate a new object for Patrick
const employee = Object.create(User);
employee.name = "Patrick";
console.log(employee.printName());
// => "Patrick"
```

- notice how `printName` can be run from the `employee` object, because the `printName` method is inside the prototype
- conversely, the `this.name` inside the prototype assumes that the `name` value will be set after the object has been instantiated (`Object.create(User)`)

[source1](https://www.telerik.com/blogs/javascript-fundamentals-prototype-chains)