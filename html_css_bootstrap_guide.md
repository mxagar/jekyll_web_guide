# Basic HTML, CSS, & Bootstrap: A Guide

These are my personal notes related to HTML, CSS, and Bootstrap. They are focused to creating and deploying static web pages with [Jekyll](https://jekyllrb.com): instead of creating HTML & CSS files from the scratch, small snipets need to be written and modified when using Jekyll.

These notes originated from various sources, among others:

- The Udemy course by José Marcial Portilla [Python and Flask Bootcamp: Create Websites using Flask!
](https://www.udemy.com/course/python-and-flask-bootcamp-create-websites-using-flask)
- [How To Build a Website with HTML](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-html?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTOnrDkTx6aH73I-I1zsNt7vZu9Ff_wGEX2sH9OdAfTZFfFIgMjQEIhPFT6WNI9fSXvQkfpC4A-DPSMjP63wwOpcHqLS8pxrjMFocGPg)
- [How To Build a Website With CSS](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-css?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTO6ayIs0-zVCBcnVyVnIMcdi5C9FiraEGRmtV2yzU2wJdb41l3l84ULsvcSqJlPbO1vFqyuQTpTNYUiprIB5BLsYVMxt-1s4LEVnj3A)
- [Intro to Javascript, Udacity](https://www.udacity.com/course/intro-to-javascript--ud803)

Mikel Sagardia, 2022.  
No guarantees.

**Overview of contents**:

1. [HTML](#1.-HTML)
	- [General Notes](#General-Notes)
	- [Basic HTML File Structure](#Basic-HTML-File-Structure)
	- [HTML Tagging: Titles](#HTML-Tagging:-Titles)
	- [Lists](#Lists)
	- [Divs and Spans with HTML](#Divs-and-Spans-with-HTML)
	- [Images and HTML Attributes](#Images-and-HTML-Attributes)
	- [Hyperlinks: Anchor Tags](#Hyperlinks:-Anchor-Tags)
	- [Forms](#Forms)
	- [Other HTML Elements and Notes](#Other-HTML-Elements-and-Notes)
2. [CSS](#2.-CSS)
	- [CSS Stylesheet and Basic Style Definitions](#CSS-Stylesheet-and-Basic-Style-Definitions)
	- [Background, Borders, Divs, Spans](#Background,-Borders,-Divs,-Spans)
	- [CSS Classes and Ids](#CSS-Classes-and-Ids)
	- [Exploring Elements in the Browser](#Exploring-Elements-in-the-Browser)
	- [Fonts](#Fonts)
3. [Bootstrap](#3.-Bootstrap)
	- [Bootstrap Basics](#Bootstrap-Basics)
	- [Forms](#Forms)
	- [Navbars](#Navbars)
4. [Javascript and jQuery](#4.-Javascript-and-jQuery)
5. [Interesting Links](#5.-Interesting-Links)

# 1. HTML

The files generated in this section are located in `06_HTML_basics/`.

Note that Sublime and Atom have HTML file autocompletion.

## General Notes

- HTML files contain the content.
- CSS files define the style.
- Bootstrap automates style elements.
- If we have a dynamic page, we're going to need a database (SQL).
- The programming and handling of the different elements is done with Javascript; however, we can use a web framework, like Flask, which allows programming the behavior in python.
- As we write our page HTML, CSS, etc., if we refresh the main HTML page we should see the changes.

## Basic HTML File Structure

The very basic HTML file create by autocompletion is the following `basic.html`:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>This is my title!</title>
</head>
<body>
This is the content.
</body>
</html>
```

Notes on the code:

- DOCTYPE tells the browser we have an HTML file.
- HTML works with tags that are opened `<html>` and sometimes closed `</html>`.
- We have 2 main parts in a HTML file: 
	- head: metadata, linkings to JS & CSS files, etc.
	- body: content

## HTML Tagging: Titles

In HTML there are elements or tags which have a structural or style meaning: titles, lists, paragraphs, etc.

Heading tags: `<h1>Heading Level 1</h1>`. There are 6 levels: `<h2>, <h3>, ...`

Spaces are not registered unless we use a paragraph tag: `<p>Text</p>`.

Trick: type `lorem + TAB`: Lorem Ipsum text is filled!

Bold and italics: `<p><strong>strong is bold</strong> and <em>emphasis is italics</em></p>
`.

Very important reference link: [Mozilla HTML elements reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

## Lists

Lists can be:

- Numbered, ordered: `<ol>`
- Bullet points, unordered: `<ul>`

Inside a list, no matter the type, we add list elements with `<li>`.

We can also nest lists by just simply adding new lists below a list item.

```html
<p>A numbered list (ordered):</p>

<ol>
	<li>First item</li>
	<li>Second item</li>
	<li>Third item</li>
</ol>

<p>A bullet list (unordered):</p>

<ul>
	<li>First item</li>
	<li>Second item</li>
	<li>Third item</li>
</ul>
```

## Divs and Spans with HTML

With divisions and spans, we can segment the page and later on apply different CSS styles to each segment:

- `<div class="">` is used for larger page divisions in which we link a CSS style class, empty in the following example; if it's empty, nothing happens in the page.
- `<span class="">` is used for sentence parts; we link the CSS style class	as in the division.

```html
<div class="">
	<p>This is a sentence in a division.</p>
</div>

<p>This is in a <span class="">span</span></p>
```

## Images and HTML Attributes

Some HTML tags have attributes or properties, such as `class`, `src`, etc.

Images, for instance, require a `src` for the source URL or path and optionally an `alt`, i.e., alternative image path/URL or string to display if the original image is not found. Additionally:

- Note that the image tag is not self-closing: everything is defined inside a unique image tag.
- Images have further attributes, like `width` and `height`.

```html
<img src="image.jpeg" alt="Uh oh, image not found...">
<img src="https://my.image" alt="Uh oh, image not found...">
<img src="https://my.image" alt="Uh oh, image not found..." width="100">
```

## Hyperlinks: Anchor Tags

Hyperlinks or anchor tags are defined with `<a>`.

```html
<!-- Link to current HTML file -->
<a href="#">This is my link</a>

<!-- Link to an URL -->
<a href="https://mikelsagardia.io">This is my link</a>

<!-- Link to an file -->
<a href="another_page.html">This is my link</a>

<!-- An image with a link -->
<a href="https://mikelsagardia.io">
<img src="eberhard-grossgasteiger-nVOPBYchSTY-unsplash.jpg" alt="mountains" width="150" height="70">
</a>
```

## Forms

Forms have `<input>` elements inside, each being a field to be filled in. We have many input `types`: text, email (correctness is checked), password (entered text is not visualized), submit (button), etc.

```html
<form>
	<h1>Log in</h1>
	<h1>Please input your email and password:</h1>
	<input type="email" name="">
	<input type="password" name="">
	<input type="color" name="">
	<input type="text" name="">
	<input type="submit" name="" value="Submit">
</form>
```

We can extend that basic form as follows:

- We can define `<labels>` which match with `<input>` `id` properties: `for` recceives the `id` value.
- We can add `value` so that it's displayed, or better, `placeholder`, so that it's displayed in gray.
- The `action` attribute connects the form with another HTML page (a file or URL). There, we apply a `method`, which can be `get` or `post`:
	- `method="get"`: data in the given representation is requested.
	- `method="post"`: data is submitted to be precessed.

```html
<form action="http://www.google.com" method="get">
	<label for="emailtag">EMAIL:</label>
	<input id="emailtag" type="email" name="useremail" value="" placeholder="my@email.net">
	<br>
	<label for="passtag">PASSWORD:</label>
	<input id="passtag" type="password" name="userpass" value="" placeholder="password">
	<br>
	<input type="submit" name="" value="Submit">
	<!-- We we hit Submit, the content of the form is passed to the action HTML page
		 and, since we use the get method, information is requested:
		 https://www.google.com/?useremail=my%40mail.com&userpass=test 
	-->
</form>
```

We can have more sophisticated `<input>` elements, such as:

- Radio buttons
- Drop-down menus
- Text area inputs

```html
<form>
	<h3>Do you already own a dog?</h3>
	<!--Input radio types that share the same name attribute are connected -->
	<label for="yes">Yes:</label>
	<input type="radio" id="yes" name="dog_choice" value="yes">
	<label for="no">No:</label>
	<input type="radio" id="no" name="dog_choice" value="no">

	<h3>How clean is your house? (1-3)</h3>
	<!--The browser shows 1/2/3 but the data processed is the value Bad/Good/Great-->
	<select name="stars">
		<option value="Great">3</option>
		<option value="Good">2</option>
		<option value="Bad">1</option>
	</select>

	<h3>Any other comments?</h3>
	<!--Text box with custom size -->
	<textarea name="textbox" rows=8 cols=80></textarea>

	<input type="submit" name="" value="Submit Feedback">

</form>
```

## Other HTML Elements and Notes

- Vertical break: `<br>`
- Comments: `<!-- ... -->`
- Sometimes we can combine tags, e.g., links and images.

# 2. CSS

CSS = Cascading Style Sheets. CSS files allow us to change style attributes of HTML elements: color, background, borders, size, location, etc.

Note that we can also do inline styling by just appending the attribute `style=...` to the tags; but that's tedious, because we'd have to add one for each tag. Instead, styling is defined in a separate CSS file.

To that end, we need to create a `*.css` file and `<link>` it to the `*.html` in its `head`; then, we define the style of the HTML elements from the `*.html` file. The idea is that we can define the style for each element type: `h1`, `li`, etc.

This section has examples in the folder

```
07_CSS_basics/
	index.html
	master.css
```

## CSS Stylesheet and Basic Style Definitions

After creating a basicc HTML file, we link to it a CSS stylesheet in which we define style properties of the elements in the HTML file.

CSS files contain HTML elements/tags and property-value definitions in them:

```css
h1{
	color:blue;
}
```

Examples:

`07_CSS_basics/index.html`:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title></title>
	<!--The link to the CSS stylesheet is realized here!-->
	<link rel="stylesheet" type="text/css" href="master.css">
</head>
<body>
	<h1>This is the heading h1</h1>
	<p>Let's see a list</p>
	<ol>
		<li>A</li>
		<li>B</li>
		<li>C</li>
	</ol>

	<h4>Heading 4</h4>
</body>
</html>
```

`07_CSS_basics/master.css`:

```css
h1{
	color: blue;
}

li{
	/*Google hex color to pick a RGB color value*/
	color: rgb(30,200,0);
}

p{
	/*Google hex color to pick a HEX color value*/
	color: #378a87;
}

h4{
	/*Google hex color to pick a RGB color value*/
	/*a = alpha = transparency*/
	color: rgba(180, 100, 0, 0.5);
}
```

Note that comments are added with `/*...*/`

## Background, Borders, Divs, Spans

We can define the style for all `<div>`, `<span>`, etc. Note that if no classes or ids are used, all elements will be affected. I we want to target specific elements or groups of elements, we need to use classes and ids -- se below.

```css
body{
	/*We can set body background colors or images*/
	/*background: gray;*/
	background: url(https://images.unsplash.com/photo-1589254065878-42c9da997008?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80);
	background-repeat: no-repeat;
}

div{
	background: blue;
	border: orange;
	border-width: medium; /*20px*/
	border-style: solid;
	/* Alternative in one line: */
	/*border: red 10px dotted;*/
}

span{
	background: red;
	color: black;
}
```

## CSS Classes and Ids

We can define style for specific elements and groups of elements. That is done by defining:

- Ids: a particular HTML element gets an `id="myId"` which is used in the CSS as `#myId{}`.
- Classes: we define a style for a group of different element types. It is very common to use classes in `divs`: `<div class="myDivClass">`; then, we define the class in the CSS file as `.myDivClass{}`.

Note that re-definitions of style property extensions are overlaid.

```html
<div class="firstDiv">
	<p>I'm inside the first div</p>
</div>

<div class="secondDiv">
	<p>I'm inside the second div</p>
</div>

<p id="singeParagraph">I'm outside any div</p>
```

```css
.firstDiv{
	color: blue;
}

.secondDiv{
	background-color: gray;
}

#singeParagraph{
	color: red;
}
```

## Exploring Elements in the Browser

On Chrome or Safari: open a website, right-click on an element and select "Inspect".

We can see the HTML and the CSS code of the element.

Additionally, we can modify on-the-fly the properties a visualize the changes.

## Fonts

One set of attributes of the HTML elements is related to the fonts: we can select the family, style, weight, etc.

We ca use these options:

- Standard fonts that are chosen by the OS: `monospace`, `cursive`, etc.
- OS-specific fonts:
	- [List of typefaces included with macOS](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_macOS)
	- [List of typefaces included with Microsoft Windows](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_Microsoft_Windows)
- [Google Fonts](https://fonts.google.com): we can get select a font link, add it to the `<head>` and use the font in the CSS stylesheet.

`index.html`:

```html
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title></title>
	<!--The link to the CSS stylesheet is realized here!-->	
	<link rel="stylesheet" type="text/css" href="master.css">
	<!--Google fonts-->
	<link rel="preconnect" href="https://fonts.googleapis.com"> 
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> 
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap" rel="stylesheet">
</head>
````

`master.css`:

```css
/*Google for fonts available on all platforms*/
/*We can also use standard family types and each platform chooses one: cursive, monospace, etc.*/
/*Or we can use Google Fonts: we add a link in the HTML head and select font on the web*/
h1{
	/* font-family: Courier; or cursive, monospace */
	font-family: 'Roboto', sans-serif; /*Google Font linked in HTML head */
}

p{
	font-size: 20px;
	font-weight: bold;
	font-style: italic;
	text-align: center;
}
```

# 3. Bootstrap

[Bootstrap](https://getbootstrap.com/) is a Front-end toolkit with many built-in components and themes ready to use.

There are 2 ways of using Bootstrap:

1. Download the toolkit and link it locally.
2. Copy the links provided in the [Bootstrap](https://getbootstrap.com/) homepage to the `<head>`.

**Important correction: we distinguish between the CSS stylesheets and `<script>` lines:**

- CSS stylesheets are integrated with `<link>` and they go in the `<head>`.
- Javascript and other files are integrated with `<cript>` and they should go at the end of the `<body>`.
- Place vendor files first and our files then so that we replace vendor styles.

```html
<html>
  <head>
    <link rel="stylesheet" href="bootstrap.css">
    <link rel="stylesheet" href="your-other-styles.css">
  </head>
  <body>
    <!-- content -->
    <script src="jquery.js"></script>
    <script src="bootstrap.js"></script>
    <script src="your-other-scripts.js"></script>
  </body>
</html>
```

Look at the [Bootstrap examples](https://getbootstrap.com/docs/5.2/examples/) for some of the available possibilities.

Look at the [Bootstrap docs](https://getbootstrap.com/docs/5.2/getting-started/introduction/): select a component, read the docs and find the HTML snippet we can directly copy & paste.

If we remove the Bootstrap CSS and JS links, the components will appear, but unformatted, i.e., ugly. In that sense, the [Bootstrap docs](https://getbootstrap.com/docs/5.2/getting-started/introduction/) are also a very good reference of components/examples we can use in HTML.

The examples from this section are in

`08_Bootstrap_basics/`

Note that the CSS stylesheet is empty, because we use the one from the Bootstrap link!

The initial template with all the imports recommended by Boostrap is the following:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap demo</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx" crossorigin="anonymous">
  </head>
  <body>
    <h1>Hello, world!</h1>
    
    <!--Bootstrap-->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-A3rJD856KowSb7dwlZdYEkO39Gagi7vIsF0jrRAoQmDKKtQBHUuLZ9AsSv4jD4Xa" crossorigin="anonymous"></script>
    <!--jQuery-->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
    <!--Popper-->
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.5/dist/umd/popper.min.js" integrity="sha384-Xe+8cL9oJa6tN/veChSP7q+mnSPaj5Bcu9mPX5F5xIGE0DVittaqT5lorf0EI7Vk" crossorigin="anonymous"></script>
    <!--Bootstrap JS-->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.min.js" integrity="sha384-ODmDIVzN+pFdexxHEHFBQH3/9/vQ9uori45z4JjnFsRydbmQbmL5t1tQ0culUzyK" crossorigin="anonymous"></script>
  </body>
</html>
```

Note that the examples in here need to be updated to use that template for imports.

## Bootstrap Basics

Basically, we add the links to the CSS stylesheet and Javascript file provided on the [Bootstrap](https://getbootstrap.com/) homepage.

Then, we have access to all the components defined in them.

We can/should have a look at the [Bootstrap docs](https://getbootstrap.com/docs/5.2/getting-started/introduction/) and play with the components that are available.

`index.html`:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title></title>
	<!--Bootstrap Stylesheet-->
	<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">
	<!--Bootstrap Javascript-->
	<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-pprn3073KE6tl6bjs2QrFaJGz5/SUsLqktiwsUTF55Jfv3qYSDhgCecCxMW52nD2" crossorigin="anonymous"></script>

</head>
<body>

	<!--If we use Bootstrap, the font and the margns change automatically and they adapt to the browser size-->
	<h1>Hello World!</h1>

	<!--Containers appear inserted to the right and they re-position with the window size-->
	<div class="container">
		<h1>Hello World!</h1>	
		<!--We can basically look at the docs of Bootstrap and take any component!-->
		<button type="button" class="btn btn-primary">Primary</button>
	</div>

</body>
</html>
```

`main.css`: empty.

## Forms

Example file; `forms.html`

```html
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <!-- Bootstrap CSS, JS, and jQuery -->
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css" integrity="sha384-WskhaSGFgHYWDcbwN70/dfYBj47jz9qbsMId/iRN3ewGhXQFZCSftd1LZCfmhktB" crossorigin="anonymous">
      <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
      <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js" integrity="sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T" crossorigin="anonymous"></script>
    <title>Forms</title>
    </head>
    <body>
      <div class="container">

      <!--
            The <fieldset> tag is used to group related elements in a form.
            The <fieldset> tag draws a box around the related elements.
      -->

        <form>

        <!-- EMAIL SUBMISSION -->

        <div class="form-group">
          <label for="exampleInputEmail1">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
          <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
        </div>

        <!-- PASSWORD -->

        <div class="form-group">
          <label for="exampleInputPassword1">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
        </div>

        <!-- DROPDOWN SELECT -->

        <div class="form-group">
          <label for="exampleSelect1">Example select</label>
          <select class="form-control" id="exampleSelect1">
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
          </select>
        </div>


        <!-- MULTIPLE SELECT OPTIONS -->

        <div class="form-group">
          <label for="exampleSelect2">Example multiple select</label>
          <select multiple class="form-control" id="exampleSelect2">
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
          </select>
        </div>

        <!-- TEXT AREA -->

        <div class="form-group">
          <label for="exampleTextarea">Example textarea</label>
          <textarea class="form-control" id="exampleTextarea" rows="3"></textarea>
        </div>

        <!-- FILE UPLOAD INPUT -->

        <div class="form-group">
          <label for="exampleInputFile">File input</label>
          <input type="file" class="form-control-file" id="exampleInputFile" aria-describedby="fileHelp">
          <small id="fileHelp" class="form-text text-muted">This is some placeholder block-level help text for the above input. It's a bit lighter and easily wraps to a new line.</small>
        </div>

        <!-- RADIO BUTTONS -->

        <fieldset class="form-group">
          <legend>Radio buttons</legend>
          <div class="form-check">
            <label class="form-check-label">
              <input type="radio" class="form-check-input" name="optionsRadios" id="optionsRadios1" value="option1" checked>
              Option one is this and that&mdash;be sure to include why it's great
            </label>
          </div>

          <div class="form-check">
          <label class="form-check-label">
              <input type="radio" class="form-check-input" name="optionsRadios" id="optionsRadios2" value="option2">
              Option two can be something else and selecting it will deselect option one
            </label>
          </div>

          <div class="form-check disabled">
          <label class="form-check-label">
              <input type="radio" class="form-check-input" name="optionsRadios" id="optionsRadios3" value="option3" disabled>
              Option three is disabled
            </label>
          </div>

        </fieldset>

        <!-- CHECK BUTTON -->

        <div class="form-check">
          <label class="form-check-label">
            <input type="checkbox" class="form-check-input">
            Check me out
          </label>
        </div>

        <button type="submit" class="btn btn-primary">Submit</button>

      </form>

    </div>

  </body>

  </html>

```

## Navbars

Have a look at the documentation: [Navbar](https://getbootstrap.com/docs/5.2/components/navbar/)

Note that sometimes some [jQuery](https://jquery.com/) links are necessary so that the navbar menus and drop-downs work correctly.

`navbar.html`:

```html
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <title></title>
      <!-- Latest compiled and minified CSS -->
      <!-- Bootstrap CSS, JS, and jQuery -->
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css" integrity="sha384-WskhaSGFgHYWDcbwN70/dfYBj47jz9qbsMId/iRN3ewGhXQFZCSftd1LZCfmhktB" crossorigin="anonymous">
      <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
      <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js" integrity="sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T" crossorigin="anonymous"></script>
  </head>

    <body>

    	<!-- DOCUMENTATION NAVBAR -->

      <nav class="navbar navbar-expand-lg navbar-light bg-light">

        <!-- TYPICALLY WE HAVE A BRAND LINK -->
          <a class="navbar-brand" href="#">BRAND</a>

          <!-- THIS SETS UP THE COLLAPSABLE BUTTON ELEMENT (HAMBURGER) -->

          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>

     <!-- THEN WE PUT AN UNORDERED LIST INSIDE OF A COLLAPSE DIV -->
    <div class="collapse navbar-collapse" id="navbarSupportedContent">

      <ul class="navbar-nav mr-auto">
         <!-- EVERY ITEM IN NAVBAR IS JUST A LIST ITEM -->
        <li class="nav-item active">
          <a class="nav-link" href="#">SomeLink</a>
        </li>

        <!-- HERE IS ANOTHER ONE, BUT THE LINK DOESNT "LOOK" ACTIVE -->
        <li class="nav-item">
          <a class="nav-link" href="#">AnotherLink</a>
        </li>

        <!-- WE CAN ALSO CREATE DROPDOWN MENUS -->
        <li class="nav-item dropdown">

          <!-- TOP LEVEL DROPDOWN -->
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Dropdown
          </a>

          <!-- ONE DIVISION IN THE DROPDOWN -->
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>

            <!-- ANOTHER DIVISION IN THE DROPDOWN -->
          <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Something else here</a>
          </div>

        </li>

      </ul>

      <!-- CAN EVEN ADD A SEARCH FORM -->
      <form class="form-inline my-2 my-lg-0">
        <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
      </form>
    </div>
  </nav>

    <!-- OTHER STUFF ON THE PAGE -->

    <div class="container">
      <div class="jumbotron">
        <h1>Hello</h1>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>

    </div>
    <div class="container">
      <h2>More Stuff</h2>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>

    </div>

    <!-- Need to have JQuery and Javascript for DropDown Actions to work -->
    <!-- NOT ANYMORE! -->

    <!--
    <script
    src="http://code.jquery.com/jquery-3.1.1.js"
    integrity="sha256-16cdPddA6VdVInumRGo6IbivbERE8p7CQR3HzTBuELA="
    crossorigin="anonymous"></script>  <!-- Latest compiled and minified JavaScript -->
    <!--
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
    -->

  </body>
</html>
```

## Dashboards

Look at my notes from the [Udacity Data Science Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025): `/ 02_SWENgineering.md: 6. Web Development`.

Examples on how to use Bootstrap to create dashboards are documented and collected in the `lab/` folder.


# 4. Javascript and jQuery

Javascript was developed to provide interactivity in HTML webpages by a programmer from the Netscape navigator. Basically, we manipulate the elements of a webpage using Javascript: change their color, fade-in, pop-up, text, etc. Although it's called *Javascript*, it has nothing to do with the Java language; that naming was a marketing decision due to the popularity of Java at the time.

Nowadays, Javascript can be used in a runtime environment like [Node](https://nodejs.org/en/). Or we can directly use the browser (Chrome) Javascript console to test our code: `View > Developer > Javascript Console`. We can copy and paste our code there.

However, since this guide is related to basic web development, note that we will use Javascript files written in `my_file.js` files and integrated into the HTML file. We can also write JS code in `<script>` elements.

## Introductory Example: Javascript and jQuery

Very simple example: we define a `headFunction()` which changes the `h1` text in the page when we click on the page image (`<img onclick=...`).

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JS Example</title>
    <script>
    	// Change the text content of the element with tag name h1
    	// Look for all elements with tag h1 and grab the first
    	// We need to trigger the function, e.g., with onclik in the img
    	function headFunction() {
    		document.getElementsByTagName("h1")[0].innerHTML = "Hello Again!";
    	}
    </script>
  </head>
  <body>
  	<h1>Hello World!</h1>
  	<!-- Function defined above is triggered here with onclick -->
    <img src="photo.jpg" alt="Hello world photo." onclick="headFunction()">
  </body>
</html>
```

Note that it is quite cumbersome having to type all that code for a simple action. To make things easier, the [jQuery](https://api.jquery.com/) Javascript can be used. We need to add the library link in a `<script>` in the body, and the code is transformed as follows:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JS Example</title>
    <script>
			// When website is ready, run this function:
			// when we click on img, change the text of h1
			// This way, we don't need the onclick attribute in the img
			// $(): grab this element, class or id
			$(document).ready(function(){
			        $("img").click(function(){
			            $("h1").text("A Photo of an Amazing  View");
			        });
			    });
    </script>
  </head>
  <body>
  	<h1>Hello World!</h1>
  	<!-- No function triggering necessary anymore -->
    <img src="photo.jpg" alt="Hello world photo.">

    <!--jQuery library URL-->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
  </body>
</html>
```

However, note that jQuery is a library for HTML element management; we still need to write *normal* Javascript code without jQuery.

If we write the JS code in a separate file `my_script.js`, we just need to integrate it in the `<head>` as follows:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JS Example</title>
    <script src="my_script.js"> </script>
  </head>
  <body>
  	<h1>Hello World!</h1>
  	<!-- No function triggering necessary anymore -->
    <img src="photo.jpg" alt="Hello world photo.">

    <!--jQuery library URL-->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
  </body>
</html>
```

`my_script.js`:

```javascript
// Click on an image to change text on screen
$(document).ready(function(){
        $("img").click(function(){
            $("h1").text("A Photo of an Amazing  View");
        });
    });

// Webpage content hides and then fades in slowly as webpage loads
$(document).ready(function(){
        $("body").hide().fadein("slow");
    });

// Image fades out when I click on title
$(document).ready(function(){
        $("h1").click(function(){
            $("img").fadeout("slow");
        });
    });

// When we click on the image, "Thank you" appears in the h2 tag
$(document).ready(function(){
        $("img").click(function(){
            $("h2").text("Thank you");
        });
    });

// When loaded the webpage, the paragraph p disappears
// but then it starts fading in slowly
$(document).ready(function(){
        $("p").hide().fadein("slow");
    });

// When we click on the h2 title, it disappears quickly
$(document).ready(function(){
        $("h2").click(function(){
            $("h2").fadeout("fast");
        });
    });
```

More modern alternatives to jQuery are React or Angular.

## Javascript Syntax

In the following, some self-explanatory lines of code.

We can define the code it in a `my_script.js` file and integrate it to our HTML or we can run in (copy & paste) in a Javascript console (e.g., in Chrome: `View > Developer Tools > Javascript Console`).

```javascript
function addValues(x) {
	/* This function gets an array x.
	All items of it are summed in a for-loop.	*/
  var sum_array = 0; // variable definition
  for (var i=0; i < x.length; i++) {
    sum_array += x[i]; // array indexing
  }
  return sum_array;
}

function main() {
  console.log("Hello"); // print to console
	var sum = addValues([3,4,5,6]); // we pass an array to a function
	console.log(sum);
	var my_string = "Hello" + " World!"; // string concatenation
	console.log(my_string[0]); // J
	var my_boolean = true;
	var my_other_boolean = false;

	var a = 1;
	var b = 2;
	if (a > b) {
	  console.log("a is greater than b");
	} else if (a == b) {
	  console.log("a is equal to b");
	} else {
	  console.log("a is less than b");
	}

	var colt = "not busy";
	var weather = "nice";

	if (colt === "not busy" && weather === "nice") {
	  console.log("go to the park");
	}

	// Ternary operator
	var isGoing = true;
	var color = isGoing ? "green" : "red";
	console.log(color);

	var start = 0; // when to start
	while (start < 10) { // when to stop
	  console.log(start);
	  start = start + 2; // how to get to the next item
	}

}

```



# 5. Interesting Links

- [An Introduction to Using Jekyll With Bootstrap 4](https://betterprogramming.pub/an-introduction-to-using-jekyll-with-bootstrap-4-6f2433afeda9)