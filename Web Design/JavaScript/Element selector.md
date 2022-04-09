## Element selector

[toc]

### Special elements

Special elements don't need to use any selector:

- document element: `document.documentElement`
- head: `document.head`
- body: `document.body`

### getElementBy...

`getElementBy` returns an **HTML collection**. It is a *live collection*, which means that if the DOM changes, then this collection is also immediately updated automatically.

- `.getElementsByTagName()` search for specific tag name like `<li>`
- `getElementsByClassName()` search for specific class name, e.g. `document.getElementByClassName("btn");`, return an array;
- `getElementById()` return a single item. e.g. select an element with id = "title" and change inner text to goodbye: `document.getElementById("title").innerHTML = "goodbye";`

### querySelector

- element:  `document.querySelector("l1");`, 
- class: `document.querySelector(".btn");`,
- id: `document.querySelector("#title");`

We can also combine them to create hierarchical selectors.

If more than one element match the selector, only the first one will be returned.

`querySelectorAll` can select all the elements that match the selector, and return an array. This returns a **node list** of all elements selexted by the selector.

Values are passed in *as strings* in js: `document.querySelectorAll("button")[2].style.color = "red";`


## Changing style

`classList` can return a list of all classed attached to the element. Once we have a list of all classes, we can use methods to like `.add` to change the classes.
Example:
```
document.querySelector("button").classList.add("invisible");
```
This will add the new class `invisible` to the button element. Then we can use css to modify the value of this new class. We can also use `.remove()` to remove a class, use `.toggle()` change the state, if the class is already applied, remove it, if it's not, add it.

## Changing text

- `.innerHTML` or `.textContent`, the former one gives you all that between the html tag, while the latter one only return the text content. So if we also need to change the style of text, we can use `document.querySelector("h1").innerHTML = "<em>goodbye</em>";`
- `.value`: change the value of a text field.

## Inserting HTML element

- `element.insertAdjacentHTML(position, text)`. *position* can take four parameters: `beforebegin`, `afterbegin`, `beforeend` and `afterend`.
- `document.createElement()` to create a DOM element
- `.prepend()` to insert something as the first child of an element; `.append` add as last child.

==Note:==
If we use `prepend` and `append` at the same time, the element will not be both prepended and appended, it will only be moved from before to after because a DOM element is unique and can only exist at one place each time. 
```
header.prepend(message);
header.append(message);
```

To insert multiple copies of the same element, we first copy the first element and pass in `true`, which means all the child elements will also be copied. 

```
header.append(message.cloneNode(true));
```

## Removing an element

`.remove()`

## Changing attributes

`document.querySelector("a").attributes;` will return a list of all the attributes that are currently attached to the html element. We can use `document.querySelector("a").getAttribute("href");` to get the attribute, use `document.querySelector("a").setAttribute("href", "http://abcd.com");` to change the attribute.

## Child & parent node / element

 ==child nodes==: `.childNodes`, returns a *live NodeList* of child nodes of the given element where the first child node is assigned index 0. Child nodes include *elements, text and comments*.

==child elements==: to get a collection containing *only elements*, use `.children` instead.

==First / last child node / element==
First child node: `.firstChild`;
First child element: `.firstElementChild`.

==Parent node / element==:
parent node: `.parentNode`;
parent element: `parentElement`.

==Ancestor==:
The `closest()` method traverses the Element and its parents (heading toward the document root) until it finds a node that matches the provided selector string. Will return itself or the matching ancestor. If no such element exists, it returns *null*.
```
h1.closest('.header').color = 'red';
```
Set the closest ancestor to h1 element with a class name of header to red.

It is extremely useful in **event delegation**.

==Siblings==:
In JavaScript, we can only access direct siblings.
Sibling nodes: `.nextSibling` and `.previousSibling`;
Sibling elements: `.nextElementSibling` and `.previousElementSibling`.

To get all the siblings (including itself), get to the parent element and get all its child elements from there:
```
[...h1.parentElement.children].forEach(function(e) {
	if (e !== h1) {
		e.backgroundColor = 'red';
	}
});
```
Here, we set the background color of all h1's siblings to red.

## Submit button

In HTML, when the submit button is clicked, the page will reload. We can prevent from submitting by adding:
```
btn.loginIn.addEventListener('click', function(e) {
	e.preventDefault();
});
```

To make the area lose focus, use:
```
inputLogin.blur();
```
