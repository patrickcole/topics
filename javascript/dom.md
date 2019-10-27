# DOM API

- Document Object Model

## closest

- selects the closes element based on the source element running the query and the actual query specified
- the example below shows an example:

```js
// find the first <p>, then the closest <div> (could be parent) element and then the next closes element that has a class that contains "content":
document.querySelector('p').closest('div').closest('.content');
```

[source](#dom1)

---

## contains

- returns a boolean whether one element contains another element

[source](#dom1)

---

## DOMParser

- allows an input string to create DOM documents
- a recommended approach is to create a function to handle the construction and just accept an input string of the element as a HTML string
- **NOTE:** this is different than `.innerHTML` and `document.createElement`
- the example below shows how to do this:

```js
let newElement = new DOMParser().parseFromString('<span>test</span>', 'text/html').body.firstChild;
document.body.appendChild(newElement);
```

[source](#dom1)

---

## getElementsByClassName

- returns a `HTMLCollection` of all elements that contain the input class name (without the dot)
- can accept multiple class names separated by spaces

[source](#dom3)

---

## getElementById

- returns an element based on if the id specified was found in the document
- the id specified is **case-sensitive** and **has to be unique**

[source](#dom3)

---

## getElementsByName

- returns a `HTMLCollection` of elements that match a name input
- multiple elements can have the same name property, for example `username`
- this is different than `getElementById` which has to be unique

[source](#dom3)

---

## getElementsByTagName

- returns a `HTMLCollection` of elements that match the tag specified
- to get all elements, specify an asterisk (*)
- not recommended to get all elements

[source](#dom3)

---

## HTMLCollection

- traditional collection of elements returned from `getElementsByName` or `getElementsByTagName` function calls
- array-like, but not an array
- can be converted to an array using `Array.from` and spread into array

[source](#dom3)

---

## insertAdjacentElement

- moves, not copies, an entire element to a new location based on another element
- rules are similar to `insertAdjacentHTML`

[source](#dom1)

---

## insertAdjacentHTML

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

[source](#dom1)
[source2](#dom2)

---

## matches

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

[source](#dom1)

---

## NodeList

- technically not an array, but is array-like as it stores a collection of elements
- can use the `forEach` method, `for of` loop
- can be converted into an array using `Array.from` and spread into array

[source](#dom3)

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

[source](#dom1)
[source](#dom3)

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

[source](#dom1)

---

## remove

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

[source](#dom1)

---

## replaceWith

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

[source](#dom1)

---

## Sources

- <a name="dom1"></a> [Using the DOM like a Pro - ITNEXT](https://itnext.io/using-the-dom-like-a-pro-163a6c552eba)
- <a name="dom2"></a> [Element.insertAdjacentHTML() - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML)
- <a name="dom3"></a> [Getting DOM Elements using JavaScript - DEV Community 👩‍💻👨‍💻](https://dev.to/attacomsian/getting-dom-elements-using-javascript-4do0)