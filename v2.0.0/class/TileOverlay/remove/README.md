:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# tileOverlay.remove()

Remove the tile overlay.

```html
<div class="map" id="map_canvas">
  <span class="smallPanel"><button>Remove the layer</button></span>
</div>
```

```js
var mapDiv = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(mapDiv, {
  'mapType': plugin.google.maps.MapTypeId.ROADMAP
});

map.addEventListener(plugin.google.maps.event.MAP_READY, function() {

  // Add a tile overlay
  map.addTileOverlay({
    // &lt;x&gt;,&lt;y&gt; and &lt;zoom&gt; are replaced with values
    // (i.e. http://tile.stamen.com/toner/2/1/2.png)
    getTile: function(x, y, zoom) {
      return "http://tile.stamen.com/toner/" + zoom + "/" + x + "/" + y + ".png";
    }
  }, function(tileOverlay) {

    var button = document.getElementsByTagName("button")[0];
    button.addEventListener("click", function() {
      // Remove the tile overlay
      tileOverlay.remove();

    });

  });

});
```

![](image.gif)
