# Rendering

## Client Side Rendering

- already downloaded file generates content via JavaScript (DOM manipulation/generation)
- HTML is rendered by the client

## Server Side Rendering

- user makes a request for content and the server sends back content file generated from the server
- HTML is produced by the server
- dynamic SSR generates content based on logic (on-the-fly)

## Static Rendering

- content is already generated (usually from compilation)
- utilizes different markup language such as Markdown

### Static SSR

- good performance, server just provides the files
- CDN, caching, compression are better utilized as the content is static
- requires a large amount of client side rendering as the static files will not be changing from the server
- API would serve data

### Dynamic SSR

- not best performance, server has to build it
- caching can be tricky
- no build process for HTML, it builds on the server
- no API would be needed

[source](https://itnext.io/server-side-rendering-the-right-way-6c6ab5995be3)