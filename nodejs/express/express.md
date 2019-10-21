# Express

## Body Parser

- the `bodyParser` functionality has been added back into `express` package by default
- use the following middlware to parse body content without using a dedicated `bodyParser` package:

```js
app.use(express.json())
app.use(express.urlencoded({ extended: false }))
```

[source](https://stackoverflow.com/a/51844327/6632985)