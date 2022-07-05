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

## HTML Tagging

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
<p>A numbered list:</p>

<ol>
	<li>First item</li>
	<li>Second item</li>
	<li>Third item</li>
</ol>

<p>A bullet list:</p>

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

# X. Interesting Links

[An Introduction to Using Jekyll With Bootstrap 4](https://betterprogramming.pub/an-introduction-to-using-jekyll-with-bootstrap-4-6f2433afeda9)