# Applied Visual Design

[toc]

## Basic Property


### Decrease the **Opacity** of an Element

The opacity property in CSS is used to adjust the opacity, or conversely, the transparency for an item. The value given will apply to the entire element, whether that's an image with some transparency, or the foreground and background colors for a block of text.
```
<p style='opacity: 0.5'>example</p>
```

<p style='opacity: 0.5'>example</p>

<br>

---

## Color Theory

### Complementary Colors

The color wheel is a useful tool to visualize how colors relate to each other - it's a circle where similar hues are neighbors and different hues are farther apart. When two colors are opposite each other on the wheel, they are called **complementary colors**. They have the characteristic that if they are **combined**, they "cancel" each other out and create a **gray color**. However, when **placed side-by-side**, these colors appear more vibrant and produce **a strong visual contrast**.

Some examples of complementary colors with their hex codes are:
> red (#FF0000) and cyan (#00FFFF)
green (#00FF00) and magenta (#FF00FF)
blue (#0000FF) and yellow (#FFFF00)

<br>

### Tertiary Colors

Red (R), green (G), and blue (B) are called **primary colors**. Mixing two primary colors creates the **secondary colors** cyan (G + B), magenta (R + B) and yellow (R + G). You saw these colors in the Complementary Colors challenge. ***These secondary colors happen to be the complement to the primary color not used in their creation***, and are opposite to that primary color on the color wheel. For example, magenta is made with red and blue, and is the complement to green.

**Tertiary colors** are the result of combining a primary color with one of its secondary color neighbors. For example, within the RGB color model, red (primary) and yellow (secondary) make orange (tertiary). This adds six more colors to a simple color wheel for a total of twelve.

There are various methods of selecting different colors that result in a harmonious combination in design. One example that can use tertiary colors is called the **split-complementary color scheme**. This scheme starts with a base color, then pairs it with the two colors that are adjacent to its complement. The three colors provide strong visual contrast in a design, but are more subtle than using two complementary colors.

Here are three colors created using the split-complement scheme:
```
<style>
  .orange {
    background-color: #FF7F00;
  }

  .cyan {
    background-color: #00FFFF;
  }
  
  .raspberry {
    background-color: #FF007F;
  }

   .box {
    height: 100px;
    width: 100px;
    margin-bottom: 5px;
  }
</style>

<div class="orange box"></div>
<div class="cyan box"></div>
<div class="raspberry box"></div>
```

<style>
  .orange {
    background-color: #FF7F00;
  }

  .cyan {
    background-color: #00FFFF;
  }

  .raspberry {
    background-color: #FF007F;
  }

   .box {
    height: 100px;
    width: 100px;
    margin-bottom: 5px;
  }
</style>

<div class="orange box"></div>
<div class="cyan box"></div>
<div class="raspberry box"></div>

<br>

### Adjust the Color of Various Elements to Complementary Colors

The strong visual contrast created by complementary colors can be jarring if it's overused on a website, and can sometimes make text harder to read if it's placed on a complementary-colored background. In practice, **one of the colors is usually dominant** and the complement is used to bring visual attention to certain content on the page.

This page will use a shade of teal (#09A7A1) as the dominant color, and its orange (#FF790E) complement to visually highlight the sign-up buttons. Change the background-color of both the header and footer from black to the teal color. Then change the h2 text color to teal as well. Finally, change the background-color of the button to the orange color. [one_dominant_color.html](https://codepen.io/ZoeyClyde/pen/rNGeebG)

<br>

### Adjust the Hue of a Color

Colors have several characteristics including **hue, saturation, and lightness**. CSS3 introduced the `hsl()` property as an alternative way to pick a color by directly stating these characteristics.

Here are a few examples of using `hsl()` with fully-saturated, normal lightness colors:

|Color|HSL|
|:---:|:---:|
|red|hsl(0, 100%, 50%)|
|yellow|hsl(60, 100%, 50%)|
|green|hsl(120, 100%, 50%)|
|cyan|hsl(180, 100%, 50%)|
|blue|hsl(240, 100%, 50%)|
|magenta|hsl(300, 100%, 50%)|

```
<style>
  .green {
    background-color: hsl(120, 100%, 50%);
  }

  .cyan {
    background-color: hsl(180, 100%, 50%);
  }

  .blue {
    background-color: hsl(240, 100%, 50%);
  }

  .block {
    display: inline-block;
    height: 100px;
    width: 100px;
  }
</style>

<div class="green block"></div>
<div class="cyan block"></div>
<div class="blue block"></div>
```

<style>
  .green {
    background-color: hsl(120, 100%, 50%);
  }

  .cyan {
    background-color: hsl(180, 100%, 50%);
  }

  .blue {
    background-color: hsl(240, 100%, 50%);
  }

  .block {
    display: inline-block;
    height: 100px;
    width: 100px;
  }
</style>

<div class="green block"></div>
<div class="cyan block"></div>
<div class="blue block"></div>

<br>

### Adjust the Tone of a Color

The `hsl()` option in CSS also makes it easy to adjust the tone of a color. Mixing white with a pure hue creates a tint of that color, and adding black will make a shade. Alternatively, a tone is produced by adding gray or by both tinting and shading. The saturation percent changes the amount of gray and the lightness percent determines how much white or black is in the color. This is useful **when you have a base hue you like, but need different variations of it**. [adjust_tone_of_color](https://codepen.io/ZoeyClyde/pen/poWyymR)

<br>

### Transform scale Property to Change the Size of an Element

To change the scale of an element, CSS has the `transform` property, along with its `scale()` function. The following code example doubles the size of all the paragraph elements on the page:
```
p {
  transform: scale(2);
}
```

[transform_scale](https://codepen.io/ZoeyClyde/pen/mdBPPZZ)

<br>

<hr>

## Transform Property

### Transform scale Property to Scale an Element on Hover

The `transform` property has a variety of functions that let you scale, move, rotate, skew, etc., your elements. When used with *pseudo-classes* such as `:hover` that specify a certain state of an element, the `transform` property can easily add interactivity to your elements.

```
<style>
  .square4 {
    width: 70%;
    height: 100px;
    margin:  2px auto;
    background: linear-gradient(
      53deg,
      #ccfffc,
      #ffcccf
    );
  }
  .square4:hover {
    transform: scale(1.1);
  }
</style>

<div class='square4'></div>
```

<style>
  .square4 {
    width: 70%;
    height: 100px;
    margin:  2px auto;
    background: linear-gradient(
      53deg,
      #ccfffc,
      #ffcccf
    );
  }
  .square4:hover {
    transform: scale(1.1);
  }


</style>

<div class='square4'></div>

<br>

### Transform Property `skewX` and `skewY` to Skew an Element Along the X-Axis and Y-Axis

The next function of the transform property is `skewX()`, which skews the selected element along its X (horizontal) axis by a given degree. The same for `skewY()`.

The following code skews the paragraph element by -32 degrees along the X-axis.
```
p {
  transform: skewX(-32deg);
}
```


```
<style>
  .pic1 {
    width: 40%;
    height: 50px;
    margin: 25px auto;
  }
  #top {
    background-color: red;
    transform: skewY(-10deg);
  }
  #bottom {
    background-color: blue;
    transform: skewX(24deg);
  }
</style>

<div class='pic1' id="top"></div>
<div class='pic1' id="bottom"></div>
```

<style>
  .pic1 {
    width: 40%;
    height: 50px;
    margin: 25px auto;
  }
  #top {
    background-color: red;
    transform: skewY(-10deg);
  }
  #bottom {
    background-color: blue;
    transform: skewX(24deg);
  }
</style>

<div class='pic1' id="top"></div>
<div class='pic1' id="bottom"></div>

<br>

<hr>

## Create a Shape with CSS and HTML

### Create a Crescent Moon Shape

For this challenge you need to work with the `box-shadow` property that sets the shadow of an element, along with the `border-radius` property that controls the roundness of the element's corners.

You will create a round, transparent object with a crisp shadow that is slightly offset to the side - the shadow is actually going to be the moon shape you see.

In order to create a round object, the `border-radius` property should be set to a value of 50%.

You may recall from an earlier challenge that the `box-shadow` property takes values for `offset-x`, `offset-y`, `blur-radius`, `spread-radius` and a `color` value in that order. The `blur-radius` and `spread-radius` values are optional.

Manipulate the square element in the editor to create the moon shape. First, change the `background-color` to `transparent`, then set the `border-radius` property to 50% to make the circular shape. Finally, change the `box-shadow` property to set the `offset-x` to 25px, the `offset-y` to 10px, `blur-radius` to 0, `spread-radius` to 0, and `color` to blue.

[moon_shape](https://codepen.io/ZoeyClyde/pen/poWyyMe)

<br>

### Create Heart Shape Using CSS and HTML
First, you need to understand the `::before` and `::after` **pseudo-elements**. `::before` creates a *pseudo-element* that is the first child of the selected element; `::after `creates a *pseudo-element* that is the last child of the selected element. In the following example, a :`:before` *pseudo-element* is used to *<u>add a rectangle</u>* to an element with the class heart.
```
.heart::before {
  content: "";
  background-color: yellow;
  border-radius: 25%;
  position: absolute;
  height: 50px;
  width: 70px;
  top: -50px;
  left: 5px;
}
```

**For the `::before` and `::after` *pseudo-elements* to function properly, they must have a defined `content` property.** This property is usually used to add things like a photo or text to the selected element. When the `::before` and `::after` *pseudo-elements* are used to make shapes, the content property is still required, but **it's set to an empty string**. In the above example, the element with the class of heart has a `::before` *pseudo-element* that produces a yellow rectangle with height and width of 50px and 70px, respectively. This rectangle has round corners due to its 25% border-radius and is positioned absolutely at 5px from the left and 50px above the top of the element.

Transform the element on the screen to a heart. In the `heart::after` selector, change the `background-color` to pink and the `border-radius` to 50%.
Next, target the element with the class `heart` (just heart) and fill in the transform property. Use the `rotate()` function with -45 degrees.
Finally, in the `heart::before` selector, set its `content` property to an empty string.

[heart_shape](https://codepen.io/ZoeyClyde/pen/rNGeLBY)

<br>

<hr>

## Animation

### How the CSS @keyframes and animation Properties Work

To animate an element, you need to know about the animation properties and the `@keyframes` rule. The animation properties control how the animation should behave and the `@keyframes` rule controls what happens during that animation. There are eight animation properties in total. This challenge will keep it simple and cover the two most important ones first:
- `animation-name` sets the name of the animation, which is later used by `@keyframes` to tell CSS which rules go with which animations.
- `animation-duration` sets the length of time for the animation.
- `@keyframes` is how to specify exactly what happens within the animation over the duration. This is done by giving CSS properties for specific "frames" during the animation, with percentages ranging from 0% to 100%. If you compare this to a movie, the CSS properties for 0% is how the element displays in the opening scene. The CSS properties for 100% is how the element appears at the end, right before the credits roll. Then CSS applies the magic to transition the element over the given duration to act out the scene. 

Here's an example to illustrate the usage of `@keyframes` and the animation properties:
```
#anim {
  animation-name: colorful;
  animation-duration: 3s;
}

@keyframes colorful {
  0% {
    background-color: blue;
  }
  100% {
    background-color: yellow;
  }
}
```
For the element with the `anim` id, the code snippet above sets the `animation-name` to colorful and sets the `animation-duration` to 3 seconds. Then the `@keyframes` rule links to the animation properties with the name colorful. It sets the color to blue at the beginning of the animation (0%) which will transition to yellow by the end of the animation (100%). You aren't limited to only beginning-end transitions, you can set properties for the element for any percentage between 0% and 100%.

[animation_rainbow](https://codepen.io/ZoeyClyde/pen/WNZwxNx)

<br>

### Use CSS Animation to Change the Hover State of a Button

You can use CSS `@keyframes` to change the color of a button in its hover state.

Here's an example of changing the width of an image on hover. Note that ms stands for milliseconds, where 1000ms is equal to 1s. The `@keyframes` rule should only have an entry for 100%.
```
<style>
  img {
    width: 30px;
  }
  img:hover {
    animation-name: width;
    animation-duration: 500ms;
	animation-fill-mode: forwards; 
  }

  @keyframes width {
    100% {
      width: 40px;
    }
  }
</style>

<img src="https://cdn.freecodecamp.org/curriculum/applied-visual-design/google-logo.png" alt="Google's Logo" />
```
<style>
  img {
    width: 30px;
  }
  img:hover {
    animation-name: width;
    animation-duration: 500ms;
	animation-fill-mode: forwards; 
  }

  @keyframes width {
    100% {
      width: 40px;
    }
  }
</style>

<img src="https://cdn.freecodecamp.org/curriculum/applied-visual-design/google-logo.png" alt="Google's Logo" />

<br>

### Modify Fill Mode of an Animation

Notice how the animation resets after 500ms has passed, causing the button to revert back to the original color. You want the button to stay highlighted.

This can be done by setting the `animation-fill-mode` property to `forwards`. The `animation-fill-mode` specifies the style applied to an element when the animation has finished. You can set it like so:
```
animation-fill-mode: forwards;
```


<br>

### Create Movement Using CSS Animation

When elements have a specified position, such as `fixed` or `relative`, the CSS offset properties right, left, top, and bottom can be used in animation rules to create movement.

As shown in the example below, you can push the item downwards then upwards by setting the top property of the 50% keyframe to 50px, but having it set to 0px for the first (0%) and the last (100%) keyframe.

```
@keyframes rainbow {
  0% {
    background-color: blue;
    top: 0px;
  }
  50% {
    background-color: green;
    top: 50px;
  }
  100% {
    background-color: yellow;
    top: 0px;
  }
}
```
[create-movement-using-css-animation](https://codepen.io/ZoeyClyde/pen/rNGeLap)

<br>

### Create Visual Direction by Fading an Element from Left to Right

You can change the `opacity` of an animated element so it gradually fades as it reaches the right side of the screen.

[create-visual-direction-by-fading-an-element-from-left-to-right](https://codepen.io/ZoeyClyde/pen/QWqNEbG?editors=1010)

<br>

### Animate Elements Continually Using an Infinite Animation Count

Another animation property is the `animation-iteration-count`, which allows you to control how many times you would like to loop through the animation. Here's an example:
```
animation-iteration-count: 3;
```
In this case the animation will stop after running 3 times, but it's possible to make the animation run continuously by setting that value to `infinite`.

[animate-elements-continually-using-an-infinite-animation-count](https://codepen.io/ZoeyClyde/pen/eYGZzJy)

<br>

### Make a CSS Heartbeat using an Infinite Animation Count

The one-second long heartbeat animation consists of two animated pieces. The heart elements (including the `:before` and `:after` pieces) are animated to change size using the `transform` property, and the background div is animated to change its color using the background property.

Keep the heart beating by adding the `animation-iteration-count` property for both the back class and the heart class and setting the value to `infinite`. The `heart:before` and `heart:after` selectors do not need any animation properties.

[make-a-css-heartbeat-using-an-infinite-animation-count](https://codepen.io/ZoeyClyde/pen/qBPZNZQ)


[animate-elements-at-variable-rates](https://codepen.io/ZoeyClyde/pen/ExwKyyp)

<br>

### Change Animation Timing with Keywords

In CSS animations, the `animation-timing-function` property controls how quickly an animated element changes over the duration of the animation. If the animation is a car moving from point A to point B in a given time (your `animation-duration`), the `animation-timing-function` says how the car accelerates and decelerates over the course of the drive.

There are a number of predefined keywords available for popular options. For example, the **default value** is `ease`, which starts slow, speeds up in the middle, and then slows down again in the end. Other options include `ease-out`, which is quick in the beginning then slows down, `ease-in`, which is slow in the beginning, then speeds up at the end, or `linear`, which applies a constant animation speed throughout.

[change-animation-timing-with-keywords](https://codepen.io/ZoeyClyde/pen/poWybEr)

<br>

---

### Bezier Curves

#### How Bezier Curves Work

The last challenge introduced the `animation-timing-function` property and a few **keywords** that change the speed of an animation over its duration. CSS offers an option other than keywords that provides even finer control over how the animation plays out, through the use of **Bezier curves**.

In CSS animations, Bezier curves are used with the `cubic-bezier` function. The shape of the curve represents how the animation plays out. **The curve lives on a 1 by 1 coordinate system. The X-axis of this coordinate system is the duration of the animation (think of it as a time scale), and the Y-axis is the change in the animation**.

The `cubic-bezier` function consists of **four main points** that sit on this 1 by 1 grid: p0, p1, p2, and p3. **p0 and p3 are set for you** - they are the **beginning and end points** which are always located respectively at the origin **(0, 0) and (1, 1)**. You set the x and y values for the other two points, and where you place them in the grid dictates the shape of the curve for the animation to follow. This is done in CSS by declaring the x and y values of the p1 and p2 "anchor" points in the form: (x1, y1, x2, y2). Pulling it all together, here's an example of a Bezier curve in CSS code:
```
animation-timing-function: cubic-bezier(0.25, 0.25, 0.75, 0.75);
```

In the example above, the x and y values are equivalent for each point (x1 = 0.25 = y1 and x2 = 0.75 = y2), which if you remember from geometry class, results in a line that extends from the origin to point (1, 1). This animation is a **linear** change of an element during the length of an animation, and is the same as using the linear keyword. In other words, it changes at a constant speed.

<br>

#### Make Motion More Natural Using a Bezier Curve

The `animation-timing-function` automatically loops at every `keyframe` when the `animation-iteration-count` is set to `infinite`. Since there is a keyframe rule set in the middle of the animation duration (at 50%), it results in *two identical animation progressions at the upward and downward movement of the ball*.

The following cubic Bezier curve simulates a juggling movement:
```
<style>
  .balls {
    border-radius: 50%;
    position: fixed;
    width: 50px;
    height: 50px;
    top: 60%;
    animation-name: jump;
    animation-duration: 2s;
    animation-iteration-count: infinite;
  }
  #red {
    background: red;
    left: 25%;
    animation-timing-function: linear;
  }
  #blue {
    background: blue;
    left: 50%;
    animation-timing-function: ease-out;
  }
  #green {
    background: green;
    left: 75%;
    animation-timing-function: cubic-bezier(0.311, 0.441, 0.444, 1.649);
  }

  @keyframes jump {
    50% {
      top: 10%;
    }
  }
</style>
<div class="balls" id="red"></div>
<div class="balls" id="blue"></div>
<div class="balls" id="green"></div>
```
Notice that the value of *y2* is larger than 1. Although the cubic Bezier curve is mapped on a 1 by 1 coordinate system, and it can **only accept *x* values from 0 to 1**, **the *y* value can be set to numbers larger than one**. This results in a bouncing movement that is ideal for simulating the juggling ball.

[Make Motion More Natural Using a Bezier Curve](https://codepen.io/ZoeyClyde/pen/KKXzMNq)