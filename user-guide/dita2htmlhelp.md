# DITA to HTML Help \(CHM\)

The htmlhelp transformation generates HTML output, CSS files, and the control files that are needed to produce a Microsoft HTML Help file.

In addition to the HTML output and CSS files, this transformation returns the following files, where mapname is the name of the master DITA map.

|File name|Description|
|---------|-----------|
|mapname.hhc|Table of contents|
|mapname.hhk|Sorted index|
|mapname.hhp|HTML Help project file|
|mapname.chm|Compiled HTML Help**Note:** This file is generated only if the HTML Help Workshop is installed on the build system.

|

**Parent topic:** [DITA-OT transformations \(output formats\)](../user-guide/AvailableTransforms.md)

**Related information**  


[HTMLHelp parameters](../parameters/parameters-htmlhelp.md)

