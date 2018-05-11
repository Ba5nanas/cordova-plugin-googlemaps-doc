# StreetView class

_This class extends [BaseClass](../BaseClass/README.md)_.

## Contents

  - <a href="#overview">Overview</a>
    - <a href="#create-a-streetview-panorama">Create a Street View Panorama</a>
    - <a href="#the-panorama_location_change-event">PANORAMA_LOCATION_CHANGE</a>
    - <a href="#panorama-id">Panorama id</a>
  - <a href="#api-reference">API Reference</a>

------------


## Overview

Google Street View provides panoramic 360 degree views from designated roads throughout its coverage area.
Street View's API coverage is the same as that for the Google Maps application (https://maps.google.com/).
The list of currently supported cities for Street View is available at the [Google Maps website](https://www.google.com/streetview/understand/#where).



------------

### Create a Street View Panorama

You can create a panorama view using `plugin.google.maps.StreetView.getPanorama(div)`.

```html
<div class="pano" id="pano_canvas1"></div>
```

```js
var div = document.getElementById("pano_canvas1");

var panorama = plugin.google.maps.StreetView.getPanorama(div);

panorama.setPosition({
  target: {lat: 42.345573, lng: -71.098326}
});
```

<img src="getPanorama/image1.png" width="250">


------------

### The `PANORAMA_LOCATION_CHANGE` event

Google takes panorama photos with special camera device on moving.
Not only special car, but also they uses Trekker, Trolly, Bike, Snow mobile,... etc.

<img src="device-car.jpg" width="250" >

Since they takes panorama photos on moving periodically, there is no panorama photo between two locations that are taken photos.

<img src="take_panorama1.png" >

For this reason, you can specify camera location, but the native API snaps to nearest available camera location.
The `PANORAMA_LOCATION_CHANGE` event gives the information where the location is.

```js
var panorama = plugin.google.maps.StreetView.getPanorama(div);

panorama.setPosition({
  target: {lat: 42.345573, lng: -71.098326}
});

panorama.on(plugin.google.maps.event.PANORAMA_LOCATION_CHANGE, function(location) {

  var panoId = location.panoId;    // unique location id

  var position = location.latLng;  // lat,lng pair

  var links = location.links;      // links to the next available locations.
                                   // The same as white arrow in panorama.

});

```


------------

### Panorama id

Panorama id (panoId) is unique identify for each panorama location.

This panoId is able to use for [Street View Service](https://developers.google.com/maps/documentation/javascript/streetview) and [Google StreetView Image API](https://developers.google.com/maps/documentation/streetview/intro).

As described in [The `PANORAMA_LOCATION_CHANGE` event](#the-panorama_location_change-event) section, the Google Maps native API searches the nearest location in 50 meters from you requested. This is mostly fine, but this might display unexpected panorama if you want to display particular location. Because Google updates panorama photos every once in a while.

<img src="take_panorama2.png" >

Using panoId avoids this trouble. Since the panoId is bounded to a particular panorama photo (location), you can always display exactly what you want.

```
panorama.setPosition({
  'target': 'FEpIJhSgQJOQCL3wOzoAAA'
})
```
**Note that the above is dummy id.**

<img src="take_panorama3.png" >

However, this panoId is **NOT** permanent Id. If Google updates new panorama photos, new panorama id is generated, and older id is no longer available.

------------------------------------------------------------

## API Reference


### Create

<table>
    <tr>
        <th><a href="./getPanorama/README.md">StreetView.getPanorama()</a></th>
        <td>Create a panorama view.</td>
    </tr>
</table>

### Methods

<table>
  <tr>
      <th><a href="./setPosition/README.md">setPosition()</a></th>
      <td>Sets the current LatLng position for the Street View panorama.</td>
  </tr>
  <tr>
      <th><a href="./setPov/README.md">setPov()</a></th>
      <td>Sets the point of view for the Street View panorama.</td>
  </tr>
  <tr>
      <th>setVisible()</th>
      <td>Change visibility of the Street View panorama.</td>
  </tr>
  <tr>
      <th>getVisible()</th>
      <td>Returns true if the panorama is visible.</td>
  </tr>
  <tr>
      <th>setPanningGesturesEnabled()</th>
      <td>Determines whether the user will be able to re-orient the camera by dragging.</td>
  </tr>
  <tr>
      <th>getPanningGesturesEnabled()</th>
      <td>Returns true if the panning gesture is enable.</td>
  </tr>
  <tr>
      <th>setZoomGesturesEnabled()</th>
      <td>Determines whether the user will be able to pinch to zoom.</td>
  </tr>
  <tr>
      <th>getZoomGesturesEnabled()</th>
      <td>Returns true if the zoom gesture is enable.</td>
  </tr>
  <tr>
      <th>setNavigationEnabled()</th>
      <td>Determines whether the user will be able to move to a different panorama. Users can use a single tap on navigation links, or double tap the view, to move to a new panorama.</td>
  </tr>
  <tr>
      <th>getNavigationEnabled()</th>
      <td>Returns true if the navigation link is enable.</td>
  </tr>
  <tr>
      <th>setStreetNamesEnabled()</th>
      <td>Determines whether the user is able to see street names displayed on the ground.</td>
  </tr>
  <tr>
      <th>getStreetNamesEnabled()</th>
      <td>Returns true if the street name label is enable.</td>
  </tr>
  <tr>
      <th>getLocation()</th>
      <td>Return the last panorama location.</td>
  </tr>
  <tr>
      <th>getPosition()</th>
      <td>Return position of the last panorama location.</td>
  </tr>
  <tr>
      <th>getLinks()</th>
      <td>Return links of the last panorama location.</td>
  </tr>
  <tr>
      <th>getPanoId()</th>
      <td>Return panoId of the last panorama location.</td>
  </tr>
  <tr>
    <th>remove()</th>
    <td>Remove the panorama view.</td>
  </tr>
</table>

### Events
<table>
  <tr>
    <th><a href="./PANORAMA_LOCATION_CHANGE/README.md">PANORAMA_LOCATION_CHANGE</a></th>
    <td>Arguments:  PanoramaLocation<br>This event is fired when StreetView panorama is moved.</td>
  </tr>
  <tr>
    <th><a href="./PANORAMA_CAMERA_CHANGE/README.md">PANORAMA_CAMERA_CHANGE</a></th>
    <td>Arguments:  PanoramaCamera<br>This event is fired when panorama is moved, such as panning gesture.</td>
  </tr>
  <tr>
    <th><a href="./PANORAMA_CLICK/README.md">PANORAMA_CLICK</a></th>
    <td>Arguments:  PanoramaClickInfo<br>This event is fired when panorama is moved, such as panning gesture.</td>
  </tr>
</table>
