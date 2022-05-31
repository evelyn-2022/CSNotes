# Bubbling and Capturing

<img src="https://s2.loli.net/2022/03/23/g2kTxeqE9PWwHJp.png" >

When the click happens, the event is actually generated at the root of the document, at the very top of the DOM tree. 

From there, the ==capturing phase== happens, where the event travels all the way down from the document root to the target element.

As soon as the event reaches the target, the ==target phase== begins, where events can be handled right at the target. We do that with *event listeners*.

After reaching the target, the event *bubbles up* to the document root again in the ==bubbling phase==. It bubbles through all its *parent elements* again.

**Event listeners** only listen to events in the bubbling phase, not the capturing phase. However, we can change this by adding the third parameter to `addEventListener`:

```
elem.addEventListener('click', function(e) {
	alert('an alert');
}, 
	true
);
```

### Target and current target

The **currentTarget** read-only property of the Event interface identifies the current target for the event, *as the event traverses the DOM*. It always refers to the element to which the *event handler* has been attached, as opposed to **Event.target**, which identifies the element on which the event occurred and which may be its descendant.


### To stop event propagation

Add `e.stopPropagation();` at the end of event handler.

### Using event delegation for efficiency

Original code: add event listener to each one of the nav links:

```
document.querySelectorAll('.nav__link').forEach(function (el) {
  el.addEventListener('click', function (e) {
    e.preventDefault();
    const id = el.getAttribute('href');
    document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
  });
});
```

Using event delegation:
```
document.querySelector('.nav__links').addEventListener('click', function (e) {
  e.preventDefault();
  if (e.target.classList.contains('nav__link')) {
    const id = e.target.getAttribute('href');
    document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
  }
});
```

1. add event listener to the parent element;
2. determine what element originated the event;
3. match the intended elements.



