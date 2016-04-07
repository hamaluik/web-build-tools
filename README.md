# load-themed-styles [![npm version](https://badge.fury.io/js/load-themed-styles.svg)](https://badge.fury.io/js/load-themed-styles)

[![Build Status](https://travis-ci.org/dzearing/load-themed-styles.svg?branch=master)](https://travis-ci.org/dzearing/load-themed-styles) [![Dependencies](https://david-dm.org/dzearing/load-themed-styles.svg)](https://david-dm.org/dzearing/load-themed-styles)

> Loads a string of style rules, but supports detokenizing theme constants built within it.

## Install

Install with [npm](https://www.npmjs.com/)

```
$ npm install --save load-themed-styles
```

## Usage

To load a given string of styles, you can do this:

```js
import { loadStyles } from 'load-themed-styles';

loadStyles('body { background: red; }');
```

This will register any set of styles given. However, in the above example the color is hardcoded to red. To make this theme-able, replace it with the string token in this format:

```
"[theme:{variableName}, default:{defaultValue}]"
```

For example:

```js
loadStyles('body { background: "[theme:primaryBackgroundColor, default: blue]"');
```

When loading, the background will use the default value, blue. Providing your own theme values using the `loadTheme` function:

```js
import { loadStyles, loadTheme } from 'load-themed-styles';

loadTheme({
  primaryBackgroundColor: "#EAEAEA"
});

loadStyles('body { background: "[theme:primaryBackgroundColor, default: #FFAAFA]"');
```

This will register #EAEAEA as the body's background color. If you call loadTheme again after styles have already been registered, it will replace the style elements with retokenized values.

## License

MIT © [David Zearing](http://github.com/dzearing)
