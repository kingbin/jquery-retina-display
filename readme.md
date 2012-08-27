# jQuery Retina Display

Swap images to higher resolution images on retina displays based off modernizer tests. I have stripped the tests in javascript so the developer can decide what conditions they want to load the higher res images. ie connection speed, network caps, future browser detection support, etc.

## Example Usage

```html
<img src="image.jpg" alt="" width="800" height="600" data-res-src="image_2x.jpg" />
```

## Use it with Modernizr

Use this script with [Modernizr](https://github.com/Modernizr/Modernizr) and set your own test cases.

```javascript

      Modernizr.addTest('retina', function () {
        var rules = [],
        result = false,
        i = 0;
        rules.push("screen and (min--moz-device-pixel-ratio: 1) and (max-width: 2000px)");

        rules.push("screen and (-webkit-min-device-pixel-ratio:1) and (max-width: 2000px)");
        rules.push("screen and (-webkit-min-device-pixel-ratio:1.5)");
        rules.push("screen and (o-min-device-pixel-ratio:3/2)");
        rules.push("screen and (min--moz-device-pixel-ratio:1.5)");
        rules.push("screen and (min-device-pixel-ratio:1.5)");
        for (i; i < rules.length; i++) {
          if (Modernizr.mq(rules[i])) {
            result = true;
            break;
          }
        }
        return result;
	      //return (window.devicePixelRatio>=1.5);
      });

      Modernizr.load([
          {
              test : Modernizr.retina,
              yep : 'js/libs/jquery-retina-display/jquery.retinadisplay.min.js',
              complete : function () {
                  if(Modernizr.retina) {
                      $('img[data-res-src]').retinaDisplay();
                  }
              }
          }
      ]);
```
