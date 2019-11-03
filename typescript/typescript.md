# TypeScript

- provides optional **strict** typing, classes and interfaces
- helps enforce good code practice
- being that JavaScript is evaluated at runtime, type checking cannot be done beforehand
- TypeScript is only used for development, the end result is compiled JavaScript

## Static Types

### String

```ts
const message: string = 'hello world';
```

### Boolean

```ts
const isType: boolean = false;
```

### Array

```ts
let newArray: string[] = ["one", "two", "three"];
// or
let newArray2: Array<string> = ["one", "two", "three"];
```

### Enum

- declares a set of values (similar to `Object`)

```ts
// Numeric enum
enum Status {
  Inactive = 0,
  active = 1
}

// String enum
enum Status {
  Inactive = "INACTIVE",
  active = "ACTIVE"
}
```

### Any

```ts
let checkValue: any = true;
checkValue = "Check";
checkValue = 14;
```

### Void

- no return value in a function

```ts
const LogIt = (): void => {
  console.log(`log it now`);
}
```

### Interface

- used for checking the type of an object

```ts
interface userData {
  name: string,
  age: number
}

let AddUserDetails = ({ name, age}: userData ): void => {
  let arr = [];
  arr.push({ name, age })
}

AddUserDetails({ name: "Patrick", age: 32 });
```

### Generics

- enable use of reusable code

```ts
// this will throw an error if something
// other than a string is passed into function
const createNewArray = (value: string): Array<string> => {
  let output: Array<string> = [];
  output.push(value);
  return output;
}

// however, a generic can help with this issue:
const createNewArray = <T>(value: T): Array<T> => {
  let output: Array<T> = [];
  output.push(value);
  return output;
}

let val = createNewArray<string>("fdfsd");
console.log(val); // => ["fdfsd"]

let val2 = createNewArray<number>(10);
console.log(val2); // => [10];
```

[source]([TypeScript Basics - A Definitive Guide - DEV Community 👩‍💻👨‍💻](https://dev.to/ganeshmani/typescript-basics-a-definitive-guide-57j))
[source2](https://dev.to/integerman/migrating-to-typescript-3bai)

---
