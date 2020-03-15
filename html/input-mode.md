# Input Mode

Allows form elements to decide which virtual keyboard (soft keyboard) to display to the user. It is treated as a "hint" to the browser on which keyboard the user might need.

```html
<input type="text" inputmode="decimal">
```

> This is meant to compliment `type=""` so that the proper virtual keyboard displays regardless of the `type`. In the example above, if a credit card number was being entered, `type="number"` would actually not be best as it would show increase (+) and decrease (-) number controls. We can use `type="text"` along with `inputmode="numeric"` to show the appropriate keyboard and also coupled with a `pattern` attribute for validation.

A [tweet](https://twitter.com/AmeliasBrain/status/973628617413476352) explaining this.

Options include:
- decimal
- tel
- numeric
- email
- url
- search

### 2FA / oAuth

```html
<input
  type="text"
  name="token"
  id="token"
  inputmode="numeric"
  pattern="[0-9]*"
  autocomplete="one-time-code"
/>
```

#### Tools

- [InputTypes.com](https://inputtypes.com)

#### Sources

- [Finger-friendly numerical inputs with inputmode](https://css-tricks.com/finger-friendly-numerical-inputs-with-inputmode/)
- [Everything You Ever Wanted to Know About Inputmode](https://css-tricks.com/everything-you-ever-wanted-to-know-about-inputmode/)
- [Improve Your User's 2FA Experience with HTML Attributes](https://medium.com/better-programming/improve-your-users-2fa-experience-with-html-attributes-c4944daed1c6)
