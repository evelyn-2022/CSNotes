# Adding Media

## Adding Images

To add images to a page, we use the `<img>` inline element. The `<img>` element is a selfcontaining, or empty, element. You can also use the `title` attribute with the `<img>` element to provide additional information about the image. Most browsers will display the content of this attribute in a tootip when the user hovers over the image.

```html
<img src="logo.png" alt="logo" title="logo" />
```

### Note:

1. Support Image Formats: We most commonly see **jpg images used for photographs** and **png images used for icons or background patterns**. When a picture has an area that is filled with exactly the same color, it is known as **flat color**. Logos, illustrations, and diagrams often use flat colors. (Note that photographs of snow, sky, or grass are not flat colors, they are made up of many subtly different shades of the same color and are not as suited to GIF or PNG format.)
   JPGs, GIFs, and PNGs belong to a type of image format known as **bitmap**. They are made up of lots of miniature squares. **Vector images** are commonly created in programs such as Adobe Illustrator by placing points on a grid, and drawing lines between those points. A color can then be added to "fill in" the lines that have been created.
2. You should save the image at <u>the same width and height</u> it will appear on the website. If the image is smaller than the width or height that you have specified, the image can be distorted and stretched. If the image is larger than the width and height if you have specified, the image will take longer to display on the page.
3. Most computer screens only show web pages at 72 pixels per inch (**72 ppi**). So saving images at a higher resolution results in images that are larger than necessary and take longer to download.
   Images in print materials (such as books and magazines) are made up of tiny circles called <i><u>dots</u></i>. These images are usually printed at a resolution of <i><u>300 dots per inch (dpi)</u></i>.
4. If the image is purely decorative, using an **empty alt attribute** is a best practice.
   ```html
   <img src="visualDecoration.jpeg" alt="" />
   ```

### Sizing Images

One option is to use the width and height attributes directly within the `<img>` tag in HTML. Additionally, images may be sized using the width and height properties in CSS. When both the HTML attributes and CSS properties are used, **the CSS attributes will take precedence over the HTML attributes**.

Specifying either a width or height will cause the other dimension to adjust automatically to maintain the _aspect ratio_ of the image.

### `figure` element and the related `figcaption`

Used together, these items wrap a visual representation (like an image, diagram, or chart) along with its caption.

Here's an example - note that the `figcaption` goes inside the `figure` tags and can be combined with other elements:

```html
<figure>
  <img src="cat.jpeg" alt="Photo of Camper Cat" />
  <br />
  <figcaption>
    Master Camper Cat demonstrates proper form of a roundhouse kick.
  </figcaption>
</figure>
```

### loading

The loading attribute on an img element can be set to `lazy` to tell the browser not to fetch the image resource until it is needed (as in, when the user scrolls the image into view). As an additional benefit, lazy loaded elements will not load until the non-lazy elements are loaded - this means users with slow internet connections can view the content of your page without having to wait for the images to load.

---

## Adding Audio

The `<audio>` element requires both opening and closing tags.

### Audio Attributes

The `src` attribute on the `<audio>` element includes **autoplay, controls, loop, and preload.**

The **autoplay, controls, and loop** attributes are all **Boolean attributes**. As Boolean attributes, they **don’t require a stated value**. Instead, when each is present on the `<audio>` element its value will be set to true, and the `<audio>` element will behave accordingly.

- autoplay: nothing will appear on the page, but the audio file will automatically play upon loading.
- controls: display a browser’s default audio controls, including play and pause, seek, and volume controls.
- loop: cause an audio file to repeat continually, from beginning to end.
- preload: helps identify what, if any, information about the audio file should be loaded before the clip is played. It accepts three values: **none**(won't preload any information about audio file), **auto**(will preload all information), and **metadata**(will preload any available metadata information, but not all information). When the preload attribute isn’t present on the `<audio>` element, all information about an audio file is loaded, as if the value was set to `auto`. For this reason, **using the preload attribute with a value of metadata or none** is a good idea when an audio file is not essential to a page. It’ll help to conserve bandwidth and allow pages to load faster.

<hr>

## Adding Video

Adding video in HTML5 is very similar to adding audio. We use the `<video>` element in place of the `<audio>` element. All of the same attributes (src, autoplay, controls, loop, and preload) and fallbacks apply here, too. In general, the best practice here is to include the `controls` Boolean attribute unless there is a good reason not to allow users to start, stop, or replay the video.

Since videos take up space on the page, we can specify their dimensions, which is most commonly done with width and height properties in CSS.

### Poster Attribute

The `poster` attribute allows us to specify an image, in the form of a URL, to be shown before a video is played.

```html
<video src="earth.ogv" controls poster="earth-video-screenshot.jpg"></video>
```

<hr>

## Adding Inline Frames

The `<iframe>` element accepts the URL of another HTML page within the `src` attribute value; this causes the content from the embedded HTML page to be displayed on the current page.

The `<iframe>` element has a few default styles, including an inset border and a width and height. These styles can be adjusted using the **frameborder, width, and height** HTML attributes or by using the **border, width, and height** CSS properties.

### Seamless Inline Frames

The `seamless` Boolean attribute, when present, specifies that the `<iframe>` should look like it is part of the containing document (no borders or scrollbars). Additionally, the `seamless` Boolean attribute allows links clicked on a page referenced within an `<iframe>` element to be opened within the same window as the original page that includes the `<iframe>` element.

```html
<iframe src="contact.html" seamless></iframe>
```
