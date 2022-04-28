# Jekyll Website Development and Deployment Guide

These are my personal notes related to creating and deploying static web pages with [Jekyll](https://jekyllrb.com).

The notes originated from various sources, among others:

- The Youtbe [tutorial by Mike Dane](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB).
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




## 1. Introduction

Jekyll generates static pages from easy Markdown files.
Static pages, in contrast to dynamic ones, don't change with user interaction, i.e., we don't have real shopping carts or the like.

Wordpress creates dynamic pages, it's a content management system (CMS). But in reality, in most of the cases we don't need a dynamic page. Plus, Wordpress introduces some vulnerabilities.

Static websites are a collection of HTML, CSS and Javascript files, in addition to any media file we want to use. They don't change in the server -- although I understand we can visualize different things, by using Javascript.

In contrast to dynamic sites (e.g., Wordpress), there is no database.

Main benefits of static sites
- Performaces: tehy are much faster
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
	- `cat1/...`: blog posts, ordered in the categoroes we assign them and year/month/day folders
- `_config.yaml`: very important file in which we configure our website; we need to change this file!
- `Gemfile`: dependencies listed by ruby/gem for our website; if we want plugins/themes, we need to specify them here.
- `index.markdown`: main website page description in markdown; we can modify its contents!
- `about.markdown`: about page description in markdown; we can modify its contents!
- `404.html`: default error/not-found website
- `.gitignore`: automatically generated git-ignore file


**Important; Jekyll tracks any change that happens in the project folder and automatically updates the `_site` folder used to serve the website; so we don't need to stop and restart the server!**

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
- `date`: use the convention, we can really write any date
- `categories`
- `author`

--- TODO

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

Edit as usually:

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

### 5.1 Installation with the `Gemfile`

In order to install it with `gem` or the `Gemfile`, we **first** need to get its name in the [rubygems.org](https://rubygems.org) repository:

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



## 6. Layouts



## X. Deployment: Setting up a GitHub Pages site with Jekyll

[Setting up a GitHub Pages site with Jekyll](https://docs.github.com/en/pages)

## X. Some Links on Themes and Websites

### Theme Portals

- [Github `#jekyll-theme`](https://github.com/topics/jekyll-theme)
- [https://jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
- [http://jekyllthemes.org](http://jekyllthemes.org)
- [https://jekyllthemes.io](https://jekyllthemes.io)

### Interesting Selected Themes


### Interesting Websites Examples



