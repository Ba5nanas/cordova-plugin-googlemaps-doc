# map.moveCameraZoomOut()

Zooming out the camera without animation.

```html
<div id="map_canvas">
    <button>Click here</button>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div, {
  "camera": {
    "target": {
      "lat": 37.422858,
      "lng": -122.085065
    },
    "zoom": 15
  }
});

var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  map.moveCameraZoomOut();
});
```

![](image.gif)
