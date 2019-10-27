# DOM - ChildNode Interface

The ChildNode interface deals with nodes or elements where a defined parent is present.

## ChildNode.after

- TODO

## ChildNode.before

- TODO

## ChildNode.remove

- elements can be easily removed now with just a `remove()` call
- previously finding the element's `parentNode` was required to remove an element
- the example below shows how to remove an element:

```js
// the new way, just using .remove():
const container = document.querySelector('#container');
container.remove();

// the old way:
const container = document.querySelector('#container');
container.parentNode.removeChild(container);
```

[source](#childnode1)

---

## ChildNode.replaceWith

- current elements can be replaced with either an entirely new element or an existing element
- existing elements that are used to replace entire other elements are not copied, but rather moved to their new location
- the example below illustrates this:

```html
<div class="first">
  <h1>Title</h1>
</div>

<div class="second">
  <h2>Subtitle</h2>
</div>
```

```js
const h1 = document.querySelector('h1');
const h2 = docuemnt.querySelector('h2');
h1.replaceWith(h2);
```

```html
<div class="first">
  <h2>Subtitle</h2>
</div>

<div class="second">

</div>
```

- notice how the `<h2>` was not copied, but moved and replaced the existing `<h1>`

[source](#childnode1)

---

## Sources

- <a name="childnode1"></a> [Using the DOM like a Pro - ITNEXT](https://itnext.io/using-the-dom-like-a-pro-163a6c552eba)
