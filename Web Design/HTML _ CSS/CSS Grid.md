# CSS Grid

[toc]

<style>

</style>
Turn any HTML element into a grid container by setting its `display` property to `grid`. This gives you the ability to use all the other properties associated with CSS Grid.

Note: In CSS Grid, the parent element is referred to as the *container* and its children are called *items*.

<br>

## Add Columns / Rows with `grid-template-columns` and `grid-template-rows` (container)

To add some columns to the grid, use the `grid-template-columns` property on a grid container as demonstrated below:

```
.container {
  display: grid;
  grid-template-columns: 50px 50px;
}
```

This will give your grid two columns that are each 50px wide. *The <u>number of parameters</u> given to the grid-template-columns property indicates the <u>number of columns</u> in the grid, and the value of each parameter indicates the <u>width of each column</u>.*

To adjust the rows manually, use the `grid-template-rows` property in the same way you used `grid-template-columns` in the previous challenge.

<br>

You can use **absolute and relative units** like `px` and `em` in CSS Grid to define the size of rows and columns. You can use these as well:

- **fr**: sets the column or row to a fraction of the available space,

- auto: sets the column or row to the width or height of its content automatically,

- %: adjusts the column or row to the percent width of its container.

Here's the code that generates the output in the preview:
```
grid-template-columns: auto 50px 10% 2fr 1fr;
```
This snippet creates five columns. The first column is as wide as its content, the second column is 50px, the third column is 10% of its container, and for the last two columns; the remaining space is divided into three sections, two are allocated for the fourth column, and one for the fifth.

<br>

---

## Grid Gap 

### Create a Column / Row Gap Using `grid-column-gap` / `grid-row-gap` (container)


So far in the grids you have created, the columns have all been tight up against each other. Sometimes you want a gap in between the columns. To add a gap between the columns, use the `grid-column-gap` property like this:
```
grid-column-gap: 10px;
```
This creates 10px of empty space between all of our columns.

<br>

### Add Gaps Faster with `grid-gap` (container)

`grid-gap` is a shorthand property for `grid-row-gap` and `grid-column-gap` from the previous two challenges that's more convenient to use. If `grid-gap` has one value, it will create a gap between all rows and columns. However, if there are two values, it will *<u>use the first one to set the gap between the rows and the second value for the columns</u>*.

Use grid-gap to introduce a 10px gap between the rows and 20px gap between the columns:
```
grid-gap: 10px 20px;
```
[Add Gaps Faster with grid-gap](https://codepen.io/ZoeyClyde/pen/zYEqmYq)

<br>

### Use `grid-column` / `grid-row` to Control Spacing (grid item)

The hypothetical horizontal and vertical lines that create the grid are referred to as lines. These lines are numbered starting with 1 at the top left corner of the grid and move right for columns and down for rows, counting upward.

This is what the lines look like for a 3x3 grid:
<img src="https://s2.loli.net/2021/12/08/wv8mOuMaDPJnxpZ.png" alt="3_by_3_grid.png" style="width: 200px">
To control the number of columns an item will consume, you can use the `grid-column` property in conjunction with the line numbers you want the item to start and stop at.

Here's an example:
```
<style>
  .item1{background:LightSkyBlue;}
  .item2{background:LightSalmon;}
  .item3{background:PaleTurquoise;}
  .item4{background:LightPink;}

  .item5 {
    background: PaleGreen;
    grid-column: 2 / 4;
    grid-row: 2 / 5;
  }

  .container {
    font-size: 20px;
	color: black;
    min-height: 100px;
    width: 100%;
    background: LightGray;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    grid-gap: 5px;
  }
</style>

<div class="container">
  <div class="item1">1</div>
  <div class="item2">2</div>
  <div class="item3">3</div>
  <div class="item4">4</div>
  <div class="item5">5</div>
</div>
```
This will make the 5th item start at the 2nd vertical line of the grid on the left and span to the 4th line of the grid, start at  the 2nd row and span to the 5th row, consuming two columns and three rows.

<style>
  .item1{background:LightSkyBlue;}
  .item2{background:LightSalmon;}
  .item3{background:PaleTurquoise;}
  .item4{background:LightPink;}

  .item5 {
    background: PaleGreen;
    grid-column: 2 / 4;
    grid-row: 2 / 5;
  }

  .container {
    font-size: 20px;
	color: black;
    min-height: 100px;
    width: 50%;
    background: LightGray;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    grid-gap: 5px;
  }
</style>

<div class="container">
  <div class="item1">1</div>
  <div class="item2">2</div>
  <div class="item3">3</div>
  <div class="item4">4</div>
  <div class="item5">5</div>
</div>

<br>

---

## Align an Item (grid item)

### Aligh an Item Horizontally using `justify-self`

In CSS Grid, the content of each item is located in a box which is referred to as a **cell**. You can align the content's position within its cell horizontally using the `justify-self` property on a grid item. By default, this property has a value of `stretch`, which will make the content fill the whole width of the cell. This CSS Grid property accepts other values as well:
- start: aligns the content at the left of the cell,
- center: aligns the content in the center of the cell,
- end: aligns the content at the right of the cell.

<br>

### Align an Item Vertically using `align-self`

This property accepts all of the same values as `justify-self` from the last challenge.
```
<style>
  .item6{background:LightSkyBlue;}
  .item7 {
    background:LightSalmon;
    justify-self: center;
  }

  .item8 {
    background: PaleTurquoise;
    align-self: end;
  }

  .item9{background:LightPink;}
  .item0{background:PaleGreen;}
</style>

<div class="container">
  <div class="item6">1</div>
  <div class="item7">2</div>
  <div class="item8">3</div>
  <div class="item9">4</div>
  <div class="item0">5</div>
</div>
```

<style>
  .item6{background:LightSkyBlue;}
  .item7 {
    background:LightSalmon;
    justify-self: center;
  }

  .item8 {
    background: PaleTurquoise;
    align-self: end;
  }

  .item9{background:LightPink;}
  .item0{background:PaleGreen;}
</style>

<div class="container">
  <div class="item6">6</div>
  <div class="item7">7</div>
  <div class="item8">8</div>
  <div class="item9">9</div>
  <div class="item0">0</div>
</div>

<br>

---

## Align All Items (container)

### Align All Items Horizontally using `justify-items`

You can use the previously learned properties and align them individually, or you can align them all at once horizontally by using `justify-items` on your grid container. This property can accept all the same values you learned about in the previous two challenges, the difference being that it will move all the items in our grid to the desired alignment.

### Align All Items Vertically using `align-items`
Using the `align-items` property on a grid container will set the vertical alignment for all the items in our grid.

<br>

---

## Area Template

### Divide the Grid Into an Area Template

You can group cells of your grid together into an area and give the area a custom name. Do this by using `grid-template-areas` ***on the container*** like this:
```
grid-template-areas:
  "header header header"
  "advert content content"
  "advert footer footer";
```
The code above groups the cells of the grid into four areas; header, advert, content, and footer. Every word represents a cell and every pair of quotation marks represent a row.

<br>

### Place Items in Grid Areas Using the `grid-area` Property

After creating an area template for your grid container, as shown in the previous challenge, you can place an item in your custom area by referencing the name you gave it. To do this, you use the `grid-area` property ***on an item*** like this:

```
.item1 {
  grid-area: header;
}
```

This lets the grid know that you want the item1 class to go in the area named `header`. In this case, the item will use the entire top row because that whole row is named as the header area.

```
<style>
  .item11{background:LightSkyBlue;}
  .item12{background:LightSalmon;}
  .item13{background:PaleTurquoise;}
  .item14{background:LightPink;}

  .item15 {
    background: PaleGreen;
    grid-area: footer;
  }

  .container {
    font-size: 20px;
    min-height: 150px;
    width: 50%;
    background: LightGray;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    grid-gap: 10px;
    grid-template-areas:
      "header header header"
      "advert content content"
      "footer footer footer";
  }
</style>

<div class="container">
  <div class="item11">11</div>
  <div class="item12">12</div>
  <div class="item13">13</div>
  <div class="item14">14</div>
  <div class="item15">15</div>
</div>
```

<style>
  .item11{background:LightSkyBlue;}
  .item12{background:LightSalmon;}
  .item13{background:PaleTurquoise;}
  .item14{background:LightPink;}

  .item15 {
    background: PaleGreen;
    grid-area: footer;
  }

  .container {
    font-size: 20px;
    min-height: 150px;
    width: 50%;
    background: LightGray;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    grid-gap: 10px;
    grid-template-areas:
      "header header header"
      "advert content content"
      "footer footer footer";
  }
</style>

<div class="container">
  <div class="item11">11</div>
  <div class="item12">12</div>
  <div class="item13">13</div>
  <div class="item14">14</div>
  <div class="item15">15</div>
</div>

<br>

### Use grid-area Without Creating an Areas Template

The grid-area property you learned in the last challenge can be used in another way. If your grid doesn't have an areas template to reference, you can create an area on the fly **for an item** to be placed like this:
```
item1 { grid-area: 1/1/2/4; }
```

This is using the line numbers you learned about earlier to define where the area for this item will be. The numbers in the example above represent these values:
```
grid-area: horizontal line to start at / vertical line to start at / horizontal line to end at / vertical line to end at;
```
So the item in the example will consume the rows between lines 1 and 2, and the columns between lines 1 and 4.

<br>

### Reduce Repetition Using the `repeat` Function (on container)

When you used `grid-template-columns` and `grid-template-rows` to define the structure of a grid, you entered a value for each row or column you created.

Let's say you want a grid with 100 rows of the same height. It isn't very practical to insert 100 values individually. Fortunately, there's a better way - by using the `repeat` function to specify **the number of times** you want your column or row to be repeated, **followed by a comma and the value you want to repeat**.

You can also repeat multiple values with the repeat function and insert the function amongst other values when defining a grid structure. Here's what that looks like:
```
grid-template-columns: repeat(2, 1fr 50px) 20px;
```
This translates to:
```
grid-template-columns: 1fr 50px 1fr 50px 20px;
```
Note: The 1fr 50px is repeated twice followed by 20px.

<br>

### Limit Item Size Using the `minmax` Function

There's another built-in function to use with `grid-template-columns` and `grid-template-rows` called `minmax`. It's used to limit the size of items when the grid container changes size. To do this you need to specify the acceptable size range for your item. Here is an example:
```
grid-template-columns: 100px minmax(50px, 200px);
```
In the code above, `grid-template-columns` is set to create two columns; the first is 100px wide, and the second has the minimum width of 50px and the maximum width of 200px.

<br>

### Create Flexible Layouts Using `auto-fill` and `auto-fit`

The `repeat` function comes with an option called `auto-fill`. This allows you to *<u>automatically insert as many rows or columns of your desired size as possible depending on the size of the container</u>*. You can create flexible layouts when combining `auto-fill` with `minmax`, like this:
```
repeat(auto-fill, minmax(60px, 1fr));
```

When the container changes size, this setup keeps inserting 60px columns and stretching them until it can insert another one. 


`auto-fit` works almost identically to `auto-fill`. The only difference is that when the container's size exceeds the size of all the items combined, `auto-fill` keeps inserting empty rows or columns and pushes your items to the side, while `auto-fit` collapses those empty rows or columns and stretches your items to fit the size of the container.
Note: If your container can't fit all your items on one row, it will move them down to a new one.

Example:
In the first grid, use auto-fill with repeat to fill the grid with columns that have a minimum width of 60px and maximum of 1fr. 
In the second grid, use auto-fit with repeat to fill the grid with columns that have a minimum width of 60px and maximum of 1fr. 
Then resize the preview to see auto-fill in action. [Create Flexible Layouts Using auto-fill and auto-fit](https://codepen.io/ZoeyClyde/pen/jOGqQeG)

<br>

---

## Use Media Queries to Create Responsive Layouts

CSS Grid can be an easy way to make your site more responsive by using media queries to rearrange grid areas, change dimensions of a grid, and rearrange the placement of items.

Example: 
When the viewport width is 400px or more, make the header area occupy the top row completely and the footer area occupy the bottom row completely.

```
  @media (min-width: 400px){
    .container{
      grid-template-areas:
        "header header"
        "advert content"
        "footer footer";
    }
```
[Use Media Queries to Create Responsive Layouts](https://codepen.io/ZoeyClyde/pen/WNZwLeX)

<br>

---

## Create Grids within Grids
Turning an element into a grid only affects the behavior of its direct descendants. So by turning a direct descendant into a grid, you have a grid within a grid.

For example, by setting the `display` and `grid-template-columns` properties of the element with the item3 class, you create a grid within your grid.
  ```
  .item3 {
    background: PaleTurquoise;
    grid-area: content;
    display: grid;
    grid-template-columns: auto 1fr;
  }
 ```
Turn the element with the item3 class into a grid with two columns with a width of auto and 1fr using `display` and `grid-template-columns`.
[Create Grids within Grids](https://codepen.io/ZoeyClyde/pen/xxXVmbo)