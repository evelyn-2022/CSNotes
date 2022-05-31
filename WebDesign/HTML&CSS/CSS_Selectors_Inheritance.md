# CSS: Selectors & Inheritance

[toc]

A *selector* designates exactly which element within our HTML to target and apply styles. Selectors generally target an attribute value, such as an `id` or `class` value, or target the type of element,  Selectors are followed with curly brackets, `{}`.

<br>


## Type Selectors

*Type* selectors target elements by their element type, such as `<h1>` or `<p>`.

## Class Selectors

Class selsctors are a little more specific than type selectors, as they select a particular group of elements rather than all elements of one type.

```
	<style>
	  .blue-text {
		color: blue;
	  }
	</style>
```

You can see that we've created a CSS class called `blue-text` within the `<style>` tag. You can apply a class to an HTML element like this: 
```
	<h2 class="blue-text">CatPhotoApp</h2>
```
Note that in your *CSS* style element, **class names start with a period**. In your *HTML* elements' class attribute, the class name **does not include the period**.

## Id Selectors

*id* selectors are even more precise than class selectors, as they target **only one element** at a time, id attribute values can only be used **once per page**.

An `id` has a higher specificity (importance) than a `class`** so if both are applied to the same element and have conflicting styles, <u>*the styles of the `id` will be applied*</u>.

```
<style>
	#cat-photo-element {
	background-color: green;
	}
</style>

<div id="cat-photo-element>...</div>"

```
Note that inside your style element, you always reference classes by putting a `.` in front of their names. You always reference ids by putting a `#` in front of their names.

## Universal Selector

The CSS universal selector (`*`) matches elements of any type.
```
/* Selects all elements */
* {
  color: green;
}
```
https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors

## Child Selector

Matches an element that is a direct child of another:

```
li>a {}
```

Targets any `<a>` elements that are children of an `<li>` element (but not other `<a>` elements in the page).

## Descendant Selector

Matches an element that is a descendent of another specified element (<u><i>not just a direct child</i></u> of that element):

```
p a {}
```

Targets any `<a>` elements that sit inside a `<p>` element, even if there are other elements nested between them.

## Adjacent Sibling Selector

Matches an element that is the next sibling of another:

```
h1+p {}
```

Targets the first `<p>` element after any `<h1>` element (but not other `<p>` elements).

## General Sibling Selector

Matches an element that is a sibling of another, although it does not have to be the directly preceding element:

```
h1~p {}
```

If you had two `<p>` elements that are siblings of an `<h1>` element, this rule would apply to both.

## `Attribute` Selectors

### Existence `[]`

Matches a specific attribute (whatever its value):

```
p[class]
```

Targets any `<p>` element with an attribute called class.

### Equality `[=]`

```
p[class="dog"]
```
Targets any `<p>` element with an attribute called class whose value is dog.
```
[type='radio'] {
  margin: 20px 0px 20px 0px;
}
```
Changes the margins of all elements with the attribute `type` and a corresponding value of radio.

### Space `[~=]`

Matches a specific attribute whose value appears in a space-separated list of words.

```
p[class~="dog"]
```
Targets any `<p>` element with an attribute called class whose value is a list of space-separated words, one of which is dog.

### Prefix `[^=]`

Matches a specific attribute whose value begins with a specific string.

```
p[attr^"d"]
```
Targets any `<p>` element with an attribute whose value begins with the letter "d".

### Substring `[*=]`

Matches a specific attribute whose value contains a specific substring.

```
p[attr*"do"]
```

Targets any `<p>` element with an attribute whose value contains the letter "do".

### Suffix `[$=]`

Matches a specific attribute whose value ends with a specific string.

```
p[attr$"g"]
```

Targets any `<p>` element with an attribute whose value ends with the letter "g".

<br>
<br>
<hr>

## Prioritize One Style Over Another

### Overriding

####  Last Rule

It **doesn't matter which order the classes are listed in the HTML element**. However, *the order of the class declarations in the `<style>` section is what is important*. Browsers read CSS from top to bottom in order of their declaration. That means that, in the event of a conflict, the browser will **use whichever CSS declaration came last**. Because .blue-text is declared second, it overrides the attributes of .pink-text. 
```
<style>
  .pink-text {
    color: pink;
  }
	
  .blue-text {
    color: blue;
  }
</style>

<p class="blue-text pink-text">blue</p>
```



#### ID Override Class
`id` declarations override class declarations, **regardless of where they are declared in your style element CSS**.
```
<style>
  #orange-text {
    color: orange;
  }

  .blue-text {
    color: blue;
  }
</style>

<p class="blue-text" id="orange-text">orange</p>
```

#### Override Class Declarations with Inline Styles

Inline styles will override all the CSS declarations in your style element.

```
<style>
  #orange-text {
    color: orange;
</style>

<p id="orange-text" style="color: yellow;">yellow</p>
```

#### Override All Other Styles by using Important

In many situations, you will use CSS libraries. These may accidentally override your own CSS. So when you absolutely need to be sure that an element has specific CSS, you can use `!important`.

```
color: red !important;
```

<br>
<br>

### Calculating Specificity

The `type` selector has the lowest specificity weight and holds a point value of *0-0-1*. The `class` selector has a medium specificity weight and holds a point value of *0-1-0*. Lastly, the `id` selector has a high specificity weight and holds a point value of *1-0-0*. As we can see, specificity points are calculated using three columns. 

```
HTML
<div class="hotdog">
	 <p>...</p>
	 <p>...</p>
	 <p class="mustard">...</p>
</div>

CSS 
.hotdog p {
background: brown;
}
.hotdog p.mustard {
background: yellow;
}
```
The selector farthest to the right, directly before the opening curly bracket, is known as the **key selector**. Reading the combined selector from right to left, it is targeting paragraphs with a class attribute value of mustard that reside within an element with the class attribute value of hotdog.

The first selector, `.hotdog p`, had both a class selector and a type selector. The total combined point value would be *0-1-1*. The second selector, `.hotdog p.mustard`, had two class selectors and one type selector. Combined, the selector has a specificity point value of *0-2-1*. Comparing the two selectors, the second selector, with its two classes, has a noticeably higher specificity weight and point value.

<br>
<br>

### Layering Styles with Multiple Classes

One way to keep the specificity weights of our selectors low is to be as modular as possible, sharing similar styles from element to element. Elements within HTML can have **more than one class attribute value** so long as each value is space separated. We can tie styles we want to continually reuse to one class and layer on additional styles from another class.

```
HTML
 <a class="btn btn-danger">...</a>

 <a class="btn btn-success">...</a>

CSS
 .btn {
 font-size: 16px;
 }
 .btn-danger {
 background: red;
 }
 .btn-success {
 background: green;
 }
```

<br>
<br>
<hr>

## Inheritance

If you specify the font-family or color properties on the `<body>` element, they will apply to most child elements. This is because the value of the font-family property is inherited by child elements. It saves you from having to apply these properties to as many elements (and results in simpler style sheets).

You can compare this with the background-color or border properties; <i><u>they are not inherited by child elements</u></i>. If these were inherited by all child elements then the page could look quite messy.

You can force a lot of properties to inherit values from their parent elements by using **inherit** for the value of the properties. In this example, the `<div>` element with a class called page inherits the padding size from the CSS rule that applies to the `<body>` element.

```
body {
	font-family: Arial, Verdana, sans-serif;
	color: #665544;
	padding: 10px;
	}
.page {
	border: 1px solid #665544;
	background-color: #efefef;
	padding: inherit;
	}
```