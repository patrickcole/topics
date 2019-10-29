# Rendering

## Client-Side Rendering (CSR)

- usually starts with an empty root node (something like `div#app`)
- build html elements via JavaScript
- can load content asynchronously and have a "blank canvas" where content is loaded into

## Isomorphic (Server-Side Rendering [SSR])

- send all the constructed HTML elements from the server
- faster perceived speed over CSR
- SEO is ranked better than CSR
- no page reflow or flash of content when items are being re-rendered

[source](https://medium.com/@sujankanwar/why-do-we-love-isomorphic-universal-rendering-988c22933933)

---