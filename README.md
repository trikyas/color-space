# Color-space [![Build Status](https://travis-ci.org/dfcreative/color-space.svg?branch=master)](https://travis-ci.org/dfcreative/color-space)

[![NPM](https://nodei.co/npm/color-space.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/color-space/)

_Color-space_ provides conversions and data for the following color spaces: RGB, HSl, HSV (HSB), [HWB](http://dev.w3.org/csswg/css-color/#the-hwb-notation), CMYK, CMY, [XYZ](http://en.wikipedia.org/wiki/CIE_1931_color_space), XYY (YXY), [LAB](http://en.wikipedia.org/wiki/Lab_color_space), LCH<sub>ab</sub>, [LUV](http://en.wikipedia.org/wiki/CIELUV), [LCH<sub>uv</sub>](http://en.wikipedia.org/wiki/CIELUV#Cylindrical_representation), [H<sub>u</sub>SL](http://www.boronine.com/husl/), [H<sub>u</sub>SL<sub>p</sub>](http://www.boronine.com/husl/), [LAB<sub>Hunter</sub>](http://en.wikipedia.org/wiki/Lab_color_space#Hunter_Lab), [LMS](http://en.wikipedia.org/wiki/LMS_color_space).


_Color-space_ has the most complete list of color convertions so far, comparing to [color-convert](https://github.com/harthur/color-convert), [chromatist](https://github.com/jrus/chromatist), [spectra](https://github.com/avp/spectra), [colorspaces.js](https://github.com/boronine/colorspaces.js) and others. It can be used both in browser and node. Each space can be required separately as `require(color-space/<space>)`.


#### [Color converter & tests](https://cdn.rawgit.com/dfcreative/color-space/master/test/index.html)


# Use

## In browser:

Include [color-space.js](https://raw.githubusercontent.com/dfcreative/color-space/master/color-space.js) or [color-space.min.js](https://raw.githubusercontent.com/dfcreative/color-space/master/color-space.min.js) on the page:

```html
<script src="path-to/color-space.js"></script>
```

You can also use a [CDN version](https://cdn.rawgit.com/dfcreative/color-space/master/color-space.min.js):

```html
<script src="https://cdn.rawgit.com/dfcreative/color-space/master/color-space.min.js"></script>
```

Then you’ll have a `window.colorSpace` object, so you can play around:

```html
<script>
	var rgb = colorSpace.rgb;

	//convert rgb to hsl
	var hslColor = rgb.hsl([255,0,0]);
</script>
```

If you aware of final size, you can include only needed target spaces. Use [browserify](https://github.com/substack/node-browserify) to get your own build.


## In node:

First install color-space as a local module:

`$ npm install --save color-space`


Include all spaces:

```js
var colorSpace = require('color-space');

//convert lab to lch
var result = colorSpace.lab.lch([80,50,60]);
```

Each space can also be required separately as `require('color-space/<space>')`:

```js
var rgb = require('color-space/rgb');
var hsl = require('color-space/hsl');

//convert rgb to hsl
rgb.hsl([200,230,100]);
```

Note that in case of requiring specific spaces you might need to add conversions via `color-space/add-convertor`.


# API

API of color-space is straightforward.

You can convert one space to another:

```js
var fromSpace = 'rgb', toSpace = 'hsl';

colorSpace[fromSpace][toSpace](array);
```

Also you can get space data:

```js
<space>.name //space name
<space>.min //channel minimums
<space>.max //channel maximums
<space>.channel //channel names
<space>.alias //alias space names, if any
xyz.whitepoint //list of whitepoint references
lms.transform //list of transform matrices
```


# Contribute

Please fork, add color space with basic conversions to/from XYZ or RGB and tests. _Color-space_ is supposed to be a basic library to work with color conversions, an enhanced replacement for [color-convert](https://github.com/harthur/color-convert).


<a href="http://unlicense.org/UNLICENSE"><img src="http://upload.wikimedia.org/wikipedia/commons/6/62/PD-icon.svg" width="40"/></a>