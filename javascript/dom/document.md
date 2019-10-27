# DOM - Document Interface

Represents the actual webpage being displayed from within the browser interface. This is mapped out as a tree-like structure known as the DOM tree.

## getElementsByClassName

- returns a `HTMLCollection` of all elements that contain the input class name (without the dot)
- can accept multiple class names separated by spaces

[source](#document1)

---

## getElementById

- returns an element based on if the id specified was found in the document
- the id specified is **case-sensitive** and **has to be unique**

[source](#document1)

---

## getElementsByName

- returns a `HTMLCollection` of elements that match a name input
- multiple elements can have the same name property, for example `username`
- this is different than `getElementById` which has to be unique

[source](#document1)

---

## getElementsByTagName

- returns a `HTMLCollection` of elements that match the tag specified
- to get all elements, specify an asterisk (*)
- not recommended to get all elements

[source](#document1)

---

## querySelector

- the example below shows how to use various query selectors to select an element:
- **NOTE:** only one element will be returned if the selector finds an element, otherwise it will return `null`
- **NOTE** `querySelector` doesn't *have* to be run off the `document`, it can be run off any valid element

```js
// get first element that contains class="btn"
document.querySelector(`.btn`);

// get element with id="primary"
document.querySelector(`#primary`);

// get first <div> element:
document.querySelector(`div`);

// get first element that has an attribute selector name="first":
document.querySelector(`[name="first"]`);

// get the first <span> that is one level deep in a <p> that is after a <div> element:
document.querySelector(`div + p > span`)
```

[source](#document1)
[source2](#document2)

---

## querySelectorAll

- unlike `querySelector`, will return a list of found elements as a `NodeList`
- a `NodeList` can be looped using a `for of` loop or converted to a regular array using `Array.from` or `spread` into an array
- **NOTE** `querySelectorAll` doesn't *have* to be run off the `document`, it can be run off any valid element
- the examples below show how to use querySelectorAll and how it can be converted to an array:

```js
// get all paragraphs:
const paragraphs = [...document.querySelectorAll('p')];

// get all sections:
const sections = Array.from(document.querySelectorAll('section'));

// now array methods can be used:
const savedSections = sections.find( element => element.classList.contains('read') );
```

- **NOTE:** This is a great quote from a sourced article:

> The querySelectorAll method differs from methods like `getElementsByTagName` and `getElementsByClassName` in that these methods return an HTMLCollection which is a live collection, whereas `querySelectorAll` returns a NodeList which is static.

- keep the above quote in mind if you are going to be adding/removing elements and still using the array or `NodeList` returned from `querySelectorAll` commands

[source](#document1)
[source](#document2)

---

## Sources

- <a name="document1"></a> [Getting DOM Elements using JavaScript - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/getting-dom-elements-using-javascript-4do0)
- <a name="document2"></a> [Using the DOM like a Pro - ITNEXT](https://itnext.io/using-the-dom-like-a-pro-163a6c552eba)