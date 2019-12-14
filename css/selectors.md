# CSS Selectors

## :is()

- group multiple alike selectors

```css
/* before */
body.theme--light button,
body.theme--light a,
body.theme--light p,
body.theme--light h1 {
  display: block;
}

/* after */
body.theme-light :is(button, a, p, h1) {
  display: block;
}
```

[source](https://bitsofco.de/chrome-dev-summit-2019/)
