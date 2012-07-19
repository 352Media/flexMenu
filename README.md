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

The menu will automatically be adjusted as the page is resized.

##Dependencies

###jQuery
I've tested the plugin in jQuery 1.7.1 and 1.7.2.

###Modernizr
[Modernizr](http://modernizr.com/) is optional. If it's available, flexMenu will use it to detect touch support. If touch support is available, we'll toggle the menu on click. If touch support is not available, we'll toggle the menu on hover in/out. That way, we can avoid triggering the funky [simulated mouseover/mouseout](http://developer.apple.com/library/ios/#DOCUMENTATION/AppleApplications/Reference/SafariWebContent/HandlingEvents/HandlingEvents.html#//apple_ref/doc/uid/TP40006511-SW17) that happens on many touchscreen devices.

If Modernizr is not available, we'll always toggle the menu on click.

The zip for flexMenu includes a build of Modernizr contains only touch detection and the has-js/no-js class. Feel free to use this build, or go with more full-featured build if you're using other features. Or, if you do want to always toggle the menu on click, there is no need to include Modernizr at all - just [set up a js/no-js class](http://paulirish.com/2009/avoiding-the-fouc-v3/) and you'll be good to go.

##Advanced usage

If you're feeling fancy, you can include any of the following options when calling flexMenu:

###threshold
(integer, defaults to 2)
If there are this many items or fewer in the list, we will not display a "View More" link and will instead let the list break to the next line. This is useful in cases where adding a "view more" link would actually cause more things to break  to the next line.

###linkText
(string, defaults to 'More')
What text should we display on the "view  more" link?

###linkTitle
(string, defaults to 'View More')
What should the title of the "view more" button be?

###showOnHover
(boolean, defaults to 'true')
Should we we show the menu on hover? If not, we'll require a click. If we're on a touch device - or if Modernizr is not available - we'll ignore this setting and only show the menu on click. The reason for this is that touch devices emulate hover events in unpredictable ways, causing some taps to do nothing.

###popupAbsolute
(boolean, defaults to 'true')
If this is set to true, the poupup will be absolutely positioned. That way, it [isn't clipped](http://www.w3.org/TR/CSS21/visufx.html#overflow-clipping) by parent elements that have ```overflow: hidden``` and appears on top of the rest of your page. Feel free to set this to false if you want to do something else in your CSS.

###undo
(boolean, defaults to 'false')
If this is true, we'll move the list items back to where they were before, and remove the "View More" link. This is useful if you actually _do_ want list items to stack in some cases. You could also undo flexMenu and run it again if you want to manually adjust the menu.

##License

flexMenu is licensesed under the MIT License, and is free for commercial or personal use.

Copyright 2012 352 Media Group

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.