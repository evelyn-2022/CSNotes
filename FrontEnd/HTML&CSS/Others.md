Use the `filter` property with the value `blur()` to make color and shape not so sharp: `filter: blur(2px);`

<hr>

Clicking on the navigation links should jump the viewport to the relevant section. However, this jumping can be disorienting for some users. Select all elements, and set the `scroll-behavior` to `smooth`.

<hr>

The navigation accessibility can be improved with providing keyboard shortcuts. The accesskey attribute accepts a space-separated list of access keys. For example: `<button type="submit" accesskey="s">Submit</button>`

<hr>
Aligning teble content:

The `flex-end` setting has also brought your row's description text to the right of the element. To fix this, create a `.name` selector and give it a `width` property of 100%, and a `text-align` property of left.
Because you're using flex, this tells your `.name` elements to **take up 100% of the remaining available width,** **which allows the text to move to the left**.

```html
<p class="row">
  <span class="name">Cash</span>
  <span>$25</span>
  <span>$30</span>
  <span class="current">$28</span>
</p>
```

```css
.row {
  display: flex;
  justify-content: flex-end;
}
.name {
  width: 100%;
  text-align: left;
}
```

<hr>

Create a `p[class~="total"]` selector to target all of your `p` elements where the class includes total (such as your `class="row total"` elements). This may seem the same as using the `.total` class selector. However, CSS is parsed top-down. Your `.row `selector comes after this new selector, and **would overwrite the `.total` selector**. Because `p[class~="total"]` has **a higher selector specificity**, it takes priority even though it comes earlier in the stylesheet.

```html
<p class="row total">
  <span class="name">Total</span>
  <span>$579</span>
  <span>$736</span>
  <span class="current">$809</span>
</p>
```

```css
p[class~="total"] {
  border-bottom: 4px double #0a0a23;
  font-weight: bold;
}
.row {
  display: flex;
  justify-content: flex-end;
  border-bottom: 1px solid #0a0a23;
  padding: 4px;
}
```

<hr>

chrome developer tool:

- in border stylesheet (the square including border, margin and content), double click to modify the value.

<hr>

font-size:

- **100%** = 16px = 1em, percentage or em can make website dynamically sized. but font size can be inherited and added on top of its parent.
- recommendation: use rem(root em) when sizing font

---

CSS: Pseudo-classes and Pseudo-elements

When pseudo-classes are used, they should appear in this order: **:link, :visited, :hover, :focus, :active**.

---

HSL & HSLa Colors:

HSL color values are stated using the `hsl()` function, which stands for hue, saturation and lightness. Within the parentheses, the function accepts three comma-separated values, much like `rgb()`.

- Hue is a unitless number from 0 to 360. The numbers 0 through 360 represent the color wheel, and the value identifies **the degree of a color on the color wheel**.
- Saturation is a percentage value from 0 to 100%. The saturation value identifies how saturated with color the hue is, **with 0 being grayscale and 100% being fully saturated**.
- Lightness is a percentage value from 0 to 100%. It identifies how dark or light the hue value is, **with 0 being completely black and 100% being completely white**, **50% is the normal color**.

Please note that lightness is a different concept to _<u>brightness</u>_. Graphic design software (such as Photoshop and GIMP) have color pickers that use hue, saturation, and brightness — but brightness only adds black, whereas lightness offers both white and black.
