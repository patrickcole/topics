# Fetch API

- **NOTE** fetch can now use the [`async/await`](./async-await.md) pattern
- uses the `promise` pattern
- used for making asynchronous requests just like `XHR` "ajax" requests
- supported in all modern browsers, for IE there's a polyfill
- being that it uses the `promise` pattern, error handling is done via an included `catch` block
- **NOTE:** fetch promises do not catch on returned errors of `404` and `500`, so some kind of check should be implemented to handle these aspects
- **NOTE:** one way to handle this is to use the `ok` property of the fetch response stream object

- the following example makes a fetch request to a json file on the same server:
- note the use of `arrow functions` in the example

```js
fetch('/js/users.json')
  .then( response => console.log(response) )
  .catch( err => console.error(err) )
```

- fetch requests perform an HTTP `GET` request by default
- additional HTTP requests such as `POST`, `PUT`, `DELETE`, `HEAD` and `OPTIONS` can be performed by a fetch request

[source](#fetch1)

---

## Fetching JSON

- the example below ensures that the response object will be treated as json
- this is because fetch promise returns a stream object that needs to be converted to json
- to return a different type such as XML, the method would be `.text()` instead of `.json()`

```js
fetch(`http://reqres.in/api/users`)
  .then(res => res.json())
  .then(res => {
    res.data.map( user => {
      console.log(`${user.id}: ${user.first_name} ${user.last_name}`);
    })
  })
```

[source](#fetch1)

---

## Requests Other Than GET

- to perform a different request than `GET`, simply set the `method` property of an `options` object passed to the fetch request
- when using methods such as `POST`, the options object provides the ability to include a request body and headers that specify what type of data is being sent via fetch
- the example below shows how to perform a `POST` request with an external API:

- **NOTE:** the body has to use `JSON.stringify()` before it can be sent
- **NOTE:** in order to send JSON, albeit "stringified", the header must be sent along as `application/json`

```js
const user = {
  first_name: 'John',
  last_name: 'Lilly',
  job_title: 'Software Engineer'
};
const options = {
  method: 'POST',
  body: JSON.stringify(user);
  headers: {
    'Content-Type':'application/json'
  }
}
fetch(`http://reqres.in/api/users`, options)
  .then( res => res.json() )
  .then( res => console.log(res) );
```

[source](#fetch1)

---

## Using Request Object with Fetch

- using javascript objects to configure a fetch request is perfectly valid
- another approach is to use a `Request` object
- the example below shows how to configure a `Request` object for use in fetch

```js
const url = 'https://reqres.in/api/users';
const user = {
  first_name: 'John',
  last_name: 'Doe',
  job_title: 'Blogger'
};
const request = new Request( url, {
  method: 'POST',
  body: JSON.stringify(user),
  headers: new Headers({
    'Content-Type': 'application/json'
  })
});
fetch(request)
  .then(res => res.json())
  .then(res => console.log(res))
  .catch(err => console.error(err));
```

[source](#fetch2)

---

## Fetch Response Object

- the following properties are available in a fetch response object:

```js
// res.headers
// res.headers.get('content-type');
// res.status
// res.ok
// res.statusText
// res.redirected
// res.type
// res.url
```

- the following methods are available to mutate the stream returned by a fetch promise

```js
// .json()
// .text()
// .blob()
// .formData()
// .arrayBuffer()
```

[source](#fetch1)

---

## Sources

<a name="fetch1"></a> [Introduction to JavaScript Fetch API - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/introduction-to-javascript-fetch-api-4f4c)
<a name="fetch2"></a> [Using JavaScript Fetch API to Get and Post Data - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/using-javascript-fetch-api-to-get-and-post-data-2anl)
