# HTML: Lists

[toc]

## Three Types of Lists

### Unordered List

By default, most browsers add a **vertical margin and left padding** to the `<ul>` element and precede each `<li>` element with a **solid dot**. This solid dot is called the **list item** marker, and it can be changed using CSS.

```
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

### Ordered List

```
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

Ordered lists have unique attributes available to them including `start` and `reversed`.

#### Start Attribute

The `start` attribute defines the number from which an ordered list should start. By default, ordered lists start at 1. The `start` attribute accepts **only integer values**, even though ordered lists may use different numbering systems, such as roman numerals.
```
<ol start="30">
```

#### Reversed Attribute

The reversed attribute, when used on the `<ol>` element, allows a list to appear in reverse order. 

```
<ol reversed>
```

#### Value Attribute

The value attribute may be used on an individual `<li>` element within an ordered list to change its value within the list. The number of any list item appearing below a list item with a value attribute will be recalculated accordingly.

```
<ol>
 <li>Head north on N Halsted St</li>
 <li value="9">Turn right on W Diversey Pkwy</li>
 <li>Turn left on N Orchard St</li>
</ol>
```

<ol>
 <li>Head north on N Halsted St</li>
 <li value="9">Turn right on W Diversey Pkwy</li>
 <li>Turn left on N Orchard St</li>
</ol>

### Description List

 Description lists are used to outline multiple terms and their descriptions, as in a glossary, for example.

Creating a description list in HTML is accomplished using the description list block-level element, `<dl>`. Instead of using a `<li>` element to mark up list items, the description list requires two block-level elements: the description term element, `<dt>`, and the description element, `<dd>`.

```
<dl>
	<dt>study</dt>
	<dd>The devotion of time and attention to acquiring knowledge on an academic subject, especially by means of books</dd>
	<dt>design</dt>
	<dd>A plan or drawing produced to show the look</dd>
	<dd>Purpose, planning, or intention that existsbehind an action, fact, or material object</dd>
	<dt>business</dt>
	<dt>work</dt>
	<dd>A person's regular occupation, profession, or trade</dd>
</dl>
```

<dl>
 <dt>study</dt>
 <dd>The devotion of time and attention to acquiring knowledge on an academic subject, especially by means of books</dd>
 <dt>design</dt>
 <dd>A plan or drawing produced to show the look</dd>
 <dd>Purpose, planning, or intention that existsbehind an action, fact, or material object</dd>
 <dt>business</dt>
 <dt>work</dt>
 <dd>A person's regular occupation, profession, or trade</dd>
</dl>

<br>
<br>
<hr>

## Nesting Lists

The only element we can place as a direct child of the `<ul>` and `<ol>` elements is the `<li>` element.  Once inside the `<li>` element, the standard set of elements may be added, including any `<ul>` or `<ol>` elements. 

```
<ol>
  <li>Walk the dog</li>
  <li>Fold laundry</li>
  <li>Go the grocery and buy:
    <ul>
      <li>Milk</li>
      <li>Bread</li>
      <li>Cheese</li>
    </ul>
  </li>
  <li>Mow the lawn</li>
  <li>Make dinner</li>
</ol>
```

<ol>
  <li>Walk the dog</li>
  <li>Fold laundry</li>
  <li>Go the grocery and buy:
    <ul>
      <li>Milk</li>
      <li>Bread</li>
      <li>Cheese</li>
    </ul>
  </li>
  <li>Mow the lawn</li>
  <li>Make dinner</li>
</ol>
<br>
<br>
<hr>

## List Item Styling

### List Style Type Property

The `list-style-type` property is used to set the content of a list item marker. 

```
HTML 
<ul>
	<li>Orange</li>
	<li>Green</li>
</ul>

CSS 
ul {
	list-style-type: square;
}
```

#### List Style Type Values

|LIST STYLE TYPE VALUE|CONTENT|
|---------------------|-------|
|none|No list item|
|disc|A filled circle|
|circle|A hollow circle|
|square|A filled square|
|decimal|Decimal numbers|
|decimal-leading-zero|Decimal numbers padded by initial zeros|
|lower-roman|Lowercase roman numerals|
|upper-roman|Uppercase roman numerals|
|lower-greek|Lowercase classical Greek|
|lower-alpha / lower-latin|Lowercase ASCII letters|
|upper-alpha / upper-latin|Uppercase ASCII letters|
|armenian|Traditional Armenian numbering|
|georgian|Traditional Georgian numbering|

### Using an Image as a List Item Marker

The process includes removing any default `list-style-type` property value and adding a background image (url or linear-gradient) to the `<li>` element. Because this property is inherited, it can be set on the parent element (normally `<ol>` or `<ul>`) to let it apply to all list items. 
```
<style type="text/css">
  ul.first {
      list-style-image: linear-gradient(to left bottom, red, blue);}
</style>

<ul class="first">
    <li>Orange</li>
    <li>Green</li>
</ul>
```

<style type="text/css">
  ul.first {
      list-style-image: linear-gradient(to left bottom, red, blue);}
</style>

<ul class="first">
    <li>Orange</li>
    <li>Green</li>
</ul>


### List Style Position Property

The `list-style-position` property takes the following values:
- *outside:* default value. All of the content will appear directly to the right, outside of the list item marker.
- *inside:* places the list item marker in line with the first line of the `<li>` element and allows other content to wrap below it as needed.
<img src="https://s2.loli.net/2021/12/11/6fMQEATYuIcy7rG.png" width=450px>
- *inherit*

### Shorthand List Style Property

Shorthand `list-style` property value include the markers' style, image and position properties in any order.

```
ul {
	list-style: circle inside;
	}
```

<br>
<br>
<hr>

## Horizontally Displaying List

### Displaying List

The quickest way to display a list on a single line is to give the `<li>` elements a `display` property value of `inline` or `inline-block`.

More often than not, we’ll use the `inline-block` property value rather than the inline property value because it allows us to easily add vertical margins and other spacing to the `<li>` elements.

When changing the display property value to inline or inline-block, the list item marker, be it a bullet, number, or other style, is removed.

### Floating List

Changing the display property value to inline or inline-block is quick; however, it removes the list item marker. If the list item marker is needed, floating each `<li>` element is a better option than changing the display property.

Setting all `<li>` elements’ float property to left will horizontally align all `<li>` elements directly next to each other without any space between them. When we float each `<li>` element, the list item marker is displayed by default and will actually sit on top of the `<li>` element next to it. To prevent the list item marker from being displayed on top of other `<li>` elements, a horizontal margin or padding should be added.

```
HTML
<ul>
	<li>Orange</li>
	<li>Green</li>
</ul>

CSS
li {
  float: left;
  margin: 0 20px;
}
```

With and without margin: 
<img src="https://s2.loli.net/2021/12/11/pJgfya2xiUeWkmP.png" width=200>





