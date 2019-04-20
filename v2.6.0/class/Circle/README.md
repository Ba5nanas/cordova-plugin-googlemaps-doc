:green_heart: This is the latest document.

# Circle class

_This class extends [BaseClass](../BaseClass/README.md)_.

## Contents

  - <a href="#overview">Overview</a>
    - <a href="#create-one-circle">Create one circle</a>
    - <a href="#listen-click-event">Click event</a>
    - <a href="#bindto-method">bindTo() method</a>
  - <a href="#api-reference">API Reference</a>

------------

## Overview


### Create one circle

```js
var GOOGLE = {"lat" : 37.422858, "lng" : -122.085065};
var mapDiv = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(mapDiv);

// Add circle
var circle = map.addCircle({
  'center': GOOGLE,
  'radius': 300,
  'strokeColor' : '#AA00FF',
  'strokeWidth': 5,
  'fillColor' : '#880000'
});

map.moveCamera({
  target: circle.getBounds()
});
```

<img src="./addCircle/image.png" width="200" />

---------------------------------------------------------------

### Listen CLICK event

In order to listen the CIRCLE_CLICK event, you need to specify the `clickable` option.
You can get the latitude/longitude pair of clicked position.

```js
// Add a circle
var circle = map.addCircle({
  'center': GOOGLE,
  'radius': 300,
  'strokeColor' : '#AA00FF',
  'strokeWidth': 5,
  'fillColor' : '#880000',
  'clickable' : true   // default = false
});

map.moveCamera({
  target: circle.getBounds()
});

// Catch the CIRCLE_CLICK event
circle.on(plugin.google.maps.event.CIRCLE_CLICK, onCircleClick);


// The CIRCLE_CLICK event passes to the callback
// with the latLng position where is you clicked.
function onCircleClick(latLng) {

  // The callback is called as the overlay instance.
  var circle = this;

  // Do something...
}
```

<img src="./CIRCLE_CLICK/image.gif" width="200" />

---------------------------------------------------------------

#### bindTo() method

Circle `bindTo()` method is useful when you manipulate multiple overlays with the same value. The `bindTo()` method comes from [BaseClass](../BaseClass/README.md).

```js
var marker = map.addMarker({
  position: {lat: 43.0741704, lng: -89.3809802},
  draggable: true
});

var circle = map.addCircle({
  center: marker.getPosition(),
  radius: 10,
  fillColor: "rgba(0, 0, 255, 0.5)",
  strokeColor: "rgba(0, 0, 255, 0.75)",
  strokeWidth: 1
});

// circle.center = marker.position
marker.bindTo("position", circle, "center");
```

<img src="bindTo.gif" width="200">

---------------------------------------------------------------

## API Reference

### Create
<table>
    <tr>
        <th><a href="./addCircle/README.md">map.addCircle()</a></th>
        <td>Add a circle.</td>
    </tr>
</table>

### Methods

<table>
    <tr>
        <th><a href="./setCenter/README.md">setCenter()</a></th>
        <td>Change the center position.</td>
    </tr>
    <tr>
        <th>getCenter()</th>
        <td>Return the current center position.</td>
    </tr>
    <tr>
        <th><a href="./setRadius/README.md">setRadius()</a></th>
        <td>Change the circle radius.</td>
    </tr>
    <tr>
        <th>getRadius()</th>
        <td>Return the current circle radius.</td>
    </tr>
    <tr>
        <th><a href="./setFillColor/README.md">setFillColor()</a></th>
        <td>Change the filling color (inner color).</td>
    </tr>
    <tr>
        <th>getFillColor()</th>
        <td>Return the current circle filling color (inner color).</td>
    </tr>
    <tr>
        <th><a href="./setStrokeWidth/README.md">setStrokeWidth()</a></th>
        <td>Change the stroke width.</td>
    </tr>
    <tr>
        <th>getStrokeWidth()</th>
        <td>Return the current circle stroke width (unit: pixel).</td>
    </tr>
    <tr>
        <th><a href="./setStrokeColor/README.md">setStrokeColor()</a></th>
        <td>Change the stroke color (outter color).</td>
    </tr>
    <tr>
        <th>getStrokeColor()</th>
        <td>Return the current circle stroke color (outer color).</td>
    </tr>
    <tr>
        <th><a href="./setClickable/README.md">setClickable()</a></th>
        <td>Enables or disables click events for this circle.</td>
    </tr>
    <tr>
        <th>getClickable()</th>
        <td>Return true if the circle is clickable.</td>
    </tr>
    <tr>
        <th><a href="./setZIndex/README.md">setZIndex()</a></th>
        <td>Change the circle zIndex order.</td>
    </tr>
    <tr>
        <th>getZIndex()</th>
        <td>Return the current circle zIndex.</td>
    </tr>
    <tr>
        <th><a href="./remove/README.md">remove()</a></th>
        <td>Remove the circle.</td>
    </tr>
    <tr>
        <th>getBounds()</th>
        <td>Return the latLngBounds (rectangle) that contains the circle.</td>
    </tr>
    <tr>
        <th>getMap()</th>
        <td>Return the map reference.</td>
    </tr>
</table>

### Events

<table>
    <tr>
        <th><a href="./CIRCLE_CLICK/README.md">CIRCLE_CLICK</a></th>
        <td><b>Arguments: <a href="../LatLng/README.md">LatLng</a></b><br>This event is fired when you click on a circle.</td>
    </tr>
</table>
