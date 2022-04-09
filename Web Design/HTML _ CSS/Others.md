- Use the `filter` property with the value `blur()` to make color and shape not so sharp: `filter: blur(2px);`

<hr>

- Give your img selector the `object-fit` property and set it to `cover`. This will tell the image to fill the img container while maintaining aspect ratio, resulting in cropping to fit.

<hr>

- Clicking on the navigation links should jump the viewport to the relevant section. However, this jumping can be disorienting for some users. Select all elements, and set the `scroll-behavior` to `smooth`.

<hr>

- The navigation accessibility can be improved with providing keyboard shortcuts. The accesskey attribute accepts a space-separated list of access keys. For example: `<button type="submit" accesskey="s">Submit</button>`

<hr>

- The `flex-end` setting has also brought your row's description text to the right of the element. To fix this, create a `.name` selector and give it a `width` property of 100%, and a `text-align` property of left.
Because you're using flex, this tells your `.name` elements to **take up 100% of the remaining available width,** **which allows the text to move to the left**.
```
<!-- html -->
<p class="row">
  <span class="name">Cash</span>
  <span>$25</span>
  <span>$30</span>
  <span class="current">$28</span>
</p>
```

```
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

- Create a `p[class~="total"]` selector to target all of your p elements where the class includes total (such as your .row total elements). This may seem the same as using the `.total` class selector. However, CSS is parsed top-down. Your `.row `selector comes after this new selector, and **would overwrite the `.total` selector**. Because `p[class~="total"]` has a higher selector specificity, it takes priority even though it comes earlier in the stylesheet.
```
<!-- html -->
<p class="row total">
  <span class="name">Total</span>
  <span>$579</span>
  <span>$736</span>
  <span class="current">$809</span>
</p>
```
```
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

- tabindex:
Arguably the most important part of a balance sheet is the totals. You want to be able to quickly cycle through the total values on your sheet. This can be achieved by using the `tabindex` attribute. Give each of your `.row total` elements a `tabindex` attribute set to 1.

<hr>

- favicon:

```
<link rel="favicon" href="favicon.ico?v=2">
```

add the "?v=2" because your browser might has cached the previous version

<hr>

- pesticide extension
press ctrl and hover over different elements, can show what element it is

<hr>

chrome developer tool
- select your interested part of the html page, click "inspect", and the element in the developer tool is highlighted.
- in border stylesheet (the square including border, margin and content), double click to modify the value.

<hr>

to center an element
- text-align center inside the container, or the parent element, will center everything inside that **doesn't have a width set**;

- if it is a block element and it has a width set, then you're going to have to center it using this **auto value in the margin**.

<hr>

font-size: **100%** = 16px = 1em, percentage or em can make website dynamically sized. but font size can be inherited and added on top of its parent.
recommendation: use rem(root em) when sizing font


