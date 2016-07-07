# jQuery Style Guide

Opinionated *jQuery Style Guide* for teams by [De Voorhoede](https://twitter.com/devoorhoede).

## Purpose

This guide aims to improve the way your team uses [jQuery](http://jquery.com/). It helps you write code which is

* close to modern web technologies and best practices.
* easy to understand for developers / team members.
* easy to reuse (in other projects).
* more performant.
* avoids overuse of jQuery and needless vendor locking.


## Table of Contents

* [About jQuery](#about-jquery)
* [Prefer CSS animations over .animate()](#prefer-css-animations-over-animate)

## About jQuery

[jQuery](http://jquery.com/) is a utility library for easy DOM access & manipulation, event handling, Ajax and more. By using jQuery you can write consise and expressive code which works across modern and legacy browsers. jQuery has extensive tests, detailed documentation, a large active community and an ecosystem of plugins.

## Prefer CSS animations over [.animate()](http://api.jquery.com/animate/)

### Why?
Most of the time the same can be accomplished with toggling classes and using CSS transition and/or keyframes.

### How?
``` javascript

// Bad
function animateElement() {
  $myElement.animate({
    	opacity: 0
    },
    1000)
    .animate({
    	opacity: 1
    },
    1000,
    function() {
    	animateElement();
    });
}
animateElement();

// Good
$myElement.addClass('is-animating');
```

``` css
.is-animating {
    animation: fade 2s infinite;
}

@keyframes fade {
	0%   { opacity: 1; }
	50%  { opacity: 0; }
	100% { opacity: 1; }
}
// vendor prefix might be required
```

[↑ back to Table of Contents](#table-of-contents)