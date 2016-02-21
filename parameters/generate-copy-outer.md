# generate.outer.copy parameter

Elaboration on how the generate.outer.copy parameter functions.

## Background

This is an issue in the following situations:

-   The DITA map is in a directory that is a peer to directories that contain referenced objects.
-   The DITA map is in a directory that is below the directories that contain the referenced objects.

Let's assume that the directory structure for the DITA content looks like the following:

```
maps
topics
images
```

The DITA map is in the maps directory, the topics are in thetopics directory, and the images are in the images directory.

## Setting the generate.outer.copy parameter to 1

Let's assume that you run the HTML5 transformation and specify an output directory of C:\\A-test. By default, The DITA-OT uses the generate.outer.copy parameter with a value of 1. Output is not built for the topics. You receive only the following output:

```
C:\A-test
--- index.html
--- commonltr.css
--- commonrtl.css
```

The index.html file contains the navigation structure, but all the links are broken, since no HTML5 files were built for the topics.

How do you fix this? By specifying a value of 3 for the generate.outer.copy parameter.

## Setting the generate.outer.copy parameter to 3

Now your output directory structure looks like this:

```
C:\A-test
--- images\
--- maps\
--- topics\
```

The index.html file is in the maps directory, and the CSS and other files are located in the output directory, C:\\A-test. Copying the output directory is simplified.

**Parent topic:** [HTML-based output parameters](../parameters/parameters-base-html.md)

