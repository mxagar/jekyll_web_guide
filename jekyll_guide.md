# Jekyll Website Development and Deployment Guide

These are my personal notes related to creating and deploying static web pages with [Jekyll](https://jekyllrb.com).

The notes originated from various sources, among others:

- The Youtube [tutorial by Mike Dane](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB).
- The orginal [Jekyll documentation page](https://jekyllrb.com/docs/).
- The Udemy course by Jana Bergant [Jekyll: make fast, secure static sites and blogs with Jekyll](https://www.udemy.com/course/static-website-generator-fast-secure-sites-blogs-with-jekyll)

Mikel Sagardia, 2022.
No guarantees.

**Overview of contents**:

1. Introduction
2. Installation
	- Mac
	- Linux
	- Windows
	- Notes on Ruby
3. Creating a New Project/Site and Serving It Locally
4. Basic Usage and Elements
	- 4.1 Front Matter
	- 4.2 Creating Posts
	- 4.3 Creating Draft Posts
	- 4.4 Creating Pages
	- 4.5 Permalinks: Permanent URLs
	- 4.6 Default Front Matter
5. Themes
	- 5.1 Installation with the `Gemfile`
	- 5.2 Manual Installation with Downloaded Theme Packages
6. Layouts, Includes, & Basic Liquid Usage
	- 6.1 Layouts
	- 6.2 Hierarchies of Layouts
	- 6.3 Variables
		- Pre-Defined Variables: [Jekyll variables](https://jekyllrb.com/docs/variables/)
		- Example with Pre-Defined and Custom Variables
	- 6.4 Includes
	- 6.5 Looping Through Pages
	- 6.6 Conditionals
	- 6.7 Data Files
	- 6.8 Static Files
	- 6.9 Filters
7. Deployment: Setting up a GitHub Pages Site with Jekyll
	- 7.1 Create and Publish First Version
	- 7.2 Check Website Locally and Work on It
	- 7.3 Use Custom Domain
8. Project 1: Create a Company Landing Page
9. Project 2: Create a Blog
10. Comments & Forms
11. Collection of Additional Things
12. Personal Project: Create a Blank Static Website with a Custom Domain
	- Step 1: Create a Blank Website in a Dedicated Github Organization (Private) Repository
	- Step 2: Create a Digital Ocean App, Buy a Domain, and Deploy
13. Some Links on Themes and Websites


## 1. Introduction

Jekyll generates static pages from easy Markdown files.
Static pages, in contrast to dynamic ones, don't change with user interaction, i.e., we don't have real shopping carts or the like.

Wordpress creates dynamic pages, it's a content management system (CMS). But in reality, in most of the cases we don't need a dynamic page. Plus, Wordpress introduces some vulnerabilities.

Static websites are a collection of HTML, CSS and Javascript files, in addition to any media file we want to use. They don't change in the server -- although I understand we can visualize different things, by using Javascript.

In contrast to dynamic sites (e.g., Wordpress), there is no database.

Main benefits of static sites
- Performace: they are much faster
- Security: since they don't change, they are inmune to attacks, as long as the files are secure.
- You can easily apply version control.
- Simplicity for buulding and maintaining
- We can use Markdown!
- We can preview easily the final content.
- Hosting is cheaper, sometimes free; the reason is that they are much less demanding for hosting companies (performance, ssecurity and storage-wise).

Most common static sites:
- Blogs
- Landing pages: information, company, selling, etc.
- Documentation pages
- Portfolios

There are plug-ins to implement dynamic elements: forms, comments, etc.

## 2. Installation

### Mac

These steps ware taken from the official Jekyll site: [Jekyll Installation on Mac](https://jekyllrb.com/docs/installation/macos/). Note that Jekyll is written on Ruby, so it uses its package distribution system, gem.

```bash
# Install chruby and roby-install
brew install chruby ruby-install

# Although we have ruby installed on Mac,
# we need to install the latest Ruby version, > 3.0
# Jot down the installed version, since it needs to be used below
ruby-install ruby

# Configure shell to automatically use chruby
# Note that in the official website there is a bug:
# they use "chruby ruby-3.1.1", but I have the version ruby-3.1.1
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.2" >> ~/.zshrc

# Source 
source ~/.zshrc

# Check version
ruby -v # ruby-3.1.2

# Check the gem version
gem -v # 3.3.7

# Install Jekyll
gem install jekyll

# Check installed version
jekyll -v # jekyll 4.2.2

# Install the bundler
gem install bundler

# Check installed version of the bundler
bundler -v # Bundler version 2.3.12

# There is a problem with the version I was using,
# and I had to manually install webrick, following this Github-issue
# https://github.com/jekyll/jekyll/issues/8523
bundle add webrick
```

### Linux Installation

[Official Ubuntu installation guide](https://jekyllrb.com/docs/installation/ubuntu/).

[Official Linux installation guide](https://jekyllrb.com/docs/installation/other-linux/).


### Windows

[Official Windows installation guide](https://jekyllrb.com/docs/installation/windows/).

### Notes on Ruby

Some notes on Ruby:

- Jekyll is written in Ruby
- Ruby packages are gems: Jekyll is a gem, as are its plugins, themes, etc.
- The `Gemfile` in a Ruby project is the ffile that lists all dependency packages; our Jekyll site needs to have one
- `bundler` is the gem that installs gems in our project, listed in the `Gemfile`

## 3. Creating a New Project/Site and Serving It Locally

Creating and starting a server that serves locally our website is very easy:

```bash
cd ~/git_repositories/jekyll_web_guide/
# Create a new project / website
jekyll new 01_my_first_website
# Go to the project directory
cd 01_my_first_website
# Execute this for every new project, it's a bug
bundle add webrick
# Compile and serve the website
bundle exec jekyll serve --trace
# Open the browser in address 127.0.0.1:4000, localhost:4000
# et voilà
# If we want to stop the server: Ctrl+C
# After the first time, we can simple use
# jekyll serve --trace 
# The option --trace is not necessary, it is to track events
```

The default template used is [minima](https://github.com/jekyll/minima). We can change it, though. Note that we have by default:
- Home site with a list of posts
- About
- Posts
- RSS feed
- Header and footer with contant info and description

Default files and folders structure in the website project:

```
01_my_first_website $ tree
.
├── 404.html
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2022-04-28-welcome-to-jekyll.markdown
├── _site
│   ├── 404.html
│   ├── about
│   │   └── index.html
│   ├── assets
│   │   ├── main.css
│   │   ├── main.css.map
│   │   └── minima-social-icons.svg
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2022
│               └── 04
│                   └── 28
│                       └── welcome-to-jekyll.html
├── about.markdown
└── index.markdown
```

Description of files and folders

- `_posts`: it contains markdown files of our ports
- `_site`: the final output or finished product, the static artefacts generated to serve the site; all markdown files converted to HTML, CSS, etc. This folder is regenerated every time we change something. Thus, this folder is ignored in git
	- `404.html`: default error/not-found page, compiled as HTML
	- `about/about.html`: about page compiled as HTML
	- `assets`: SVGs, CSS, media, etc.
	- `feed.xml`: RSS feed file
	- `index.html`: main/home page compiled as HTML
	- `cat1/...`: blog posts, ordered in the categoroes we assign them (e.g., `cat1`) and year/month/day folders
- `_config.yaml`: very important file in which we configure our website; we need to change this file! Every time we change this file, the serving must be re-started.
- `Gemfile`: dependencies listed by ruby/gem for our website; if we want plugins/themes, we need to specify them here.
- `index.markdown`: main website page description in markdown; we can modify its contents!
- `about.markdown`: about page description in markdown; we can modify its contents!
- `404.html`: default error/not-found website; note that it is not markdown, but directly HTML
- `.gitignore`: automatically generated git-ignore file

Additional important folders that often appear are:
- `_includes/` contains re-usable components of our website, such as headers, footers, navigation lists, etc. See Section 6.
- `_layouts` contains page style templates within the theme: `post`, `page`, `default`, etc. Then, in each markdown, we can specify which layout we'd like to use. However, note that layouts can be also defined in the theme; the `_layouts/` folder is usually for user-generated types of layouts. See Section 6 on the topic.
- `_data/` contains static databases of teh format `YAML`, `JSON` or `CSV`; these can be accessed from the website.
- `assets/` contains all static files; static files are the ones that are not parsed and compiled by Jekyll for rendering, e.g., images, PDFs, CSS files, Javascript files, etc. However, note that static files are not necessary in this folder: that name is a soft convention.

**Important; Jekyll tracks any change that happens in the project folder and automatically updates the `_site` folder used to serve the website; so we don't need to stop and restart the server!**

- All files and folders which start with `_` are used to generate the site elements and are tracked.
- All the rest of the files we add in the folder are copied to `_site/`; if we remove any of these files in the project folder, they are removed automatically from the `_site/` folder, too!

Default content of the `_config.yaml` file using the [minima](https://github.com/jekyll/minima):

```yaml
title: Your awesome title
email: your-email@example.com
description: >- # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
github_username:  jekyll

# Build settings
theme: minima
plugins:
  - jekyll-feed
```

## 4. Basic Usage and Elements

Recall, to start/stop the server:

```bash
# Go to the project directory
cd .../01_my_first_website
# Compile and serve the website
bundle exec jekyll serve --trace
# Open the browser in address 127.0.0.1:4000, localhost:4000
# TO STOP: Ctrl+C
# After the first time, we can simple use
# jekyll serve --trace 
# The option --trace is not necessary, it is to track events
```

BUT: Jekyll tracks any changes and updates `_site` automatically, so we don't need to restart the server every time!

### 4.1 Front Matter

The front matter is the configuration that appears in any markdown file in the beginning, with the delimiter `---`.

Front matter of the default blog post `_posts/2022-04-28-welcome-to-jekyll.markdown`

```yaml
---
layout: post
title:  "Welcome to Jekyll!"
date:   2022-04-28 09:10:48 +0200
categories: jekyll update
---
```

We can write the front matter in JSON or YAML. It contains important key-value pairs that configure the page.

We can change the post title, date, etc.; and everything will be updated automatically if we refresh the browser (even the URLs)!

Front matter variables:
- `layout`: the theme scheme we want to use, the style
- `title`
- `date`: use the convention, we can really write any date; the date in the front matter overwrites the date of the filename
- `categories`
- `author`

Hint: we can define a default post image as a placeholder in the front matter!

### 4.2 Creating Posts

Just go to the `_post` folder and create a new file

```bash
cd .../01_my_first_website
cd _posts
touch 2022-01-15-my-awsome-title.markdown
```

Use the naming convention: date-title, spaces with `-` so that Jekyll knows where a spaces comes:

```
year-month-day-title.markdown
2022-01-15-my-awsome-title.markdown
```

Always add a basic front matter. Note that the date in the front matter and in the file name must match.

```yaml
---
layout: post
title:  "My title"
date:   2022-01-15
---
```

The post will automatically be processed to obtain its HTML and it will appear on the main page, because the default theme displays the posts on the main page.

We can create subdirectories inside `_posts` and move markdonw files around - it won't affect anything, they will be ordered according to their date. That's a nice way of organizing the posts :)

### 4.3 Creating Draft Posts

We can create draft posts and store them in a `_draft` folder; they are visualized only if we serve them with the `--draft` option.

```bash
cd .../01_my_first_website
mkdir _drafts
cd _drafts
# no date is necessary
touch my-draft-post.markdown
```

Edit `my-draft-post.markdown` as usually:

```yaml
---
layout: post
title:  "My draft post"
---

This is a draft.

```

Serve with the option `--draft` if we want to see it rendered; otherwise it's not rendered:

```bash
jekyll serve --draft --trace
# The date is automatically the last modification date
# The option --trace is not necessary, it is to track events
```

### 4.4 Creating Pages

Any page that is not a blog post is in the root directory. Typical pages:
- About
- Donations
- Contact
- Services
- ...


```bash
cd .../01_my_first_website
# no date is necessary
touch donation.markdown
```

Edit using the layout `page`:

```yaml
---
layout: page
title:  "Donations"
---

This is my donations page

```

Serve it:

```bash
jekyll serve --trace
```

Depending on the template/theme we're using, the page link will appear in the menu (as it happpens with the `minima` theme).

We can also create a folder in the root directory, e.g., `dir`, and store there our pages. In that case, the URL will be `.../dir/donations.html`.

### 4.5 Permalinks: Permanent URLs

Note that the URLs of our pages/posts depend:
- on the `category` list we define for them in the front matter
- on the date we assign them

The `_site/` folder creates subfolders for `year/month/day` and for each category, in the order we list them `cat1/cat2/...`.

That folder structure is reflected in the URLs. Now, that might be a problem, because if we change the categories/date, any external links to our pages break!

We can solve that with the option `permalink` in the front matter; we can assign each post/page a unique URL very easily:

```yaml
---
permalink: "/my-new-url/"
---
```

We can use any URLs and even access variables with `:`:

```yaml
permalink: "/my-new-url/"
permalink: /:categories/:year/:month/:day/:title
...
```

The last one replicates the default behaviour. We can even add custom extensions: `.../:title.html`.

**Recommendation**: always define fixed permalinks to avoid breaking links! For instance

```yaml
permalink: /blog/:title
```

### 4.6 Default Front Matter

We ca define the default front matter for any page/post we create in the `_config.yaml`. We add the following:

```yaml
...
# Default settings
defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "Mikel Sagardia"
```

That piece of code will add the default front matter under `values` for all pages that are under the folder `_posts`. If we add a string to `path`, we can specify the folder in which the default is applied.

## 5. Themes

The theme is specified in the `_config.yaml` file, in the key `theme`. By default it is `minima`. We can check where its files are with

```bash
bundle show minima
# ~/.gem/ruby/3.1.2/gems/minima-2.5.1
```

There are several ways to change the theme:
- We can download it manually and copy its files to our jekyll website project
- We can install it with `gem` or with the `Gemfile`

**Recommendation**: always first choose the theme, because changing it after the site is built is more difficult; some page layouts might be different, etc.

**Hint**: if we install the themes through the `Gemfile`, where are the HTML and CSS files used to create the site located? We can execute the following command to check their location in the local computer:

```bash
cd .../my_website
# Replace 'minima' with the name of the theme we have installed in the Gemfile
bundle info minima # ~/.gem/ruby/3.1.2/gems/minima-2.5.1
```

### 5.1 Installation with the `Gemfile`

In order to install it with `gem` or the `Gemfile`, **first** we need to get its name in the [rubygems.org](https://rubygems.org) repository:

- Go to [rubygems.org](https://rubygems.org)
- Search for `jekyll-theme`; many Jekyll themes start with those two words.
- Note at the package sites the installation command with `gem install`, the homepage / github repo (often with examples and previews).
- Select one theme, e.g., [jekyll-theme-hacker](https://rubygems.org/gems/jekyll-theme-hacker)

**Second**, we create/select a project and add the theme dependency in the `Gemfile`:

```bash
jekyll new 02_new_theme 
cd ../02_new_theme
bundle add webrick
# Edit Gemfile: add this line below 'gem "minima", "~> 2.5"'
# gem "jekyll-theme-hacker"
# Install the theme with bundle install
bundle install
```

**Third**, we specify the new theme in the `_config.yaml`, right below `minima`:

```yaml
...
#theme: minima
theme: jekyll-theme-hacker
...
```

**Fourth**, change any layouts from `minima` that are not available in our new theme, `jekyll-theme-hacker`. To that end:

- we go to the repository of the theme [https://github.com/pages-themes/hacker](https://github.com/pages-themes/hacker)
- we check the possible layouts in the folder `_layouts`: `default` and `post`
- we manually change all page and post markdowns in our our project to have any of these two layouts in the front matter:
	- `index.markdown`
	- `about.markdown`
	- `_posts/*`

**Fifth**, serve the website locally; everything is set up for us:

```bash
# Serve
bundle exec jekyll serve
# Open the browser at localhost:4000
```

### 5.2 Manual Installation with Downloaded Theme Packages

This approach is the most general one: we download a theme from the internet as a ZIP and we want to use it.

**First**, we find and download a theme (provided in the Udemy course by Jana Bergant):

`./themes/jekyll_template_udemy/`

**Second**, we create a new project:

```bash
jekyll new 03_new_theme_manual 
cd 03_new_theme_manual
bundle add webrick
```

**Third**, we delete and modify some files in the default generated project.

Delete all the files with any content:
- The post markdowns in `_posts/*`, but not the `_posts` folder
- `about.markdown`
- `index.markown`

Modify the configuration files that reference the default theme:
- `_config.yaml`: remove the theme line: `theme: minima`
- `Gemfile`: remove the theme file: `gem "minima", "~> 2.5"`

In the remaining markdown/content files, remove any layout references:
- `404.html`: remove `layout: default`

**Fourth**, we remove the dependencies in the project:

```bash
bundle
```

**Fifth**, we add new folders in the website project root:

- `./03_new_theme_manual/_includes/`
- `./03_new_theme_manual/_layouts/`

**Sixth**, we copy all the contents from the template/theme folder 

`./themes/jekyll_template_udemy/*`

to our website project folder

`./03_new_theme_manual/`

**Seventh**, we build and serve our project:

```bash
bundle exec jekyll serve
```

## 6. Layouts, Includes, & Basic Liquid Usage

Each theme has layouts or page-style templates: `default`, `page`, `post`, etc. These are like skeleton HTML definitions. Then, we choose for each markdown website which layout we'd like to use in the front matter (see Section 4.1).

These layouts are usually defined in the theme code. However, we can create a folder `_layouts/` in the website root folder and define/overwrite layouts with custom HTML and [Liquid](https://shopify.github.io/liquid/) code, e.g.:  `_layouts/post.html`

[Liquid](https://shopify.github.io/liquid/) is a templating language maintained by Shopify that allows variable and logic statement handling inside HTML. We can use Liquid with the curly braces: `{}`:
- `{{ ... }}`: output markups, used to ouput variables
- `{% ... %}`: tag markups, used to perform logic operations

For this section, I create a new website project to mess around with layouts and Liquid:

```bash
cd ~/git_repositories/jekyll_web_guide/
jekyll new 04_minima_layouts
cd 04_minima_layouts
bundle add webrick
bundle exec jekyll serve --trace
```

### 6.1 Layouts

In the default `minima` theme, we have the layouts `default`, `post` and `page` define in the theme code. We can overwrite them as follows:

- In the website project root folder, we create the folder `_layouts/`
- Inside `_layouts/`, we create the file `post.html`; with that, we overwrite the `post` layout defined in the theme.

Now, let's play around with that `post.html` with HTML and Liquid: we add a header title (which is always the same) and the use Liquid to add the variable `content`:

```html
<h1>This is a post</h1>
<hr>

{{ content }}
```

Now, if we open `localhost:4000` and click on the post, we see an ungly post display.

We can also create our own `layouts`: `_layouts/mylayout.html`; then, we need to specify them in the front matter of the pages we want.

`_layouts/mylayout.html`:

```html
<h1>This is my layout</h1>
<hr>

{{ content }}
```

### 6.2 Hierarchies of Layouts

We can create different levels of layouts that wrap one to the other.

`_layouts/wrapper.html`:

```html
<html>
<head>
	<meta charset="utf-8">
	<title>Document</title>
</head>
<body>
	START <br>
	{{ content }}
	</br> END
</body>
</html>
```

Now, we add in the front matter of the `post.html` layout the `wrapper.html` layout!

```html
---
layout: wrapper
---

<h1>This is a post</h1>
<hr>

{{ content }}
```

The effect is that the post has two layouts: `wrapper` wraps `post`, so the content is formatted with both; the words "Wrapper" appear on the rendered page. It is as if `wrapper` were the parent layout.

### 6.3 Variables

Jekyll uses variables that can be handled in Liquid blocks. One of these is `{{ content }}`. Roughly, we have two types of variables:

- Pre-defined variables of Jekyll: [Jekyll variables](https://jekyllrb.com/docs/variables/)
- Custom variables defined by the user in the front matter of the layout or the page/post.

#### Pre-Defined Variables: [Jekyll variables](https://jekyllrb.com/docs/variables/)

In general, there are some global variables which contain other sub-variables: :

- `site`: general info + settings from `_config.yaml`
	- `site.pages`: a list of all pages
	- `site.posts`: a reverse chronological list of all Posts
	- `site.categories.CATEGORY`: The list of all Posts in category CATEGORY
	- `site.url`: site URL; default: `http://localhost:4000`
	- `site.static_files`: a list of all static files, i.e., images, PDFs, CSS, Javascript, etc.
	- ...
- `page`: current page specific variables + user-defined in the front matter
	- `page.title`
	- `page.url`
	- `page.date`
	- `page.categories`
	- ...
- `layout`: current layout specific variables + user-defined in the front matter
- `content`: the content itself
- `paginator`: available when pagination is active: content (e.g., blog post) is break down into several pages.

#### Example with Pre-Defined and Custom Variables

`_layouts/post.html`

```html
---
layout: wrapper
author: "Mikel"
---

<h1>{{ page.title }}</h1>
<h3>{{ layout.author }}</h3>
<hr>

{{ content }}
```

Then, our post will have now its page title, the author name of the layout and the content. Additionally, everythin is wrapped by the parent layout `wrapper.html`.

### 6.4 Includes

Includes are used to define **headers**, **footers**, **navigation lists**, or similar components that are repeated in different pages/layouts. This keeps the HTML code of each component modularized in a unique place.

Example of how to create a header:

- In the website project root folder, we create the folder `_includes/`.
- Inside `_includes/`, we create the file `header.html`.
- It makes sense to include that header in the `wrapper.html` layout, since it's used as the parent layout; that can be done with `	{% include header.html %}`.

This is how the different HTML files wouldd look like:

`_includes/header.html`:

```html
<h1>{{ site.title }}</h1>
<hr><br>
```

`_layouts/wrapper.html`:

```html
<html>
<head>
	<meta charset="utf-8">
	<title>{{ site.title }}</title>
</head>
<body>
	{% include header.html %}
	{{ content }}
</body>
</html>
```

`_layouts/post.html`:

```html
---
layout: wrapper
---

<h1>{{ page.title }}</h1>
<hr>

{{ content }}
```

We can also pass variables to the includes, which can be used in them. For instance, if we want to be able to change the color of the header:

`_includes/header.html`:

```html
<h1 style="color: {{ include.color }}">{{ site.title }}</h1>
<hr><br>
```

`_layouts/wrapper.html`:

```html
<html>
<head>
	<meta charset="utf-8">
	<title>{{ site.title }}</title>
</head>
<body>
	{% include header.html color="blue"%}
	{{ content }}
</body>
</html>
```

### 6.5 Looping Through Pages

Looping is necessary if we want to create navigation lists: we loop over all our posts.

We overwrite the `home` layout from `minima`:

`_layouts/home.html`:

```html
{% for post in site.posts %}
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
```

If we create several posts in `_posts`, we'll see a list of posts on our home page.

### 6.6 Conditionals

These are basically `if`-`else` statements.

Example: `_layouts/post.html`:

```html
---
layout: wrapper
---

<h1>{{ page.title }}</h1>
<hr>

{% if page.title == "My first post!" %}
	This is my first post.
{% elsif page.title == "My second post!" %}
	This is my second post.
{% else %}
	This is another post.
{% endif %}

{{ content }}
```

### 6.7 Data Files

We can have 3 types of data files that act like small static databases: `JSON`, `YAML` and `CSV`.

To that end, we need to create the folder `_data/` in the root website folder, and move our data files there. Then, we can access those files with `site.data.<filename>`.

Example:

`_data/people.yaml`:

```yaml
- name: "Mikel"
  occupation: "Research Engineer"

- name: "Ana"
  occupation: "Scrum Master"

- name: "Unai"
  occupation: "Engineer"

- name: "June"
  occupation: "Astronaut"
```

`_layouts/home.html`:

```html
{% for post in site.posts %}
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}

<hr>

{% for person in site.data.people %}
	{{ person.name }}, {{ person.occupation }} <br>
{% endfor %}
```

### 6.8 Static Files

A static file is any file which is not being parsed and compiled by Jekyll. For instance:

- Images
- CSS, Javascript, etc.
- PDFs

By convention, we often see a folder called `assets` in the website root folder to keep those files; recall that Jekyll moves to `_site` all the files & folders that are not preceeded by `_`. However, we can have the static files in other places, too.

Let's create the folder `assets/` with these files:
- `datamix_logo_draft.png`
- `doc.pdf`

Then, we can access the files as done in `_layouts/home.html`:

```html
{% for post in site.posts %}
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}

<hr>

{% for person in site.data.people %}
	{{ person.name }}, {{ person.occupation }} <br>
{% endfor %}

<hr>

{% for file in site.static_files %}
	{{ file.path }} <br>
{% endfor %}

```

Now, we can see the paths of the static files in the home page. However, it's irrelevant for Jekyll where the static files are located, so *all* static files (also the ones not in `assets/`) are displayed:

```
Welcome to Jekyll!
My third post!
My second post!
My first post!
---
Mikel, Research Engineer 
Ana, Scrum Master 
Unai, Engineer 
June, Astronaut 
---
/assets/datamix_logo_draft.png 
/assets/doc.pdf 
/assets/minima-social-icons.svg 
```

Other file attributes we can access:

- `file.name`: filename without path
- `file.basename`: without extension
- `file.extname`: extension

It is also possible to assign attributes to folers in the `_config.yaml` file so that they're assigned to the contained files; that way, we can tag all files in `assets/img` as images.

### 6.9 Filters

Filters can be used to extract information from variables. Several types of filters ccan be distinguished:

- [Standard Liquid Filters](https://shopify.github.io/liquid/filters/abs/)
- [Jekyll specific filter](https://jekyllrb.com/docs/liquid/filters/)
- User-defined [Jekyll filters that are created as plugins](https://jekyllrb.com/docs/plugins/filters/)

Typical [Standard Liquid Filters](https://shopify.github.io/liquid/filters/abs/):

```yaml
{{ -17 | abs }} # 17

{{ "March 14, 2016" | date: "%b %d, %y" }} # Mar 14, 16

{{ "now" | date: "%Y-%m-%d %H:%M" }} # 2022-03-11 16:24

{{ article.published_at | date: "%Y" }} # 2015

{{ "/my/fancy/url" | append: ".html" }} # /my/fancy/url.html

{% assign filename = "/index.html" %}
{{ "website.com" | append: filename }} # website.com/index.html

{{ "title" | capitalize }} # Title

{{ "Parker Moore" | upcase }} # PARKER MOORE

{{ "Parker Moore" | downcase }} # parker moore

{{ "Ground control to Major Tom." | split: " " | first }} # Ground

{% assign my_array = "zebra, octopus, giraffe, tiger" | split: ", " %}
{{ my_array.first }} # zebra

{% if my_array.first == "zebra" %}
  Here comes a zebra!
{% endif %}

{{ "Ground control to Major Tom." | split: " " | last }} # Tom.

{% assign beatles = "John, Paul, George, Ringo" | split: ", " %}
{{ beatles | join: " and " }} # John and Paul and George and Ringo

{{ "Have you read 'James & the Giant Peach'?" | escape }} # Have you read &#39;James &amp; the Giant Peach&#39;?

```

## 7. Deployment: Setting up a GitHub Pages Site with Jekyll

See the official guide: [Setting up a GitHub Pages site with Jekyll](https://docs.github.com/en/pages)

I followed that guide with some changes. I add the summary here, divided in the following sections/stages:

1. Create and Publish First Version
2. Check Website Locally and Work on It

Note that I wrote the howto for a concrete case:
- Github user: mxagar
- Github website repository: mxagar.github.io
- New domain, bought on namecheap: mikelsagardia.io

### 7.1 Create and Publish First Version

```
Create a new repository on GitHub: mxagar.github.io

	I set it public
	Is it possible to make it private?

Create a git repository on local machine and configure it properly

	cd ~/git_repositories
	git init mxagar.github.io
	cd mxagar.github.io

	# We need to use the gh-pages branch for automatic publishing
	# Create it without history and remove anything we have
	git checkout --orphan gh-pages
	git rm -rf 

Create a new Jekyll website project and configure it properly

	# Create a new Jekyll website project
	jekyll new --skip-bundle .

	# Open the Gemfile and change it
	# - Comment out:
			gem "jekyll"
	# - Change the line '# gem "github-pages"' to be:
			gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
	# - Note: GITHUB-PAGES-VERSION = 226 
			https://pages.github.com/versions/

	# Install Ruby/Jekyll dependencies
	bundle install

	# Fix webrick bug
	bundle add webricks

	# Update github-pages plugin
	bundle update github-pages

	# Configure _config.yaml: add/modify these lines
		domain: mxagar.github.io
		url: https://mxagar.github.io
		baseurl: ""

	# Upload website contents to the remote repository
	git add .
	git commit -m 'Initial GitHub pages site with Jekyll'
	git remote add origin git@github.com:mxagar/mxagar.github.io.git

	# Always push to the branch gh-pages for automatic publishing!
	git pull
	git push -u origin gh-pages

Check settings on GitHub
	
	Go to repository Settings: mxagar.github.io
	Left panel: Code and automation > Pages
	Check:
		Source
			Branch: gh-pages
			/ (root)
	Click on "Enforce HTTPS" if option is available

Check: website should be live, accessible online	
	https://mxagar.github.io
```

### 7.2 Check Website Locally and Work on It

If we want to render the website locally:

```
# Go to repository
cd ~/git_repositories/mxagar.github.io

# Get changes
git pull

# Update github-pages plugin
bundle update github-pages

# Serve the website locally
# For non-first times, we can also run 'jekyll serve'
bundle exec jekyll serve

# Open browser on localhost:4000
```

For working on the website:

```
# Always get changes that might have happened!
git pull

# Make changes locally

# Commit changes
git add <FILES>
git commit -m "message"

# Push to gh-pages branch
git push -u origin gh-pages

# New version will be deployed in few minutes automatically
```

### 7.3 Use Custom Domain

There are three main types of domains:
- `www` domain: `www.mikelsagardia.io` 
- Subdomains: `blog.mikelsagardia.io`
- Apex domains `mikelsagardia.io`

Github reocmmends using `www` domains, because they redirect them to apex domains, too.
I am using an apex domain: `mikelsagardia.io`

Here it is how I set it up:

```
Buy domain at wwww.namecheap.com
	
	mikelsagardia.io

Create a CNAME file on the website repository which contains the domain string
That is automatically generated if we insert the domain name on the GitHub settings
	
	Go to Github repository Settings
	Left panel: Code and automation > Pages: Custom domain
		mikelsagardia.io
		Check domain
			First time won't work, because we need to make chanes on the DNS provider: namecheap
			After the changes in the DNS provider, we probably need to wait 30 mins
		Enforce HTTPS
	
Go to domain provider and add the IPs of the Hosting (Github): 
DNS provider: www.namecheap.com

	Domain list > Select domain: mikelsagardia.io > Manage > Advanced DNS
	HOST Records: Add Records (one record for each IP)

		Type: A
		Host: @ (bare domain)
		TTL: Automatic
		Value: IPs rovided by Github
			185.199.108.153
			185.199.109.153
			185.199.110.153
			185.199.111.153

Check that the records were propagated: open Terminal 30 mins later and execute

	dig mikelsagardia.io +noall +answer -t AAAA

	# The response should be

		; <<>> DiG 9.10.6 <<>> mikelsagardia.io +noall +answer -t A
		;; global options: +cmd
		mikelsagardia.io.	1799	IN	A	185.199.111.153
		mikelsagardia.io.	1799	IN	A	185.199.108.153
		mikelsagardia.io.	1799	IN	A	185.199.110.153
		mikelsagardia.io.	1799	IN	A	185.199.109.153

Go to GitHub repository Settings again:


	Left panel: Code and automation > Pages: Custom domain
		mikelsagardia.io
		Check domain
			After the changes in the DNS provider, we probably need to wait 30 mins
			Then, it should work
		Enforce HTTPS

Open browser: and check the website is deployed!
	
	https://mikelsagardia.io

Go to local website repostory: pull changes: CNAME

	cd ~/git_repositories/mxagar.github.io
	git pull

```

## 8. Project: Create a Company Landing Page with a Blog

In this section, I play around with the theme and website project from the Udemy course by Jana Bergant [Jekyll: make fast, secure static sites and blogs with Jekyll](https://www.udemy.com/course/static-website-generator-fast-secure-sites-blogs-with-jekyll).

First, we create a new website project following Section 5.2: Manual Installation with Downloaded Theme Packages.

That leads to the project `05_website_project/`.

All the changes are committed, but I don't thoroughly explain all the changes here. Instead, if techniques are relevant, they are written in the other sections. Here, a simple list of actions is collected in sections

### Modularization: Layouts & Includes

- A default layout is created: `_layouts/default.html`. It contains the header and footer HTML code wrapping the `{{content}}`. In the rest of the HTML files, the header & footer HTML code is removed and we add a front matter with the `layout: default`, and their title. This makes possible to control our header and footer in one file!
- The metadata title of each page is changed to be a Liquid conditional in the `default.html`: `{% if page.title %}{{ page.title }}{% else %}Great web agency{% endif %}`. This allows to display the title of each page, as defined in its front matter!
- Includes are created: `_includes/subpage-header.html`, `_includes/home-slider.html`. Similarly as before, code pieces are removed from the other pages and inludes are done with Liquid; e.g.: `{% include home-slider.html %}`.
- Include HTML files are also customized with Liquid: `{{ page.title }}`. That way, each injected include adapts its content to the page it is inserted into.
- Similarly, includes are created for all the reusable components of the web, and injected where it proceeds (in all pages execpt in `post.html`). A list of the contents in `_includes/` after the moddularization:
	- `about.html`
	- `call-to-action.html`
	- `contact-info.html`
	- `home-services.html`
	- `nav.html`
	- `subpage-header.html`
	- `believe.html`
	- `clients.html`
	- `footer-nav.html`
	- `home-slider.html`
	- `portfolio.html`
	- `blog-posts.html`
	- `contact-form.html`
	- `google-map.html`
	- `home-testimonials.html`
	- `social-icons.html`

### Configuration

The main configuration happens in `_config.yaml`. Every time we change this file, the serving must be restarted.

The variables in it are discussed. Note that `description` is very important: it is used by Google (include relevant keywords) and it is shown by Google!

Additionally, the `default.html` is updated to contain these updated lines:

```html
<title>{% if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}</title>
<meta name="description" content="{% if page.description %}{{ page.description }}{% else %}{{ site.description }}{% endif %}">
<base href="{{ site.url }}">
```

### Navigation Menu

The navigation menu in `nav.html` is modified to contain the correct links and highlight the active page. Note that th eindex page needs to be detected with `"/"` only.

```html
<!-- Collect the nav links, forms, and other content for toggling -->
<div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
  <ul class="nav navbar-nav navbar-right">
    <li {% if page.url == "/" %} class="active" {% endif %}><a href="index.html">Home</a></li>
    <li {% if page.url == "/about-us.html" %} class="active" {% endif %}><a href="about-us.html">About</a></li>
    <li {% if page.url == "/work.html" %} class="active" {% endif %}><a href="work.html">Portfolio</a></li>
    <li {% if page.url == "/blog.html" %} class="active" {% endif %}><a href="blog.html">Blog</a></li>
    <li {% if page.url == "/contact.html" %} class="active" {% endif %}><a href="contact.html">Contact</a></li>
  </ul>
</div><!-- /.navbar-collapse -->
```

### Blog Post Layout: `_layouts/post.html`

- Blog posts can be written by adding `_posts/YEAR-MONTH-DAY-my-title.markdown` files. They are written with front matter and HTML, Markdown & Liquid content.
- The post layout `_layouts/post.html` is created using the provided code. In it, HTML code is pasted with Liquid variables.
	- Conditionals, loops, variable filters, etc.: many Liquid functionalities are used
	- Includes are done with HTML pieces
	- Side panels or Widgets (posts with same categories, contact) are created/displayed

Example post `2022-05-01-benefits-of-static-site-generators.markdown`. Note that later some variables are defined in the default front matter in `_config.yaml`:

```yaml
---
layout: post
title: Benefits of static site generators
date: 2022-05-01 12:00
author: Mikel
image: https://place-hold.it/900x300
lead: "Leading sentences of the post. If there is a lesson to be learned, it is the futility of seeking fulfillment in outer space. We need to judge ourselfs by who we are, not by where we go."
categories:
- jekyll
- static website generation
- blogging
subtitle: Post subtitle - Create ultra fast, secure blog posts
permalink: /blog/:year/:title
---

Text.

```

Blog post layout `_layouts/post.html`

```html
---
layout: default
---

{% include subpage-header.html %}

<!-- POST HTML -->
<article id="post">
    <div class="container">

        <div class="row">

            <!-- Blog Post Content Column -->
            <div class="col-lg-8">

                <!-- Blog Post -->

                <!-- Title -->
                <h1>{{ page.title }}</h1>

                <!-- Author -->
                <p class="lead">
                    by {{ page.author }}
                </p>

                <hr>

                <!-- Date/Time -->
                <p><span class="glyphicon glyphicon-time"></span> Posted on {{ page.date | date: "%B %d, %Y"}}</p>

                <hr>
                
                   <!-- Preview Image -->
                   {% if page.image %}
                   <img class="img-responsive" src="{{ page.image }}" alt="{{ page.image }}">
                   {% endif %}

                <hr>

                <!-- Post Content -->
                {% if page.lead %}
                <p class="lead">{{ page.lead }}</p>
                {% endif %}
                
				{{ content }}

                <hr>

                  <span class="previous-link">
                  	{% if page.previous %}
                    <a rel="prev" href="{{ page.previous.url }}">Previous article</a>
                    {% endif %}
                  </span>
                
                  <span class="next-link pull-right">
                  	{% if page.next %}
                    <a rel="next" href="{{ page.next.url }}">Next article</a>
                    {% endif %}
                  </span>               
                <hr>
            </div>

            <!-- Blog Sidebar Widgets Column -->
            <div class="col-md-4">

                <!-- Blog Categories Well -->
                <div class="well">
                	{% for category_name in page.categories limit:1 %}
                    <h4>{{ category_name | capitalize }}</h4>
                    <div class="row">
                        <div class="col-lg-12">
                            <ul class="list-unstyled">
                            	{% for post in site.categories[category_name] limit:5 %}
                                <li><a href="{{ post.url }}">{{ post.title }}</a>
                                </li>
                                {% endfor %}
                            </ul>
                        </div>
                    </div>
                    {% endfor %}
                    <!-- /.row -->
                </div>

                <!-- Side Widget Well -->
                <div class="well">
                	{% include contact-info.html %}
                </div>

            </div>

        </div>
        <!-- /.row -->
    </div>
</article>

```

### Blog Post List

A blog post loop is created in `_layouts/blog-posts.html`, included in `blog.html`

```html
<!-- Blog HTML -->
<section id="blog">
    <div class="container"> 
        <div class="row">
            <div class="col-lg-10 col-lg-offset-1 col-md-10 col-md-offset-1"> 
                {% for post in site.posts %}
                <!-- Blog Post -->
                <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

                <p class="lead">by <a href="#">{{ post.author }}</a></p>
                <p><span class="glyphicon glyphicon-time"></span> Posted on {{ post.date | date: "%B %d, %Y" }}</p>
                {% if page.image %}
                <img class="img-responsive" src="{{ post.image }}" alt="{{ post.title }}">
                <hr>
                {% endif %}
                {{ post.excerpt }}             
                <a class="btn btn-primary" href="{{ post.url }}">Read More <span class="glyphicon glyphicon-chevron-right"></span></a>
                <hr> 
                {% endfor %}

            </div>
        </div> 
    </div>
</section>
```

## 9. Comments

Even though ststic site generators cannot natively have databases with dynamic content, we can add comments to our blog/website via third party services. [Disqus](https://disqus.com) is a commonly used service.

Steps:
- Create a Disqus account.
- Add a new disqus site: Settings > Add Disqus to Site
	- Scroll down: Get Started
- I want to install Disqus on my site
- Write our website name, category, etc.
- Select free plan
- Select Jekyll / Universal code
- Follow instructions; see summary below.

My Disqus page settings are as follows:
- Shortname: mikelsagardia
- Website Name: mikelsagardia.io
- Website URL: https://mikelsagarda.io

After setting the Disqus page up, we need to inject the HTML code in our posts. The easiest way is to create `_includes/disqus-comments.html` with the Disqus-provided code and then include & enable it in the post markdown.

Post markdown:

```html
---
comments: true
---

My post text.

{% if page.comments %} 
{% include disqus-comments.html %}
{% endif %}

```

Disqus comments injenction HTML code: `_includes/disqus-comments.html`

```html
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    
    var disqus_config = function () {
    this.page.url = '{{ page.url | absolute_url }}';  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = '{{ page.url | absolute_url }}'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://mikelsagardia.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
```

## 10. Forms

There are several options to add forms to Jekyll websites: [Jekyll Contact Forms](https://jekyllthemes.io/resources/jekyll-contact-forms)

The recommended option is [Formspree](https://formspree.io). I will list the steps that need to be carried out, but no detailed code pieces are collected here:

- We create a free account.
- We create a new form, with a unique identifier and a specific code to be injected.
- A file `_includes/contact-form.html` is created, where the code generated by Formspree needs to be pasted. We can use the blueprint from Section 8. Note that probably the HTML and CSS files need to be modified, if the field number and order do not match...
- After the visitors submit the form, a "Thank you" page can be shown, using the hidden variable `_next` provided by Formspree. We basically create a "Thank you" page and paste its URL to the variable.

## 11. Collection of Additional Things

### Exclude Pages from Navigation Menu in Jekyll

https://mycyberuniverse.com/exclude-pages-from-navigation-menu-in-jekyll.html

- Add `exclude: true` in front matter
- Use `{% unless page.exclude %}` in `_includes/header.html`

However, if we're using minima or any other theme not in our local site repo, we need to change the theme definition files:

```bash
bundle show minima
# ~/.gem/ruby/3.1.2/gems/minima-2.5.1
```

And then, move the changed files to the local site repo.

## 12. Personal Project: Create a Blank Static Website with a Custom Domain

This section explains how I created a blank static site with a custom domain. I bought the domain(s) at [www.namecheap.com](https://www.namecheap.com) and hosted the site(s) at [DigitalOcean](https://www.digitalocean.com). The first three static websites are free at Digital Ocean.

Some interesting links related to the topic:

- [How To Deploy a Static Website to the Cloud with DigitalOcean App Platform](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-static-website-to-the-cloud-with-digitalocean-app-platform)
- [Sample App for Jekyll](https://docs.digitalocean.com/products/app-platform/languages-frameworks/static-assets/jekyll/)
- [How To Deploy a Static Site from GitHub with DigitalOcean App Platform [Quickstart]](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-static-site-from-github-with-digitalocean-app-platform-quickstart)
- [Jekyll without a theme](https://stackoverflow.com/questions/57419996/jekyll-without-a-theme)
- [empty-jekyll-theme](https://github.com/garcon/empty-jekyll-theme)


### Step 1: Create a Blank Website in a Dedicated Github Organization (Private) Repository

I basically followed this Stackoverflow post: [Jekyll without a theme](https://stackoverflow.com/questions/57419996/jekyll-without-a-theme).

Before creating the empty website, I created a provate repo with a `README.md`; this time, under the/my organization: `machine-vision-academy`.

```bash
# Create a repository and clone it
# I created an organization and a private repo in it
# https://github.com/machine-vision-academy/machine-vision-academy-website
# Then, I directly cloned that repo
cd ~/git_repositories
git clone git@github.com:machine-vision-academy/machine-vision-academy-website.git
# Then, inside the repository, create a blank website
cd ~/git_repositories/machine-vision-academy-website
jekyll new . --blank --force # force ignores
bundle init
bundle add jekyll
bundle add webrick
# copy a 404 error page from any other project
cp .../404.html .
vim .gitignore # _site, etc.
# Edit the folloing files
# _config.yaml: add a title
# index.md: Add 'Coming Soon' content
# Test the website locally
bundle exec jekyll serve
# Browser: localhost:4000
# I had to execute this for a correct build on Digital Ocean
bundle lock --add-platform x86_64-linux
# Push the website to Github
git add .
git commit -m "..."
git push
```

### Step 2: Create a Digital Ocean App, Buy a Domain, and Deploy

I registered at [DigitalOcean](https://www.digitalocean.com) with my Github account.

The first 3 static websites are free and they are deployed as apps.

There is a [Sample App for Jekyll](https://docs.digitalocean.com/products/app-platform/languages-frameworks/static-assets/jekyll/), but you need to fork it; the issue is that I want to have a private repo for the website, which is not possible with forks.

Thus, I tried the following approach and it worked:

```
Buy domain at wwww.namecheap.com
	
	e.g., 
	machinevision.academy
		msagardia@machinevision.academy
	datamix.ai
		hello@datamix.ai

Create a Digital Ocean App

	Log in
	Apps > Create App
		Source: Github
		Edit Github permissions: add any permisions needed
			machine-vision-academy/machine-vision-academy-website
		Repository: Select
			machine-vision-academy/machine-vision-academy-website
		Branch: main
		Source Directory: /
		Autodeploy: ON
		Continue, Next, Create...

		Result: we will have an app
		with a static website nested beneath!
		Note: app containers are called jelly-app, orca-app, urchin-app, etc.

		Wait until the first deplozment is successful.

	App: Select our app
	Settings > Domains
		We see the default URL
			orca-app-tkq7l.ondigitalocean.app
			That's our URL!
			We can open it with a browser

If changes need to be made, make them in the website repo.
Push a working version to git.
	
	cd ~/git_repositories/machine-vision-academy-website
	make changes
	git add .
	git commit -m "..."

DigitalOcean dashboard: check deployment works

	Since deployment is automatic
	we should see site is building;
	check logs for any issues.

	Check: App > Settings > Components: machine-vision-academy-website

		We can see
			the source repo URL
			Command: bundle exec jekyll build -d ./public
				I did not write that, it was automatically generated!

	Check: App > Overview

		We should see the deployment status

DigitalOcean: Add Domain

	machinevision.academy
		https

	Two options: I selected: You manage your domain
		
		Copy add URL: orca-app-tkq7l.ondigitalocean.app.
		Add domain

Go to domain provider and add the App URL of the Hosting (DigitalOcean): 
DNS provider: www.namecheap.com

	Domain list > Select domain: machinevision.academy > Manage > Advanced DNS
	HOST Records: Add Records (one record for each IP)

		Type: CNAME Record
		Host: @ (bare domain)
		TTL: Automatic
		Value: orca-app-tkq7l.ondigitalocean.app

Check that the records were propagated: open Terminal 30 mins later and execute

	dig machinevision.academy +noall +answer -t AAAA

Go to DigitalOcean App Settings again:

	Check that domain is verified

	Wait 1h so tha changes are propagated

Open browser: and check the website is deployed!
	
	https://machinevision.academy

```

## 13. Some Links on Themes and Websites

### Theme Portals

- [Github `#jekyll-theme`](https://github.com/topics/jekyll-theme)
- [https://jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
- [http://jekyllthemes.org](http://jekyllthemes.org)
- [https://jekyllthemes.io](https://jekyllthemes.io)

### Interesting Selected Themes

- [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [How To Build a Website with HTML](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-html?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTOnrDkTx6aH73I-I1zsNt7vZu9Ff_wGEX2sH9OdAfTZFfFIgMjQEIhPFT6WNI9fSXvQkfpC4A-DPSMjP63wwOpcHqLS8pxrjMFocGPg)
- [How To Build a Website With CSS](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-website-with-css?mkt_tok=MTEzLURUTi0yNjYAAAGETSYTO6ayIs0-zVCBcnVyVnIMcdi5C9FiraEGRmtV2yzU2wJdb41l3l84ULsvcSqJlPbO1vFqyuQTpTNYUiprIB5BLsYVMxt-1s4LEVnj3A)

### Interesting Websites Examples

- Very interesting web and profile to use as a template: [Vincent Driessen](https://nvie.com):
	- Consulting company web
	- Personal page with about and posts
	- Linkedin profile: how to describe building a product, etc.

