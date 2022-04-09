# Styles

To set the style of an element:

```
elem.style.backgroundColor = '#37383d';
```

To print the style of an element:

```
console.log(elem.style.background);
// Can only print inline styles set in html

console.log(getComputedStyle(elem).color);
// Can get all kinds of values, returns a string
```

To use this to compute values:

```
elem.style.height = Number.parseFloat(getComputedStyle(elem).height, 10) + 40 + 'px';

// Add 40 to height
```


To change a property:

```
document.documentElement.style.setProperty('--color-primary', 'oranged');
// Change the custom property to orange
```

To get the attribute of an element:
```
const logo = document.querySelector('.nav__logo');
logo.alt = 'beautiful logo'
// Select the logo and change its attribute

console.log(document.querySelector('.nav__logo').className)
// Print the class name
```

This is silimar to `getAttribute` and `setAttribute`.

The difference is that when `src` is set as relative path, `logo.src` will print the *absolute path* while `getAttribute('src')` will get the *relative path*. The same is true for links `href`.

### Data attributes

Data attributes are a special kind of attributes that start with the words *data*.

```
<img class='nav__logo' data-version-number = '3.0'>

// To get the value
console.log(logo.dataset.versionNumber('href'))
```

### Classlist

```
logo.classList.add('newClass');
logo.classList.remove('newClass');
logo.classList.toggle('newClass');
logo.classList.contains('newClass');
```



