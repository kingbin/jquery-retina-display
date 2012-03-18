# jQuery Retina Display

Swap images to higher resolution images on retina displays.

## Example Usage

```html
<img src="image.jpg" alt="" width="800" height="600" data-res-src="image_2x.jpg" />
```

```javascript
$('img[data-res-src]').retinaDisplay();
```

## Use it with Modernizr

To not load the script for non-retina displays, you can use it with [Modernizr](https://github.com/Modernizr/Modernizr). 

```javascript
Modernizr.addTest('retina', function () {
	return (!!navigator.userAgent.match(/iPhone|iPad/i) && window.devicePixelRatio==2);
});

Modernizr.load([
	{
		test : Modernizr.retina,
		yep : 'js/libs/jquery.retinadisplay.min.js', 
		complete : function () {
			if(Modernizr.retina) {
				$('img[data-res-src]').retinaDisplay();
			}
		}
	}
]);
```