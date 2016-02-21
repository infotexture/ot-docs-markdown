# JavaHelp processing

The javahelp transformation runs several additional Ant targets after the XHTML processing is completed in order to create control files for the JavaHelp output.

There are two primary Ant targets:

`dita.map.javahelp`
:   Creates all of the files that are needed to compile JavaHelp, including a table of contents, sorted index, and help map file.

`compile.Java.Help`
:   Searches for a JavaHelp compiler on the system. If a compiler is found, the help project is compiled.

**Parent topic:** [HTML-based processing modules](../dev_ref/XhtmlWithNavigation.md)

