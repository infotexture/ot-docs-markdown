# Migrating to Release 1.7

In DITA-OT 1.7, a new preprocessing step implements flagging for HTML-based output formats. PDF processing was corrected with regard to `shortdesc` handling, and a new XSLT template mode was introduced for HTML TOC processing. Several stylesheets were moved to plug-in specific folders and deprecated properties and XSLT variables were removed.

A new job status file .job.xml has been introduced and replaces dita.list and dita.xml.properties as the normative source for job status. If you have custom processing which modifies the job properties, you should change your code to modify .job.xml instead.

Support for the following deprecated properties has been removed:

-   `dita.input`
-   `dita.input.dirname`
-   `dita.extname`

Stylesheets for the following transformation types have moved to plug-in specific folders:

-   docbook
-   eclipsecontent
-   troff
-   wordrtf

If custom plug-ins have hard coded paths to these stylesheets, update references to use either `plugin` URIs in `xsl:import` instructions or use `dita.plugin.*` Ant properties.

The integration process has been changed to use strict mode by default. For old plug-ins which are not valid, lax processing mode can still be used.

Plug-ins that use the `MessageUtils` Java class must use `getInstance` method to access the `MessageUtils` instance, as `getMessage` methods have been changed to instance methods.

## Preprocessing

The preprocessing Ant dependency chain has been cleaned up. Tasks no longer depend on the previous task in the default chain, but rather the whole preprocess dependency chain is defined by the `preprocess` task.

## HTML

Core TOC generation has been moved to a separate XSLT stylesheet xsl/map2htmtoc/map2htmlImpl.xsl and the new templates use the mode `toc`. Plug-ins which override HTML TOC processing should change the map processing templates to `toc` mode.

## HTML and extended transformation types

Flagging logic has been pulled out of the core X/HTML code and moved to a preprocess step. This significantly simplifies and optimizes the X/HTML code, while making flagging logic available to any other transformation type. The new preprocess step implements all flagging logic; for each active flag, it adds a DITA-OT specific hint into the intermediate topics \(implemented as a specialization of the DITA <foreign\> element\). As part of this change, all flagging-related templates in the XHTML code \(such as start-flagit and gen-style\) are deprecated.

If you override the X/HTML transforms, you may need to update your overrides to use the new flagging logic. In most cases this just means deleting calls to the deprecated templates; in some cases, the calls can be replaced with 2 lines to process flags in new places. You should compare your override to the updated XHTML code and update as needed. See [XHTML migration for flagging updates in DITA-OT 1.7](flagging-migration.md) for details.

Plug-ins that provide support for new transforms need to ensure that they properly support the DITA <foreign\> element, which should be ignored by default; if so, this change will have no immediate impact. Support for flagging new transformation types may be more easily added based on this update, because there is no need to re-implement flagging logic, but this is not required. See [Flagging in the toolkit](preprocess-flagging.md) for details on how to add flagging support.

## PDF

The following deprecated XSLT variables have been removed:

-   `page-margin-left`
-   `page-margin-right`

XSLT stylesheets have been split to separate specialization topic code and new `xsl:import` instructions have been added to topic2fo.xsl. Plug-ins which define their own shell stylesheet should be revised to import all the required stylesheet modules.

PDF processing used to replace topic `shortdesc` with map `shortdesc`, but this behavior was incorrect and was removed to comply with the DITA specification.

A new `#note-separator` variable string was added to facilitate customization.

-   **[XHTML migration for flagging updates in DITA-OT 1.7](../dev_ref/flagging-migration.md)**  
This topic is primarily of interest to developers with XHTML transform overrides written prior to DITA-OT 1.7. Due to significant changes in the flagging process with the 1.7 release, some changes may be needed to make overrides work properly with DITAVAL based flagging. The new design is significantly simpler than the old design; in many cases, migration will consist of deleting old code that is no longer needed.

**Parent topic:** [Migrating customizations](../dev_ref/migration.md)

