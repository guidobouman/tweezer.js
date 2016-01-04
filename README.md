# Tweezer.js

[![Tweezer.js on NPM](https://img.shields.io/npm/v/tweezer.js.svg)](https://www.npmjs.com/package/tweezer.js)

A small, dependency-free, ES6 library for smooth animations. [Demo](http://jaxgeller.com/tweezer.js/)

## Example

Smooth Scroll to an Element
```es6
let button = document.querySelector('#jump-button')
button.onclick = () => {
  new Tweezer({
    start: window.scrollY,
    end: document.body.clientHeight - window.innerHeight
  }).on('tick', v => window.scrollTo(0, v)).begin()
}
```

## Use

Tweezer was developed with a modern JavaScript workflow in mind. To use it, it's recommended you have a build system in place that can transpile ES6, and bundle modules. For a minimal boilerplate that fulfills those requirements, check out [outset](https://github.com/callmecavs/outset) or the [gh-pages branch](https://github.com/jaxgeller/tweezer.js/tree/gh-pages) of this repo.

To get started, follow these steps,

+ Install and Import
+ Instantiate and Configure
+ Register Events and Fire Animations

### Install and Import

In the commandline
```bash
$ npm install tweezer.js --save
```
In your ES6 Application

```es6
import Tweezer from 'tweezer.js'
```

### Instantiate and Configure

```es6
let animator = new Tweezer({
    start: 0,
    end: 9000
})
```

### Usage

Two parameters are required to start Tweezer, a `start` and an `end` value. Tweezer works by emitting values via an event emitter. It is up to you on how to use these values.

#### Target

To tween from 0 to 9000

```es6
new Tweezer({
  start: 0,
  end: 9000
})
```

#### Options

Note that **duration is required** for every `jump()`.

Defaults are shown below, explanation of each option follows.

```es6
Jump.jump('.selector', {
  duration: /* REQUIRED, no default */,
  offset: 0,
  callback: undefined,
  easing: (t, b, c, d) => {
    // Robert Penner's easeInOutQuad - http://robertpenner.com/easing/
    t /= d / 2
    if(t < 1) return c / 2 * t * t + b
    t--
    return -c / 2 * (t * (t - 2) - 1) + b
  }
})
```

## Browser Support

Tweezer.js depends on the following browser APIs:

* [requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)

Consequently, it supports the following natively:

* Chrome 24+
* Firefox 23+
* Safari 6.1+
* Opera 15+
* IE 10+
* iOS Safari 7.1+
* Android Browser 4.4+

To add support for older browsers, consider including [polyfills/shims](https://gist.github.com/paulirish/1579671) for the APIs listed above. There are no plans to include any in the library, in the interest of file size.

## License

[MIT](https://github.com/jaxgeller/tweezer.js/blob/master/LICENSE)

[![Built With Love](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)



## What is tweening?

A tween is when you animate something with some kind of [easing(http://easings.net/). Any time you want to animate something smoothly with JS, you need to tween it. For example, you can tween count-up-buttons, smooth scrolling, and the height of elements. Instead of requiring libraries for all of these same functions, you can use this library as a utility to build out these examples.