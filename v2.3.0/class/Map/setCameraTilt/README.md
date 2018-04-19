# map.setCameraTilt()

Change the camera view angle.

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
