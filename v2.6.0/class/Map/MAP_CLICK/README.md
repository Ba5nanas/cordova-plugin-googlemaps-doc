:green_heart: This is the latest document.

# MAP_CLICK event

This event is fired when you click on the map.

## Parameters

name       | type                              | description
-----------|-----------------------------------|-----------------
latLng     | [LatLng](../../LatLng/README.md)  | clicked position
-----------------------------------------------------------------

## Demo code

```html
<div id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

map.on(plugin.google.maps.event.MAP_CLICK, function(latLng) {

  map.addMarker({
    position: latLng,
    title: latLng,
    animation: plugin.google.maps.Animation.DROP
  });
});
```

![](image.gif)
