:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# marker.isInfoWindowShown()

Return true if the infoWindow is shown on the marker.

```html
<div id="map_canvas">
    <table style="margin:1em;width:100px;">
      <tr>
        <th>marker1</th>
        <td nowrap id="marker1">close</td>
      </tr>
      <tr>
        <th>marker2</th>
        <td nowrap id="marker2">close</td>
      </tr>
      <tr>
        <th>marker3</th>
        <td nowrap id="marker3">close</td>
      </tr>
    </table>
</div>
```

```js
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div);
map.one(plugin.google.maps.event.MAP_READY, function() {

  var data = [
    {
      position: {lng: -122.1180187, lat: 37.3960513},
      title: "Ardis G Egan Intermediate School"
    },
    {
      position: {lng: -122.1102408, lat: 37.3943847},
      title: "Portola School"
    },
    {
      position: {lng: -122.0848257, lat: 37.3818032},
      title: "Isaac Newton Graham Middle School"
    }
  ];

  // Add markers
  addMarkers(map, data, function(markers) {

    // Set camera position that include all markers.
    var bounds = [];
    data.forEach(function(POI) {
      bounds.push(POI.position);
    });

    map.moveCamera({
      target: bounds
    }, function() {

      // After camera moving, open the last marker.
      markers[markers.length - 1].showInfoWindow();
    });

  });
});

function addMarkers(map, data, callback) {
  var markers = [];
  function onMarkerAdded(marker) {
    markers.push(marker);

    marker.set("label", "marker" + markers.length);
    marker.on(plugin.google.maps.event.INFO_OPEN, onInfoWindowEvents);
    marker.on(plugin.google.maps.event.INFO_CLOSE, onInfoWindowEvents);

    if (markers.length === data.length) {
      callback(markers);
    }
  }
  data.forEach(function(markerOptions, idx) {
    map.addMarker(markerOptions, onMarkerAdded);
  });
}
function onInfoWindowEvents(position) {
  var marker = this;
  var labelStr = marker.get("label");
  var label = document.getElementById(labelStr);
  label.innerText = marker.isInfoWindowShown() ? "open" : "close";
}
```

![](image.gif)
