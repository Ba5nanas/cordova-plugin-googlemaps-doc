:green_heart: This is the latest document.

# map.moveCamera()

You can change camera position **without** animation.

```
map.moveCamera(options, callback);
```

## Parameters

name     | type                                             | description
---------|--------------------------------------------------|----------------------
options  | [CameraPosition](../../CameraPosition/README.md) | new camera position (the duration property is ignored.)
callback | Function                                         | (optional) callback
-----------------------------------------------------------------------------------

## Demo code

```html
<div class="map" id="map_canvas">
    <button>Click here</button>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  map.moveCamera({
    target: {lat: 37.422359, lng: -122.084344},
    zoom: 17,
    tilt: 60,
    bearing: 140
  }, function() {
    alert("Camera target has been changed");
  });
});

```

![](image.gif)
