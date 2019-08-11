# Add Aircraft Marker (Bitmap).html

Works for all versions of VRS.

If you have SVG markers configured in V3 then it will not use custom bitmap markers.

## Configure the script in the Custom Content Plugin
Add the HTML script file to the END of HEAD for address *.

## Configure the site root in the Custom Content Plugin
The script relies on custom marker images. Without those images the script will not work.

The sample custom images are in the **sample-images** folder.

1. Create a folder called **Web** somewhere. Under that create a folder called **images**.
   In there create a folder called **markers**.

2. Copy the two files from **sample-images** into your **markers** folder.

3. In the custom content plugin set **Site root folder** to the full path to the **Web** folder
   that you created.

This is how the folders and files should be arranged when you are finished, where **Site Root Folder**
is the **Web** folder that you created:

````
Site Root Folder
+-- images
    +-- markers
        |-  custom-not-selected.png
        |-  custom-selected.png
 ````


### Warning
The Custom Content plugin will serve any file that is in your custom **Site root folder**. Do not
put files in there that should not be visible to the public.

## How custom markers work

Each aircraft marker is described by an object of type **VRS.AircraftMarker**.

The AircraftMarker type has four fields:

|Field Name|Type|Description|
|----------|----|-----------|
|normalFileName|`string`|The filename of the image in **markers** to use when the aircraft has not been selected by the user|
|selectedFileName|`string`|The filename of the image in **markers** to use when the aircraft has been selected by the user|
|size|`{ width: number, height: number}`|The size in pixels of both variants of the aircraft marker|
|matches|`function`|A function that is passed an **aircraft** object and returns true if the marker should be shown for that aircraft|

The aircraft marker objects are stored in an array called **VRS.globalOptions.aircraftMarkers**.

When the site wants to show a marker for an aircraft it loops through each AircraftMarker object in the
aircraftMarkers array from start to finish. The first AircraftMarker whose *matches* function returns
true for the aircraft gets used.

The very last entry in aircraftMarkers is a catch-all marker whose *matches* function just returns true
for all aircraft.

When you add your custom markers you need to add them to the start of the **VRS.globalOptions.aircraftMarkers** array. You do this by using *unshift*(), not push().

### Aircraft fields

Documentation on the Aircraft object's fields can be found here:

[../docs/aircraft-fields.md](../docs/aircraft-fields.md).

## Troubleshooting

### The page does not load correctly

You have a syntax error in your script. Press F12 to get the browser console window open and correct
the errors that it reports in the console tab.

### The aircraft are shown using the standard markers

1. Your script is not loading. Double-check the custom content plugin settings - ensure the filename
   is correct, that you have enabled the script and that it is configured to be added to the END of
   HEAD and that you have entered a single asterisk for the **Address** field.

   If you are comfortable with HTML then you can double-check that the script is loading by pressing
   F12 to enter the browser console and checking that the script appears at the end of the <HEAD> section.

2. The script is loading but your rules are wrong. Did you use *push*() to add your custom markers to
   the end of *VRS.globalOptions.aircraftMarkers* display? If so then your rule will never be used,
   there is a catch-all rule in the stock site that will run before your rule. You must use **unshift**
   to add new rules to the start of the array.

   Are your rules correct? If you are using === to compare values then make sure that the literal is
   the correct type.

### The aircraft markers are the browser's "missing image" symbol

1. You have not configured the correct **Site root folder** in the Custom Content plugin options. The
   folder that you specify must contain a folder called *images*, within that folder should be another
   folder called *markers* and your custom markers must be in that folder.

   ````
   Site Root Folder
   +-- images
       +-- markers
           |-  your-custom-marker-01.png
           |-  your-custom-marker-02.png
           |-  ...
    ````

2. The marker filenames contain characters that need to be URL encoded (e.g. spaces). Do not use complicated
   filenames, just use plain latin characters, numbers and hyphens.

3. You did not have the correct Site root folder and VRS has cached the fact that the images are missing.
   If you had the wrong site root folder then you should restart VRS after correcting the setting. You should
   also force the browser to clear its image cache by reloading the page with CTRL+F5.

Note that the URL for the marker will refer to a folder called *web-markers*. That is not the name of the folder
that your markers should be in. The markers folder must be called **markers**.
