# JavaScript Operators

## Delete

> remove a specific own property of an object

- properties passed to a delete that do not exist do not return an error

```js
// example

let debt = {
  amount: 1000
};
console.log(debt.amount); // 1000
delete debt.amount;
console.log(debt.amount); // undefined
```

- in the example above `amount` is actually still "defined", but no value exists for it; this is because in JavaScript `undefined` actually means "no value yet"
- delete only works on configurable objects (custom objects you create)
- cannot remove properties from non-configurable objects

### Create A Non-Configurable Object Property

```js
let user = {
  ssn: "111-11-1111"
}
Object.defineProperty(user, "ssn", { configurable: false });
console.log(user.ssn);  // "111-11-1111"
delete user.ssn;
console.log(user.ssn);  // "111-11-1111"
```

- you can check the configuration of an object property using `Object.getOwnPropertyDescriptor(obj, prop)`

- **`var`,`let` and `const` declare non-configurable properties**
- they cannot be removed from the global scope
- **functions declarations cannot be deleted**
- however, functions declared as an object property can be deleted, but same rules apply when declared as `configurable: false`

- variables declared in the local scope without `var`, `let` or `const` can be deleted

### Delete and Prototype Chain

- a property declared in a function can be deleted and if a prototype value exists, it will be used
- the prototype value can also be deleted

```js
// for example:
function User() {
  this.first_name = "Patrick";
}
User.prototype.first_name = "User";

var employee = new User();
console.log(employee.first_name); // "Patrick";
delete employee.first_name;
console.log(employee.first_name); // "User";
```

### Delete and Arrays

- performing a delete on an array will only remove the value, but not the item's position in array
  - this means that if you had two items in the array, and performed `delete` on the first item, the `.length` of the array would still be 2

---

[source1](https://blog.bitsrc.io/understanding-the-delete-operator-in-javascript-3791ba6f3a08)
