# Scroll and Coordinates

To get the current scroll of viewport:

```js
console.log(window.pageXOffset, window.pageYOffset);
```

To get the current width and height of viewport:

```js
console.log(
  document.documentElement.clientHeight,
  document.documentElement.clientWidth
);
```

To get the position of one element `.getBoundingClientRect`:

```js
btn.addEventListener("click", function (e) {
  console.log(e.target.getBoundingClientRect());
});

// Output:
// DOMRect {x: 0, y: 138.5, width: 369, // height: 2953.6953125, top: 138.5, …}
// bottom: 3092.1953125
// height: 2953.6953125
// left: 0
// right: 369
// top: 138.5
// width: 369
// x: 0
// y: 138.5
// [[Prototype]]: DOMRect
```

Then we can use the global function on the window to scroll to certain position (we need to add scroll position to its position relative to viewport):

```js
window.scrollTo(
  s1coords.left + window.pageXOffset,
  s1coords.top + window.pageYOffset
);
```

<img src='https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect/element-box-diagram.png'>

To implement smooth scroll, we can specify an object with left, top and behavior properties:

```js
const s1coords = section1.getBoundingClientRect();
window.scrollTo({
  left: s1coords.left + window.pageXOffset,
  top: s1coords.top + window.pageYOffset,
  behavior: "smooth",
});
```

A modern way to scroll to `section1` without calculating the coordinates:

```js
section1.scrollToView({ behavior: "smooth" });
```

### window scroll

To add sticky navbar when the page scrolls to a certain position:

```js
window.addEventListener("scroll", function () {
  if (section1.getBoundingClientRect().top <= 0) {
    nav.classList.add("sticky");
  } else {
    nav.classList.remove("sticky");
  }
});
```

But `scroll` fires every time there is a tiny scroll, which is bad for performance.

## [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
