# MAP_LONG_CLICK event

This event is fired when you press your finger a few seconds on the map.

```html
<div id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

map.on(plugin.google.maps.event.MAP_LONG_CLICK, function(latLng) {

  map.addMarker({
    position: latLng,
    title: latLng,
    animation: plugin.google.maps.Animation.DROP
  });
});
```

![](image.gif)
