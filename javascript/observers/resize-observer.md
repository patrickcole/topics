# Resize Observer

- reports any dimension change of an element when observed
- replaces custom built scripts that would be listening for changes on an element, usually in a non-efficient manner (i.e. `setInterval`)
- streamlines the process to observe a singular element rather than listening for the entire document (i.e. `window.onresize` or `window.resize`)
- also useful if the DOM has been updated (an element added or removed) causing a parent element's dimensions to be affected

```js
// Setup an observer:
const primaryObserver = new ResizeObserver(entries => {
  // Perform an update or get dimensions
  // here via the entries parameter
});

const heading = document.querySelector('h1');
primaryObserver.observe(heading);
```

---

[source1](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver)
[example1](https://mdn.github.io/dom-examples/resize-observer/resize-observer-text.html)
[source2](https://dev.to/yashints/let-s-get-to-know-the-resizeobserver-lae)
