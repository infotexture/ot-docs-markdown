# TocJS processing

The tocjs transformation was originally created as a plug-in that distributed outside of the toolkit, but it now ships bundled in the default packages. This HTML5-based output type creates a JavaScript based frameset with TOC entries that expand and collapse.

The following Ant targets control most of the TocJS processing:

 `tocjsInit`
 :   Sets up default properties. This target detects whether builds have already specified a name for JavaScript control file; if not, the default name toctree.js is used.

  `map2tocjs`
 :   Calls the `dita.map.tocjs` target, which generates the contents frame for TocJS output.

  `tocjsDefaultOutput`
 :   Ensures that the HTML5 processing module is run. If scripts are missing required information, such as a name for the default frameset, this target copies default style and control files. This target was add to the DITA-OT in version 1.5.4; earlier versions of the TocJS transformation created only the JavaScript control file by default.

 