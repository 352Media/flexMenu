#flexMenu
flexMenu is a jQuery plugin that lets you create responsive menus that automatically collapse into a "more" drop-down when they run out of space.

[Demo](http://352media.github.com/flexMenu/)

[Source on GitHub](https://github.com/352Media/flexMenu)

Written by [Ryan DeBeasi](http://www.ryandebeasi.com/) of [352 Media Group](http://www.352media.com/).

##Usage

Create an unordered list that contains your menu items. In CSS, use `display: inline-block;` or `float: left;` to get the  `li` elements to line up horizontally.

Call flexMenu on an unordered list that contains your menu items.

```javascript
$('ul.menu.flex').flexMenu();
```

If you are using this script on a responsive site, you'll also want to recalculate the menus on resize. Because many resize events will be fired as the user resizes the window, it's best to wait a few hundred milliseconds after the last resize event fires before recalculating the menu.

```javascript
$(window).resize(function () {
	resizeTimeout = setTimeout(resizeFunctions, 300);
});

function resizeFunctions() {
	$('ul.menu.flex').flexMenu({'undo': true });
	$('ul.menu.flex').flexMenu();
}
```

In most cases, you'll also want to set the popup menu to be absolutely positioned:
```css
.flexMenu-popup {
  position: absolute;
}
```

##Dependencies

###jQuery
I've tested the plugin in jQuery 1.7.1 and 1.7.2.

###Modernizr
[Modernizr](http://modernizr.com/) is optional. If it's available, flexMenu will use it to detect touch support. If touch support is available, we'll toggle the menu on click. If touch support is not available, we'll toggle the menu on hover in/out. That way, we can avoid triggering the funky [simulated mouseover/mouseout](http://developer.apple.com/library/ios/#DOCUMENTATION/AppleApplications/Reference/SafariWebContent/HandlingEvents/HandlingEvents.html#//apple_ref/doc/uid/TP40006511-SW17) that happens on many touchscreen devices.

If Modernizr is not available, we'll always toggle the menu on click.

The zip for flexMenu includes a build of Modernizr contains only touch detection and the has-js/no-js class. Feel free to use this build, or go with more full-featured build if you're using other features. Or, if you do want to always toggle the menu on click, there is no need to include Modernizr at all.

##Advanced usage

If you're feeling fancy, you can include any of the following options when calling flexMenu:

###threshold
(integer, defaults to 2)
If there are this many items or fewer in the list, we will not display a "View More" link and will instead let the list break to the next line. This is useful in cases where adding a "view more" link would actually cause more things to break  to the next line.

###linkText
(string, defaults to 'More')
What text should we display on the "view  more" link?

###linkTitle'
(string, defaults to 'View More')
What should the title of the "view more" button be?

###showOnHover
(boolean, defaults to 'true')
Should we we show the menu on hover? If not, we'll require a click. If we're on a touch device - or if Modernizr is not available - we'll ignore this setting and only show the menu on click. The reason for this is that touch devices emulate hover events in unpredictable ways, causing some taps to do nothing.

###undo
(boolean, defaults to 'false')
If this is true, we'll move the list items back to where they were before, and remove the "View More" link. This is useful if you actually _do_ want list items to stack in some cases, or if you want to recalculate the menu.
