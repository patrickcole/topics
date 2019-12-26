# Web Speech

- speech synthesis (text-to-speech)
- speech recognition (speak-to-text)

## Speech Synthesis

- utilizes the `SpeechSynthesisUtterance` object to parse the text and convert it to audio
- can queue multiple `SpeechSynthesisUtterance` objects and it will speak one after another

```js
speechSynthesis.speak(
  new SpeechSynthesisUtterance("Hello!")
);
```

- multiple voices are available in compatible browsers
- the voices are obtained via a call: `speechSynthesis.getVoices()`
- a voice can be assigned to the `SpeechSynthesisUtterance` object before the `.speak()` method is invoked

### Events

- the `SpeechSynthesisUtterance` object contains multiple events that can be hooked into for visual cues or other functionality

```js
let utterance = new SpeechSynthesisUtterance("Hello");
utterance.addEventListener("start", () => console.log(`speaking`));
utterance.addEventListener("end", () => console.log(`stopped speaking`));
speechSynthesis.speak(utterance);
```

- the `speechSynthesis` API also contains an event to detect when a voice has changed: `speechSynthesis.onvoiceschanged`

## Speech Recognition

- identifies and translates audio into text
- this is still in progress and has not been implemented widely amongst browsers

---

- [source1](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)
- [source2](https://dev.to/twilio/text-to-speech-in-the-browser-with-the-web-speech-api-20nk)
- [source3](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis)
- [source4](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition)