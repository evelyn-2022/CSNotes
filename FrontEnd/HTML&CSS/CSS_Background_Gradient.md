# CSS: Background & Gradient

### Background Size

Possible values of background-size:

- auto - Renders the image at full size
- length - Sets the width and height of the background image. The first value sets the width, and the second value sets the height. If only one value is given, the second is set to auto.
- percentage - Sets the width and height of the background image in percent of the parent element. The first value sets the width, and the second value sets the height. If only one value is given, the second is set to auto.

It also has 2 special values:

- **_contain_**: It preserves the original aspect ratio of the image, but the image is resized so that it is fully visible. The longest of either the height or width will fit in the given dimensions, regardless of the size of the containing box.
- **_cover_**: It preserves the original aspect ratio but resizes the image to cover the entire container, even if it has to upscale the image or crop it.

### Background Repeat

By default, a background image will repeat indefinitely, both vertically and horizontally, unless otherwise specified.

The background-repeat property accepts four different values:

- _repeat_: default value, repeat a background image both vertically and horizontally
- _repeat-x_: repeat the background image horizontally
- _repeat-y_: repeat the background image vertically
- _no-repeat_: display the background image only once

### Background Attachment

- fixed: The background image stays in the same position on the page.
- scroll: The background image moves up and down as the user scrolls up and down the page.

### Background Position

By default, background images are positioned at the **left top** corner of an element.

The background-position property requires two values: a _<u>horizontal offset</u>_ (from top) and a _<u>vertical offset</u>_ (from left). If only one value is specified, that value is used for both the horizontal and the vertical offsets.

To set a background-position value, we can use the top, right, bottom, and left keywords, pixels, percentages, or any length measurement. Keywords and percentages work very similarly. The keyword value left top is identical to the percentage value 0 0, which will keep an image positioned at the left top corner of the element. The keyword value right bottom is identical to the percentage value 100% 100%, which will position an image in the right bottom corner of the element.

**One advantage of percentages over keywords is the ability to center a background image by using 50% as a value.**

### Shorthand Background Image Value

The **background-color**, **background-image**, **background-repeat**, **background-attachment**, **background-position**, and properties may be rolled up into a shorthand value for the `background` property alone.

```css
div {
  background: #b2b2b2 url("alert.png") 20px 10px no-repeat;
}
```

## Gradient Background

### Linear Gradient

Within CSS, gradient backgrounds are treated as background images.
Linear gradients are identified by using the `linear-gradient() `function within the `background` or `background-image` property. The linear-gradient() function must include two color values, the beginning and the ending color value.

### Radial Gradient Background

Radial gradients work from the inside to the outside of an element, using the `radial-gradient()` function. The first color identified within the radial-gradient() function will sit in the absolute center of the element, and the second color will sit on the outside of an element.

### Gradient Color Stops

We can add color stops to the given gradient function, with commas separating each color stop from the next. By default, the browser will position every color stop an equal distance from the next and will transition between them accordingly. If more control over how colors are positioned is desired, a location along the gradient can be declared as a length value and placed after the color value.

```css
div {
  background: #648880;
  background: linear-gradient(to right, #f6f1d3, #648880 85%, #293f50);
}
```

### Use Linear Gradient to Create a Striped Element

The `repeating-linear-gradient()` function is very similar to `linear-gradient()` with the major difference that it repeats the specified gradient pattern.

```css
.div {
  background: repeating-linear-gradient(
    45deg,
    yellow 10px,
    red 40px,
    green 50px,
    cyan 80px
  );
}
```

How to adjust the position: https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/radial-gradient()

## Background Clip & Background Origin

The `background-clip` property specifies the surface area a background image will cover, and the `background-origin` property specifies where the background-position should originate.

The introduction of these two new properties corresponds with the introduction of three new keyword values: `border-box`, `padding-box`, and `content-box`. Each of these three values may be used for the `background-clip` and `background-origin` properties.

```css
div {
  background: url("shay.jpg") 0 0 no-repeat;
  background-clip: padding-box;
  background-origin: border-box;
}
```

The `background-clip` property value is set to **border-box** by default, allowing a background image to extend into the same area as any border. Meanwhile, the `background-origin` property value is set to **padding-box** by default, allowing the beginning of a background image to extend into the padding of an element.

## Multiple background

You can apply multiple backgrounds to elements. These are **layered atop one another with the first background you provide on top and the last background listed in the back**. Only the last background can include a background color.

```css
.myclass {
  background: background1, background2, ..., backgroundN;
}
```
