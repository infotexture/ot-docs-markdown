# DITA Open Toolkit 2.2.2 Release Notes

DITA Open Toolkit 2.2.2 is a maintenance release that includes fixes for issues reported in DITA-OT 2.2, which includes new features and enhancements and provides additional support for the OASIS DITA 1.3 specification.

Issue numbers correspond to the tracking number in the [GitHub issues tracker](https://github.com/dita-ot/dita-ot/issues).

## Maintenance Release 2.2.2

DITA Open Toolkit Release 2.2.2 includes the following bug fixes.

-   PDF: In earlier DITA-OT 2.x releases, short description content was not rendered when publishing from a bookmap with the args.chapter.layout parameter set to BASIC. Short descriptions are now rendered properly. [\#2023](https://github.com/dita-ot/dita-ot/issues/2023)
-   *Windows:* The name of the JAR file for Apache Ant has been corrected to fix the `ANT_HOME is set incorrectly or ant could not be located` error that appeared when running the bundled Ant version on Windows in DITA-OT 2.2. [\#2172](https://github.com/dita-ot/dita-ot/issues/2172)
-   The order in which plugins are integrated has been revised to guarantee that the base DITA-OT plugins always come first. This ensures that base target code cannot be overridden. [\#2180](https://github.com/dita-ot/dita-ot/issues/2180)
-   Content references with relative paths were not properly resolved to the target document in some cases. The conref base URI resolution mechanism was fixed to ensure that relative references are now resolved correctly. [\#2192](https://github.com/dita-ot/dita-ot/issues/2192)
-   The documentation has been updated with links to the final [DITA 1.3 specification](http://docs.oasis-open.org/dita/dita/v1.3/os/part3-all-inclusive/dita-v1.3-os-part3-all-inclusive.html).

## Maintenance Release 2.2.1

DITA Open Toolkit Release 2.2.1 included the following bug fixes.

-   PDF: Several templates in the pr-domain.xsl file used `value-of` rather than `apply-templates` to output the element contents. This prevented flagging from working as intended in PDF output. This has been corrected to ensure that elements in the programming domain are properly flagged. [\#2170](https://github.com/dita-ot/dita-ot/issues/2170)
-   The name of the JAR file for the Apache Commons library that provides reusable Java components has been corrected in the integrator Ant script to fix the `NoClassDefFoundError` error that appeared when the integrator ran in DITA-OT 2.2. [\#2163](https://github.com/dita-ot/dita-ot/issues/2163)
-   PDF title metadata is now generated correctly for DITA maps that set the `@xml:lang` attribute. In certain cases, previous versions of DITA-OT displayed the `XMP structure: 1` label in the Document Properties dialog instead of the map title. [\#2154](https://github.com/dita-ot/dita-ot/issues/2154)

## Requirements

DITA Open Toolkit Release 2.2 requires the Java Runtime Environment \(JRE\) version 7 or later.

## Release Highlights

### DITA 1.3 support

DITA Open Toolkit 2.2 provides processing support for the OASIS DITA 1.3 specification. Initial preview support for this specification was added in version 2.0 of the toolkit; version 2.2 extends this foundation to support key scopes and branch filtering along with additional DITA 1.3 features.

Because DITA 1.3 is fully backwards compatible with previous DITA DTDs and schemas, DITA-OT 2.2 provides the 1.3 materials as the default DTDs for processing. The XML Catalog resolution maps any references for unversioned DITA doctypes to the 1.3 DTDs. All processing ordinarily dependent on the 1.0, 1.1, or 1.2 definitions continues to work as usual, and any documents that make use of the newer DITA 1.3 elements or attributes will be supported with specific new processing.

DITA Open Toolkit Release 2.2 extends DITA 1.3 support with the following enhancements:

**Important:** The DITA 1.3 grammars are now used as the default DTDs for processing [\#2094](https://github.com/dita-ot/dita-ot/issues/2094)

-   Initial implementation of DITA 1.3 branch filtering [\#1969](https://github.com/dita-ot/dita-ot/pull/1969), [\#1637](https://github.com/dita-ot/dita-ot/issues/1637)
-   Initial support for DITA 1.3 key scopes, including multiple scope names in a single `@keyscope` attribute [\#1979](https://github.com/dita-ot/dita-ot/pull/1979), [\#1648](https://github.com/dita-ot/dita-ot/issues/1648), [\#2004](https://github.com/dita-ot/dita-ot/issues/2004)
-   The `@keyref` attribute is now supported on `object` elements [\#1783](https://github.com/dita-ot/dita-ot/issues/1783)
-   Processing order has been revised to process any same topic fragments used in conrefs before the conref phase, to enable content references to elements in the same topic using a reference such as `<p conref="#./ID"/>` as reported in [\#1649](https://github.com/dita-ot/dita-ot/pull/1649). [\#1968](https://github.com/dita-ot/dita-ot/pull/1968)

### New HTML5 output

-   The HTML5 transformation has been moved to a separate plugin to facilitate customization of modern HTML5-based output. The default CSS has been refactored in [Sass](http://sass-lang.com) as a foundation for further extensions with CSS frameworks, custom plugins and future toolkit versions. \(The original XHTML plugin remains available to support existing legacy HTML-based output formats such as TocJS, HTML Help and JavaHelp.\) [\#2099](https://github.com/dita-ot/dita-ot/pull/2099)
-   The HTML5 transformation has been extended with a new nav-toc parameter that can be used to generate a table of contents in the HTML5 `nav` element of each page. The navigation can then be rendered in a sidebar or menu via CSS. This parameter is disabled by default \(none\), but can be enabled by setting the value to partial \(which includes the current topic in the ToC along with its parents, siblings and children\), or full \(which generates a ToC for the entire map\). [\#2103](https://github.com/dita-ot/dita-ot/pull/2103)

### PDF supports new languages

The PDF transformation has been extended to support additional languages with localized strings files and index collation. [\#2085](https://github.com/dita-ot/dita-ot/pull/2085), [\#2089](https://github.com/dita-ot/dita-ot/pull/2089)

-   Arabic
-   Catalan
-   Croatian
-   Czech
-   Danish
-   Hungarian
-   Icelandic
-   Latvian
-   Norwegian
-   Polish
-   Portuguese
-   Portuguese \(Brazil\)
-   Slovak
-   Turkish

**Related information**  


[DITA 1.3 specification](http://docs.oasis-open.org/dita/dita/v1.3/os/part3-all-inclusive/dita-v1.3-os-part3-all-inclusive.html)

[DITA 1.3 support](../user-guide/DITA_v1-3-support.md)

## Resolved issues

In addition to the highlights mentioned above, DITA Open Toolkit Release 2.2 includes the following changes.

### Features

DITA Open Toolkit Release 2.2 includes the following new features:

-   The args.artlbl parameter previously provided in HTML-based transformations to show the source file name along with referenced images has been added to the PDF transformation. For inline images, the label appears immediately after the image; for standalone images, it appears on a line following the image. [\#2072](https://github.com/dita-ot/dita-ot/pull/2072), [\#2062](https://github.com/dita-ot/dita-ot/issues/2062)
-   In PDF output, any index entries that begin with special characters are now moved to a dedicated section of the index. \(Previous toolkit versions issued a warning and dropped any unexpected index terms.\) [\#2073](https://github.com/dita-ot/dita-ot/pull/2073), [\#2071](https://github.com/dita-ot/dita-ot/pull/2071)
-   The plugin configuration file resources/plugins.xml generated by the integration process now adds the `@xml:base` attribute to each plugin configuration element so that file paths in the plugin configuration can be resolved relative to the plugin folder. This makes it easier to share a DITA-OT distribution with others via a version control system or bundle it with an application without re-running the integration process in each installation location. [\#2018](https://github.com/dita-ot/dita-ot/issues/2018)
-   The `move-meta-entries` and `mappull` steps have been merged. The `mappull` step has been moved into `move-meta-entries` and an empty target for mappull is retained for backwards compatibility. [\#1995](https://github.com/dita-ot/dita-ot/issues/1995)
-   The generation of page masters and page sequence masters in the PDF plugin has been modularized to make it easier to extend or override the default set of masters. [\#1984](https://github.com/dita-ot/dita-ot/issues/1984)
-   The PDF plugin has been extended with two new extension points for `flagging-preprocess` and `i18n-postprocess` to alllow plugins to customize these steps of the flagging process. [\#1976](https://github.com/dita-ot/dita-ot/pull/1976)
-   The key definition reading process has been moved from the `gen-list` preprocessing module to the `keyref` module to further modularize the code and support additional DITA 1.3 use cases for keys, such as a map that includes a map that then includes another map with a key definition. [\#1962](https://github.com/dita-ot/dita-ot/pull/1962)
-   The mapref processing stage has been moved to the beginning of the preprocessing pipeline to simplify keyref processing and support DITA 1.3 branch filtering by allowing all processing to be performed on a single map. [\#1961](https://github.com/dita-ot/dita-ot/pull/1961)
-   The dita-install option can now be used to integrate multiple plugins at once. If no file or url argument is provided, the integration process reloads plugins from the plugins directory, so you can unzip multiple plugins to the plugins directory and run dita-install to integrate them all at once. [\#1957](https://github.com/dita-ot/dita-ot/issues/1957)
-   The PDF transformation has been extended with XML catalog support for RenderX XEP. The main DITA-OT catalog file is now used to ensure that doctypes such as SVG graphics pass validation when generating PDF output using XEP. [\#1955](https://github.com/dita-ot/dita-ot/pull/1955)
-   The Java code has been refactored to use URI-based processing \(rather than File objects or Strings\) wherever possible to permit automatic validation of values and support the use of external URIs. This allows non-file resources to be processed with commands such as dita-i http://example.com/test.ditamap -f html5. [\#1544](https://github.com/dita-ot/dita-ot/issues/1544), [\#1953](https://github.com/dita-ot/dita-ot/pull/1953)
-   Plugin folders are now sorted before the integration process runs to ensure predictable results and consistent order each time plugins are reloaded. [\#1905](https://github.com/dita-ot/dita-ot/issues/1905)
-   The metadata format in the plugin.xml file for the org.dita.xhtml plugin has been refactored with abstract transtypes that group common parameters used in multiple transformation types. This approach allows common parameters to be defined in one place and re-used for multiple output formats as necessary. [\#1866](https://github.com/dita-ot/dita-ot/issues/1866)
-   The dita command options have been extended to add -t as a synonym for the -temp option used to specify the location of the temporary directory. [\#1836](https://github.com/dita-ot/dita-ot/issues/1836), [\#2039](https://github.com/dita-ot/dita-ot/pull/2039)
-   The validation of the table group `@cols` attribute has been relaxed to support use cases in which tables containing auto-generated `@cols` values are reused via content references. [\#1835](https://github.com/dita-ot/dita-ot/issues/1835)
-   The format of the plugin.xml file has been extended to allow plugins to specify the list of public parameters added for each transformation type and announce extensions to a list of arguments defined in another transtype. [\#1757](https://github.com/dita-ot/dita-ot/issues/1757)

### Enhancements

DITA Open Toolkit Release 2.2 includes the following enhancements and changes to existing features:

-   PDF: Table body rows now use the keep-together.within-page attribute to prevent page breaks within rows. [\#2118](https://github.com/dita-ot/dita-ot/issues/2118)
-   PDF: List item numbers are now aligned with the baseline to prevent issues when list items include icons or other inline elements that affect line spacing. [\#2117](https://github.com/dita-ot/dita-ot/issues/2117)
-   PDF: Step section bodies within task topics now honor the `$side-col-width` value from basic-settings.xsl, which defines a uniform indent relative to the page margin and aligns with other body text. \(Earlier toolkit versions used a hard-coded 9-mm start-indent setting.\) [\#2116](https://github.com/dita-ot/dita-ot/issues/2116)
-   PDF: The index generation process has been rewritten using XSL keys for better performance. The optimizations yield significantly faster PDF builds when using Apache FOP. [\#2098](https://github.com/dita-ot/dita-ot/issues/2098), [\#2086](https://github.com/dita-ot/dita-ot/issues/2086)
-   HTML5 and XHTML table border processing has been optimized to match the expected output based on the table width, column separation, row separation and frame settings in the source files, permit easier integration of CSS frameworks, and output valid documents. [\#2097](https://github.com/dita-ot/dita-ot/issues/2097)
-   The task headings \(About this task, Procedure, etc.\) and flags for Optional and Required steps in the PDF transformation have been synchronized with those available in the common string files, XHTML and ODT transformations. Source files that make use of these options should now yield more more consistent results when generating output in multiple formats. [\#2088](https://github.com/dita-ot/dita-ot/issues/2088)
-   PDF: The index groups for Numerics and Special Characters have been aligned for greater consistency across languages. [\#2080](https://github.com/dita-ot/dita-ot/pull/2080), [\#2074](https://github.com/dita-ot/dita-ot/issues/2074)
-   PDF: The “pointing finger” image hand.gif is no longer used to highlight `note` elements, as it may be considered offensive in some cultures. The image file is still available for backwards compatibility with any customization that references it, and the "Note Image Path" variables are still present to permit the use of custom image files, but they are now empty by default. Text-only note labels appear instead, and the default indentation is reduced by the width of the empty note image column.

    **Note:** The warning.gif file is still used for Attention, Caution, Danger and Warning admonitions.

    [\#2076](https://github.com/dita-ot/dita-ot/pull/2076), [\#1577](https://github.com/dita-ot/dita-ot/issues/1577)

-   The outer.control parameter description was corrected to clarify how the DITA-OT handles content files that are not located in or below the directory containing the master DITA map. [\#1707](https://github.com/dita-ot/dita-ot/pull/1707)[\#2066](https://github.com/dita-ot/dita-ot/pull/2066)
-   Formatter-specific code for XSL-FO rendering engines has been removed from the PDF plugin and split into separate plugins for Apache FOP, Antenna House Formatter and RenderX XEP. [\#2058](https://github.com/dita-ot/dita-ot/pull/2058)
-   The classpath order is now retained when generating the env.sh and env.bat environment files to ensure predictable results when a plugin that uses Java libraries presupposes a certain classpath order. [\#2053](https://github.com/dita-ot/dita-ot/pull/2053)
-   The PDF2 flagging step that converted stage1.xml to stage1a.xml in the PDF process has been refactored to take advantage of the flagging information added during the common preprocessing stage. [\#2049](https://github.com/dita-ot/dita-ot/pull/2049), [\#2047](https://github.com/dita-ot/dita-ot/pull/2047)
-   The dita.bat Windows batch file for the dita command now sets the DITA\_HOME variable to point to the correct location of the DITA-OT. [\#2046](https://github.com/dita-ot/dita-ot/pull/2046)
-   PDF: A new axf.opt parameter has been added to specify the user configuration file for Antenna House Formatter. [\#2041](https://github.com/dita-ot/dita-ot/pull/2041)
-   Processing mode coverage has been improved to treat error messages as fatal errors, so the DITA-OT will now stop processing if any source files are missing when the processing-mode parameter is set to strict. [\#1986](https://github.com/dita-ot/dita-ot/issues/1986)
-   Table columns for which no width is defined in a `colspec` element are no longer set to `1*` per the CALS Table Model. Instead, empty `@colwidth` attributes are generated to allow formatter-specific auto-layout. The FO processor can then set the width of the columns based on the column content. [\#1970](https://github.com/dita-ot/dita-ot/issues/1970)

### Bugs

DITA Open Toolkit Release 2.2 provides fixes for the following bugs:

-   Inconsistency in naming of flow name, region definition [\#2128](https://github.com/dita-ot/dita-ot/issues/2128)
-   Third relcolspec title on a reltable no longer taken into account for publishing [\#2119](https://github.com/dita-ot/dita-ot/issues/2119)
-   Topic in temp folder is not wellformed [\#2109](https://github.com/dita-ot/dita-ot/issues/2109)
-   gradle build fails with ‘Could not load FFI Provider ..’ on Windows [\#2108](https://github.com/dita-ot/dita-ot/issues/2108)
-   Behavior of the force-unique flag [\#2105](https://github.com/dita-ot/dita-ot/issues/2105)
-   Site builds fail after `html5` changes [\#2101](https://github.com/dita-ot/dita-ot/issues/2101)
-   Generated HTML table is invalid according to HTML5 specs [\#2095](https://github.com/dita-ot/dita-ot/issues/2095)
-   Fix table and figure list to include number, title [\#2093](https://github.com/dita-ot/dita-ot/pull/2093)
-   Remove obsolete info from codepage list [\#2091](https://github.com/dita-ot/dita-ot/pull/2091)
-   Add axf.jar into log-processor taskdef classpath [\#2090](https://github.com/dita-ot/dita-ot/pull/2090)
-   Add PFD2 index groups for a-breve, a-circ in Romanian [\#2081](https://github.com/dita-ot/dita-ot/pull/2081)
-   Ambiguous message for example with two titles [\#2078](https://github.com/dita-ot/dita-ot/pull/2078)
-   Table not localized in French translation org.dita.pdf2 - fr.xml [\#2061](https://github.com/dita-ot/dita-ot/pull/2061)
-   French translation of Table of contents is incorrect [\#2060](https://github.com/dita-ot/dita-ot/pull/2060)
-   Fix ODT title generation [\#2059](https://github.com/dita-ot/dita-ot/pull/2059), [\#2034](https://github.com/dita-ot/dita-ot/issues/2034)
-   Catch null FileInfo object being referenced in move-meta. [\#2051](https://github.com/dita-ot/dita-ot/pull/2051)
-   Flagging preprocess grabs too much with check for defaults [\#2050](https://github.com/dita-ot/dita-ot/pull/2050), [\#2048](https://github.com/dita-ot/dita-ot/issues/2048)
-   Error message not properly formatted [\#2027](https://github.com/dita-ot/dita-ot/issues/2027)
-   Can no longer publish to XHTML image with data protocol [\#2012](https://github.com/dita-ot/dita-ot/issues/2012)
-   Ensuring @chunk inside topicgroups functions as expected. [\#2009](https://github.com/dita-ot/dita-ot/pull/2009), [\#1991](https://github.com/dita-ot/dita-ot/issues/1991)
-   Copy-to usage with URI support does not properly work [\#2006](https://github.com/dita-ot/dita-ot/issues/2006)
-   Cannot publish remote HTTP DITA Map to XHTML [\#2003](https://github.com/dita-ot/dita-ot/issues/2003)
-   Branch filtering does not seem to work with entire DITA Maps [\#1992](https://github.com/dita-ot/dita-ot/issues/1992)
-   Add proper mappings for topicrefs with copy-to attributes in JavaHelp [\#1989](https://github.com/dita-ot/dita-ot/pull/1989)
-   Use the fragment part of KeyDef @href attribute when building @conref [\#1974](https://github.com/dita-ot/dita-ot/pull/1974)
-   Remove unwanted $PATH2PROJ remnant from $entry-file definition \(glossary entry file resolution fails from term and abbreviated-form DOTX058W\) [\#1967](https://github.com/dita-ot/dita-ot/pull/1967), [\#1966](https://github.com/dita-ot/dita-ot/issues/1966)
-   DITA-OT 2.0 - Build Error \(Windows\) - Illegal character - keyref target [\#1823](https://github.com/dita-ot/dita-ot/issues/1823)
-   abbreviated-form and term keyref links are not resolved when chunk="to-content" [\#1816](https://github.com/dita-ot/dita-ot/issues/1816)
-   Two levels of map ref causes good key ref to fail [\#1605](https://github.com/dita-ot/dita-ot/issues/1605)

### Contributors

DITA Open Toolkit Release 2.2 includes [contributions](https://github.com/dita-ot/dita-ot/graphs/contributors) by the following people:

1.  Jarno Elovirta
2.  Robert D. Anderson
3.  Roger Sheen
4.  Eero Helenius
5.  Radu Coravu
6.  Tom Glastonbury
7.  Kendall Shaw
8.  Eliot Kimber
9.  Chris Nitchie
10. Stefan Eike

For the complete list of changes since the previous release, see the [changelog](https://github.com/dita-ot/dita-ot/compare/2.1...release/2.2) on GitHub.

