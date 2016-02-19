# HTML Help processing

The htmlhelp transformation created HTML Help control files. If the build runs on a system that has the HTML Help compiler installed, the control files are compiled into a CHM file.

Once the pre-processing and XHTML processes are completed, most of the HTML Help processing is handled by the following targets:

`dita.map.htmlhelp`
:   Create the HHP, HHC, and HHK files. The HHK file is sorted based on the language of the map.

`dita.htmlhelp.convertlang`
:   Ensures that the content can be processed correctly by the compiler, and that the appropriate code pages and languages are used.

`compile.HTML.Help`
:   Attempts to detect the HTML Help compiler. If the compiler is found, the full project is compiled into a single CHM file.

**Parent topic:**[HTML-based processing modules](../dev_ref/XhtmlWithNavigation.md)

