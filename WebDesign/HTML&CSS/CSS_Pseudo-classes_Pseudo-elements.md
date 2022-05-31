# CSS: Pseudo-classes and Pseudo-elements

[toc]

`pseudo-classes` and `pseudo-elements` are keywords that may be added to the end of a selector to style an element when it’s in a unique state. [Read more](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)


## First Letter or Line

You can specify different values for the first letter or first line of text inside an element using `:first-letter` and `:first-line`. 

## Styling Links

Browsers tend to show links in blue with an underline by default, and they will change
the color of links that have been visited to help users know which pages they have been to.
`:link`: This allows you to set styles for links that have not yet been visited. 
`:visited`: This allows you to set styles for links that have been clicked on.

## Responding to Users

`:hover`: This is applied when a user hovers over an element with a pointing device such as a mouse. 
`:active`: This is applied when an element is being activated by a user; for example, when a button is being pressed or a link being clicked. Sometimes this is used to make a button or link feel more like it is being pressed by changing the style or position of the element slightly.
`:focus`: Focus occurs when a browser discovers that you are ready to interact with an element on the page. For example, when your cursor is in a form input ready to accept typing, that element is said to have focus. 

When pseudo-classes are used, they should appear in this order: **:link, :visited, :hover, :focus, :active**.

<br>
<br>
<hr>