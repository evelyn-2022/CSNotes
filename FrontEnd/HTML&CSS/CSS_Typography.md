# CSS: Typography

## Changing Font Properties

### Font Family

Font names consisting of two or more words need to be wrapped in quotation marks. Additionally, **the last font should be a keyword value**, which will use the system default font for the specified type, most commonly either _sans-serif_ or _serif_.

```css
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

#### Embedding Web Fonts

We can also specify non-standard, custom web fonts for use on our website via the CSS **@font-face** at-rule. First, we use the **@font-face** at-rule to identify our font’s name, via the `font-family` property, as well as the source of our font (the path to the font file containing our chosen font), via the `src` property. From there we are able to use this font by including its name within any font-family property value.

```css
@font-face {
  font-family: "Lobster";
  src: local("Lobster"), url("lobster.woff") format("woff");
}
body {
  font-family: "Lobster", "Comic Sans", cursive;
}
```

If the `local()` function is provided, specifying a font name to look for on the user's computer, and the user agent finds a match, that local font is used. Otherwise, the font resource specified using the `url()` function is downloaded and used.
https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face

### Font Style

To change text to italics, or to prevent text from being italicized, we’ll use the `font-style` property. The `font-style` property accepts four keyword values: **_normal_**, **_italic_**, **_oblique_**, and **_inherit_** (Italic fonts were traditionally stylized versions of the font based on calligraphy, whereas an oblique version would take the normal version and put it on an angle).

### Font Variant

The `font-variant` property accepts three values: _normal_, _small-caps_, and _inherit_.

### Line Height

**Leading** (pronounced ledding) is a term typographers use for the vertical space between lines of text. In a typeface, the part of a letter that drops beneath the baseline is called a descender, while the highest point of a letter is called the ascender. **Leading is measured from the bottom of the descender on one line to the top of the ascender on the next.**
<img src="https://s2.loli.net/2021/12/17/FWTw5Kbltn9NkiA.png" >

In CSS, the `line-height` property sets the height of an entire line of text, so the
difference between the fontsize and the line-height is equivalent to the leading.
<img src="https://s2.loli.net/2021/12/17/35EN9ocpxI1JjDH.png" width='360'>

`line height` property declares the distance between two lines of text (often referred to as leading). The line-height property accepts all general length values.
The best practice for legibility is to set the line-height to around **one and a half times our font-size property value**. This could be quickly accomplished by setting the lineheight to 150%, or just 1.5 or 1.5em.

Line height may also be used to vertically center a single line of text within an element. **Using the same property value for the line-height and height properties will vertically center the text**:

```css
.btn {
  height: 22px;
  line-height: 22px;
}
```

This technique may be seen with buttons, alert messages, and other single-line text blocks.

<hr>

## Changing Text Properties

### Text Shadow

The `text-shadow` property allows us to add a shadow or multiple shadows to text. The property generally takes four values: **offset-x, offset-y, blur radius and color**.
The text-shadow property here is casting a 30% opaque black shadow 3 pixels towards the right, 6 pixels down, and blurred 2 pixels off all `<p>` element text:

```
 p {
 text-shadow: 3px 6px 2px rgba(0, 0, 0, .3);
 }
```

Using negative length values for the horizontal and vertical offsets allows us to move shadows toward the left and the top.
Multiple text shadows can also be chained together using comma-separated values, adding more than one shadow to the text.

#### Box Shadow

The `text-shadow` property places a shadow specifically on the text of an element. If we’d like to place a shadow on the element as a whole, we can use the `box-shadow` property.
The `box-shadow` property takes values for <u>**inset**, _offset-x_, _offset-y_, _blur-radius_, **spread-radius**, _color_</u>.
The **optional inset value at the beginning of the value** determines whether to place the shadow inside an element as opposed to outside the element.
The optional fourth length value, **spread-radius**, indicates the spread of a shadow. As a positive length value, the spread will expand the shadow larger than the size of the element it’s applied to, and as a negative length value the spread will shrink.

### Letter Spacing

**Kerning** is the term typographers use for the space between each letter. The `letter-spacing` property, we can adjust the space (or tracking) between the letters on a page. A positive length value will push letters farther apart from one another, while a negative length value will pull letters closer together. The keyword value _none_ will return the space between letters back to its normal size. Using a _<u>relative length value (em)</u>_ with the letter-spacing property will help ensure that we maintain the correct spacing between letters as the font-size of the text is changed.

The default gap between words is set by the typeface (often around 0.25em), and
it is unlikely that you would need to change this property regularly. <i><u>You may need to increase the kerning when your heading or sentence is all in uppercase.</u></i>

### Word Spacing

Much like the `letter-spacing` property, we can also adjust the space between words within an element using the `word-spacing` property.

<hr>

## Citations & Quotes

- `<cite>`: Used to reference a creative work, author, or resource, the element must include either the title of the work, the author’s name, or a URL reference to the work.
- `<q>`: Used for short, inline quotations, dialogue or prose. By default, the browser will insert the proper **quotation marks** for us and will even change the quotation marks based on the language identified within the lang global attribute.
- `<blockquote>`: Used for longer external quotations. The `<blockquote>` is a block-level element that may have other block-level elements nested inside it, including headings and paragraphs. It can have the attribute `cite` to designate a source url.
- Both `<q>` and `<blockquote>` can use `cite` attribute to indicate the URL the quotation is from.

<hr>

## Typeface Terminology

- Serif: Serif fonts have extra details on the ends of the main strokes of the letters. These details are known as serifs. In print, serif fonts were traditionally used for long passages of text because they were considered easier to read.
- Sans-Serif: Sans-serif fonts have straight ends to letters, and therefore have a much cleaner design. Screens have a lower resolution than print. So, if the text is small, sans-serif fonts can be clearer to read.
- Monospace: Every letter in a monospace (or fixed-width) font is the same width. (Non-monospace fonts have different widths.) Monospace fonts are commonly used for code because they align nicely, making the text easier to follow.
