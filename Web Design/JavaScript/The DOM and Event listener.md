## The DOM

[toc]

We called a method on `document`. `document` is a globally available variable in the browser that you use to interact with the HTML and CSS.

To modify multiple elements:

```
<ul>
  <li class="js-target">Unchanged</li>
  <li class="js-target">Unchanged</li>
  <li>Won't Change</li>
  <li class="js-target">Unchanged</li>
  <li>Won't Change</li>
  <li class="js-target">Unchanged</li>
</ul>
<script>
  const elementsToChange = document.querySelectorAll('.js-target');
  for (let i = 0; i < elementsToChange.length; i++) {
    const currentElement = elementsToChange[i];
    currentElement.innerText = "Modified by JavaScript!";
  }
</script>
```

## Events and listeners

```
<button class="event-button">Click me!</button>
<script>
  const button = document.querySelector('.event-button');
  button.addEventListener('click', function () {
    alert("Hey there!");
  });
 ```

People often get confused seeing `});` on the last line. The first `}` is closing the function, the second `)` is closing the function call of `addEventListener`, and the `;` ends the statement.

### With and without parenthesis

```
document.querySelector("button").addEventListener("click", handleClick);
function handleClick() {
  alert("I got clicked!");
}
```

The alert will appear when the button gets clicked.
However, if we *add parenthesis after the function call* `document.querySelector("button").addEventListener("click", handleClick());`, the alert will show up when we open the page, because it is a straight up method call, and will call that method straight away when adding the event listener.

Without the parenthesis, it is passing a function as an input so that it can be called at a later time.

We can replace it with an anonymous function:

```
document.querySelector("button").addEventListener("click", function() {
	alert("I got clicked!");
});
```

If you need to pass arguments to a function that is called by an event handler or listener, but cannot add parenthesis, you can wrap the function call in an anonymous function, and the named function that requires the arguments lives inside the anonymous function.

### Keyboard event listener

To listen for keyboard events, we can add the event listener to the whole document.
We pass in a parameter `event` or `e` in the function to allow us to tap into the event that triggered the event listener.
If we `console.log(event);`, we get back the information about which key get pressed and other information.

```
document.addEventListener("keydown", function(event) {
  console.log(event.key);
});
```

## Event delegation (event bubbling / event flow)

If you have a bunch of elements that you need to listen for events on, you could attach an event listener to each but that's a bit tedious to do. Instead what is sometimes easier to do is to use what's called **event bubbling**. When event fires on an element, after that "bubbles" up to its parent, and then its parent, and its parent, etc. until it's at the root element.

```
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
</script
```

You can see that we only bound one event listener, and that was the `div` above it. Then, when we click the button, we're using the event parameter that is being passed into the callback. An event listener's first parameter is always an event object. There's lots of information on the event object but we're most concerned with `event.target`. target is **the tag that the event originated from**. In this case it'll be the button that caused the event. And we know that with tags you can use the innerText property to get the text inside of them. That's how we able to alert the correct number. 


