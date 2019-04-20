:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.fromPointToLatLng()

Convert the unit from the pixels from the left/top to the LatLng.

```
map.fromPointToLatLng(point, callback);
```

## Parameters

name      | type                     | description
----------|--------------------------|----------------------
point     | [x: number, y: number]   | position
callback  | Function                 | function(point) {}
------------------------------------------------------------

## Demo code

```html
<div class="map" id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

map.setClickable(false);

div.addEventListener("click", function(e) {

  // Get the tapped position by pixels
  var clickX = e.pageX - this.offsetLeft;
  var clickY = e.pageY - this.offsetTop;

  // Convert point to LatLng.
  map.fromPointToLatLng([clickX, clickY], function(latLng) {

    // Add a marker
    var marker = map.addMarker({
      position: latLng,
      title: "Point: " + clickX + ", " + clickY
    });
    marker.showInfoWindow();
  });
});

```

![](image.gif)
