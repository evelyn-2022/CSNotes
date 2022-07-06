# Building Forms

The `<form>` element identifies where on the page control elements will appear. Additionally, the `<form>` element will wrap all of the elements included within the form, much like a `<div>` element.

A handful of different attributes can be applied to the `<form>` element, the most common of which are **action** and **method**. The `action` attribute contains the URL to which information included within the form will be sent for processing by the server.

There are two methods, `get` and `post`.
With the **get** method, the values from the form are added to the end of the URL specified in the action attribute. The get method is ideal for:

- short forms (such as search boxes)
- when you are just retrieving data from the web server (not sending information that should be added to or deleted from a database)

With the **post** method the values are sent in what are known as <u><i>HTTP headers</i></u>. As a rule of thumb you should use the post method if your form:

- allows users to upload a file
- is very long
- contains sensitive data (e.g. passwords)
- adds information to, or deletes information from, a database

If the `method` attribute is not used, the form data will be sent using the `get` method.

## Text Fields & Textareas

When it comes to gathering text input from users, there are a few different elements available for obtaining data within forms.

The `<input>` element is used to obtain text from users.

- `type` attribute: define what type of information is to be captured within the control. The most popular type attribute value is `text`, which denotes a single line of text input.
- `name` attribute: is used as the name of the control and is submitted along with the input data to the server.
- `maxlength` attribute: to limit the number of characters a user may enter into the text field. Its value is the number of characters they may enter.

==Note:== make sure there is a space between the element and the text.

```html
<input type="checkbox" /> Loving
```

## Multiple Choice Inputs & Menus

### Radio Buttons

Radio buttons permit users to select one option only, as opposed to multiple options.

- type:
  To create a radio button, the `<input>` element is used with `type="radio";`.
  To create a radio button, the `<input>` element is used with `type="radio";`.
  To create a radio button, the `<input>` element is used with `type="radio";`.
- id:
  The id attribute is used to identify specific HTML elements.
  The id attribute is used to identify specific HTML elements.
  The id attribute is used to identify specific HTML elements.
- name:
  Each radio button element should have <em><u>**the same name attribute value**</u></em> so that all of the buttons within a group correspond to one another. In other words, **to make it so selecting one radio button automatically deselects the other**, both buttons must have a `name` attribute with the same value.
- value:
  When a form gets submitted, the form data for the button is based on its **_name and value attributes_**. Inputs of type radio and checkbox report their values from the `value` attribute.

```html
<label for="indoor">
  <input
    id="indoor"
    value="indoor"
    type="radio"
    name="indoor-outdoor"
    checked
  />Indoor
</label>
<label for="outdoor">
  <input
    id="outdoor"
    value="outdoor"
    type="radio"
    name="indoor-outdoor"
  />Outdoor
</label>
```

Here, you have two radio inputs. When the user submits the form with the indoor option selected, the form data will include the line: **_indoor-outdoor=indoor_**. This is from the `name` and `value` attributes of the "indoor" input.

If you omit the value attribute, the submitted form data uses the default value, which is `on`. In this scenario, if the user clicked the "indoor" option and submitted the form, the resulting form data would be **_indoor-outdoor=on_**, which is not useful. So the `value` attribute needs to be set to something to identify the option.

Additionally, to preselect a radio button for users we can use the Boolean attribute **checked**.

### Check Boxes

Check boxes `type="checkbox"` are very similar to radio buttons. The difference between the two is that check boxes allow users to select multiple values and tie them all to one control name, while radio buttons limit users to one value.

### Drop-Down Lists

To create a drop-down list we’ll use the `<select>` and `<option>` elements. The `<select>` element wraps all of the menu options, and each menu option is marked up using the
`<option>` element.
The **name** attribute resides on the `<<select>` element, and the **value** attribute resides on the `<option>` elements that are nested within the `select>` element.

```
<select name="day" multiple>
	<option value="Friday" selected>Friday</option>
	<option value="Saturday">Saturday</option>
	<option value="Sunday">Sunday</option>
</select>
```

Much like the checked Boolean attribute for radio buttons and check boxes, drop-down menus can use the **selected** Boolean attribute to preselect an option for users.

#### Multiple Selection

The Boolean attribute **multiple**, when added to the `<select>` element for a standard drop-down list, allows a user to choose more than one option from the list at a time.

#### Multiple Select Box

You can turn a drop down select box into a box that shows more than one option by adding the `size` attribute. Its value should be the number of options you want to show at once.

```html
<form action="http://www.example.com/profile.php">
  <p>
    Do you play any of the following instruments? <br />
    (You can select more than one option by holding down control on a PC o r
    command key on a Mac while selecting different options.)
  </p>
  <select name="instruments" size="3" multiple>
    <option value="guitar" selected="selected">Guitar</option>
    <option value="drums">Drums</option>
    <option value="keyboard" selected="selected">Keyboard</option>
    <option value="bass">Bass</option>
  </select>
</form>
```

It is helpful to indicate that on a PC users should hold down the <i><u>control</u></i> key while selecting multiple options and on a Mac they should use the <i><u>command</u></i> key while selecting options.

<hr>

## Submit

After a user inputs the requested information, buttons allow the user to put that information into action. Most commonly, a submit input or submit button is used to process the data.

### Submit Input

The submit button is created using the `<input>` element with `type="submit"`. The **value** attribute is used to specify **the text that appears within the button**.

```html
<input type="submit" name="submit" value="Send" />
```

### Use Image Button

If you want to use an image for the submit button, you can give
the `type=image`.

```html
<form action="http://www.example.com/upload.php" method="post">
  <p>Upload your song in MP3 format:</p>
  <input type="file" name="user-song" /><br />
  <input type="image" src="3311729024751126.jpg" width="100" height="80" />
</form>
```

### Submit Button

The `<button>` element was introduced to allow users more control over how their buttons appear, and to allow other elements to appear inside the button. This means that you can combine text and images between the opening and closing `</button>` tag.

Rather than using the `value` attribute to control the text within the submit button, the text that appears between the opening and closing tags of the `<button>` element will appear.

```html
<form action="http://www.example.com/add.php">
  <button><img src="star.jpg" alt="add" width="100" height="50" /> Add</button>
</form>
```

<img src="https://s2.loli.net/2021/12/16/bUZWH4KBGnVYuxS.png" >

<hr>

## Organizing Form Elements

### Label

Labels provide captions or headings for form controls. It can be used in two ways:

1. Wrap around both the text description and the form input (as shown on the first line of the example).
2. Be kept separate from the form control and use the `for` attribute to indicate which form control it is a label for (as shown with the radio buttons). The value of the `for` attribute should be the same as the value of the `id` attribute on the form control the label corresponds to. Matching up the **for and id attribute values** ties the two elements together, allowing users to click on the `<label>` element to bring focus to the proper form control. The position of the label is very important:
   - Above or to the left:
   - Above or to the left:
   - Above or to the left:
     - Text inputs
     - Text areas
     - Select boxes
     - File uploads
   - To the right:
     - Individual checkboxes
     - Individual radio buttons

```
<label for="username">Username</label>
<input type="text" name="username" id="username">
```

<img src="https://s2.loli.net/2021/12/16/ZPb54nfYHJoVCzG.png" >

If desired, the `<label>` element may wrap form controls, such as radio buttons or check boxes. Doing so allows omission of the for and id attributes.

```
<label>
	<input type="radio" name="day" value="Friday" checked> Friday
</label>
<label>
	<input type="radio" name="day" value="Saturday"> Saturday
</label>
```

### Fieldset

Much like a `<section>` or other structural element, the `<fieldset>` is a block-level element that wraps related elements, specifically within a `<form>` element, for better organization.
Fieldsets, by default, also include a border outline, which can be modified using CSS.

### Legend

A `legend` provides a caption, or heading, for the `<fieldset>` element. The `<legend>` element wraps text describing the form controls that fall within the fieldset. The markup should include the `ledend` element directly after the opening `<fieldset>` tag.

```
<form>
  <fieldset>
    <legend>Choose one of these three items:</legend>
    <input id="one" type="radio" name="items" value="one">
    <label for="one">Choice One</label><br>
    <input id="two" type="radio" name="items" value="two">
    <label for="two">Choice Two</label><br>
    <input id="three" type="radio" name="items" value="three">
    <label for="three">Choice Three</label>
  </fieldset>
</form>
```

<img src="https://s2.loli.net/2021/12/07/txQCdwZuPSs9m7b.png" alt="field_set.png">

<br>
<br>
<hr>

## Form & Input Attributes

### Disabled

The `disabled` Boolean attribute turns off an element or control so that it is not available for interaction or input.

Applying the disabled Boolean attribute to a `<fieldset>` element will disable all of the form controls within the fieldset.

```
<label>
	Username
	<input type="text" name="username" disabled>
</label>
```

### Required

The `required` HTML5 Boolean attribute enforces that an element or form control must contain a value upon being submitted to the server. It also occurs specific to a control’s type.

```
<label>
	Email Address
	<input type="email" name="email-address" required>
</label>
```

<hr>

## Styling Forms

### Aligning Fieldsets & Legends

Labels for form elements are often different lengths, which means that the form controls will not appear in a straight line.
<img src="https://s2.loli.net/2021/12/17/rRMItjviDfQO9wJ.png" width=230 ><img src="https://s2.loli.net/2021/12/17/9a3jm6YXEW1RZxc.png"  width=230>
When the form only contains text inputs, by setting all of the text inputs to be the same width, as well as <i><u>aligning all of the form content to the right</u></i>, the fields line up and the labels are in a consistent place.

```
<style type="text/css">
  fieldset {
    width: 250px;
    border: 1px solid #dcdcdc;
    border-radius: 10px;
    padding: 20px;
    text-align: right;
  }
  legend {
    background-color: #efefef;
    border: 1px solid #dcdcdc;
    border-radius: 10px;
    padding: 10px 20px;
    text-align: left;
    text-transform: uppercase;
  }
  input {
    margin: 10px 0;
  }
</style>

<fieldset>
  <legend>newsletter</legend>
  <label for="name">Name:</label>
  <input type="text" name="name" id="name">
  <br>
  <label for="email">Email:</label>
  <input type="email" name="email" id="email">
</fieldset>
```

For more complex forms below, each row of the form has a `class="title"` telling users what they need to enter. We can use a property called `float` to move the titles to the left of the page. By setting the width property on those elements, we know that the titles will each take up the same width. The text-align property is used to align the titles to the right.
<img src="https://s2.loli.net/2021/12/17/cnrBhzfATq6gx1j.png" width=230>
<img src="https://s2.loli.net/2021/12/17/qjDYcBaV37Kweig.png" width=230>

```
<style type="text/css">
  form {
    text-align: right;
  }
  div {
    margin: 10px;
    padding-bottom: 10px;
    width: 300px;}
  .title {
    float: left;
    width: 100px;
    text-align: right;
    padding-right: 10px;}
  .radio-buttons label {
    float: none;}
</style>
```

```
<form action="example.php" method="post">
  <div>
    <label for="name" class="title">Name:</label>
    <input type="text" id="name" name="name">
  </div>
  <div>
    <label for="email" class="title">Email:</label>
    <input type="email" id="email" name="email">
  </div>
  <div>
    <span class="title">Gender:</span>
    <input type="radio" name="gender" id="male" value="M">
    <label for="male">Male</label>
    <input type="radio" name="gender" id="female" value="F">
    <label for="female">Female</label><br>
  </div>
  <div>
    <input type="submit" value="Register" id="submit">
  </div>
</form>
```

## Searching

```
<form action="https://www.google.com/search" method="get">
	<input name="q" type="text">
	<input type="submit">
</form>
```

When we open the file in our browser, we can use the form to search via Google.
