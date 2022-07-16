# Basic HTML, CSS, & Bootstrap: A Guide

These are my personal notes related to HTML, CSS, and Bootstrap. They are focused to creating and deploying static web pages with [Jekyll](https://jekyllrb.com): instead of creating HTML & CSS files from the scratch, small snipets need to be written and modified when using Jekyll.

These notes originated from various sources, among others:

- The Udemy course by José Marcial Portilla [Python and Flask Bootcamp: Create Websites using Flask!
](https://www.udemy.com/course/python-and-flask-bootcamp-create-websites-using-flask)
- [How To Build a Website with HTML](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-html?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTOnrDkTx6aH73I-I1zsNt7vZu9Ff_wGEX2sH9OdAfTZFfFIgMjQEIhPFT6WNI9fSXvQkfpC4A-DPSMjP63wwOpcHqLS8pxrjMFocGPg)
- [How To Build a Website With CSS](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-css?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTO6ayIs0-zVCBcnVyVnIMcdi5C9FiraEGRmtV2yzU2wJdb41l3l84ULsvcSqJlPbO1vFqyuQTpTNYUiprIB5BLsYVMxt-1s4LEVnj3A)

Mikel Sagardia, 2022.  
No guarantees.

**Overview of contents**:

1. [HTML](#HTML)
	- [General Notes](#General-Notes)
	- [Basic HTML File Structure](#Basic-HTML-File-Structure)
	- [HTML Tagging: Titles](#HTML-Tagging:-Titles)
	- [Lists](#Lists)
	- [Divs and Spans with HTML](#Divs-and-Spans-with-HTML)
	- [Images and HTML Attributes](#Images-and-HTML-Attributes)
	- [Hyperlinks: Anchor Tags](#Hyperlinks:-Anchor-Tags)
	- [Forms](#Forms)
	- [Other HTML Elements and Notes](#Other-HTML-Elements-and-Notes)
2. CSS
3. Bootstrap
X. Interesting Links

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

We need to create a `*.css` file and `<link>` it to the `*.html` in its `head`; then, we define the style of the HTML elements from the `*.html` file. The idea is that we can define the style for each element type: `h1`, `li`, etc.

This section has examples in the folder

```
07_CSS_basics/
	index.html
	master.css
```

## CSS Stylesheet and Basic Style Definitions (Color)

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

[List of typefaces included with macOS](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_macOS)

[List of typefaces included with Microsoft Windows](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_Microsoft_Windows)

# 3. Bootstrap



# X. Interesting Links

[An Introduction to Using Jekyll With Bootstrap 4](https://betterprogramming.pub/an-introduction-to-using-jekyll-with-bootstrap-4-6f2433afeda9)