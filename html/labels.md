# Labels

- a label can be referenced if it is properly attached to an `id` of an `element`

```html
<label for="inputUsername">Username</label>
<input type="text" id="inputUsername" name="inputUsername">
```

```js
let usernameLabels = document.getElementById('inputUsername').labels;
console.log(usernameLabels);
// => NodeList (1) [label]
```

## Editor's Note / Commentary

It's a shame that CSS can't have this information as well. Something like a selector:

```css
#inputUsername:label
/* or */
#inputUsername:attached-label
```

Would make styling labels on-hover or on-focus much easier.

[source1](https://www.stefanjudis.com/today-i-learned/input-elements-hold-references-to-their-labels/)
