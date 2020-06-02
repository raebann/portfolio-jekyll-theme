# Portfolio Website

This is a portfolio site built using a modified version of the [Portfolio Jekyll Theme by LeNPaul](https://github.com/LeNPaul/portfolio-jekyll-theme). This file is intended to be a brief-ish and fairly non-technical guide to instruct the site owner on how to configure, edit, and maintain the site. It's a lot of information, so don't worry if you don't remember everything or feel overwhelmed! This file will stay here as a reference, so no worries. :slightly_smiling_face:

## Table of Contents

1. [Introduction](#introduction)
   1. [Directory Structure](#directory-structure)
   2. [File Types](#file-types)
      1. [YAML](#yaml)
      2. [Markdown](#markdown)
      3. [Others](#others)
   3. [Jekyll & Liquid](#jekyll--liquid)
2. [Configuration & Usage](#configuration--usage)
   1. [Site Settings](#site-settings)
      1. [General Configuration](#general-configuration)
      2. [Theming](#theming)
      3. [Static Content](#static-content)
   2. [Managing Projects](#managing-projects)
      1. [Categories](#categories)
      2. [Project Pages](#project-pages)
      3. [Images](#images)
3. [Accessibility Considerations](#accessibility-considerations)
   1. [Colour Contrast](#colour-contrast)
   2. [Descriptive Test](#descriptive-text)
   3. [Semantic Markup](#semantic-markup)
   4. [Auditing](#auditing)

## Introduction

### Directory Structure

The site's directory structure pretty closely follows a standard Jekyll project (some files that you hopefully won't need to worry about have been omited):

```bash
Portfolio Jekyll Theme/
├── _data/                 # Data files
|   ├── layout.yml         # Theme settings (colours)
|   └── settings.yml       # Site settings and custom text
├── _includes/             # Theme includes
├── _layouts/              # Theme layouts
├── _pages/                # Theme/menu pages
├── assets/                # Stylesheets and images
|   ├── css/               # Stylesheets
|   └── img/               # Images, split by category
├── projects/              # Project pages, split by category
├── _config.yml            # Site build settings
├── favicon.ico            # Site favicon
├── index.html             # Home page
└── …                    # Mostly irrelevant stuff
```

### File Types

There are two file types that you will most likely have to edit: `.yml` (YAML) files for configuration & settings, and `.md` (Markdown) files for site content.

#### YAML

YAML is a simple markup language for defining data in plain text. In this site it's used for anything from defining theme colours, to menu items, to SEO (search engine optimization) tags. You generally won't have to edit these files often as the settings are mostly static.

Something you might notice about this file format is that any line that starts with `#` is a **comment**,which means it's ignored by the computer. You might also notice that some values are wrapped in single or double quotes (`'` or `"`) while others are not.  good rule of thumb is that when defining a value that will be dispalyed on some page or that contains spaces, you want to use quotes; when defining keywords for the computer, you don't. When you edit these files, also keep in mind that YAML is **whitespace-sensitive**, so the number of spaces at the beggining of a line matters.

This might be a bit overwhelming at first, so if you're confused, just try to match the formatting of similar sections in the YAML file.

#### Markdown

Markdown is a markup language for formatting documents (_e.g._ adding headers, bold and italic text, or links) in plain text. Here we use it to define the contents of the project pages. This is the format you'll be using most. There are plenty of [very](https://www.markdownguide.org/cheat-sheet/) [good](https://commonmark.org/help/) [guides](https://guides.github.com/features/mastering-markdown/) on to write Markdown, so I won't be going over the basics here.

> Markdown implementations tend to differ from one another, so your mileage may vary with any specific guide. Generally speaking the most common features are consistent, but if all else fails [this guide](https://kramdown.gettalong.org/quickref.html) should be the authoritative one for this site, since that's the Markdown version being used.

#### Others

Obviously there's a few other file types in the project, most notably:

* the site's layout is defined by `.html` files in `_includes/`, `_layouts/`, and `_pages/`;
* the styles are defined by the `.sass` files in `assets/css/`; and
* any images included in the website (probably `.jpg`, though in theory they could be any image format) are in `/assets/img/`.

Other than images ([discussed below](#images)) you won't have to touch these unless you want to change the site's fundamental appearance or behaviour.

### Jekyll & Liquid

TODO
* short overwiew of what exactly jekyll does
* mention frontmatter in md files
* brief explanation of what liquid is + link to docs (exlpain {% ... %} tags)

## Configuration & Usage

### Site Settings

Site settings live in one of two places: the `_config.yml` file, or the `_data/` folder. The former holds information about how the site is structured, while the latter has data about the presentation and content of the site's pages.

#### General Configuration

The `_config.yml` file has a bunch of boilerplate at the top, which you can ignore; it's just telling Jekyll how to process the files it finds. The interesting sections are `collections`, `title`, `description`, and `author`. We'll cover `collections` in the [categories section below](#categories). For now, all you need to know is that this defines the project categories for the site.

The `title`, `description`, and `author` values are mostly used for SEO. They should accurately describe the site. The `title` is also used as the site title (the text that appears in the browser tab) as well as in the site's "logo" (the text that appears on the top-left in the navigation menu).

#### Theming

The `_data` folder contains the `layout.yml` and `settings.yml` files. The first of these defines theme colours for the site. These colours are defined as hex codes, which look like `#1a2b3c` or `#789` (which is short for `#778899`). If you're not familiar with these, it should be relatively easy to figure out what colour a code represents: just Googling it shows the colour at the top of the search results. The colours in the file are:

* `accent`: This is the site's accent colour. It's used for the link colour, the hover colour of menu items, and the text highlight colour.
* `textColor`: This is the base text colour for most of the site. Note that links, menu items, and headers do not use this colour.
* `headlineColor`: This is the colour for individual page titles.
* `documentBackgroundColor`: This is the site's background colour.

When choosing colours, make sure the contrast between the foreground and background is high enough to abide by [accessibility requirements](#accessibility-considerations). Also note that (for now) menu items don't have any colour settings; they'll always be black (`#000000`). This means you can't give the site a dark theme as the menus will be illegible.

#### Static Content

The second file in `_data/`, `settings.yml`, contains the site's "static" content (I'm just calling it static because it presumably changes less often than projects, not because it can't or shouldn't change). It comprises three sections: `menu` at the top, `about` `cv` and `contact` in the middle, and `social` at the bottom. This mirrors the order they would appear in a page.

The `menu` section defines the menu on the top-right of every page. Each entry needs to have a `name` which will be displayed, and a `url` which is the page that should be linked. Optionally, a menu item can have a list of `children`, which each have the same structure. Note that the menu doesn't support a depth of more than two (_i.e._ children can't themselves have children).

The `about`, `cv`, and `contact` sections define the contents of each of those pages in Markdown. Notice that the first line of each starts with `>`. This just tells the YAML file that every indented line coming after is part of this section.

The `social` section behaves mostly like the `menu` above: each entry will add a social icon in the bottom menu. Each entry needs an `icon` (refer to [this list](https://fontawesome.com/v4.7.0/icons#brand) for available icons and their codes), a `link` to the social media profile, and a `name`. The name is for screenreader users, who can't see the icon and so need a brief textual description of where the link will go (the site's name should be enough in most cases). For email, the `link` should be formatted like `mailto:email@example.com`.

### Managing Projects

Of course, the cruz of the portfolio website is the **Projects** section. This section contains a bunch of project pages, split up into different categories. Managing these projects and categories is probably where you'll spend most of your time working on this site.

#### Categories

As [mentioned above](#general-configuration), the project categories are defined in the `_congif.yml` file, specifically in the `collections` section. It contains a list of categories, each labelled with a computer-friendly value used for the URL (meaning avoid spaces and uncommon characters) and containing the following parameters:

* `name`: The name to be displayed on the website.
* `weight`: This defines the order in which the categories are dispalyed on the home page; a lower number means it will show up first. Note that this doesn't affect the order of the menu items under **Projects**.
* `output`: This should always be `true`, otherwise Jekyll won't generate the category's project pages.

Each category additionally needs a folder inside the `projects/` directory. This folder should have the same name as the computer-friendly label we set in `collections`, prefixed with an underscore, and should contain an `index.md` file. Each `index.md` file should start with some boilerplate [frontmatter](#jekyll--liquid) containing at least these three values:

* `layout: default`;
* , `title: Category Name`, where `Category Name` is what you defined in `collections` (unfortunately because of the way Jekyll works I couldn't avoid duplicating this); and
* `permalink: /:collection`.

The file's contents should be a single [Liquid tag](#jekyll--liquid) that looks like so (where `CATEGORY_LABEL` is the computer-friendly category label mentioned above:

```liquid
{% include projects.html category=site.CATEGORY_LABEL %}
```

All this means that if you wanted to add a "Web Development" category, you might add the following lines to the `collections` object:

```yaml
collections:
  # the other categories omitted for brevity
  web_dev:
    name: "Web Development"
    weight: 4
    output: true
```

You would then create a folder named `_web_dev/` inside the `projects/` folder and add the following file to it with the name `index.md` (notice the Liquid tag at the end):

```md
---
layout: default
title: Web Development
permalink: /:collection
---

{% include projects.html category=site.web_dev %}
```

And **ta-dah**, you've got yourself a brand new project category! You can navigate to `yoursite.com/web_dev` to see the projects in this category: there are none right now, since we just created it. Obviously we want to change that, so let's see how to manage project pages.

> If you visit your home page after making these changes you'll notice that something's missing: the web development category doesn't have a thumbnail image. I'm going to go over project pages first, but if you want to you can [skip to the images section](#images) for instructions on how to fix that.

#### Project Pages

Now that we have a brand-new category, it's time to add content to it! Fortunately, managing projects is a lot easier than categories. Each project is just a single `.md` file in the category's folder. The file name is the URL where we can find it, while the file contents should be the frontmatter `layout: post` and `title: Project Page Title` (where `Project Page Title` is replaced with the actual page title, of course).

This will automatically generate the project page and add a link to it in its category page. Navigate to `yoursite.com/category/project/` to see the (still empty) page. To add content just type your Markdown under the frontmatter and save, and you should see the changes.

:tada: That's it! You have a new project page! :confetti_ball:

> If you go to the category page you'll see that the project page is automatically listed; however, as when we added a new category, the thumbnail image is missing. Keep reading to see how to add it!

#### Images

At this point, you know how to add text content to your site and to style it through Markdown, but you might be wondering about adding images to project pages. In fact, if you were eager and read through any of [the Markdown guides linked above](#markdown), you might've noticed that Markdown provides a way to include images. Howeber, this method gives up limited support over the end product, so we'll be using a [Liquid tag](#liquid--jekyll) instead.

But first, where should images live? If you recall the [directory structure](#directory-structure), there's a folder named `assets/img/`. The stucture of this folder should mirror the structure of the `projects/` folder: for each category folder in `projects/`, there should be a folder in `assets/img/` with the same **minus the leading underscore**. Each of those folders should contain one image named `thumb.jpg`, which is the category's thumbnail. Additionally, there should be a folder per project page, with the same name as the project. This folder should similarly include a `thumb.jpg` file that will be the project's thumbnail. So if you have a `web_dev` category with one project named `my_first_site.md`, you would have something like this:

```bash
Portfolio Jekyll Theme/
├── assets/
|   ├── img/                     # Images, split by category
|   |   └── web_dev/             # Web Development (category)
|   |       ├── thumb.jpg        # Category thumbnail
|   |       └── my_first_site/   # My First Site (project)
|   |           ├── thumb.jpg    # Project thumbnail
|   |           └── …            # Other project images
|   └── …
├── projects/                    # Project pages, split by category
|   └── _web_dev/                # Web Development (category)
|       └── my_first_site.md     # my First Site (project)
└── …
```

Any images contained **inside** a project should be in the same directory as that project's thumbnail (in this case, `assets/img/web_dev/my_first_site/`). To add the image to the project, include the following code in the Markdown file:

```liquid
{%
   include image.html image="filename.jpg"
   alt="A text description of the image."
   caption="An optional caption for the image."
%}
```

The tag can be written on a single line or split for legibility (as above). It contains the mandatory keywords `include image.html`, followed by three attributes:

* `image`: This should correspond to the image's filename, including the file extension.
* `alt`: A description of the image's contents, [required for accessibility](#descriptive-text).
* `caption`: Optionally used to add supplementary information about the image, such as copyright.

Assuming the image is in the correct location, it will then show up in the project page.

> Images load a lot slower than any other part of this site, because they're way way bigger. In order to use less bandwidth and to make the website load quickly, you want to avoid adding huge images to pages, especially if they won't be displayed at their original size. The site's theme currently constrains images to at most 615 pixels wide (there's no limit to the image height), so scale your images down before uploading them.

## Accessibility Considerations

Web accessibility can be hard! The WCAG (Web Consortium Accessibility Guidelines) are the gold standard for web accessibility, and they're notoriously complicated (for good reason). They have three levels of compliance which are, in order of most basic to most complete, A, AA, and AAA.

Fortunately, this site is fairly simple (and yours truly tried their best to make it accessible) so there shouldn't be too much for you to do. Mostly you'll need to make sure that any changes you make don't break the site's current level of accessibility. In that respect, there's two main things that I can think of:

* colour contrasts; and
* descriptive text for icons and images.

### Colour Contrast

The colours defined in `_data/layout.yml` need to conform to contrast requirements. Users with low vision (and also everyone else tbh) have trouble reading text when the contrast between the foreground and background are too low.

The WCAG mandates specific thresholds for different font sizes, so it's easiest to use [a tool like this](https://accessible-colors.com/) to check your chosen colours. For reference, at time of writing, the font size of your body text is 16px, and your headers range from 24px to 30px.

### Descriptive Text

Users who use screenreaders can't see your images or icons, so you need to provide them with some descriptive text instead. In this case, there's two places where that needs to happen: on the social menu icons, and in any images you include in project pages. The social menu icons were covered above in [the section about static content](#static-content).

Descriptive text for images was briefly mentioned in [the image section](#images). It should be contained in the `alt` attribute of the image, and should "convey the meaning or content that is displayed visually" ([W3C, 2019](https://www.w3.org/WAI/tutorials/images/informative/)). Note that a literal description is sometimes, but not always, the appropriate text. More detailed guidelines can be found at the page cited above.

This text will not be visible to sighted users. As such, if you want to include **complementary** rather than **descriptive** text (such as attribution information), you should do so in the `caption` attribute, which will show up underneath the image and will also be accessible to screenreaders. The usage of the `caption` does not make the `alt` tag unecessary; rather, they fulfill distinctly different purposes.

> There are **some** cases where it's appropriate to leave the `alt` tag empty: when an image serves a [purely decorative purpose](https://www.w3.org/WAI/tutorials/images/decorative/). This doesn't mean that the image contains no textual information, but rather that no information whatsoever is conveyed through them. This is the case for category of project thumbnail images: they're just there to make the links prettier. A photo of an art installation in a project page, on the other hand, might contain no textual information but probably conveys some (visual) information and as such requires descriptive text.

### Semantic Markup

TODO
* avoid # or === in md bc we already have an h1 tag in post pages

### Auditing

TODO
* how to run an accessibility audit on a page
