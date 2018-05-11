# htmlInfoWindow.open()

Open the htmlInfoWIndow.

```
htmlInfoWindow.open(marker);
```


## Parameters

name           | type          | description
---------------|---------------|---------------------------------------
marker         | Marker        | Marker instance
-----------------------------------------------------------------------


## Demo code

```html
<div id="map_canvas"></div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

var htmlInfoWindow = new plugin.google.maps.HtmlInfoWindow();

var html = "&lt;img src='./House-icon.png' width='64' height='64' &gt;" +
           "&lt;br&gt;" +
           "This is an example";
htmlInfoWindow.setContent(html);

var marker = map.addMarker({
  position: {lat: 0, lng: 0}
});

marker.on(plugin.google.maps.event.MARKER_CLICK, function() {
  htmlInfoWindow.open(marker);
});
marker.trigger(plugin.google.maps.event.MARKER_CLICK);

```

![](image.png)
