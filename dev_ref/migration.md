# Migrating customizations

If you have XSL transformation overrides, plugins or other customizations written prior to DITA-OT 2.2, you may need to make changes to ensure your overrides work properly with the latest toolkit versions.

In some cases, you may be able to remove old code that is no longer needed. In other cases, you may need to refactor your code to point to the modified extension points, templates or modes in recent toolkit versions.

-   **[Migrating to Release 1.8](../dev_ref/migrating-to-1.8.md)**  
In DITA-OT 1.8, certain stylesheets were moved to plug-in specific folders and various deprecated Ant properties, XSLT stylesheets, parameters and modes were removed from the XHTML, PDF and ODT transformations.
-   **[Migrating to Release 1.7](../dev_ref/migrating-to-1.7.md)**  
In DITA-OT 1.7, a new preprocessing step implements flagging for HTML-based output formats. PDF processing was corrected with regard to `shortdesc` handling, and a new XSLT template mode was introduced for HTML TOC processing. Several stylesheets were moved to plug-in specific folders and deprecated properties and XSLT variables were removed.
-   **[Migrating to Release 1.6](../dev_ref/migrating-to-1.6.md)**  
In DITA-OT 1.6, various demo plugins were removed along with many deprecated properties, targets, templates and modes. The PDF2 transformation no longer supports the beta version of DITA from IBM, the "bkinfo" demo plug-in, or layout-masters.xml configuration.
-   **[Migrating to Release 1.5.4](../dev_ref/migrating-to-1.5.4.md)**  
DITA-OT 1.5.4 adds new extension points to configure behavior based on file extensions, declare print transformation types and add mappings to the PDF configuration catalog file. PDF output supports mirrored page layout and uses new font family definitions. Support for several new languages was added for PDF and XHTML output.

**Parent topic:**[DITA Open Toolkit Developer Reference](../dev_ref/index.md)

