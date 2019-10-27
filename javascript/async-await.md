# Async / Await

## Fetch

- being that fetch uses the promise pattern, async/await can be used with fetch
- the following example shows async/await with fetch

```js
const fetchUsers = async () => {
  try {
    const res = await fetch(`https://reqres.in/api/users`);
    if ( !res.ok ) {
      throw new Error(res.status);
    }
    const data = await res.json();
    console.log(data);
  } catch ( err ) {
    console.error(err)
  }
}

fetchUsers();
```

[source](#asyncAwait1)

---

## Sources

<a name="asyncAwait1"></a> [Introduction to JavaScript Fetch API - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/introduction-to-javascript-fetch-api-4f4c)
