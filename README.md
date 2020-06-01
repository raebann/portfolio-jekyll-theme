# Portfolio Website

This is a portfolio site built using a modified version of the [Portfolio Jekyll Theme by LeNPaul](https://github.com/LeNPaul/portfolio-jekyll-theme). This file is intended to be a brief non-technical guide to instruct the site owner on how to configure, edit, and maintain the site.

## Table of Contents

1. [Introduction](#introduction)
   1. [Directory Structure](#directory-structure)
   2. [File Types](#file-types)
2. [Configuration & Usage](#configuration-&-usage)
   1. [Site Settings](#site-settings)
   2. [Categories](#categories)
   3. [Project Pages](#project-pages)
   4. [Images](#images)
   5. [Accessibility Considerations](#accessibility-considerations)

## Introduction

### Directory Structure

The site's directory structure pretty closely follows a standard Jekyll project (some files that you hopefully won't need to worry about have been ommited):

```bash
Portfolio Jekyll Theme/
├── _data/                  # Data files
|  ├── layout.yml           # Theme settings (colours)
|  └── settings.yml         # Site settings and custom text
├── _includes/              # Theme includes
├── _layouts/               # Theme layouts
├── _pages/                 # Theme/menu pages
├── assets/                 # Stylesheets and images
|  ├── css/                 # Stylesheets
|  └── img/                 # Images, split by category
├── projects/               # Project pages, split by category
├── _config.yml             # Site build settings
├── favicon.ico             # Site favicon
├── index.html              # Home page
└── ...                     # Mostly irrelevant stuff
```

### File Types

There are two file types that you will most likely have to edit: `.yml` (YAML) files for configuration & settings, and `.md` (Markdown) files for site content.

YAML is a simple markup language for defining data in plain text. In this site it's used for anything from defining theme colours, to menu items, to SEO tags. You generally won't have to edit these files often as the settings are mostly static.

Markdown is a markup language for formatting documents (_e.g._ adding headers, bold and italic text, or links) in plain text. Here we mostly use to define the contents of the project pages. This is the format you'll be using most. There are plenty of [very](#https://www.markdownguide.org/cheat-sheet/) [good](#https://commonmark.org/help/) [references](#https://guides.github.com/features/mastering-markdown/) online for how to write Markdown.

> Markdown implementations tend to differ from one anotother, so your mileage may vary with any specific guide. Generally speaking, the most common features are consistent, but if all else fails, [this guide](#https://kramdown.gettalong.org/quickref.html) should be the authoritative one for this site, since that's the Markdown version being used.

Obviously there's a few other file types in the project, most notably:

* the site's layout is defined by `.html` files in `_includes/`, `_layouts/`, and `_pages/`,
* the styles are defined by the `.sass` files in `assets/css/`, and
* any images included in the website (probably `.jpg`, though in theory they could be any image format) are in `/assets/img/`.

Other than images ([discussed below](#images)) you won't have to touch these unless you want to change the site's fundamental appearance or behaviour.

## Configuration & Usage

### Site Settings

TODO

### Categories

TODO

### Projects Pages

TODO

### Images

TODO

### Accessibility Considerations

TODO
