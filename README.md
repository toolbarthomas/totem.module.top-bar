# Totem module: Top bar
Totem Module for displaying a sticky header

This module is created for [Totem](https://www.github.com/toolbarthomas/totem) projects but can also be used in any other Twig related project.

## Installation

Install totem.module.top-bar with [npm](https://www.npmjs.com/) (we assume you have pre-installed [node.js](https://nodejs.org/)).

```bash
$ npm install totem.module.top-bar --save
```

## Setup
Import all stylesheets within ITCSS order from your project stylesheet:

```scss
@import "...node_modules/totem.module.top-bar/stylesheets/shared/**";
@import "...node_modules/totem.module.top-bar/stylesheets/helpers/**";
@import "...node_modules/totem.module.top-bar/stylesheets/settings/**";
@import "...node_modules/totem.module.top-bar/stylesheets/tools/**";
@import "...node_modules/totem.module.top-bar/stylesheets/properties/**";
@import "...node_modules/totem.module.top-bar/stylesheets/generic/**";
@import "...node_modules/totem.module.top-bar/stylesheets/base/**";
@import "...node_modules/totem.module.top-bar/stylesheets/objects/**";
@import "...node_modules/totem.module.top-bar/stylesheets/components/**";
@import "...node_modules/totem.module.top-bar/stylesheets/utilities/**";
```

Next you should import jQuery before you can init the top bar module.
You can use the following example if your working withing a Totem project*:

```js
var $ = require('jquery'); //Require jQuery
window.jQuery = $; //Define jQuery as a global variable.

require('totem.module.top-bar'); // Require Top Bar module

$(function() {
    setTopBar(); // Init Top Bar
})
```

* Since we're requiring the above dependencies with Browserify you should only include the above example.

## Options
You can enable/disable certain settings from **stylesheets/settings/_settings.top-bar-features.scss**:

```scss
$top-bar-features: (
    'is-sticky': true, // Set the position to absolute or fixed
    'can-autohide': true, // Enable/disable autohide behaviour if the scroll position is larger than our the top-bar offset + height
    'can-peek': true // Enable/disable peek behaviour when scrolling upwards
) !default;
```

The easiest way to override these settings is by overriding the whole Sass Map: **$top-bar-features**.

## Extending
Because the stylesheets are loaded within the ITCSS it's very easy to include any extra styles.

You should do this with [Generator Totem](https://www.github.com/toolbarthomas/generator-totem) and generate a new module were you place any overrrides in.