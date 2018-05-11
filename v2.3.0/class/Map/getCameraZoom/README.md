# map.getCameraZoom()

Get the current camera zoom level.

------------------------------------------------------------

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
    zoom: 15,
    bearing: 150
  }
});

var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {

  // Show the current camera zoom level.
  alert("zoom: " + map.getCameraZoom());
});

```

![](image.gif)
