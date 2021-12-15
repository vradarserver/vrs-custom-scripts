# Configure globalOptions Before VRS Runs.html

Add this to the START of HEAD for *.

There are some `globalOptions` that are used by the site as soon as a script is loaded.
These options can be reconfigured with a custom script at the END of HEAD (see other
examples) but you will have a burst of default behaviour before your custom script
runs. Sometimes that is not desirable.

However, you can work around this by moving your custom script to the START of HEAD
instead. Most of the variables in `globalOptions` are only defaulted if they do not
already have a value, so you are safe to set most of them at the START of HEAD.

The drawback with doing this is that none of the site's scripts will have run so
`VRS.globalOptions` will not exist when your script runs. This means that you have to
create it yourself.

This example shows how to do this to change the URL that the site will intermittently
poll for an aircraft list. It defaults to `AircraftList.json`, this example changes
it to `MyCustomUrl`.
