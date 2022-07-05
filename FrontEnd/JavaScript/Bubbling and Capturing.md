# Bubbling and Capturing

<img src="https://s2.loli.net/2022/03/23/g2kTxeqE9PWwHJp.png" >

When the click happens, the event is actually generated at the root of the document, at the very top of the DOM tree.

From there, the ==capturing phase== happens, where the event travels all the way down from the document root to the target element.

As soon as the event reaches the target, the ==target phase== begins, where events can be handled right at the target. We do that with _event listeners_.

After reaching the target, the event _bubbles up_ to the document root again in the ==bubbling phase==. It bubbles through all its _parent elements_ again.

**Event listeners** only listen to events in the target and bubbling phase, not the capturing phase. However, we can change this by adding the third parameter to `addEventListener`:

```js
elem.addEventListener(
  "click",
  function (e) {
    alert("an alert");
  },
  true
);
```

### Target and current target

```html
<nav class="nav">
  <div class="nav-links">
    <div class="nav-link"></div>
    <div class="nav-link"></div>
    <div class="nav-link"></div>
  </div>
</nav>
```

```js
document.querySelector("nav-link").addEventListener("click", function (e) {
  console.log(e.target, e.currentTarget);
});
document.querySelector("nav-links").addEventListener("click", function (e) {
  console.log(e.target, e.currentTarget);
});
document.querySelector("nav").addEventListener("click", function (e) {
  console.log(e.target, e.currentTarget);
});
```

When we click on the first nav link, we can see that all three `e.target` point to the first nav link that gets clicked, but `e.currentTarget` point to the element to which the event listener is attached.

The **currentTarget** read-only property of the Event interface identifies the current target for the event, _as the event traverses the DOM_. It always refers to the element to which the _event handler_ has been attached, as opposed to **Event.target**, which identifies the element on which the event occurred and which may be its descendant.

### To stop event propagation

Add `e.stopPropagation();` at the end of event handler.

### Using event delegation for efficiency

Original code: add event listener to each one of the nav links

```js
document.querySelectorAll(".nav__link").forEach(function (el) {
  el.addEventListener("click", function (e) {
    e.preventDefault();
    const id = el.getAttribute("href");
    document.querySelector(id).scrollIntoView({ behavior: "smooth" });
  });
});
```

Using event delegation:

```js
// 1. Add event listener to common parent element
document.querySelector(".nav__links").addEventListener("click", function (e) {
  e.preventDefault();

  // 2. Determine what element originated the event
  if (e.target.classList.contains("nav__link")) {
    const id = e.target.getAttribute("href");
    document.querySelector(id).scrollIntoView({ behavior: "smooth" });
  }
});
```

1. add event listener to the parent element;
2. determine what element originated the event;
3. match the intended elements.

```js
<div class="button-container">
  <button>1</button>
  <button>2</button>
  <button>3</button>
  <button>4</button>
  <button>5</button>
</div>
<script>
  document.querySelector('.button-container').addEventListener('click', function(event) {
    alert(`You clicked on button ${event.target.innerText}`);
  });
</script>
```

🟡 Note: Event delegation is extremely useful when we add event listener to elements that don't exist when the page first loads, because we can add event listener to their parent elements instead.
