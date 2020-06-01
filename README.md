# Portfolio Website

This is a portfolio site built using a modified version of the [Portfolio Jekyll Theme by LeNPaul](https://github.com/LeNPaul/portfolio-jekyll-theme). This file is intended to be a brief-ish and fairly non-technical guide to instruct the site owner on how to configure, edit, and maintain the site.

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
   2. [Categories](#categories)
   3. [Project Pages](#project-pages)
   4. [Images](#images)
3. [Accessibility Considerations](#accessibility-considerations)
   1. [Colour Contrast](#colour-contrast)
   2. [Descriptive Test](#descriptive-text)

## Introduction

### Directory Structure

The site's directory structure pretty closely follows a standard Jekyll project (some files that you hopefully won't need to worry about have been ommited):

```bash
Portfolio Jekyll Theme/
├── _data/                  # Data files
|   ├── layout.yml          # Theme settings (colours)
|   └── settings.yml        # Site settings and custom text
├── _includes/              # Theme includes
├── _layouts/               # Theme layouts
├── _pages/                 # Theme/menu pages
├── assets/                 # Stylesheets and images
|   ├── css/                # Stylesheets
|   └── img/                # Images, split by category
├── projects/               # Project pages, split by category
├── _config.yml             # Site build settings
├── favicon.ico             # Site favicon
├── index.html              # Home page
└── ...                     # Mostly irrelevant stuff
```

### File Types

There are two file types that you will most likely have to edit: `.yml` (YAML) files for configuration & settings, and `.md` (Markdown) files for site content.

#### YAML

YAML is a simple markup language for defining data in plain text. In this site it's used for anything from defining theme colours, to menu items, to SEO tags. You generally won't have to edit these files often as the settings are mostly static.

When you do edit them though, keep in mind that YAML is *whitespace-sensitive*, so the number of spaces at the beggining of a line matters.

#### Markdown

Markdown is a markup language for formatting documents (_e.g._ adding headers, bold and italic text, or links) in plain text. Here we mostly use to define the contents of the project pages. This is the format you'll be using most. There are plenty of [very](#https://www.markdownguide.org/cheat-sheet/) [good](#https://commonmark.org/help/) [references](#https://guides.github.com/features/mastering-markdown/) online for how to write Markdown.

> Markdown implementations tend to differ from one anotother, so your mileage may vary with any specific guide. Generally speaking, the most common features are consistent, but if all else fails, [this guide](#https://kramdown.gettalong.org/quickref.html) should be the authoritative one for this site, since that's the Markdown version being used.

#### Others

Obviously there's a few other file types in the project, most notably:

* the site's layout is defined by `.html` files in `_includes/`, `_layouts/`, and `_pages/`,
* the styles are defined by the `.sass` files in `assets/css/`, and
* any images included in the website (probably `.jpg`, though in theory they could be any image format) are in `/assets/img/`.

Other than images ([discussed below](#images)) you won't have to touch these unless you want to change the site's fundamental appearance or behaviour.

### Jekyll & Liquid

TODO
* short overwiew of what exactly jekyll does
  * mention frontmatter?
* brief explanation of what liquid is + link to docs (will be useful in images section later maybe)

## Configuration & Usage

### Site Settings

Site settings live in one of two places: the `_config.yml` file, or the `_data/` folder. The former holds data about how the site is structured, while the latter has information about the presentation and content of the site's pages.

#### General Configuration

The `_config.yml` file has a bunch of boilerplate at the top, which you can ignore; it's just telling Jekyll how to process the files it finds. The interesting sections are `collections`, `title`, `description`, and `author`. We'll cover `collections` in the [categories section below](#categories). For now, all you need to know is that this defines the project categories for the site.

The `title`, `description`, and `author` values are mostly used for SEO. They should accurately describe the site. The `title` is also used as the site title (the text that appears in the browser tab) as well as in the site's "logo" (the text that appears at the top-left in the navigation menu).

#### Theming

The `_data` folder contains the `layout.yml` and `settings.yml` files. The first of these defines theme colours for the site. These colours are defined as hex codes, which look like `#1a2b3c` or `#789` (which is short for `#778899`). It should be relatively easy to figure out what colour a code represents: just Googling shows the colour at the top of the search results. The colours in the file are:

* `accent`: This is the site's accent colour. It's used for the link colour, the hover colour of menu items, and the text highlight colour.
* `textColor`: This is the base text colour for most of the site. Note that links, menu items, and headers do not use this colour.
* `headlineColor`: This is the colour for individual page titles.
* `documentBackgroundColor`: This is the site's background colour.

When choosing colours, make sure the contrast between the foreground and background is high enough to abide by [accessibility requirements](#accessibility-considerations). Also note that (for now) menu items don't have any colour settings; they'll always be black. This means you can't give the site a dark theme as the menus will be illegible.

#### Static Content

The second file in `_data`, `settings.yml` contains the site's "static" content (I'm just calling it static because it presumably changes less often than projects, not because it can't or shouldn't change). It comprises three sections: `menu` at the top, `about` `cv` and `contact` in the middle, and `social` at the bottom. This mirrors where in a page each of these things would appear.

The menu `section` defines the menu on the top-right of every page. Each entry needs to have a `name` which will be displayed, and a `url` which is the page that should be linked. Optionally, a menu item can have a list of `children`, which follow the same structure. Note that the menu doesn't support a depth of more than two (_i.e._ children can't themselves have children).

The `about`, `cv`, and `contact` sections define the contents of each of those pages in Markdown. Notice that the first line of each starts with `>`: this just tells the YAML file that every indented line coming after is part of this section.

The `social` section behaves mostly like the `menu` above: each entry will add a social icon in the bottom menu. Each entry needs an `icon` (refer to [this list](https://fontawesome.com/v4.7.0/icons#brand) for available icons and their names), a `link` to the profile, and a `name`. The name is for screenreader users, who can't see the icon and so need a bref textual description of where the link will go (the site's name should be enough in most cases). For email, the `link` should be formatted like `mailto:email@example.com`.

### Categories

TODO
* how to manage (existing & new) categories (`_config.yml`, subdir structure, and `index.html` files)
  * don't forget that title lives in two places ugh

### Projects Pages

TODO
* how to add a project page, how to edit, what the frontmatter settings are, etc
* make sure to mention images in brief (link below), and links

### Images

TODO
* how to add an image to a post, where they should live, how to make sure they're as accessible as possible, etc

## Accessibility Considerations

Web accessibility is hard! The WCAG (Web Consortium Accessibility Guidelines) are the gold standard for web accessibility, and they're notoriously complicated (for good reason). They have three levels of compliance which are, in order of most basic to most complete, A, AA, and AAA.

Fortunately, this site is fairly simple (and yours truly tried their best to make it accessible) so there shouldn't be too much for you to do. Mostly you'll need to make sure that any changes you make don't break the site's accessibility. In that respect, there's only two things you need to pay attention to, both mentioned elsewhere in the document:

* colour contrasts, and
* descriptive text for icons and images.

### Colour Contrast

The colours defined in `_data/layout.yml` need to conform to contrast requirements. Users with low vision (and also everyone else tbh) have trouble reading text when the contrast between the foreground and background are too low.

The WCAG mandates specific thresholds for different font sizes, so it's easiest to use [a tool like this](https://accessible-colors.com/) to check your chosen colours. For reference, at time of writing, the font size of your body text is 16px, and your headers range from 24px to 30px.

### Descriptive Text

Users who use screenreaders can't see your images or icons, so you need to provide them with some descriptive text instead. In this case, there's two places where that needs to happen: on the social menu icons, and in any images you include in project pages. The social menu icons were covered above in [the section about static content](#static-content).

<TODO images>
