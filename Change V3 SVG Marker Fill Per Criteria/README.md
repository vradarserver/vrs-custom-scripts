# Change V3 SVG Marker Default Fill Colours.html

Only works for version 3 (preview 6 onwards) when SVG markers are switched on.

Add this to the END of HEAD for *.

This script starts by looping through all of the aircraft markers and changing the SVG fill
colour callback to a function that the script provides.

The callback is called every time the site wants to set a colour for an aircraft. It is
passed the aircraft and a bool indicating whether the user has selected the aircraft and
it is expected to return a CSS colour string.

The example looks at the operator code for the aircraft. If it's Virgin then it fills the
aircraft red, easyJet is filled with green and British Airways blue. Otherwise it'll return
the default colours (white for not selected, yellow for selected).
