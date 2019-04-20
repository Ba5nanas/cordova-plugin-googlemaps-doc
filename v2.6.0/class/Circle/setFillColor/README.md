:green_heart: This is the latest document.

# circle.setFillColor()

Change the inside color of the circle.

```
circle.setFillColor(color);
```

## Parameters

name           | type          | description
---------------|---------------|---------------------------------------
color          | string        | HTML color strings (i.e., `red`, `rgb(255, 0, 255)`)
-----------------------------------------------------------------------

## Demo code

```html
<div id="map_canvas"></div>
```

```js
var GOOGLE = {"lat" : 37.422858, "lng" : -122.085065};
var mapDiv = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(mapDiv);

// Add circle
var circle = map.addCircle({
  'center': GOOGLE,
  'radius': 300,
  'strokeColor' : '#AA00FF',
  'strokeWidth': 5,
  'fillColor' : '#880000',
  'clickable' : true   // default = false
});

map.moveCamera({
  target: circle.getBounds()
});

// Change the fill color.
var idx = 0;
circle.on(plugin.google.maps.event.CIRCLE_CLICK, function(latLng) {

  // Available HTML colors
  // https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v1.4.0/Available-HTML-colors/README.md
  //
  circle.setFillColor(["skyblue", "lime", "tomato", "bisque"][idx++]);
  idx = idx > 3 ? 0 : idx;
});
```

![](image.gif)
