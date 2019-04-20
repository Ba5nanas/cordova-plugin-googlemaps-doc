:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.setCameraTilt()

Change the camera view angle.

```
marker.setCameraTilt(tilt);
```

## Parameters

name       | type     | description
-----------|----------|---------------------------------------
tilt       | number   | new camera tilt
--------------------------------------------------------------

## Demo code

```html
<div class="map" id="map_canvas">
    <span class="smallPanel"><button>Click here</button></span>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div, {
  camera: {
    target: {
      lat: 37.422858,
      lng: -122.085065
    },
    zoom: 15
  }
});

var tilt = 0;
var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  tilt += 45;
  map.setCameraTilt(tilt);
});

```

![](image.gif)
