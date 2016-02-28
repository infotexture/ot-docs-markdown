# Migrating to Release 1.8

In DITA-OT 1.8, certain stylesheets were moved to plug-in specific folders and various deprecated Ant properties, XSLT stylesheets, parameters and modes were removed from the XHTML, PDF and ODT transformations.

Stylesheets for the following transformation types have moved to plug-in specific folders:

-   eclipsehelp
-   htmlhelp
-   javahelp
-   odt
-   xhtml

## Preprocessing

The following deprecated Ant properties have been removed:

-   `dita.script.dir`, use `${dita.plugin.id.dir}` instead
-   `dita.resource.dir`, use `${dita.plugin.org.dita.base.dir}/resource` instead
-   `dita.empty`
-   `args.message.file`

## XHTML

XSLT Java extension `ImgUtils` has been removed from stylesheets and been replaced with preprocessing module `ImageMetadataModule`. The old `ImgUtils` Java classes are still included in the build.

## PDF

The following deprecated XSLT stylesheets have been removed:

-   artwork-preprocessor.xsl
-   otdita2fo\_frontend.xsl

The following deprecated XSLT templates have been removed:

-   `insertVariable.old`

The following deprecated XSLT modes have been removed:

-   `layout-masters-processing`
-   `toc-prefix-text`, use `tocPrefix` mode instead
-   `toc-topic-text`, use `tocText` mode instead

Link generation has been simplified by removing deprecated arguments in favor of `args.rellinks`. The following deprecated Ant properties have been removed:

-   `args.fo.include.rellinks`

The following XSLT parameters have been removed:

-   `antArgsIncludeRelatedLinks`
-   `disableRelatedLinks`

A call to a named template `pullPrologIndexTerms.end-range` has been added to `processTopic*` templates to handle topic wide index ranges.

## Legacy PDF

The following deprecated XSLT stylesheets have been removed:

-   dita2fo-shell\_template.xsl
-   topic2fo-shell.xsl

## ODT

Link generation has been simplified by removing deprecated arguments in favor of `args.rellinks`. The following deprecated Ant properties have been removed:

-   `args.odt.include.rellinks`

The following XSLT parameters have been added:

-   `include.rellinks`

The following XSLT parameters have been removed:

-   `disableRelatedLinks`

