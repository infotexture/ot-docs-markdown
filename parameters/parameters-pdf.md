# PDF parameters

Certain parameters are specific to the PDF transformation.

args.artlbl
:   Specifies whether to generate a label for each image; the label will contain the image file name. The allowed values are yes and no; the default value is no.

args.bookmap-order
:   Specifies if the frontmatter and backmatter content order is retained in bookmap. The allowed values are retain and discard; the default value is discard.

args.bookmark.style
:   Specifies whether PDF bookmarks are by default expanded or collapsed. The allowed values are EXPANDED and COLLAPSE.

args.chapter.layout
:   Specifies whether chapter level TOCs are generated. The allowed values are MINITOC and BASIC; the default value is MINITOC.

args.fo.userconfig
:   Specifies the user configuration file for FOP.

args.xsl.pdf
:   Specifies an XSL file that is used to override the default XSL transformation.

:   You must specify the fully qualified file name.

axf.opt
:   Specifies the user configuration file for Antenna House Formatter.

custom.xep.config
:   Specifies the user configuration file for RenderX.

customization.dir
:   Specifies the customization directory.

org.dita.pdf2.i18n.enabled
:   Enables I18N font processing. The following values are supported:

    -   true \(default\) – Enables I18N processing
    -   false – Disables I18N processing

pdf.formatter
:   Specifies the XSL processor. The following values are supported:

    -   ah – Antenna House Formatter
    -   xep – RenderX XEP Engine
    -   fop \(default\) – Apache FOP

publish.required.cleanup
:   Specifies whether draft-comment and required-cleanup elements are included in the output. The allowed values are yes, no, yes, and no.

:   The default value is the value of the args.draft parameter. Corresponds to the XSLT parameter publishRequiredCleanup.

    **Note:** This parameter is deprecated in favor of the args.draft parameter.

**Related information**  


[PDF transformation](../user-guide/dita2pdf.md)

[Common parameters](../parameters/parameters-base.md)

