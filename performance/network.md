# Network Performance

## Browser Adaptive Loading

- loads based on multiple criteria (device, network, browser)
- utilizes the `Network Information API`

- Examples from ChromeDevSummet2019

```js
const network = navigator.connection.effectiveType;
const isOnSaveData = navigator.connection.saveData;
```

[source](https://bitsofco.de/chrome-dev-summit-2019/)
