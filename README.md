# equi2cube
Converts equirectangular images to 6 sided cube maps (JavaScript)

```javascript
'use strict';

function loadImage(src, xo) {
	return new Promise(function (resolve, reject) {
		var i = new Image();
		if (xo) i.crossOrigin = xo;
		i.onload = function () {
			resolve(i);
		};
		i.onerror = reject;
		i.src = src;
	});
}

loadImage('path/to/equirectangularimage.jpg', 'Anonymous').then(function (i) {
	var cs = equirectToCubemapFaces(i);
	cs.forEach(function (c) {
	  // returns a canvas element for each side of the cube (c)
		document.body.appendChild(c);
	});
});
```

