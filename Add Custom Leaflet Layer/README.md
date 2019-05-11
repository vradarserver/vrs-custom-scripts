# Add Custom Leaflet Layer.html
Only works for version 3+ and version 2.4.3+

Add this to the END of HEAD for *.

There are two ways you can add your own layers to the Leaflet map. One is to add the layer's
tile server to TileServerSettings-Custom.json in the VRS configuration folder. The other is
to add it at run-time by making calls to VRS.mapLayerManager.

This script is an example of the latter.