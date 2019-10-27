# DOM - DOMParser Interface

- allows an input string to create DOM documents
- a recommended approach is to create a function to handle the construction and just accept an input string of the element as a HTML string
- **NOTE:** this is different than `.innerHTML` and `document.createElement`
- the example below shows how to do this:

```js
let newElement = new DOMParser().parseFromString('<span>test</span>', 'text/html').body.firstChild;
document.body.appendChild(newElement);
```

[source](#domparser1)

---

## Sources

- <a name="domparser1"></a> [Using the DOM like a Pro - ITNEXT](https://itnext.io/using-the-dom-like-a-pro-163a6c552eba)