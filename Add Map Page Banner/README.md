# Add Map Page Banner.html

Add this to the END of HEAD for *.

This script adds some inline CSS that resizes and repositions the splitter area so that you can add
a banner to the page.

The splitter area has the ID #splitters. It is usually sized to occupy 100% of its parent's width
and height. Its parent is usually the ```<body>``` tag.

If you add a header element to the body tag then the splitters element will continue to occupy the
full width and heigth of the body but it will be displaced by the banner. Normally this means that
an edge (usually the bottom edge) of the splitters goes off the page.

You can use the ```calc()``` CSS function to subtract the size of your banner element from the width
and / or height of the splitters. The example subtracts 90 pixels from the splitter's height:

```
    height: calc(100% - 90px) !important;
```

The splitter is normally rendered at location 0,0 so the 90 pixels of room that has been carved out
will be at the bottom of the page. You will need to move the splitter down 90 pixels if you want the
room to appear at the top of the page:

```
    top: 90px;
```

After that you can add a pseudo element to body or use JavaScript to add the elements you need for your
banner. The example creates a pseudo element and styles it to show the area occupied by the "banner" in
yellow.
