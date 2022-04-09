# Basic HTML 

[toc]

## Elements

*Elements* are designators that define the structure and content of objects within a page. It generally includes a <u>start tag, element content and end tag</u>. Some elements have no content or end tag (like the `<br>` `<img>` element), are called empty (self-closing) elements. 

<br>
<br>

### Semantic Markup

#### Headings 

Headings are block-level elements, and come in six different rankings, `<h1>` through `<h6>`. Each page should always have **one (and only one) `<h1>` element**, which is the main subject of your content.

#### Bold Text with `<strong>`

To make text bold and place a strong importance on it, we’ll use the `<strong>` inline-level element. This is often used to draw attention to text and symbolize that it is important. With the `<strong>` tag, the browser applies the CSS of `font-weight: bold;` to the element.
```
Google was founded by Larry Page and Sergey Brin at <strong>Stanford University</strong>.
```

Google was founded by Larry Page and Sergey Brin at <strong>Stanford University</strong>.

There are two elements that will bold text for us: the `<strong>` and `<b>` elements. The `<strong>` element is semantically used to **give strong importance to text**, and is thus the most popular option for bolding text. The `<b>` element, on the other hand, semantically means to *stylistically offset text*, which isn’t always the best choice for text deserving prominent attention.

#### Italicize Text with Emphasis 

To emphasize text, you can use the `<em>` inline-level element. This displays text as italicized, as the browser applies the CSS of `font-style: italic;` to the element.

As with the elements for bold text, there are two different elements that will italicize text. The `<em>` element is used semantically to **place a stressed emphasis** on text; it is thus the most popular option for italicizing text. The other option, the `<i>` element, is used semantically to convey text in an *alternative voice or tone*, almost as if it were placed in quotation marks.

#### Use the `<u>` Tag to Underline Text
To underline text, you can use the `<u>` tag. This is often used to signify that a section of text is important, or something to remember. With the `<u>` tag, the browser applies the CSS of `text-decoration: underline;` to the element.

#### Use the `<s>` Tag to Strikethrough Text
To strikethrough text, which is when a horizontal line cuts across the characters, you can use the `<s>` tag. It shows that a section of text is no longer valid. With the `<s>` tag, the browser applies the CSS of `text-decoration: line-through;` to the element.
```
<s>to be deleted</s>
```

#### Use  `<abbr>` for Abbreviation

The `<abbr>` is used for abbreviation or acronym. A title attribute in the opening tag is used to specify the full term.

```
<p><abbr title="Professor">Prof</abbr> Stephen
 Hawking is a theoretical physicist and
 cosmologist.</p>
```

#### Use  `<dfn>` for Definition

The `<dfn>` element is used to indicate the defining instance of
a new term.
```
<p>A <dfn>black hole</dfn> is a region of space from
 which nothing, not even light, can escape.</p>
```

#### Use `<address>` to Contain Contact Details

The `<address>` element is used to contain contact details for the author of the page, including a physical address, or a phone number or email address.

Read more about [hCard](https://www.htmlandcssbook.com/extras/introduction-to-hcard/)

####  `<ins>` and `<del>`

The `<ins>` element can be usedto show content that has been inserted into a document, while the `<del>` element can show text that has been deleted from it.
The content of a `<ins>` element is usually underlined, while the content of a `<del>` element usually has a line through it.

```
<p>It was the <del>worst</del> <ins>best</ins> idea she had ever had.</p>
```

<p>It was the <del>worst</del> <ins>best</ins> idea she had ever had.</p>

#### `time` element and `datetime` attribute

HTML5 introduced the `time` element along with a `datetime` attribute to standardize times. The time element is an inline element that can wrap a date or time on a page. A `datetime` attribute holds **a valid format of that date**. This is the value accessed by assistive devices. It helps avoid confusion by stating a standardized version of a time, even if it's informally or colloquially written in the text.
```
<element datetime="YYYY-MM-DDThh:mm:ssTZD"> 
```
T: a required separator; 
ZD: Time Zone Designator (Z denotes Zulu, also known as Greenwich Mean Time).

<br>
<br>

### Structural Markup

HTML5 introduced new structurally based elements, including the `<header>`, `<nav>`, `<article>`, `<section>`, `<aside>`, and `<footer>` elements.

#### Header

The `<header>` element is used to identify the top of a page, article, section, etc. In general, the `<header>` element may include a heading, introductory text, and even navigation.
```
<header>...</header>
```


==Note:== `<header>` vs. `<head>` vs. `<h1>` through `<h6>` elements
- The `<header>` element is a structural element that outlines the heading of a segment of a page. **It falls within the `<body>` element.**
 - The `<head>` element is **not displayed on a page** and is used to outline metadata, including the document title, and links to external files. It falls directly within the `<html>` element.
- Heading elements, `<h1>` through `<h6>`, are used to designate multiple levels of text headings throughout a page.

#### Heading Group

The purpose of the `<hgroup>` element is to group together a set of one or more `<h1>` through `<h6>` elements so that they are treated as one single heading. It has been popular with those developers who believe that it is useful to group together the primary heading and the subheading (as both can be integral parts of a heading).

#### `<main>` element 

The `main` HTML5 tag helps search engines and other developers find the *main content* of your page. There should be **only one per page**. It's meant to surround the information related to your page's central topic. It's not meant to include items that repeat across pages, like navigation links or banners.

The `main` tag also has an embedded **landmark feature** that assistive technology can use to navigate to the main content quickly. If you've ever seen a "*Jump to Main Content*" link at the top of a page, using the `main` tag automatically gives assistive devices that functionality.

#### Navigation

The `<nav>` element identifies a section of major navigational links on a page. The `<nav>` element should be reserved for primary navigation sections only. Most commonly, links included within the `<nav>` element will link to other pages within the same website or to parts of the same web page.

#### Article

`<article>` element is used to wrap independent, self-contained content. The tag works well with blog entries, forum posts, or news articles. When deciding whether to use the `<article>` element, we must determine if the content within the element could be replicated elsewhere without any confusion.

#### Section

The `<section>` element is used to identify a **thematic grouping** of content, which generally, but not always, includes a heading.

==Note:== Deciding Between `<article>`, `<section>`, or `<div>` Elements
- An `article` is for standalone content, and a `section` is for grouping thematically related content. They can be used within each other, as needed. For example, if a book is the `article`, then each chapter is a `section`. 
- When there's no relationship between groups of content, then use a `<div>`.

#### Aside

The `<aside>` element holds content, such as sidebars, inserts, or brief explanations, that is tangentially related to the content surrounding it. When used within an `<article>` element, for example, the `<aside>` element may identify content related to the author of the article.

#### Footer

Similar to `header` and `nav`,  the `footer` element has a built-in landmark feature that allows assistive devices to quickly navigate to it. It's primarily used to contain copyright information or links to related documents that usually sit at the bottom of a page.
```
<footer>&copy; 2018 Camper Cat</footer>
```

==Note:== Encoding Special Characters
Special characters include various punctuation marks, accented letters, and symbols. Each encoded character begins with an ampersand, &, and end with a semicolon, ;. What falls between the ampersand and semicolon is a character's unique encoding, such as copyright: <footer>&copy; 2018 Camper Cat</footer>
For reference, character encoding can be found at https://copypastecharacter.com/.

#### `div` & `span`

`<div>` and `<span>` do not hold any semantic meaning and are simply containers for styling purposes.

A `<div>` is a **block-level** element that is commonly used to identify large groupings of content, and which helps to build a web page’s layout and design. A `<span>`, on the other hand, is an **inline-level** element commonly used to identify smaller groupings of text within a block-level element.
```
<!-- Division -->
<div class="social">
	<p>I may be found on...</p>
	<p>Additionally, I have a profile on...</p>
</div>

<!-- Span -->
<p>Soon we'll be <span class="tooltip">writing HTML</span> with
the best of them.</p>
```

#### HTML Page Structure

The `<title>` element specifies a title for the HTML page, which is shown in the browser's title bar or in the page's tab. The content inside the `<body>` section will be displayed in a browser.

<img src="https://s2.loli.net/2021/12/09/mL5iaqJtMuVTQ97.jpg" alt="page_layout.jpg" width=45%>

[basic layout of a page](https://codepen.io/EvelynWang/pen/oNGxKRB)


<br>
<br>
<hr>

## Attributes

*Attributes* are defined within the opening tag, after an element's name. Generally attributes include a name and a value. The most common attributes include the `id` attribute, `class` attribute, `src` attribute which specifies a source for embeddable content, and `href` attribute, which provides a hyperlink reference to a linked resourse. It is important that no two elements on the same page have the same value for their id attributes, but class attributes can be used more than once.

<br>
<br>
<hr>

## Placeholder Text 

**Placeholder** Text: web developers traditionally use *lorem ipsum* text as placeholder text. The lorem ipsum text is randomly scraped from a famous passage by Cicero of Ancient Rome.

<br>
<br>
<hr>

## Metadata

The `<meta>` element can use attributes to contain information. 

### `name` and `content` attributes

Some defined values for `name` attribute that are commonly used are:

- description: 
This contains a description of the page. This description is commonly used by search engines to understand what the page is about and should be a maximum of 155 characters. Sometimes it is also displayed in search engine results.
- keywords:
This contains a list of comma-separated words that a user might search on to find the page. <u>*In practice, this no longer has any noticeable effect on how search engines index your site.*</u>
- robots: 
This indicates whether search engines should add this page to their search results or not. A value of *noindex* can be used if this page should not be added. A value of *nofollow* can be used if search engines should add this page in their results but not any pages that it links to.

### `http-equiv` and `content` attributes

Three common instances of `http-equiv` attribute:
- author: This defines the author of the web page.
- pragma: This prevents the browser from caching the page. (That is, storing it locally to save time downloading it on subsequent visits.)
- expires: Because browsers often cache the content of a page, the expires option can be used to indicate when the page nshould expire (and no longer be cached). Note that the date must be specified in the format shown.

```
<!DOCTYPE html>
<html>
	<head>
		<title>Information About Your Pages</title>
		<meta name="description" content="An Essay on Installation Art" />
		<meta name="keywords" content="installation, art, opinion" />
		<meta name="robots" content="nofollow" />
		<meta http-equiv="author" content="Jon Duckett" />
		<meta http-equiv="pragma" content="no-cache" />
		<meta http-equiv="expires" content="Fri, 04 Apr 2014 23:59:59 GMT" />
	</head>
	<body>
	</body>
</html>
```

## Metadata

```
<meta name="viewport" content="initial-scale=1, width=device-width">
```