Lasso.Crop
==========

This is an updated version of Nathan White's MooTools-based image cropping tool.
The original code and a live demo can be found at: http://www.nwhite.net/2009/02/25/lassocrop-preview

This version has been modified to upgrade it to MooTools 1.3+ (tested on MooTools 1.3.2, 1.4.5, and 1.5.1), a few bug fixes, and also to add basic support for touchscreen devices.

Example
-------
HTML

	<script type="text/javascript" src="mootools-core.js"></script>
	<script type="text/javascript" src="lassocrop.js"></script>
	...
	<img src="/images/bee.jpg" id="bee" />

JS

	new Lasso.Crop('bee', {
		ratio : false,
		preset : [20,20,300,300],
		min : [50,50],
		handleSize : 8,
		opacity : .6,
		color : '#7389AE',
		border : 'crop.gif',
		onResize : updateCoords,
		onComplete : updateCoords
	});

	function updateCoords(coords) {
		console.log(coords);
	}

Documentation
-------------
### Lasso.Crop constructor arguments
* element - An image element or ID
* options - See below

### Options
* min - `[w,h] / false` - sets the minimum lasso width and height, default `false`
* max - `[w,h] / false` - sets the maximum lasso width and height, default `false`
* ratio - `[16,9] / false` - sets a lasso aspect ratio constraint, default `false`
* preset - [x,y,w,h] - initial lasso size, default `false`
* contain - `true / false` - if set lasso will be contained within the image, default `true`
* border - hex color or image path - sets the border of the lasso, default `#999`
* color - masking color, default `#7389AE`
* opacity - opacity of mask, default `0.3`
* zindex - used to make sure lasso is above all elements, default `10000`
* handleSize - size of lasso handles, default `8`
* handleStyle - css styles for the lasso handles, see code for defaults

### Methods
* attach - Attaches listeners
* detach - Detaches all listeners

### Events
* start - Event fired when lasso begins
* resize - Event fired during every mousemove while the lasso is active. Provides `{ x, y, w, h }`. If `contain` is set, positions are relative to the container element
* complete - Event fired on mouseup. Provides `{ x, y, w, h }`. If `contain` is set, positions are relative to the container element
