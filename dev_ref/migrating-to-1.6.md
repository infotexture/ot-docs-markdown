# Migrating to Release 1.6

In DITA-OT 1.6, various demo plugins were removed along with many deprecated properties, targets, templates and modes. The PDF2 transformation no longer supports the beta version of DITA from IBM, the "bkinfo" demo plug-in, or layout-masters.xml configuration.

Support for the old DITAVAL format \(used before OASIS added DITAVAL to the standard in 2007\) has been removed.

The demo folder has been deprecated and the following plug-ins have been moved to the plugins folder:

|old path|new path|
|--------|--------|
|demo/dita11|plugins/org.dita.specialization.dita11|
|demo/dita132|plugins/org.dita.specialization.dita132|
|demo/eclipsemap|plugins/org.dita.specialization.eclipsemap|
|demo/fo|plugins/org.dita.pdf2|
|demo/tocjs|plugins/com.sophos.tocjs|
|demo/h2d|plugins/h2d|
|demo/legacypdf|plugins/legacypdf|

The remaining plug-ins in the demo folder have been moved to a separate repository at [github.com/dita-ot/ext-plugins](https://github.com/dita-ot/ext-plugins).

The deprecated property `dita.input.valfile` should be replaced with the new argument property `args.filter`.

The `dita-preprocess` target has been removed and dependencies should be replaced with a target sequence `build-init, preprocess`.

Support for the `args.message.file` argument has been removed as message configuration has become static configuration.

The `workdir` processing instruction has been deprecated in favor of `workdir-uri`. The only difference between the two processing instructions is that `workdir-uri` contains a URI instead of a system path.

## Preprocessing

The following deprecated templates and modes have been removed in topic pull stylesheets:

-   inherit
-   get-stuff
-   verify-type-attribute
-   classval
-   getshortdesc
-   getlinktext
-   blocktext
-   figtext
-   tabletext
-   litext
-   fntext
-   dlentrytext
-   firstclass
-   invalid-list-item
-   xref

## PDF2

The following deprecated items are no longer supported in the PDF transform:

-   Support for the beta version of DITA, available from IBM before the OASIS standard was created in 2005.
-   Support for the "bkinfo" demo plug-in, used to support book metadata before OASIS created the BookMap format in 2007.
-   Support for layout-masters.xml configuration. Plug-ins should use the `createDefaultLayoutMasters` template instead.

The following extension-points have been added:

-   `dita.conductor.pdf2.param` to add XSLT parameters to XSL FO transformation.

Custom PDF2 shell stylesheets need to be revised to not include separate IBM and OASIS DITA stylesheets. The \*\_1.0.xsl stylesheets have been removed and their imports must be removed from shell stylesheets.

The following template modes have been deprecated:

-   toc-prefix-text
-   toc-topic-text

The following named templates have been removed:

-   processTopic
-   createMiniToc
-   processTopicTitle
-   createTopicAttrsName
-   processConcept
-   processReference
-   getTitle
-   placeNoteContent
-   placeImage
-   processUnknowType
-   insertReferenceTitle
-   buildRelationships
-   processTask

The main FO generation process now relies on the merging process to rewrite duplicate IDs. The default merging process did this already in previous releases, but now also custom merging processes must fulfill the duplicate ID rewrite requirement.

## XHTML

The following named templates have been deprecated:

-   make-index-ref

The following deprecated templates have been removed:

-   revblock-deprecated
-   revstyle-deprecated
-   start-revision-flag-deprecated
-   end-revision-flag-deprecated
-   concept-links
-   task-links
-   reference-links
-   relinfo-links
-   sort-links-by-role
-   create-links
-   add-linking-attributes
-   add-link-target-attribute
-   add-user-link-attributes

The removed templates have been replaced by other templates in earlier releases and plug-ins should be changed to use the new templates.

## ODT

The following deprecated templates have been removed:

-   revblock-deprecated
-   revstyle-deprecated
-   start-revision-flag-deprecated
-   end-revision-flag-deprecated

The removed templates have been replaced by other templates in earlier releases and plug-ins should be changed to use the new templates.

