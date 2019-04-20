:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# groundOverlay.setBounds()

Change the bounds of the ground overlay.

```html
<div id="map_canvas"></div>
```

```js
var bounds = [
  {"lat": 40.712216, "lng": -74.22655},
  {"lat": 40.773941, "lng": -74.12544}
];
var mapDiv = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(mapDiv, {
  camera: {
    target: bounds,
    padding: 50
  }
});

map.addEventListener(plugin.google.maps.event.MAP_READY, function() {

  var markers = [];

  // Add ground overlay
  map.addGroundOverlay({
    'url': "../images/newark_nj_1922.jpg",
    'bounds': bounds,
    'opacity': 1
  }, function(groundOverlay) {

    bounds.forEach(function(position) {
      map.addMarker({
        position: position,
        draggable: true
      }, function(marker) {
        marker.on("position_changed", onChanged.bind(groundOverlay));
        markers.push(marker);
      });
    });
  });

  function onChanged() {
    var groundOverlay = this;  // since onChanged.bind() method.

    groundOverlay.setBounds([
      markers[0].getPosition(),
      markers[1].getPosition()
    ]);
  }
});
```

![](image.gif)
