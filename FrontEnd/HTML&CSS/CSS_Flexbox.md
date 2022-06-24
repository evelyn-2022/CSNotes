23/12/2021 22:50# CSS Flexbox

[toc]

This section uses alternating challenge styles to show how to use CSS to **position elements in a flexible way**. 

Placing the CSS property `display: flex;` on an element allows you to use other flex properties to build a responsive page.

<br>

---

## Properties for flex container (the parent of the flex items)

### `flex-direction` Property

Adding `display: flex` to an element turns it into a flex container. This makes it possible to **align any children of that element into rows or columns**. You do this by adding the `flex-direction` property to the parent item and setting it to `row` or `column`. Creating a row will align the children horizontally, and creating a column will align the children vertically. Other options for flex-direction are `row-reverse` and `column-reverse`.

Note: The **default value** for the flex-direction property is **row**.

```
  #box-container {
    display: flex;
    height: 500px;
    flex-direction: row-reverse;
  }
 ```
 
[flex-direction property](https://codepen.io/ZoeyClyde/pen/RwLaJQe)

<br>

---

### `justify-content` Property

The `justify-content` property has several options to tell CSS how to align and space out the flex items a certain way. 

Recall that setting a flex container as a row places the flex items side-by-side from left-to-right. A flex container set as a column places the flex items in a vertical stack from top-to-bottom. For each, the direction the flex items are arranged is called the **main axis**. For a *row*, this is a *horizontal line* that cuts through each item. And for a *column*, the main axis is a *vertical line* through the items.

There are several options for how to space the flex items along the line that is the main axis.
-  `center`: aligns all the flex items to the center inside the flex container. 
- `flex-start`: aligns items to the start of the flex container. For a row, this pushes the items to the left of the container. For a column, this pushes the items to the top of the container. This is the **default alignment** if no justify-content is specified.
- `flex-end`: aligns items to the end of the flex container. For a row, this pushes the items to the right of the container. For a column, this pushes the items to the bottom of the container.
- `space-between`: aligns items to the center of the main axis, with extra space placed between the items. *<u>The first and last items are pushed to the very edge*</u> of the flex container. For example, in a row the first item is against the left side of the container, the last item is against the right side of the container, then the remaining space is distributed evenly among the other items.
- `space-around`: similar to `space-between` but the first and last items are not locked to the edges of the container, the space is distributed around all the items with a half space on either end of the flex container.
- `space-evenly`: distributes space evenly between the flex items with a full space at either end of the flex container.

<br>

---

### `align-items` Property

Flex containers also have a **cross axis** which is *<u>the opposite of the main axis</u>*. For rows, the cross axis is vertical and for columns, the cross axis is horizontal.
<img src="https://www.w3.org/TR/css-flexbox-1/images/flex-direction-terms.svg" style="background-color: white"/>
CSS offers the `align-items` property to align flex items along the cross axis. For a row, it tells CSS how to push the items in the entire row up or down within the container. And for a column, how to push all the items left or right within the container.

The different values available for `align-items` include:

- `flex-start`: aligns items to the start of the flex container. For rows, this aligns items to the top of the container. For columns, this aligns items to the left of the container.
- `flex-end`: aligns items to the end of the flex container. For rows, this aligns items to the bottom of the container. For columns, this aligns items to the right of the container.
- `center`: align items to the center. For rows, this vertically aligns items (equal space above and below the items). For columns, this horizontally aligns them (equal space to the left and right of the items).
- `stretch`: stretch the items to fill the flex container. For example, rows items are stretched to fill the flex container top-to-bottom. This is the **default value** if no align-items value is specified.
- `baseline`: align items to their baselines. Baseline is a text concept, think of it as the line that the letters sit on.
```
<style>
  #box-container {
    background: gray;
    display: flex;
    height: 100px;
    justify-content: space-evenly;
	align-items: baseline;
  }
  #box-1 {
    background-color: dodgerblue;
    width: 25%;
    height: 80%;
	font-size: 24px;
  }

  #box-2 {
    background-color: orangered;
    width: 25%;
    height: 80%;
	font-size: 14px;
  }
</style>

<div id="box-container">
  <div id="box-1">Hello</div>
  <div id="box-2">Goodbye</div>
</div>
```

<style>
  #box-container {
    background: gray;
    display: flex;
    height: 100px;
    justify-content: space-evenly;
	align-items: baseline;
  }
  #box-1 {
    background-color: dodgerblue;
    width: 25%;
    height: 80%;
	font-size: 24px;
  }

  #box-2 {
    background-color: orangered;
    width: 25%;
    height: 80%;
	font-size: 14px;
  }
</style>

<div id="box-container">
  <div id="box-1">Hello</div>
  <div id="box-2">Goodbye</div>
</div>

[Use the align-items Property in the Tweet EmbedPassed](https://codepen.io/ZoeyClyde/pen/MWEyXQe)

<br>

---

### `flex-wrap` Property

CSS flexbox has a feature to *<u>split a flex item into multiple rows (or columns)</u>*. By default, a flex container will fit all flex items together. For example, a row will all be on one line.

However, using the `flex-wrap` property tells CSS to wrap items. This means extra items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.

CSS also has options for the direction of the wrap:

- `nowrap`: this is the **default setting**, and does not wrap items.
- `wrap`: wraps items onto multiple lines from top-to-bottom if they are in rows and left-to-right if they are in columns.
- `wrap-reverse`: wraps items onto multiple lines from bottom-to-top if they are in rows and right-to-left if they are in columns.
[flex-wrap property](https://codepen.io/ZoeyClyde/pen/mdBPjvV)
*if it doesn't show, view in Atom*

<br>

---

## Properties for flex items

### `flex-shrink` Property

Items shrink when the width of the parent container is smaller than the combined widths of all the flex items within it.

The `flex-shrink` property takes numbers as values. The higher the number, the more it will shrink compared to the other items in the container. 

<br>


### `flex-grow` Property

Recall that `flex-shrink` controls the size of the items when the container shrinks. The `flex-grow` property controls the size of items when the parent container expands.

<br>

### `flex-basis` Property

The `flex-basis` property specifies the **initial size** of the item before CSS makes adjustments with `flex-shrink` or `flex-grow`.

The units used by the flex-basis property are the same as other size properties (px, em, %, etc.). The value `auto` sizes items based on the content.

<br>

### Use the `flex` Shorthand Property

There is a shortcut available to set several flex properties at once. The `flex-grow`, `flex-shrink`, and `flex-basis` properties can all be set together by using the `flex` property.

For example, `flex: 1 0 10px;` will set the item to `flex-grow: 1;`, `flex-shrink: 0;`, and `flex-basis: 10px;`.

The default property settings are `flex: 0 1 auto;`.

<br>

---

### Use the `order` Property to Rearrange Items

The `order` property is used to tell CSS the order of how flex items appear in the flex container. By default, items will appear in the same order they come in the source HTML. The property takes numbers as values, and negative numbers can be used.

```
  #box-1 {
    background-color: dodgerblue;
    order: 2;
  }

  #box-2 {
    background-color: orangered;
    order: 1;
  }
 ```
 
 [order Property](https://codepen.io/ZoeyClyde/pen/yLzOxNq)
 
 <br>
 
 ---
 
 ### `align-self` Property
 
This property allows you to adjust each item's alignment individually, instead of setting them all at once. This is useful since other common adjustment techniques using the CSS properties `float`, `clear`, and `vertical-align` do not work on flex items.

`align-self` accepts the same values as `align-items` and will **override any value set by the `align-items` property**.


 
