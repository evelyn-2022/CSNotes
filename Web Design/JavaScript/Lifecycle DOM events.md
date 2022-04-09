# Lifecycle DOM events

## After HTML is loaded

```
document.addEventListener('DOMContentLoaded', function (e) {
	console.log('HTML parsed and DOM tree built!');
});
```

## After all resources are loaded

```
window.addEventListener('loaded', function (e) {
	console.log('Page fully loaded');
});
```

## Before leaving the page

```
window.addEventListener('beforeunload', function (e) {
	e.preventDefault();
	e.returnValue = '';
});
```