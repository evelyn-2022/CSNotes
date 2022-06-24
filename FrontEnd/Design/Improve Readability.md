# Improve Readability

[toc]



## Make Elements Only Visible to a Screen Reader

CSS's magic can also improve accessibility on your page when you want to visually hide content meant only for screen readers. This happens when information is in a visual format (like a chart), but screen reader users need an alternative presentation (like a table) to access the data. CSS is used to position the screen reader-only elements off the visual area of the browser window.

Here's an example of the CSS rules that accomplish this:
```
.sr-only {
  position: absolute;
  left: -10000px;
  width: 1px;
  height: 1px;
  top: auto;
  overflow: hidden;
}
```

Example (*Uncomment the style, and the table is gone.*):
<head>
  <style>
/*   .sr-only {
    position: absolute;
    left: -10000px;
    width: 1px;
    height: 1px;
    top: auto;
    overflow: hidden;
  } */
  </style>
</head>

  <section>
    <table class="sr-only">
      <thead>
        <tr>
          <th></th>
          <th scope="col">Stealth &amp; Agility</th>
          <th scope="col">Combat</th>
          <th scope="col">Weapons</th>
          <th scope="col">Total</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">Week One</th>
          <td>3</td>
          <td>5</td>
          <td>2</td>
          <td>10</td>
        </tr>
        <tr>
          <th scope="row">Week Two</th>
          <td>4</td>
          <td>5</td>
          <td>3</td>
          <td>12</td>
        </tr>
        <tr>
          <th scope="row">Week Three</th>
          <td>4</td>
          <td>6</td>
          <td>3</td>
          <td>13</td>
        </tr>
      </tbody>
    </table>
  </section>



==Note:== The following CSS approaches will NOT do the same thing:

- `display: none;` or `visibility: hidden;` hides content for everyone, including screen reader users
- Zero values for pixel sizes, such as `width: 0px; height: 0px;` removes that element from the flow of your document, meaning screen readers will ignore it

<br>

## Improve Readability with High Contrast Text

Low contrast between the foreground and background colors can make text difficult to read. Sufficient contrast improves your content's readability, but what exactly does "sufficient" mean?

The Web Content Accessibility Guidelines (WCAG) recommend at least a **4.5 to 1 contrast ratio** for color use as well as gray-scale combinations. The ratio is calculated by comparing the relative luminance values of two colors. This ranges from 1:1 for the same color, or no contrast, to 21:1 for white against black, the most substantial contrast. There are many contrast checking tools available online that calculate this ratio for you.

<br>

## Avoid Colorblindness Issues by Using Sufficient Contrast

There are various forms of colorblindness. The most common form is a reduced sensitivity to detect greens. Close colors can be thought of as **neighbors on the color wheel**, and those combinations should be avoided when conveying important information.

<br>

## Make Links Navigable with HTML Access Keys

HTML offers the `accesskey` attribute to specify a **shortcut key** to activate or bring focus to an element. Adding an accesskey attribute can make navigation more efficient for keyboard-only users.

HTML5 allows this attribute to be used on any element, but it's particularly useful when it's used with interactive ones. This includes links, buttons, and form controls.

Here's an example:
```
<a id="first" href="#" accesskey="g">The Garfield Files: Lasagna as Training Fuel?</a>
```

<br>

## Use tabindex to Add Keyboard Focus to an Element

The HTML `tabindex` attribute has three distinct functions relating to an element's **keyboard focus** (*Keyboard focus refers to the element that is currently receiving keyboard input*). When it's on a tag, it indicates that the element can be focused on. The value (an integer that's positive, negative, or zero) determines the behavior.

Certain elements, such as links and form controls, automatically receive keyboard focus when a user tabs through a page. It's in the same order as the elements come in the HTML source markup. This same functionality can be given to other elements, such as div, span, and p, by placing a `tabindex="0" `attribute on them. Here's an example:
```
<div tabindex="0">I need keyboard focus!</div>
```

Note: A negative tabindex value (typically -1) indicates that an element is focusable, but is not reachable by the keyboard. This method is generally used to bring focus to content programmatically (like when a `div` used for a pop-up window is activated), and is beyond the scope of these challenges.

Camper Cat created a new survey to collect information about his users. He knows input fields automatically get keyboard focus, but he wants to make sure his keyboard users pause at the instructions while tabbing through the items. Add a `tabindex `attribute to the `p` tag and set its value to 0. Bonus - using tabindex also enables the CSS pseudo-class `:focus` to work on the `p` tag.

[use-tabindex-to-add-keyboard-focus-to-an-element](https://codepen.io/ZoeyClyde/pen/BawKKBG)

<br>

## Use tabindex to Specify the Order of Keyboard Focus for Several Elements

The `tabindex` attribute also specifies the **exact tab order** of elements. This is achieved when the attribute's value is set to a positive number of 1 or higher.

Setting a `tabindex="1"` will bring keyboard focus to that element first. Then it cycles through the sequence of specified tabindex values (2, 3, etc.), before moving to default and `tabindex="0"` items.

[use-tabindex-to-specify-the-order-of-keyboard-focus-for-several-elements](https://codepen.io/ZoeyClyde/pen/vYeGLwp)
