:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.setVisible()

If set false, the map is hidden.

```html
<div class="map" id="map_canvas">
  <span class="smallPanel"><button>current: map.visible = true</button></span>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);

var visible = true;
var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  visible = !visible;
  map.setVisible(visible);
  button.innerHTML = "current: map.visible = " + visible;
});

```

![](image.gif)
