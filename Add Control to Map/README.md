# Add Control to Map.html
Add this to the END of HEAD for *.

This is a sample script showing how to add a control to the map. It will work
for both versions 2 and 3 of VRS, and both Google Maps and Leaflet.

## `mapPlugin.addControl`
This method takes two parameters - the control to add to the map and a value indicating
where it should be placed.

The first parameter is the control to be added to the map. This can either be a standard
HTML node or it can be a jQuery object. The example shows the use of a jQuery object.

The second parameter is the the position enum. The example places the control in the
bottom left of the map. The full list of enums / positions is:

* `VRS.MapPosition.BottomCentre`
* `VRS.MapPosition.BottomLeft`
* `VRS.MapPosition.BottomRight`
* `VRS.MapPosition.LeftBottom`
* `VRS.MapPosition.LeftCentre`
* `VRS.MapPosition.LeftTop`
* `VRS.MapPosition.RightBottom`
* `VRS.MapPosition.RightCentre`
* `VRS.MapPosition.RightTop`
* `VRS.MapPosition.TopCentre`
* `VRS.MapPosition.TopLeft`
* `VRS.MapPosition.TopRight`

If you want to see all of the available methods on the mapPlugin then review the `IMap` interface here:

https://github.com/vradarserver/vrs/blob/master/VirtualRadar.WebSite/Site/typings/typedefs.d.ts
