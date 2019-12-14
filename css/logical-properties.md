# CSS Logical Properties

- rather than assuming that each element is read from left-to-right and top-to-bottom; logical properties move to a "more agnostic approach."
- previous terms: `top, right, bottom, left`
- new terms: `block-start, inline-end, block-end, inline-start`

- this allows settings where languages are right-to-left or bottom-to-top, they are not penalized

- for example:

```css
.announcement {
  padding-inline-start: 2rem;
}
```

- the example above on a left-to-right (ltr) language, would have `2rem` of padding on the `left`
- for right-to-left (rtl) language, the `2rem` of padding would be on the `right`
- this effectively defines both rules in one line rather than having to use a `media query`
- the traditional properties are not being replaced, these logical properties are just enhancements

