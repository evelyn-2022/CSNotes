# CSS selectors

## Child Selector

Matches an element that is a direct child of another:

```css
li > a {
}
```

Targets any `<a>` elements that are children of an `<li>` element (but not other `<a>` elements in the page).

## Descendant Selector

Matches an element that is a descendent of another specified element (<u><i>not just a direct child</i></u> of that element):

```css
p a {
}
```

Targets any `<a>` elements that sit inside a `<p>` element, even if there are other elements nested between them.

## Adjacent Sibling Selector

Matches an element that is the next sibling of another:

```css
h1 + p {
}
```

Targets the first `<p>` element after any `<h1>` element (but not other `<p>` elements).

## General Sibling Selector

Matches an element that is a sibling of another, although it does not have to be the directly preceding element:

```css
h1 ~ p {
}
```

If you had two `<p>` elements that are siblings of an `<h1>` element, this rule would apply to both.

## `Attribute` Selectors

### Existence `[]`

Matches a specific attribute (whatever its value):

```css
p[class]
```

Targets any `<p>` element with an attribute called class.

### Equality `[=]`

```css
p[class="dog"]
```

Targets any `<p>` element with an attribute called class whose value is dog.

```css
[type="radio"] {
  margin: 20px 0px 20px 0px;
}
```

Changes the margins of all elements with the attribute `type` and a corresponding value of radio.

### Space `[~=]`

Matches a specific attribute whose value appears in a space-separated list of words.

```css
p[class~="dog"]
```

Targets any `<p>` element with an attribute called class whose value is a list of space-separated words, one of which is dog.

### Prefix `[^=]`

Matches a specific attribute whose value begins with a specific string.

```css
p[attr^"d"]
```

Targets any `<p>` element with an attribute whose value begins with the letter "d".

### Substring `[*=]`

Matches a specific attribute whose value contains a specific substring.

```css
p[attr*"do"]
```

Targets any `<p>` element with an attribute whose value contains the letter "do".

### Suffix `[$=]`

Matches a specific attribute whose value ends with a specific string.

```css
p[attr$"g"]
```

Targets any `<p>` element with an attribute whose value ends with the letter "g".
