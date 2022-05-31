# Event 

[event reference](https://developer.mozilla.org/en-US/docs/Web/Events)

remove event listener

```
const h1 = document.querySelector('h1');

const alertH1 = function(e) {
	alert('an alert');
};

h1.addEventListener('mouseenter', alertH1);

setTimeout(() => h1.removeEventListener('mouseenter', alertH1), 3000);
```

`mouseover` is similar to `mouseenter`, except that `mouseenter` does not bubble.