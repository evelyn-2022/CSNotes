# CSS: Box Model and Display Property

[toc]

## Display

There are quite a few values for the display property, but the most common are **block**,
**inline**, **inline-block**, and **none**.

To change an element’s display property: 

```
p {
  display: inline-block;
}
```

- **inline:** do NOT start on a new line and only takes up as much width as its content. ==*You can’t set the width or height*==. Also, ==*vertical margins, top and bottom*==, are not accepted by inline-level elements. ==*Vertical padding*== property works on inline-level elements. This vertical padding may blend into the line above or below the given element, but it will be displayed.
 Here are a few elements that have a default inline property: `<span>`, `<a>`, `<img>`, and most of the formatting tags are also inherently inline: `<em>`, `<strong>`,`<small>`.
- **inline-block:** it’s formatted just like the inline element, where it doesn’t start on a new line. BUT, you can set width and height values.
- **block:** the element will start on a new line and occupy the full width available. And you can set width and height values.
 Here are a few elements that have a default block property: `<div>`, `<h1>`, `<p>`, `<li>`, `<section>`.
- **none:** hide an element and render the page as if that element doesn’t exist. Any elements nested within this element will also be hidden. The `<script>` element uses `display: none;` as default.
 `visibility: hidden` also hides an element. However, the element will **still take up the same space as before**. The element will be hidden, but still affect the layout.

<br>
<br>
<hr>

## Box Model

All HTML elements can be considered as rectangular boxes. The CSS box model consists of: margins, borders, padding, and the actual content. 
<img src="https://s2.loli.net/2021/12/09/SAqtmTu2EevUoXQ.jpg" alt="box_model.jpg" width=40%>
- **Content:** the content of the box, where text and images appear.
- **Padding:** clears an area around the content. The padding is transparent.
- **Border:** a border that goes around the padding and content.
- **Margin:** clears an area outside the border. The margin is transparent.

==Note:== when you set the width and height properties of an element with CSS, you just set the content area. To calculate the full size of an element, you must also add padding, borders and margins.
Example: the total width of the element is 320 + 10 * 2 + 5 * 2 + 0 * 2 = 350 px.
```
div {
  width: 320px;
  padding: 10px;
  border: 5px solid gray;
  margin: 0;
}
```

<br>

### Height / Width

The default width of an element depends on its display value. Block-level elements have a default width of 100%, consuming the entire horizontal space available. Inline and inline-block elements expand and contract horizontally to accommodate their content.

The height and width properties may have the following values:
- auto: This is default. The browser calculates the height and width.
- length: Defines the height/width in px, cm etc.
- %: Defines the height/width in percent of the containing block.
- initial: Sets the height/width to its default value.
- inherit: The height/width will be inherited from its parent value.

#### Setting max-width / max-height / min-width / min-height
```
div {
	max-width: 500px;
}
```

<br>

### Margin

All the margin property can have the following values: 
- ==*auto*:== 
	set the margin property to *auto* to **horizontally center** the element within its container
- *inherit:*
	```
	<style>
  	div {
    border: 1px solid red;
    margin-left: 100px;
  }

  p.ex1 {
    margin-left: inherit;
  }
	</style>

	<div>
 	 <p class="ex1">this paragraph has an inherited left margin from the div element</p>
	</div>
	```
- *length:* 
	- Shorthand: specify all the margin properties in one property
		- If the margin property has four values: 
			```
			margin: 25px 50px 75px 100px;
			```
			top margin 25px, right margin 50px, bottom margin 75px, left margin 100px
		- If the margin property has three values: 
			```
			margin: 25px 50px 75px;
			```
			top margin 25px, right and left margin 50px, bottom margin 75px
		- If the margin property has two values: 
			```
			margin: 25px 50px;
			```
			top and bottom margins 25px, left and right margins 50px
		- If the margin has one value: 
			```
			margin: 25px;
			```
			all four margins are 25px
	- Longhand: set the value for one side at a time using unique properties
		```
		margin-top: 10px;
		```
- *%:* 
	specify a margin in % of the width of the containing element
			
#### Margin Collapse

If the bottom margin of any box touches the top margin of another, the browser will render it differently than you might expect. It will only show the larger of the two margins. If both margins are the same size, it will only show one. (https://stackoverflow.com/questions/19718634/how-to-disable-margin-collapsing#:~:text=%20There%20are%20two%20main%20types%20of%20margin,margins%20between%20parent%20and%20child%20elements%20More%20)

#### Negative Value

If you set an element's margin to a **negative value**, the element will grow larger.

==Note:==
**The value of border, margin and padding property is not inherited by child elements** in the same way that the color value of the font-family property is; so you need to specify the padding for every element that needs to use it.

<br>

### Padding

All padding property can have the properties of margins except *auto*.


<br>

### Borders

The border property requires three values: ***width, style, and color***. Shorthand values for the border property are stated in that order. In longhand, these three values can be broken up into the border-width, border-style, and border-color properties.

#### Border Styles

The `border-style` property specifies what kind of border to display:
- *dotted*
- *dashed*
- *solid*
- *double*
- *groove*: defines a 3D grooved border. The effect depends on the border-color value
- *ridge*: defines a 3D ridged border. The effect depends on the border-color value
- *inset*: defines a 3D inset border. The effect depends on the border-color value
- *outset*: defines a 3D outset border. The effect depends on the border-color value
- *none*: defines no border
- *hidden*: defines a hidden border

The border-style property can have from one to four values (for the top, right, bottom and left border)

```
p.mix {border-style: dotted dashed solid double;}
```
![mixed_border.jpg](https://s2.loli.net/2021/12/10/SCkwGdHWTiuYAse.jpg)

==Note:== NONE of the OTHER CSS border properties will have ANY effect unless the `border-style` property is set!

#### Border Width

The `border-width` can be set as a specific size (in px, cm, em, etc) or by using one of the three pre-defined values: *thin, medium, or thick*. The `border-width` property can have from one to four values. (==Note:== You cannot use percentages with this property.)
You can control the individual size of borders using four
separate properties: **border-top-width, border-right-width, border-bottom-width, border-left-width**. You can also specify different widths for the four border values in one property, like so:
`border-width: 2px 1px 1px 2px;`.

#### Border Color

The `border-color` property can be set by keyword colors, HEX, RGB, HSL or transparent. If `border-color` is not set, it inherits the color of the element.

#### Border Image

The `border-image` CSS property draws an image around a given element. It replaces the element's regular border. **You need to specify `border-width` and `border-style` first for the border image to be rendered**. This property is a shorthand for the following CSS properties:
1. `border-image-source`
2. `border-image-slice`: divides the image specified by border-image-source into nine regions. It may be specified as one, two, three, or four values. When four values are specified, they create slices measured from the top, right, bottom, and left in that order (clockwise).
	<img src="https://s2.loli.net/2021/12/17/oHTkC6WBxf7d5y9.png" >
	- Zones 1-4 are <i><u>corner regions</u></i>. Each one is used **a single time** to form the corners of the final border image.
	- Zones 5-8 are <i><u>edge regions</u></i>. These are **repeated, scaled, or otherwise modified** in the final border image to match the dimensions of the element.
	- Zone 9 is the middle region. It is discarded by default, but is used like a background image if the keyword **fill** is set.
3. `border-image-width`: sets the width of an element's border image. It may be specified as one, two, three, or four values.
4.  `border-image-outset`: sets the distance by which an element's border image is set out from its border box. It may be specified as one, two, three, or four values.
5.  `border-image-repeat`: defines how the <u><i>edge regions</i></u> of a source image are adjusted to fit the dimensions of an element's border image. It may be specified using *one or two* values.
	- stretch: The source image's edge regions are stretched to fill the gap between each border.
	- repeat: The source image's edge regions are tiled (repeated) to fill the gap between each border. Tiles may be clipped to achieve the proper fit.
	- round: The source image's edge regions are tiled (repeated) to fill the gap between each border. Tiles may be stretched to achieve the proper fit.
	- space: The source image's edge regions are tiled (repeated) to fill the gap between each border. Extra space will be distributed in between tiles to achieve the proper fit.

Example: 
Use the followingi image (81px &times;81px) as border image:
<img src="https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png" >
```
<style type="text/css">
  p.one {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: solid;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 
				  27 27 27 27 stretch;}
  p.two {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: dotted;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 
				  27 27 27 27 round;}
  p.three {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: double;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 
			      27 27 27 27 space;}
</style>

<p class="one"></p>
<p class="two"></p>
<p class="three"></p>
```

<style type="text/css">
  p.one {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: solid;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 27 27 27 27 stretch;}
  p.two {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: dotted;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 27 27 27 27 round;}
  p.three {
    display: inline-block;
    width: 100px;
    height: 50px;
    border-width: 10px;
    border-style: double;
    border-image: url("https://s2.loli.net/2021/12/17/YVIxGCF8DZ6LKmu.png") 27 27 27 27 space;}
</style>

<p class="one"></p>
<p class="two"></p>
<p class="three"></p>

#### Border Radius

A single value will round all four corners of an element equally; two values will round the *top-left/bottom-right* and *top-right/bottom-left* corners in that order; four values will round the *top-left*, *top-right*, *bottom-right*, and *bottom-left* corners in that order.
The `border-radius` property may also be broken out into longhand properties that allow us to change the radii of individual corners of an element. These longhand properties begin with border, continue with the corner’s vertical location (top or bottom) and the corner’s horizontal location (left or right), and then end with radius.
```
 div {
 border-top-right-radius: 5px;
 }
```

##### Elliptical Shapes
To create more complex shapes, you can specify different distances for the horizontal and the vertical parts of the rounded corners.
Example: 
```
border-top-right-radius: 80px 50px;
```
<img src="https://s2.loli.net/2021/12/17/Cjfdg3OZRPaL97B.png" width=250 >

There is also a shorthand for targetting all four corners at once; first you specify the four horizontal values, then the four vertical values.

```
<style type="text/css">
  p.rad{
    border: 10px solid pink;
    width: 100px;
    height: 50px;
    border-radius: 1em 4em 1em 4em / 2em 1em 2em 1em;
</style>

<p class="rad"></p>
```

<style type="text/css">
  p.rad{
    border: 10px solid pink;
    width: 100px;
    height: 50px;
    border-radius: 1em 4em 1em 4em / 2em 1em 2em 1em;
</style>

<p class="rad"></p>


<br>

### Boxing Sizing

The CSS `box-sizing` property allows us to include the padding and border in an element's total width and height.

#### Content Box

The content-box value is the default value, leaving the box model as an additive design. 

#### Border Box

 The `border-box` value alters the box model so that any **border or padding** property values are included within the *width* and *height* of an element.
 For example, to keep the width at 300px, no matter the amount of padding, you can use the `box-sizing` property. This causes the element to maintain its width; if you increase the padding, the available content space will decrease: 
```
div {
	width: 300px;
	padding: 25px;
	box-sizing: border-box;
}
```
 
 #### Padding Box
 
The `padding-box` value alters the box model by including any **padding** property values within the *width* and *height* of an element. 


#### Browser Compatibility

As CSS3 was introduced, browsers gradually began to support different properties and values, including the box-sizing property, by way of vendor prefixes. As time goes on, vendor prefixes are unlikely to be a problem; however, they still provide support for some of the older browsers that leveraged them.
```
. div {
	-webkit-box-sizing: content-box;
	-ms-box-sizing: content-box;
	-moz-box-sizing: content-box;
 }
```

For reference, the most common vendor prefixes are outlined here:
- Mozilla Firefox: -moz-
- Microsoft Internet Explorer: -ms-
- Webkit (Google Chrome and Apple Safari): -webkit-

More about browser compatibility:
https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing?redirectlocale=en-US&redirectslug=CSS%2Fbox-sizing

<br>
<br>
<hr>

## Developer Tool

Most browsers have what are known as *Developer Tools*. These tools allow us to inspect an element on a page, see where that element lives within the HTML document, and see what CSS properties and values are being applied to it.
![developer_tool.png](https://s2.loli.net/2021/12/10/VHNAxLp7YUu8hi1.png)

### Web Developer Toolbar
Download this tool from: www.chrispederick.com/work/web-developer

