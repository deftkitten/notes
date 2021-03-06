# Table of Contents

[**HTML Elements**](#html-elements)
- [Main Body](#main-body)
- [Sub-Elements](#sub-elements)
- [Forms](#forms)
- [Div](#div)
- [Basic Page Structure](#basic-page-structure)
- [ID Attribute](#id-attribute)
- [Body Elements](#body-elements)

[**Accessibility**](#accessibility)
- [Label Tags](#label-tags)
- [Using `fieldset` for Radio Buttons](#using-fieldset-for-radio-buttons)
- [Accessible Date Picker](#accessible-date-picker)
- [Standardize Times with `datetime` Attribute](#standardize-times-with-datetime-attribute)
- [Give Links Meaning](#give-links-meaning)
- [Make Links Navigatable with HTML Access Keys](#make-links-navigatable-with-html-access-keys)
- [Using `tabindex`](#using-tabindex)


# HTML Elements

## Main Body

- `<h1>`  heading - should only use one `<h1>` element in a page (for accessibility reasons)
- `<p>`   paragraph
- `<br>`  break line
- `<!--`  comment here    `-->`
- `<head>` this is NOT a header, metadata elements, such as `link`, `meta`, `title`, and `style` typically go inside the head element.
- `<main>` - has an embedded landmark feature that assistive technology can use to quickly navigate to the main content
- `<header>` - used to wrap introductory information or navigation links for its parent tag, and works well around content that's repeated at the top on multiple pages
  - shares the embedded landmark feature you saw with main, allowing assistive technologies to quickly navigate to that content
- `<footer>` - has a built-in landmark feature that allows assistive devices to quickly navigate to it. It's primarily used to contain copyright information or links to related documents that usually sit at the bottom of a page
- `<nav>` - another HTML5 item with the embedded landmark feature for easy screen reader navigation. This tag is meant to wrap around the main navigation links in your page
- `<article>` - a sectioning element, and is used to wrap independent, self-contained content. The tag works well with blog entries, forum posts, or news articles.
- `<section>` - for grouping thematically related content
- `<audio> ` - gives semantic meaning when it wraps sound or audio stream content in your markup
  - Audio content also needs a text alternative to be accessible to people who are deaf or hard of hearing
  - This can be done with nearby text on the page or a link to a transcript
  - the `controls` attribute shows the browser default play, pause, and other controls, and supports keyboard functionality
  - Example: 

    ```
    <audio id="meowClip" controls>
      <source src="audio/meow.mp3" type="audio/mpeg" />
      <source src="audio/meow.ogg" type="audio/ogg" />
    </audio>
    ```
- `<figure>` and `<figcaption>`
  - Example:

```
<figure>
  <img src="roundhouseDestruction.jpeg" alt="Photo of Camper Cat executing a roundhouse kick">
  <br>
  <figcaption>
    Master Camper Cat demonstrates proper form of a roundhouse kick.
  </figcaption>
</figure>
```

## Sub-Elements

**image** - `<img src="url" alt="alt text">`

**link to url** - `<a href="url">link title as shown in-line</a>`

**link to internal sections**
```
<a href="#contacts-header">Contacts</a>
...
<h2 id="contacts-header">Contacts</h2>
```

**dead link (to be updated later)** - set `href="#" `

make an image a link: `<a href="#"><img src="url" alt="alt text"></a>`

bulleted ordered list:
```
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

ordered list:
```
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

text field with placeholder: `<input type="text" placeholder="this is placeholder text">`

## Forms

Basic Form:
`<form action="/url-where-you-want-to-submit-form-data"></form>`

Form with radio buttons, checkboxes, required text inputs, and pre-checked items:
```
 <form action="/submit-cat-photo">
   <label><input type="radio" name="indoor-outdoor" checked> Indoor</label>
   <label><input type="radio" name="indoor-outdoor"> Outdoor</label><br>
   <label><input type="checkbox" name="personality" checked> Loving</label>
   <label><input type="checkbox" name="personality"> Lazy</label>
   <label><input type="checkbox" name="personality"> Energetic</label><br>
   <input type="text" placeholder="cat photo URL" required>
   <button type="submit">Submit</button>
 </form>
  ```
  
## Div
  
The div element, also known as a division element, is a general purpose container for other elements.
`<div> ... </div>`

## Basic Page Structure

DOCTYPE tells the browser which version of HTML you're using
```
<!DOCTYPE html>
<html>
  <!-- Your HTML code goes here -->
</html>
```
every HTML document has a `body` element

## ID Attribute
id attributes should be UNIQUE, as they are used by javascript and to select specific elements in CSS
`<h2 id="cat-photo-app">`

class declarations take precedence according to chronological order  
id declarations override class declarations

## Body Elements

| element | purpose | CSS equivalent|
|---|---|---|
|`<strong>`|bold|font-style: bold\
|`<hr>`|separation line|none|

# Accessibility

## Label Tags  
- The `for` attribute on a label tag explicitly associates that label with the form control and is used by screen readers.
```
<form>
  <label for="name">Name:</label>
  <input type="text" id="name" name="name">
</form>
```  
\*Note: The value of the `for` attribute must be the same as the value of the `id` attribute of the form control

## Using `fieldset` for Radio Buttons  

there's a way to semantically show the choices are part of a set.

EXAMPLE:
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

__Why use fieldset?__  
This allows each radio button to be labeled while also providing a label for the group as a whole. This is especially important where assistive technology (such as a screen reader) is being used where the association of the controls and their legend cannot be implied by visual presentation

Tips:
- The `fieldset` wrapper and `legend` tag are not necessary when the choices are self-explanatory, like a gender selection. Using a `label` with the `for` attribute for each radio button is sufficient.  

## Accessible Date Picker  

```
<label for="input1">Enter a date:</label>
<input type="date" id="input1" name="input1">
```  

## Standardize Times with `datetime` Attribute  

```
<time datetime="2013-02-13">last tuesday</time>
```

This is the value accessed by assistive devices. It helps avoid confusion by stating a standardized version of a time, even if it's written in an informal or colloquial manner in the text.  

## Give Links Meaning  

A screen reader option is to only hear the links available on a page. Screen readers do this by reading the link text, or what's between the anchor (a) tags. Make the clickable part of the sentence the part that's informative:

"_Click here_ for our nutritional information" is different than "Click here for our _nutritional information_"

EXAMPLE: `<p>Click here for <a href="">information about batteries<a href=""></p>`  

## Make Links Navigatable with HTML Access Keys

HTML5 allows this attribute to be used on any element, but it's particularly useful when it's used with interactive ones. This includes links, buttons, and form controls.

EXAMPLE: `<button accesskey="b">Important Button</button>`

## Using `tabindex`  

Certain elements, such as links and form controls, automatically receive keyboard focus when a user tabs through a page. It's in the same order as the elements come in the HTML source markup. This same functionality can be given to other elements, such as div, span, and p, by placing a tabindex="0" attribute on them. 

EXAMPLE: `<div tabindex="0">I need keyboard focus!</div>`  

`tabindex` also enables the CSS pseudo-class `:focus` to work on the p tag.
