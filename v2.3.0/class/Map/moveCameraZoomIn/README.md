:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.moveCameraZoomIn()

Zooming in the camera without animation.

```
map.moveCameraZoomIn(callback);
```

## Parameters

name     | type      | description
---------|-----------|----------------------
callback | Function  | (optional) callback
--------------------------------------------

## Demo code

```html
<div id="map_canvas">
    <button>Click here</button>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  map.moveCameraZoomIn();
});
```

![](image.gif)
