# Web Share API

`navigator.share`

- works on `https` connections only (or `localhost`)
- must be performed by a user click action, not `onload` or `setTimeout`
- Uses device's sharing capabilities to share content
- can be connected to services such as Facebook, Twitter, etc.
- the idea to remove the need for custom scripts built by each of the providers, so a Twitter share script, Facebook share script, etc.
- controls the sharing experience so that users (and browsers) can expect consistent behavior
- originally only shared text links

## Level 2

`navigator.canShare`

- can now share files (images, audio, video)

- [source](https://bitsofco.de/chrome-dev-summit-2019/)
- [source2](https://blog.bitsrc.io/understanding-web-share-apis-d987ea3648ad)
- [source3](https://web.dev/web-share/)
- [source4](https://css-tricks.com/how-to-use-the-web-share-api/)
- [source5](https://blog.bitsrc.io/how-to-use-the-web-share-api-99460be88ad8)
