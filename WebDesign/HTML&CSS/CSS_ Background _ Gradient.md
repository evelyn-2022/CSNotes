# CSS: Background & Gradient

[toc]

## Adding a Background Color

```
div {
 background-color: #b2b2b2;
 }
```

### Fallback Color

When using an RGBa or HSLa value as a transparent background color, it’s a good idea to provide a fallback color, too, because not all browsers recognize RGBa or HSLa values. 
We can use two background-color properties within a single rule set. **The first background-color property will use a “safe” background color**, such as a hexadecimal value, and the second background-color property will use an RGBa or HSLa value. Here, if a browser understands the RGBa or HSLa value it will render it, and if it doesn’t, it will fall back to the hexadecimal value above it.

```
div {
	background-color: #b2b2b2;
	background-color: rgba(0, 0, 0, .3);
}
```

<br>
<br>
<hr>

## Adding a Background Image

The `url()` function value will be the background image’s path:

```
div {
 background-image: url("alert.png");
 }
```

### Background Size

Possible values of background-size:
- auto - Renders the image at full size
- length - Sets the width and height of the background image. The first value sets the width, and the second value sets the height. If only one value is given, the second is set to auto.
- percentage - Sets the width and height of the background image in percent of the parent element. The first value sets the width, and the second value sets the height. If only one value is given, the second is set to auto. 

It also has 2 special values:
- ***contain***: It preserves the original aspect ratio of the image, but the image is resized so that it is fully visible. The longest of either the height or width will fit in the given dimensions, regardless of the size of the containing box.
- ***cover***: It preserves the original aspect ratio but resizes the image to cover the entire container, even if it has to upscale the image or crop it.

### Background Repeat

By default, a background image will repeat indefinitely, both vertically and horizontally, unless otherwise specified.

The background-repeat property accepts four different values:
- *repeat*: default value, repeat a background image both vertically and horizontally
- *repeat-x*: repeat the background image horizontally
- *repeat-y*: repeat the background image vertically
- *no-repeat*: display the background image only once

### Background Attachment

- fixed: The background image stays in the same position on the page.
- scroll: The background image moves up and down as the user scrolls up and down the page.

### Background Position

By default, background images are positioned at the **left top** corner of an element. 

The background-position property requires two values: a *<u>horizontal offset</u>* (from top) and a *<u>vertical offset</u>* (from left). If only one value is specified, that value is used for both the horizontal and the vertical offsets.

To set a background-position value, we can use the top, right, bottom, and left keywords, pixels, percentages, or any length measurement. Keywords and percentages work very similarly. The keyword value left top is identical to the percentage value 0 0, which will keep an image positioned at the left top corner of the element. The keyword value right bottom is identical to the percentage value 100% 100%, which will position an image in the right bottom corner of the element.

**One advantage of percentages over keywords is the ability to center a background image by using 50% as a value.**

### Shorthand Background Image Value

The **background-color**, **background-image**, **background-repeat**, **background-attachment**, **background-position**, and  properties may be rolled up into a shorthand value for the `background` property alone. 

```
 div {
 background: #b2b2b2 url("alert.png") 20px 10px no-repeat;
 }
```

### Using Multiple Background Images

we can use more than one background image on an element by comma-separating multiple background values within a background or background-image property.

```
. div {
 background:
 url("foreground.png") 0 0 no-repeat,
 url("middle-ground.png") 0 0 no-repeat,
 url("background.png") 0 0 no-repeat;
 }
```

### Image Rollovers and Sprites

To reduce the number of images your browser has to load, you can create image sprites. It is possible to create a link or button that changes to a second style when a user moves their mouse over it (known as a **rollover**) and a third style when they click on it. When a single image is used for several different parts of an interface, it is known as a **sprite**. This is achieved by setting a background image for the link or button that has three different styles of the same button (but only allows enough space to show one of them at a time).

<br>
<br>
<hr>



## Gradient Background

### Linear Gradient

Within CSS, gradient backgrounds are treated as background images. 
Linear gradients are identified by using the `linear-gradient() `function within the `background` or `background-image` property. The linear-gradient() function must include two color values, the beginning and the ending color value.

```
div {
 background: #466368;
 background: -webkit-linear-gradient(#648880, #293f50);
 background: -moz-linear-gradient(#648880, #293f50);
 background: linear-gradient(#648880, #293f50);
 }
```
==Note:== Gradient Background Vendor Prefixes

#### Changing the Direction of a Gradient Background

By default, linear gradient backgrounds move from the top to the bottom of an element. This direction may be changed with the use of keywords or a degree value stated before any color values.

```
background: linear-gradient(gradient_direction, color 1, color 2, color 3, ...);
```

About how to use keywords: http://meyerweb.com/eric/thoughts/2012/04/26/lineargradient-keywords/

### Radial Gradient Background

Radial gradients work from the inside to the outside of an element, using the `radial-gradient()` function. The first color identified within the radial-gradient() function will sit in the absolute center of the element, and the second color will sit on the outside of an element.

### Gradient Color Stops

We can add color stops to the given gradient function, with commas separating each color stop from the next. By default, the browser will position every color stop an equal distance from the next and will transition between them accordingly. If more control over how colors are positioned is desired, a location along the gradient can be declared as a length value and placed after the color value.
```
div {
 background: #648880;
 background: linear-gradient(to right, #f6f1d3, #648880 85%, #293f50);
 }
```


### Use Linear Gradient to Create a Striped Element

The `repeating-linear-gradient()` function is very similar to `linear-gradient()` with the major difference that it repeats the specified gradient pattern.

```
  .div{
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
<br>
<br>
<hr>

## Background Clip & Background Origin

The `background-clip` property specifies the surface area a background image will cover, and the `background-origin` property specifies where the background-position should originate. 

The introduction of these two new properties corresponds with the introduction of three new keyword values: `border-box`, `padding-box`, and `content-box`. Each of these three values may be used for the `background-clip` and `background-origin` properties.

```
div {
 background: url("shay.jpg") 0 0 no-repeat;
 background-clip: padding-box;
 background-origin: border-box;
 }
```

The `background-clip` property value is set to **border-box** by default, allowing a background image to extend into the same area as any border. Meanwhile, the `background-origin` property value is set to **padding-box** by default, allowing the beginning of a background image to extend into the padding of an element.

<br>
<br>
<hr>

## Multiple background

You can apply multiple backgrounds to elements. These are **layered atop one another with the first background you provide on top and the last background listed in the back**. Only the last background can include a background color.

```
.myclass {
  background: background1, background2, ..., backgroundN;
}
```