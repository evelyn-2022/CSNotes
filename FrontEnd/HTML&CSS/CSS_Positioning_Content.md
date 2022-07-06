# CSS: Positioning Content

## Position Property

The `position` property specifies the type of positioning method used for an element (**_static, relative, fixed, absolute, sticky_**).

<br>

### Static

HTML elements are positioned static by default. An element with `position: static;` is always positioned according to the normal flow of the page.

### Relative

An element with `position: relative;` is positioned relative to its original position. It still <u><em>appears within the normal flow a page</em></u> and other content will not be adjusted to fit any gap left by the element.
The following example moves the paragraph 10 pixels up (away from the bottom):

```
p {
  position: relative;
  bottom: 10px;
}
```

### Absolute

An element with `position: absolute;` is positioned **in relation to its containing element**. Should a relatively positioned parent element not exist, the absolutely positioned element will be positioned in relation to the `<body>` element, and moves along with page scrolling. The element is <u><em>removed from the normal flow of a page</em></u>.

### Fixed

An element with `position: fixed;` is locked **relative to the browser window**, which means it always stays in the same place even if the page is scrolled. The element is <u><em>removed from the normal flow of a page</em></u>.

### Sticky

An element with `position: sticky;` is positioned based on the user's scroll position. A sticky element toggles between `relative` and `fixed`, depending on the scroll position.
https://www.w3schools.com/css/tryit.asp?filename=trycss_position_sticky

<hr>

## Float Property

The `position` property push an element to either the `left` or `right` of its containing parent element. All other elements on the page will then wrap around the floated element. As the width of the element will default to the width of its content, it's commonly used with the `width` property to specify how much horizontal space the floated element requires. The element is <u><em>removed from the normal flow of a page</em></u>.

The `float` property can have one of the following values:

- left: the element floats to the left of its container
- right: the element floats to the right of its container
- none: default. The element will be displayed just where it occurs in the text
- inherit: the element inherits the float value of its parent

> ==Note: Floats May Change an Element’s Display Value==
> When floating an element, the float property relies on an element having a **display value of block**. When an inline element is floated, the display value will be changed to block, and can then accept height or width property values.

### Clear and Clearfix

#### Clear

To prevent content from wrapping around floated elements, we need to clear, or contain, those floats and return the page to its normal flow. The clear property specifies what elements can float beside the cleared element and on which side. The most commonly used values are left, right, both and inherit. For example, `clear: left;` means that no floating elements are allowed on the left side.

#### Clearfix

If an element is taller than the element containing it, and it is floated, it will overflow outside of its container. Use `overflow: auto;` or `overflow: hidden` or the following code to fix it.

```
.clearfix:before,
.clearfix:after {
	content: "";
	display: table;
}
.clearfix:after {
	clear: both;
}
.clearfix {
	clear: both;
	*zoom: 1;
}
```

https://www.w3schools.com/howto/howto_css_clearfix.asp
https://pageaffairs.com/notebook/containing-floats/

## Positioning with Inline-Block

Using inline-block elements allows us to take full advantage of the box model without having to worry about clearing any floats.
The problem is that because inline-block elements are displayed on the same line as one another, they include a single space between them.

<img src="https://s2.loli.net/2021/12/10/MrUXaLw3o94sR2C.png" width=400>

### Removing Spaces Between Inline-Block Elements

The first solution is to **put each new `<section>` element’s opening tag on the same line as the previous `<section>` element’s closing tag**. Rather than using a new line for each element, we’ll end and begin elements on the same line. Our HTML could look like this:

```
<header>...</header>
<section>
 ...
 </section><section>
 ...
</section><section>
 ...
</section>
<footer>...</footer>
```

<img src="https://s2.loli.net/2021/12/10/Qn9C3pwgbjy52HR.png" width=400>

Another way to remove the white space between inline-block elements is to open an HTML comment directly after an inline-block element’s closing tag. Then, close the HTML comment immediately before the next inline-block element’s opening tag. Doing this allows inline-block elements to begin and end on separate lines of HTML and “comments out” any potential spaces between the elements. The resulting code would look like this:

```
<header>...</header>
<section>
 ...
</section><!--
--><section>
 ...
</section><!--
--><section>
 ...
</section>
<footer>...</footer>
```

<hr>

## Multiple Style Sheets

### @import

Your HTML page can link to one style sheet and that stylesheet can use the `@import` rule to import other style sheets. (If a styesheet uses the @import rule, it should appear before the other rules)

### link

In the HTML you can use a separate `<link>` element for each style sheet. As with all style sheets, if two rules apply to the same element then rules that appear later in a document will take precedence over previous rules.
