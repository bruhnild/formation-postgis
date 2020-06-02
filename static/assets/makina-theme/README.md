# Custom Makina themes for reveal

Install dependencies

```
npm i
```

Build themes

```
npm run build
```

# Use with Reveal.js

Add this repository as a submodule of yours by executing:

```sh
$ git submodule add git@gitlab.makina-corpus.net:formation/theme-reveal.git makina-theme
```

Then create a symlink to the `css/theme` directory by doing:


```sh
$ ln -s makina-theme/makina.css css/theme
```

Now you can use it in your index.html:

```html
…
<link rel="stylesheet" href="css/theme/makina.css">
…
```

Later to update the theme, you can execute:

```sh
$ git submodule update
```

# Use with Reveal-md

Add this repository as a submodule of yours by executing:

```sh
$ git submodule add git@gitlab.makina-corpus.net:formation/theme-reveal.git makina-theme
```

Caution: the `makina-theme` dir should be at the same level as the markdown file.

Then you can use it by using a *Front matter* on top of your markdown slide file:

```md
---
title: Your title
separator: <!--h-->
verticalSeparator: \n---\n
css: 'theme-makina/makina.css' # Here
revealOptions:
  transition: 'slide'
  slideNumber: true
  fragmentInURL: true
---

[…]
```

or by using command line parameter:

```sh
$ reveal-md slide.md --css makina-theme/makina.css
```

Later to update the theme, you can execute:

```sh
$ git submodule update
```

# Some specific helpers

- Add `title` class to a slide to display makina-corpus logo.
- Add `logo` class to a slide to display makina-corpus logo.
- Add `alternate` to make a reversed color slide
- Add `program` to make a program slide
- Add `progress` to make a progress slide
- Add `bg-rocks` or `bg-dog-grey` or  `bg-dog` or  `bg-lenin` 
  or  `bg-lion-left` or   `bg-python` or  `bg-lion` to add an image.

# Reveal instructions to build custom theme

## Dependencies

Themes are written using Sass to keep things modular and reduce the need for repeated selectors across files. Make sure that you have the reveal.js development environment including the Grunt dependencies installed before proceeding: https://github.com/hakimel/reveal.js#full-setup

## Creating a Theme

To create your own theme, start by duplicating a ```.scss``` file in [/css/theme/source](https://github.com/hakimel/reveal.js/blob/master/css/theme/source). It will be automatically compiled by Grunt from Sass to CSS (see the [Gruntfile](https://github.com/hakimel/reveal.js/blob/master/Gruntfile.js)) when you run `npm run build -- css-themes`.

Each theme file does four things in the following order:

1. **Include [/css/theme/template/mixins.scss](https://github.com/hakimel/reveal.js/blob/master/css/theme/template/mixins.scss)**
Shared utility functions.

2. **Include [/css/theme/template/settings.scss](https://github.com/hakimel/reveal.js/blob/master/css/theme/template/settings.scss)**
Declares a set of custom variables that the template file (step 4) expects. Can be overridden in step 3.

3. **Override**
This is where you override the default theme. Either by specifying variables (see [settings.scss](https://github.com/hakimel/reveal.js/blob/master/css/theme/template/settings.scss) for reference) or by adding any selectors and styles you please.

4. **Include [/css/theme/template/theme.scss](https://github.com/hakimel/reveal.js/blob/master/css/theme/template/theme.scss)**
The template theme file which will generate final CSS output based on the currently defined variables.
