# Responsive Web Design

[toc]

## Create a Media Query

Media Queries are a new technique introduced in CSS3 that *change the presentation of content based on different viewport sizes*. The viewport is a user's visible area of a web page, and is different depending on the device used to access the site.

Media Queries consist of a media type, and if that media type matches the type of device the document is displayed on, the styles are applied. You can have as many selectors and styles inside your media query as you want.

Here's an example of a media query that returns the content when the device's width is less than or equal to 100px:
```
@media (max-width: 100px) { /* CSS Rules */ }
```

Remember, the CSS inside the media query is applied only if the media type matches that of the device being used.

Example: 
Add a media query, so that the `p` tag has a font-size of 10px when the device's height is less than or equal to 800px.

```
<style>
  p {
    font-size: 20px;
  }

  @media (max-height: 800px) {
    p {
      font-size: 10px;
    }
  }
</style>

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus quis tempus massa. Aenean erat nisl, gravida vel vestibulum cursus, interdum sit amet lectus.</p>
```

<br>

---

## Make an Image Responsive

Making images responsive with CSS is actually very simple. You just need to add these properties to an image:
```
img {
  max-width: 100%;
  height: auto;
}
```

The max-width of 100% will make sure the image is never wider than the container it is in, and the height of auto will make the image keep its original aspect ratio (*<u>The aspect ratio is the ratio between the width and height of the screen</u>)*.

[Make an Image Responsive](https://codepen.io/ZoeyClyde/pen/eYGZdZX)
After you have added your code, resize the preview to see how your images behave.

<br>

---

## Use a Retina Image for Higher Resolution Displays

Pixel density is an aspect that could be different on one device from others and this density is known as *Pixel Per Inch(PPI)* or *Dots Per Inch(DPI)*. The most famous such display is the one known as a "**Retina Display**" on the latest Apple MacBook Pro notebooks, and recently iMac computers. Due to the difference in pixel density between a "Retina" and "Non-Retina" displays, some images that have not been made with a High-Resolution Display in mind could look "pixelated" when rendered on a High-Resolution display.

The simplest way to make your images properly appear on High-Resolution Displays, such as the MacBook Pros "retina display" is to define their width and height values **as only half of what the original file is**.

Example:
Set the width and height of the img tag to half of their original values. In this case, both the original height and the original width are 200px.
```
<style>
  img { height: 100px; width: 100px; }
</style>

<img src="https://s3.amazonaws.com/freecodecamp/FCCStickers-CamperBot200x200.jpg" alt="freeCodeCamp sticker that says 'Because CamperBot Cares'">
```

<style>
  img { height: 100px; width: 100px; }
</style>

<img src="https://s3.amazonaws.com/freecodecamp/FCCStickers-CamperBot200x200.jpg" alt="freeCodeCamp sticker that says 'Because CamperBot Cares'">

<br>
<br>

---

### Make Typography Responsive

Instead of using `em` or `px` to size text, you can use **viewport units** for responsive typography. Viewport units, like percentages, are *relative units*, but they are based off different items. **Viewport units are relative to the viewport dimensions (width or height) of a device**, and percentages are relative to the size of the parent container element.

The four different viewport units are:

- **vw** (viewport width): 10vw would be 10% of the viewport's **width**.
- **vh** (viewport height): 3vh would be 3% of the viewport's **height**.
- **vmin** (viewport minimum): 70vmin would be 70% of the viewport's **smaller dimension** (height or width).
- **vmax** (viewport maximum): 100vmax would be 100% of the viewport's **bigger dimension** (height or width).

Example: 
Set the width of the h2 tag to 80% of the viewport's width and the width of the paragraph as 75% of the viewport's smaller dimension.

```
<style>
  h2 {
    width: 80vw;
  }

  p {
    width: 75vmin;
  }
</style>

<h2>Importantus Ipsum</h2>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus quis tempus massa. Aenean erat nisl, gravida vel vestibulum cursus, interdum sit amet lectus.</p>
```

[viewport units](https://codepen.io/ZoeyClyde/pen/ExwKgLV)