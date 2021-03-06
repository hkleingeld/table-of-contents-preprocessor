# Table of Contents Generator

## About

Say you've got a README.md file with lots of information, and you want to
create a table of contents with reference links

This script will help you to do so. It extracts information of titles
in a given file and inserts a formatted table of contents in the position,
specified by `@@TOC@@` line.

## Table of Contents

The table of contents for the README.md was generated with
this utility, so you can treat it as a demo

- [Table of Contents Generator](#table-of-contents-generator)
    - [About](#about)
    - [Installation](#installation)
    - [Usage](#usage)
    - [Example](#example)
    - [Limitations](#limitations)

## Installation

Easy with npm
```
npm install -g md-toc-filter
```

## Usage

First, make sure you've got `@@TOC@@` token on a separate
line in your markdown-file. This is the place the table of contents
will be inserted to.

Then, preprocess the file:
```
md-toc-filter README.md > NEW_README.md
```

You can also specify the maximal heading depth to be included in the TOC by
passing the `-d` argument:
```
md-toc-filter -d 2 README.md > NEW_README.md
```
This will include headings up to depth 2 (##).

Pass the `-a` argument to use an alternative link generation mode, e.g. convert
the heading "3.1.1. Foo" to "3-1-1-foo" instead of "311-foo". This argument will
also strip all the non-Latin and non-numeric characters. This is useful for some
Markdown renderers like the GitLab Markdown renderer.
## Example

```
# Foo Great Project

Hey, this is my project

## Contents
@@TOC@@

## About

Some info about it

## Authors

My picture here
```

Will be transformed to
```
# Foo Great Project

Hey, this is my project

## Contents
- [Foo Great Project](#foo-great-project)
    - [Contents](#contents)
    - [About](#about)
    - [Authors](#authors)

## About

Some info about it

## Authors

My picture here
```

After the preprocessing you're free to modify the result as you wish.
For example, it makes sense to remove reference to table of contents from
table of contents

## Limitations

The script doesn't support underlined titles like this
```
My Title
========
```

Use sharps instead
```
# My Title
```
