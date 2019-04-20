:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# MAP_READY event

This event is fired when the map is created using the `map.getMap()` method.

```html
<div id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

// At this time, the map instance is not ready yet.
// So don't do anything.
//
// map.setCameraZoom(3);  <--- This is bad timing.

// After the MAP_READY event, you can modify the map.
map.one(plugin.google.maps.event.MAP_READY, function() {

});
```

![](image.png)
