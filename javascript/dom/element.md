# DOM - Element Interface

## Element.closest

- selects the closes element based on the source element running the query and the actual query specified
- the example below shows an example:

```js
// find the first <p>, then the closest <div> (could be parent) element and then the next closes element that has a class that contains "content":
document.querySelector('p').closest('div').closest('.content');
```

[source](#element1)

---

## Element.insertAdjacentElement

- moves, not copies, an entire element to a new location based on another element
- rules are similar to `insertAdjacentHTML`

[source](#element1)

---

## Element.insertAdjacentHTML

- provides the ability to generate an element and add it to a current element based on a string provided
- much faster than `.innerHTML`
- the position of where the new element is based on one of four values:

```js
// beforebegin = places new element before opening tag of adjacent element
// afterbegin = places new element after opening tag of current element
// beforeend = places new element before closing tag of current element
// afterend = places new element after closing tag of current element
```

- **NOTE:** `beforebegin` and `afterend` only work if a parent element of the current element is present

[source](#element1)
[source2](#element2)

---

## Element.matches

- returns a boolean whether an element matches an query string input
- the example below shows this:

```html
<p class="announcement">Hello Everyone!</p>
```

```js
const paragraph = document.querySelector('p');
p.matches('p'); // true
p.matches('.announcement'); // true
p.matches('.primary');  // false
```

[source](#element1)

---

## Sources

- <a name="element1"></a> [Using the DOM like a Pro - ITNEXT](https://itnext.io/using-the-dom-like-a-pro-163a6c552eba)
- <a name="element2"></a> [Element.insertAdjacentHTML() - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML)