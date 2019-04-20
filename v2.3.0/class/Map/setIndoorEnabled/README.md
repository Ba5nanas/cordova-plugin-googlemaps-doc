:warning: **This document is aim for older versions (from 2.3.0 to 2.5.3).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# map.setIndoorEnabled()

Set true if you want to show the indoor map.

```
marker.setIndoorEnabled(flag);
```

## Parameters

name           | type     | description
---------------|----------|---------------------------------------
flag           | boolean  | `false`: disabled, `true`: enabled
------------------------------------------------------------------

## Demo code

```html
<div class="map" id="map_canvas">
  <span class="smallPanel"><button>current: map.indoorEnable = false</button></span>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div, {
  camera: {
    target: {
      lat: 37.422375,
      lng: -122.084207
    },
    zoom: 17
  },
  controls: {
    indoorPicker: true
  }
});

var isEnabled = false;
var button = div.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  isEnabled = !isEnabled;
  map.setIndoorEnabled(isEnabled);
  button.innerHTML = "current: map.indoorEnable = " + isEnabled;
});

```

![](image.gif)
