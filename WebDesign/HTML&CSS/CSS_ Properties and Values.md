# Properties and Values

[toc]

Once an element is selected, a *property* determines the styles that will be applied to that element, such as `color`, `font-size`.

```
p {
	color: orange;
}
```

<br>

## Colors

All color values within CSS are defined on an sRGB (or standard red, green, and blue) color space. Currently there are four primary ways to represent sRGB colors within CSS: keywords, hexadecimal notation, and RGB and HSL values.

### Keyword Colors

Keyword color values are names (such as red, green, or blue) that map to a given color. A complete list of these keyword names can be found within the CSS specification (http://www.w3.org/TR/css3-color/). 

### Hexadecimal Colors

Hexadecimal color values consist of a pound, or hash, #, followed by a three or six character figure. Adobe has created Adobe Kuler (https://color.adobe.com/create/color-wheel), a free application that provides a color wheel to help us find any color we want and its corresponding hexadecimal value.

Six-character hexadecimal values may be written as three-character hexadecimal values when the red, green, and blue color channels each contain a repeating character: #ff6600 = #f60.

### RGB & RGBa Colors

RGB color values may also include an alpha, or transparency, channel by using the `rgba()` function. The `rgba()` function requires a fourth value, which must be a number between 0 and 1, including decimals, and is used to adjust **opacity**. *<u>A value of 0 creates a fully transparent color, meaning it would be invisible, and a value of 1 creates a fully opaque color</u>*. 
For example, if we wanted our shade of orange to appear 50% opaque, we would use an RGBa color value of `rgba(255, 102, 0, .5)`.

### HSL & HSLa Colors

HSL color values are stated using the `hsl()` function, which stands for hue, saturation and lightness. Within the parentheses, the function accepts three comma-separated values, much like `rgb()`.
- Hue is a unitless number from 0 to 360. The numbers 0 through 360 represent the color wheel, and the value identifies **the degree of a color on the color wheel**.
- Saturation is a percentage value from 0 to 100%. The saturation value identifies how saturated with color the hue is, **with 0 being grayscale and 100% being fully saturated**.
- Lightness is a percentage value from 0 to 100%. It identifies how dark or light the hue value is, **with 0 being completely black and 100% being completely white**, **50% is the normal color**.
Please note that lightness is a different concept to *<u>brightness</u>*. Graphic design software (such as Photoshop and GIMP) have color pickers that use hue, saturation, and brightness — but brightness only adds black, whereas lightness offers both white and black.

HSL color values, like RGBa, may also include an alpha, or transparency, channel with the use of the `hsla()` function. 

<br>
<br>

## Lengths

### Absolute Length: pixels

The pixel is equal to 1/96th of an inch; thus there are 96 pixels in an inch. As an absolute unit of measurement, they don’t provide too much flexibility.

### Relative Length

#### Percentages

Percentages, represented by the % unit notation, are defined in relation to the length of another object. For example, to set the width of an element to 50%, we have to know the width of its parent element the element is nested within, and then identify 50% of the parent element’s width.

#### Em

The em unit is calculated based on an element’s font size. **A single em unit is equivalent to an element’s font size**. So, for example, if an element has a font size of 14 pixels and a width set to 5em, the width would equal 70 pixels. 

```
.banner {
 font-size: 14px;
 width: 5em;
 }
```

Relative article: [rem or em](https://zellwk.com/blog/rem-vs-em/)

When a font size is not explicitly stated for an element, the em unit will be relative to the font size of the closest parent element with a stated font size.

<br>
<hr>

## Referencing CSS

Our CSS file should be saved within the same folder, or a subfolder , where our HTML file is located. 
Within the `<head>` element of the HTML document, the `<link>` element is used to define the relationship between the HTML file and the CSS file. We use the `rel` attribute with a value of `stylesheet` to specify their relationship, the `href` attribute is used to identify the path of the CSS file.
```
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
    <link rel="stylesheet" href="assets/main.css">
  </head>
 ```

<br>
<hr>

## Using CSS Resets

Every web browser has its own default styles for different elements. To ensure cross-browser compatibility, CSS resets have become widely used. 
Head over to Eric’s website (http://meyerweb.com/eric/tools/css/reset/) to copy his reset, and paste it at the top of our CSS file.

Another choice:
Normalize.css (http://necolas.github.io/normalize.css/), which focuses not on using a hard reset for all common elements, but instead on setting common styles for these elements.