# HTML-based output parameters

Certain parameters apply to all the HTML-based transformation types: Eclipse help, HTML Help, JavaHelp, TocJS, HTML5, and XHTML.

args.artlbl
:   Specifies whether to generate a label for each image; the label will contain the image file name. The allowed values are yes and no; the default value is no.

args.breadcrumbs
:   Specifies whether to generate breadcrumb links. The allowed values are yes and no; the default value is no.

:   Corresponds to the XSLT parameter BREADCRUMBS.

args.copycss
:   Specifies whether to copy the custom .css file to the output directory. The allowed values are yes and no; the default value is yes.

args.css
:   Specifies the name of a custom .css file.

args.csspath
:   Specifies the location of a copied .css file relative to the output directory.

:   Corresponds to the XSLT parameter CSSPATH. DITA-OT will copy the file to this location.

args.cssroot
:   Specifies the directory that contains the custom .css file.

:   DITA-OT will copy the file from this location.

args.dita.locale
:   Specifies the language locale file to use for sorting index entries.

:   **Note:** This parameter is not available for the XHTML transformation.

args.ftr
:   Specifies an XML file that contains content for a running footer.

:   Corresponds to the XSLT parameter FTR.

    **Note:** The footer file should be specified using an absolute path and must contain valid XML. A common practice is to place all content into a <div\> element.

args.gen.default.meta
:   Specifies whether to generate extra metadata that targets parental control scanners, meta elements with name="security" and name="Robots". The allowed values are yes and no; the default value is no.

:   Corresponds to the XSLT parameter genDefMeta.

args.hdf
:   Specifies an XML file that contains content to be placed in the document head.

args.hdr
:   Specifies an XML file that contains content for a running header.

:   Corresponds to the XSLT parameter HDR.

    **Note:** The header file should be specified using an absolute path and must contain valid XML. A common practice is to place all content into a <div\> element.

args.hide.parent.link
:   Specifies whether to hide links to parent topics in the HTML or XHTML output. The allowed values are yes and no; the default value is no.

:   Corresponds to the XSLT parameter NOPARENTLINK.

    **Note:** This parameter is deprecated in favor of the args.rellinks parameter.

args.indexshow
:   Specifies whether the content of <indexterm\> elements are rendered in the output. The allowed values are yes and no; the default value is no.

args.outext
:   Specifies the file extension for HTML or XHTML output.

:   Corresponds to the XSLT parameter OUTEXT.

args.xhtml.classattr
:   Specifies whether to include the DITA class ancestry inside the XHTML elements. The allowed values are yes and no; the default value is yes.

:   For example, the <prereq\> element \(which is specialized from section\) would generate `class="section prereq`. The allowed values are yes and no; the default value is yes. Corresponds to the XSLT parameter PRESERVE-DITA-CLASS.

    **Note:** Beginning with DITA OT release 1.5.2, the default value is yes. For release 1.5 and 1.5.1, the default value was no.

args.xsl
:   Specifies a custom XSL file to be used instead of the default XSL transformation.

:   The parameter must specify a fully qualified file name.

-   **[generate.outer.copy parameter](../parameters/generate-copy-outer.md)**  
Elaboration on how the generate.outer.copy parameter functions.

**Parent topic:** [DITA-OT parameters](../parameters/parameters_intro.md)

**Related information**  


[Eclipse content parameters](../parameters/parameters-eclipsecontent.md)

[Eclipse Help parameters](../parameters/parameters-eclipsehelp.md)

[HTMLHelp parameters](../parameters/parameters-htmlhelp.md)

[JavaHelp parameters](../parameters/parameters-javahelp.md)

[HTML5 and XHTML parameters](../parameters/parameters-common-html.md)

