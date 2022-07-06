# Creating Tables

## Basic Elements

At a minimum a table must consist of `<table>`, `<tr>` (table row), and `<td>` (table data) elements. For greater structure and additional semantic value, tables may include the `<th>` (table header) element and a few other elements as well.

Table headers may be used within both columns and rows. The `scope` attribute can indicate whether it is a heading for a column or a row.. It accepts the following values: **col, row, colgroup, and rowgroup**.

```html
<table>
  <tr>
    <th scope="col">Item</th>
    <th scope="col">Availability</th>
    <th scope="col">Qty</th>
    <th scope="col">Price</th>
  </tr>
  <tr>
    <td>Don&#8217;t Make Me Think by Steve Krug</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.02</td>
  </tr>
  <tr>
    <td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
    <td>Out of Stock</td>
    <td>1</td>
    <td>$22.23</td>
  </tr>
  <tr>
    <td>Bulletproof Web Design by Dan Cederholm</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.17</td>
  </tr>
</table>
```

<table>
	<tr>
		<th scope="col">Item</th>
		<th scope="col">Availability</th>
		<th scope="col">Qty</th>
		<th scope="col">Price</th>
	</tr>
	<tr>
		<td>Don&#8217;t Make Me Think by Steve Krug</td>
		<td>In Stock</td>
		<td>1</td>
		<td>$30.02</td>
	</tr>
	<tr>
		<td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
		<td>Out of Stock</td>
		<td>1</td>
		<td>$22.23</td>
	</tr>
	<tr>
		<td>Bulletproof Web Design by Dan Cederholm</td>
		<td>In Stock</td>
		<td>1</td>
		<td>$30.17</td>
	</tr>
</table>

==Note:==
Even if a cell has no content, you should still use a `<td>` or `<th>` element to represent the presence of an empty cell otherwise the table will not render correctly.
When you have empty cells in your table, you can use the `empty-cells` property to specify whether or not their borders should be shown. It can take one of three values: _show_(This shows the borders of any empty cells), _hide_, _inherit_.

```html
<table>
  <tr>
    <th></th>
    <th scope="col">Saturday</th>
    <th scope="col">Sunday</th>
  </tr>
  <tr>
    <th scope="row">Tickets sold:</th>
    <td>120</td>
    <td>135</td>
  </tr>
  <tr>
    <th scope="row">Total sales:</th>
    <td>$600</td>
    <td>$675</td>
  </tr>
</table>
```

<table>
	<tr>
 		<th></th>
		<th scope="col">Saturday</th>
		<th scope="col">Sunday</th>
	</tr>
	<tr>
		<th scope="row">Tickets sold:</th>
		<td>120</td>
		<td>135</td>
	</tr>
	<tr>
		<th scope="row">Total sales:</th>
		<td>$600</td>
		<td>$675</td>
	</tr>
</table>

<br>
<br>
<hr>

## Table Structure

### Table Caption

The `<caption>` element provides a caption or title for a table. The `<caption>` element must come immediately after the opening `<table>` tag, and it is positioned at the top of a table by default.

### Table Head, Body, & Foot

The content within tables can be broken up into multiple groups, including a head, a body, and a foot.

- `<thead>` (table head): wraps the heading row or rows of a table to denote the head. The table head should be placed at the top of a table, after any `<caption>` element and before any `<tbody>` element.
- `<tbody>` (table body): contain the primary data within a table.
- `<tfoot>` (table foot): contain data that outlines the contents of a table

```html
<table>
  <caption>
    Design and Front-End Development Books
  </caption>
  <thead>
    <tr>
      <th scope="col">Item</th>
      <th scope="col">Availability</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Don&#8217;t Make Me Think by Steve Krug</td>
      <td>In Stock</td>
      <td>1</td>
      <td>$30.02</td>
    </tr>
    ......
  </tbody>
  <tfoot>
    <tr>
      <td>Subtotal</td>
      <td></td>
      <td></td>
      <td>$135.36</td>
    </tr>
    ......
  </tfoot>
</table>
```

<table>
	<caption>Design and Front-End Development Books</caption>
	<thead>
		<tr>
			<th scope="col">Item</th>
			<th scope="col">Availability</th>
			<th scope="col">Qty</th>
			<th scope="col">Price</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Don&#8217;t Make Me Think by Steve Krug</td>
			<td>In Stock</td>
			<td>1</td>
			<td>$30.02</td>
		</tr>
		<tr>
			<td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
			<td>Out of Stock</td>
			<td>1</td>
			<td>$22.23</td>
		</tr>
		<tr>
			<td>Bulletproof Web Design by Dan Cederholm</td>
			<td>In Stock</td>
			<td>1</td>
			<td>$30.17</td>
		</tr>
	</tbody>
	<tfoot>
		<tr>
			<td>Subtotal</td>
			<td></td>
			<td></td>
			<td>$135.36</td>
		</tr>
		<tr>
			<td>Tax</td>
			<td></td>
			<td></td>
			<td>$13.54</td>
		</tr>
	</tfoot>
</table>

### Combining Multiple Cells

We can use the `colspan` and `rowspan` attributes. These two attributes work on either the `<td>` or `<tr>` elements.

```html
<table>
  <caption>
    Design and Front-End Development Books
  </caption>
  <thead>
    <tr>
      <th scope="col" colspan="2">Item</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    ......
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr>
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
  </tfoot>
</table>
```

<table>
	<caption>Design and Front-End Development Books</caption>
	<thead>
		<tr>
			<th scope="col" colspan="2">Item</th>
			<th scope="col">Qty</th>
			<th scope="col">Price</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Don&#8217;t Make Me Think by Steve Krug</td>
			<td>In Stock</td>
			<td>1</td>
			<td>$30.02</td>
		</tr>
		<tr>
			<td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
			<td>Out of Stock</td>
			<td>1</td>
			<td>$22.23</td>
		</tr>
		<tr>
			<td>Bulletproof Web Design by Dan Cederholm</td>
			<td>In Stock</td>
			<td>1</td>
			<td>$30.17</td>
		</tr>
	</tbody>
	<tfoot>
		<tr>
			<td colspan="3">Subtotal</td>
			<td>$135.36</td>
		</tr>
		<tr>
			<td colspan="3">Tax</td>
			<td>$13.54</td>
		</tr>
	</tfoot>
</table>

<br>
<br>
<hr>

## Table Borders

### Border Collapse Property

When we apply borders around parent `<table>` element as well as nested `<th>` or `<td>` elements, those borders will begin to stack up, with the border of one element sitting next to that of another element. The `border-collapse` property determines a table’s border model. There are three values for the `border-collapse` property:

- separate: default value. All of the different borders will stack up next to one another.
- collapse: collapse into a single border where possible. (border-spacing will be ignored and cells pushed together, and empty-cells properties will be ignored.)
- inherit

### Border Spacing Property

The `border-spacing` property can determine how much space, if any, appears between the borders. (By default, browsers often leave a small gap between each table cell)

For example, a table with a 1-pixel border around the entire table and a 1-pixel border around each cell will have a 2-pixel border all around every cell because the borders stack up next to one another. Adding in a border-spacing value of 4 pixels separates the borders by 4 pixels.

```css
table {
  border-collapse: separate;
  border-spacing: 4px;
}
table,
th,
td {
  border: 1px solid #c6c7cc;
}
th,
td {
  padding: 10px 15px;
}
```

<img src="https://s2.loli.net/2021/12/12/NsAGhHmyrWc6zaL.png" >

### Adding Borders to Rows

Adding borders to a table can be tricky at times, particularly when putting borders between rows, because borders cannot be applied to `<tr>` elements or table structural elements.

We’ll begin by making sure `border-collapse: collapse`, and then add a bottom border to each table cell, regardless of whether it’s a `<th>` or `<td>` element. If we wish, we can remove the bottom border from the cells within the last row of the table by using the `last-child` pseudo-class selector to select the last `<tr>` element within the table and target the `<td>` elements within that row. Additionally, if a table is using the structural elements, we’ll want to make sure to prequalify the last row of the table as being within the `<tfoot>` element.

```css
table {
  border-collapse: collapse;
}
th,
td {
  border-bottom: 1px solid #c6c7cc;
  padding: 10px 15px;
}
tfoot tr:last-child td {
  border-bottom: 0;
}
```

<img src="https://s2.loli.net/2021/12/12/nN8sU1fLBy5GjKt.png" >

<hr>

## Table Striping

In the effort to make tables more legible, one common design practice is to “stripe” table rows with alternating background colors. One way to do this is to place a class on every other `<tr>` element and set a background color to that class. Another, easier way is to use the `:nth-child` pseudo-class selector with an even or odd argument to select every other `<tr>` element.

```html
table { border-collapse: separate; border-spacing: 0; } th, td { padding: 10px
15px; } thead { background: #395870; color: #fff; } tbody tr:nth-child(even) {
background: #f0f0f2; } td { border-bottom: 1px solid #c6c7cc; border-right: 1px
solid #c6c7cc; } td:first-child { border-left: 1px solid #c6c7cc; }
```

The `<table>` element has an explicit `border-collapse` property set to separate and a `border-spacing` property set to 0. The reason for this is that the `<td>` elements include borders, while the `<th>` elements do not. Without the border-collapse property set to separate the borders of the `<td>` elements would make the body and foot of the table wider than the head.

## Aligning Text

We can move text horizontally using the `text-align` property, align text vertically using the `vertical-align` property (accepts top, middle, and bottom values).
