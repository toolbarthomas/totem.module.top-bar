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

Next you must import jQuery before you can init the top bar module.
You can use the following example if your working withing a Totem project*:

```js
var $ = require('jquery'); //Require jQuery from Node with Browserify
window.jQuery = $; // Define the jQuery namespace as a global variable.

require('totem.module.top-bar'); //Require jQuery from Node with Browserify

$(function() {
    setTopBar(); // Init Top Bar
})
```

* Since we're requiring the above dependencies with Browserify you should only include the above example.

## CSS Options
You can enable/disable certain settings from **stylesheets/settings/_settings.top-bar-features.scss**:

```scss
$top-bar-features: (
    'is-sticky': true, // Set the position to absolute or fixed
    'can-autohide': true, // Enable/disable autohide behaviour if the scroll position is larger than our the top-bar offset + height
    'can-peek': true // Enable/disable peek behaviour when scrolling upwards
) !default;
```

### is-sticky
By default, the top bar element will stick to the top of the viewport by using position: absolute.
You can change this behaviour by changing the key **is-sticky** within the $top-bar-features Sass map.

### can-autohide
By default, the top bar element will autohide when the scrolk position of the viewport is greater than the vertical position & outerheight of the top bar.
You can change this behaviour by changing the key **can-autohide** within the $top-bar-features Sass map.

### can-peek
By default, the top bar element will show when scrolling upwards after it faded out.
You can change this behaviour by changing the key **can-peek** within the $top-bar-features Sass map.

## JS Options

### Custom push element
By default, the top bar script will generate a push element so it won't overlap any content.
You can define a custom element that will be used as push element.

```js
setTopBar(
    $('.my-custom-push') // Will set the height of every .my-custom-push element to the top bar's height
);
```

### Custom trigger position
By default, the top bar will trigger some classes based on the viewports scroll position:

1. Small - Uses the class: .js__top-bar--small to the top bar wich can be used for styling purposes. This class will be added if the viewports scrolltop is higher than the top bar element position + outerheight
2. Autohide - Uses the class: .js__top-bar--autohide to hide the top bar element. This class will be added if the viewports scrolltop is higher than the top bar element position + (outerheight * times 2).

You can adjust the trigger position by defining a custom trigger element

```js
setTopBar(
    undefined, //Push Element is not used in this examle
    $('.my-custom-trigger') // The top bar will trigger it's classes when the user scrolls passed this element
);
```

## Styling
This module only offers some base styling (e.g. autodhide & sticky position). Any other styles should be defined from any child element within the top bar.