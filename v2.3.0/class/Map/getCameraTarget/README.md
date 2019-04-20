:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.getCameraTarget()

Get the current camera target(latitude/longitude) position.

------------------------------------------------------------

## Demo code

```html
<div class="map" id="map_canvas">
    <span class="smallPanel"><button>Click here</button></span>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);
var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {

    // Show the current camera target position.
    var target = map.getCameraTarget();
    alert([
      "lat: " + target.lat,
      "lng: " + target.lng
    ]);
});

```

![](image.gif)
