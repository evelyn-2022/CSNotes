# HTML: Links

## Linking to an Email Address

- To create an email link, the href attribute value needs to start with `mailto:` followed by the email address to which the email should be sent. To create an email link to shay@ awesome.com, for example, the href attribute value would be `mailto:shay@awesome.com`.
- To add a _<u>subject line</u>_, we’ll include the `subject=` parameter after the email address. The first parameter following the email address must begin with a question mark, `?`, to bind it to the hyperlink path. Multiple words within a subject line require that spaces be encoded using `%20`.
- Adding _<u>body text</u>_ works in the same way as adding the subject, this time using the `body=` parameter in the href attribute value. Because we are binding one parameter to another, we need to use the ampersand, `&`, to separate the two. As with the subject, spaces must be encoded using `%20`, and line breaks must be encoded using `%0A`.

Here’s the full breakdown:

```html
<a
  href="mailto:13092257456@163.com?subject=Reaching%20Out&body=Hello,%20Zoey.%0AHow%20are%20you?"
  >Email Me</a
>
```

<a href="mailto:13092257456@163.com?subject=Reaching%20Out&body=Hello,%20Zoey.%0AHow%20are%20you?">Email Me</a>

## Linking to a Specific Part of the Same Page

We can create an on-page link by first setting an `id` attribute on the element we wish to link to, then using the value of that `id` attribute within an anchor element’s `href` attribute:

```html
<a href="#contacts-header">Contacts</a>
......
<h2 id="contacts-header">Contacts</h2>
```

### Linking to a Specific Part of Another Page

As long as the page you are linking to has `id` attributes that identify specific parts of the page, you can simply <u>add the id attribute to the end of the link for that page</u>.

```html
<a href="http:/www.htmlandcssbookcom/#contact-header"></a>
```

## Turn an Image into a Link

You can make elements into links by nesting them within an `a` element. Nest your image within an a element. Here's an example:

```html
<a href="#"
  ><img
    src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg"
    alt="Three kittens running towards the camera."
/></a>
```

<a href="#"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="Three kittens running towards the camera."></a>

Hover over your image with your cursor. Your cursor's normal pointer should become the link clicking pointer. The photo is now a link.

==Note:== Make <u>_Dead Links_</u> Using the Hash Symbol
Sometimes you want to add `<a>` elements to your website before you know where they will link. Use `href="#"` to create a dead link.
