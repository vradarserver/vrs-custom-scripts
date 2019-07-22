# Suppress Standard Map Layer.html
Only works for version 3+ and version 2.4.3+

Add this to the END of HEAD for *.

This shows how you can prevent all users from seeing or selecting one of the
standard map layers whose details are sent from the SDM site.

In this example the layer that is being suppressed is the OpenAIP layer. You
can find the name of each layers in TileServerSettings-Downloaded.json in the
configuration folder.

Layer names are case sensitive.
