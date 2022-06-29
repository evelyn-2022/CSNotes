# Tailwind: extra white border over outline in input elements

## Problem:

With tailwind css, when I set an outline to an input element, it will automatically get a white border around it:
<img src='./resources/outline.png' style='width:500px'>

```html
<input
  class="rounded py-2.5 mb-4 px-3 bg-white focus:outline-red "
  type="search"
  name="input url"
  placeholder="Shorten a link here..."
/>
```

## Cause:

1. Firstly, I need to set the outline style to `solid`.
2. From styles panel, I can see that tailwind automatically gives a `-2px` offset to `[type='search']`, which needs to be reset to zero explicitly.

```css
[type="search"] {
  -webkit-appearance: textfield;
  outline-offset: -2px;
}
```

## How to fix it:

```html
<input
  class="rounded py-2.5 mb-4 px-3 bg-white focus:outline focus:outline-red focus:outline-offset-0 "
  type="search"
  name="input url"
  placeholder="Shorten a link here..."
/>
```
