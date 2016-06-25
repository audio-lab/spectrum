# gl-spectrum [![unstable](http://badges.github.io/stability-badges/dist/unstable.svg)](http://github.com/badges/stability-badges)

Spectrum rendering component.

[![Spectrum](https://raw.githubusercontent.com/audio-lab/gl-spectrum/gh-pages/preview.png "Spectrum")](http://audio-lab.github.io/gl-spectrum/)


## Usage

[![npm install gl-spectrum](https://nodei.co/npm/gl-spectrum.png?mini=true)](https://npmjs.org/package/gl-spectrum/)

```js
var Spectrum = require('gl-spectrum');

var spectrum = new Spectrum({
	container: document.body,
	canvas: canvas,
	context: 'webgl',

	//decibels data, -100...0
	frequencies: frequenciesData,

	//audio settings
	maxDecibels: -30,
	minDecibels: -100,
	maxFrequency: 20000,
	minFrequency: 20,
	sampleRate: 44100,

	//perceptual loudness weighting, 'a', 'b', 'c', 'd', 'itu' or 'z' (see a-weighting)
	weighting: 'itu',

	//draw frequency/decibels grid
	grid: true,
	axes: false,
	logarithmic: true,

	//rendering settings
	smoothing: 0.5,
	details: 1,

	//hits FPS twice, so performance is over aesthetics
	antialias: false,

	//0 - place at the bottom, .5 - place symmetrically, 1. - place at the top
	align: 0,

	//Display max within the last N snapshots. 0 - no trail.
	trail: 0,

	//the width of a bar. Affects the mask.
	group: 0,

	//The levels of magnitude/frequency - a colormap name, colormap, pixels array, imageData, imageElement or canvas. Null disables fill.
	fill: 'greys',

	//A color tuple, imageData, imageElement, canvas or url. Default is 0-level of the fill
	background: null,

	//defines mask image for a bar. Image, imageData or canvasElement.
	mask: null
});

//pass db frequencies in -100...0 range
spectrum.setFrequencies(frequencies);
spectrum.setFill(colors, inverse?);
spectrum.setBackground(image);

//update state according to the params
spectrum.update();
```

## Related

* [a-weighting](https://github.com/audio-lab/a-weighting) — perception loudness weighting for audio.
* [colormap](https://github.com/bpostlethwaite/colormap) — list of js color maps.
* [cli-visualizer](https://github.com/dpayne/cli-visualizer) — C++ spectrum visualizer.