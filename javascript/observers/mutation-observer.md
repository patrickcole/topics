# Mutation Observer

- establishes a method to watch for changes in the DOM
- can watch a specific element inside the DOM
- the options to observe are: 
  - attributes
  - character data
  - add/removal of child elements to the observed target
  - all the sub-elements ("children") of the target, this effectively applies the rules to all sub-elements instead of just the target

[source1](https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver)
[source2](https://developer.mozilla.org/en-US/docs/Web/API/MutationObserverInit)

---

## Mutation Record

- provides a `MutationRecord` "report object" of what was changed, based on what options were configured with the observer

[source1](https://davidwalsh.name/mutationobserver-api)
[source2](https://blog.sessionstack.com/how-javascript-works-tracking-changes-in-the-dom-using-mutationobserver-86adc7446401)

## Example

```js
const node = document.getElementById('output');
const config = { 
  attributes: true,
  childList: true,
  subtree: true
}
const callback = (mutationsList, observer) => {
  for ( let mutation of mutationsList ) {
    switch ( mutation.type ) {
      case: "childList":
        console.log(`Child node has been added or removed`);
      break;
      case: "attributes":
        console.log(`The ${mutation.attributeName} attribute was modified.`);
      break;
    }
  }
}
const observer = new MutationObserver(callback);
observer.observe(node, config);

// if you need to stop observing,
// call .disconnect()
observer.disconnect();
```

## Sample Repo

- [SantiagoGdaR/mutation-observer on Github](https://github.com/SantiagoGdaR/mutation-observer)
