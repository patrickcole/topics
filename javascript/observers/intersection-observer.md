# Intersection Observer

- API to listen/observe changes for a specific element inside a document
- only available on `modern browsers`
- a traditional approach to lazy-load images, now support for image lazy loading is coming to browsers
- additional advantage to native lazy-load being supported is no more worries about `<noscript>` for lazy loading

## Syntax

- the following example adds a class of `read` to each `li` when the have overlapped the browser's viewport:

```html
<body>
    <main>
      <ul>
        <li id="item1" class="item"></li>
        <li id="item2" class="item"></li>
        <li id="item3" class="item"></li>
        <li id="item4" class="item"></li>
        <li id="item5" class="item"></li>
        <li id="item6" class="item"></li>
        <li id="item7" class="item"></li>
        <li id="item8" class="item"></li>
        <li id="item9" class="item"></li>
        <li id="item10" class="item"></li>
        <li id="item11" class="item"></li>
        <li id="item12" class="item"></li>
        <li id="item13" class="item"></li>
        <li id="item14" class="item"></li>
        <li id="item15" class="item"></li>
        <li id="item16" class="item"></li>
        <li id="item17" class="item"></li>
        <li id="item18" class="item"></li>
        <li id="item19" class="item"></li>
        <li id="item20" class="item"></li>
      </ul>
    </main>
    <script src="intersection.js"></script>
  </body>
```

```css
body, ul, li {
  margin: 0;
  padding: 0;
}

ul { 
  list-style-type: none;
}

.item {
  width: calc(100vw - 2rem);
  min-height: 100px;
  background-color: red;
  margin: 1rem;
  transition: background-color 1s ease-in;
}

.item.read {
  background-color: green;
}
```

```js
const observer = new IntersectionObserver( (entries, observer) => {
  entries.forEach( (entry) => {
    if ( entry.isIntersecting ) {
      let element = entry.target;
      element.classList.add('read');
      observer.unobserve(element);
    }
  });
}, {
  threshold: 0    // 0 = any pixel is present, 1 = all pixels are present
});
const listItems = document.querySelectorAll('.item');
listItems.forEach(el => observer.observe(el));
```

[source](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
[source2](https://blog.bitsrc.io/lazy-loading-images-using-the-intersection-observer-api-5a913ee226d)
[source3](https://dev.to/ekafyi/lazy-loading-images-with-vanilla-javascript-2fbj)

---

## Load More Content Example

- [Lazy Loading with the IntersectionObserver API - DEV Community 👩‍💻👨‍💻](https://dev.to/aligoren/lazy-loading-with-the-intersectionobserver-api-44pe)

## Update Title with Active Section Example

- [Scroll listener vs Intersection Observers: a performance comparison](https://itnext.io/1v1-scroll-listener-vs-intersection-observers-469a26ab9eb6)
