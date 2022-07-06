# CSS: Variables

[toc]

**Custom properties** (sometimes referred to as **CSS variables** or **cascading variables**) are entities defined by CSS authors that contain specific values to be reused throughout a document.

To create a CSS variable, you just need to give it a name with **two hyphens in front of it** and assign it a value. A common best practice is to define custom properties on the `:root` pseudo-class, so that it can be applied globally across your HTML document:

```
:root {
  --main-bg-color: brown;
}
```

After you create your variable, you can assign its value to other CSS properties by referencing the name you gave it.

```
element {
  background-color: var(--main-bg-color);
}
```

<br>
<hr>

## Fallback Value

### Attach a Fallback value to a CSS Variable

When using your variable as a CSS property value, you can attach a fallback value that your browser will revert to if the given variable is invalid. Here's how you do it:

```css
background: var(--main-bg-color, black);
```

==Note:== This fallback is **not used to increase browser compatibility**, and it will not work on IE browsers. Rather, it is used so that the browser has a color to display if it cannot find your variable.

<br>

### Improve Compatibility with Browser Fallbacks

When working with CSS you will likely run into browser compatibility issues at some point. This is why it's important to provide browser fallbacks to avoid potential problems. When your browser parses the CSS of a webpage, it ignores any properties that it doesn't recognize or support.
For example, if you use a CSS variable to assign a background color on a site, **Internet Explorer** will ignore the background color because it **does not support CSS variables**. In that case, the browser will use whatever value it has for that property.

This means that if you do want to provide a browser fallback, it's as easy as providing another more widely supported value **_immediately before your declaration_**. That way an older browser will have something to fall back on, while a newer browser will just interpret whatever declaration comes later in the cascade.

```css
.red-box {
  background: red;
  background: var(--red-color);
  height: 200px;
  width: 200px;
}
```
