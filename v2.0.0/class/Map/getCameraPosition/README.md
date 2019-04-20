:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.getCameraPosition()

Get the current [camera position](../../CameraPosition/README.md).

```html
<div class="map" id="map_canvas">
    <span class="smallPanel"><button>Click here</button></span>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);
map.one(plugin.google.maps.event.MAP_READY, function() {

  var button = div.getElementsByTagName('button')[0];
  button.addEventListener('click', function() {

      // Get the current camera position.
      var cameraPosition = map.getCameraPosition();

      // Show the results
      var text = ["Current camera position:\n",
        "-------------------------------",
        "latitude:" + cameraPosition.target.lat,
        "longitude:" + cameraPosition.target.lng,
        "zoom:" + cameraPosition.zoom,
        "tilt:" + cameraPosition.tilt,
        "bearing:" + cameraPosition.bearing].join("\n");

      alert(text);
  });

});
```

![](image.gif)
