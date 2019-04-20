:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# htmlInfoWindow.open(marker)

Open the htmlInfoWIndow.

```html
<div id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);
map.one(plugin.google.maps.event.MAP_READY, function() {
  var htmlInfoWindow = new plugin.google.maps.HtmlInfoWindow();

  var html = "&lt;img src='./House-icon.png' width='64' height='64' &gt;" +
             "&lt;br&gt;" +
             "This is an example";
  htmlInfoWindow.setContent(html);

  map.addMarker({
    position: {lat: 0, lng: 0}
  }, function(marker) {

    marker.on(plugin.google.maps.event.MARKER_CLICK, function() {
      htmlInfoWindow.open(marker);
    });
    marker.trigger(plugin.google.maps.event.MARKER_CLICK);

  });
});
```

![](image.png)
