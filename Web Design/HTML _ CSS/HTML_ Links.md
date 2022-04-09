# HTML: Links

[toc]

## Link to **External** Pages

Hyperlinks are established using the anchor, `<a>`, inline-level element `<a>` elements need a destination web address called an `href` *<u>(Hypertext Reference)</u>* attribute. They also need **anchor text**. Here's an example: 
```
<a href="https://www.freecodecamp.org">anchor text: this links to freecodecamp.org</a>
```
<a href="https://www.freecodecamp.org">anchor text: this links to freecodecamp.org</a>

### Open Link in a New Window
 `target` is an anchor tag attribute that specifies where to open the link. The value `_blank` specifies to open the link in a new window. 
```
<a href="https://www.freecodecamp.org" target="_blank"> a new window </a>
```
<a href="https://www.freecodecamp.org" target="_blank"> a new window </a>

### Relative & Absolute Paths

Links pointing to other pages of the same website will have a *relative path*, which does not include the domain (.com, .org, .edu, etc.) in the href attribute value. Because the link is pointing to another page on the same website, the href attribute value needs to include only the filename of the page being linked to.
Linking to other websites outside of the current one requires an *absolute* path, where the href attribute value must include the full domain.

```
<!-- Relative Path -->
<!-- Child Folder -->
<a href="music/listings.html">Listings</a>
<!-- Parent Folder -->
<a href="../index.html">Home</a>
<!-- Grandparent Folder -->
<a href="../../index.html">Home</a>

<!-- Absolute Path -->
<a href="http://www.google.com/">Google</a>
```

### Linking to an Email Address
- To create an email link, the href attribute value needs to start with `mailto:` followed by the email address to which the email should be sent. To create an email link to shay@ awesome.com, for example, the href attribute value would be `mailto:shay@awesome.com`.
- To add a *<u>subject line</u>*, we’ll include the `subject=` parameter after the email address. The first parameter following the email address must begin with a question mark, `?`, to bind it to the hyperlink path. Multiple words within a subject line require that spaces be encoded using `%20`.
- Adding *<u>body text</u>* works in the same way as adding the subject, this time using the `body=` parameter in the href attribute value. Because we are binding one parameter to another, we need to use the ampersand, `&`, to separate the two. As with the subject, spaces must be encoded using `%20`, and line breaks must be encoded using `%0A`.

Here’s the full breakdown:
```
<a href="mailto:13092257456@163.com?subject=Reaching%20Out&body=Hello,%20Zoey.%0AHow%20are%20you?">Email Me</a>
```
<a href="mailto:13092257456@163.com?subject=Reaching%20Out&body=Hello,%20Zoey.%0AHow%20are%20you?">Email Me</a>

<br>
<br>
<hr>

## Link to **Internal** Sections of a Page

### Linking to a Specific Part of the Same Page

We can create an on-page link by first setting an `id` attribute on the element we wish to link to, then using the value of that `id` attribute within an anchor element’s `href` attribute:
```
<a href="#contacts-header">Contacts</a>
......
<h2 id="contacts-header">Contacts</h2>
```

### Linking to a Specific Part of Another Page

As long as the page you are linking to has `id` attributes that
identify specific parts of the page, you can simply <u>add the id attribute to the end of the link for that page</u>.

```
<a href="http:/www.htmlandcssbookcom/#contact-header">
```

<br>
<br>
<hr>

##  Turn an Image into a Link

You can make elements into links by nesting them within an `a` element. Nest your image within an a element. Here's an example:
```
<a href="#"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="Three kittens running towards the camera."></a>
```

<a href="#"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="Three kittens running towards the camera."></a>

Hover over your image with your cursor. Your cursor's normal pointer should become the link clicking pointer. The photo is now a link.

==Note:== Make <u>*Dead Links*</u> Using the Hash Symbol
Sometimes you want to add `<a>` elements to your website before you know where they will link. Use `href="#"` to create a dead link.

<br>
<br>
<hr>

## Cursor Styles

The `cursor` property allows you to control the type of mouse cursor that should be displayed
to users. Here are the most commonly used values for this property: auto, crosshair, default, pointer, move, text, wait, help, url("cursor.gif").
