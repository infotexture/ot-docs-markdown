# Creating plug-ins

The DITA Open Toolkit comes with a built in mechanism for adding in extensions through plug-ins. These plug-ins may do a wide variety of things, such as adding support for specialized DITA DTDs or Schemas, integrating processing overrides, or even providing entirely new output transforms. Plug-ins are the best way to extend the toolkit in a way that is consistent, easily sharable, and easy to preserve through toolkit upgrades.

A plug-in consists of a directory, typically stored directly within the plugins/ directory inside of the DITA-OT. Every plug-in is controlled by a file named plugin.xml, located in the plug-in's root directory.

Benefits of extending the toolkit through plug-ins include:

-   Plug-ins are easily sharable with other users, teams, or companies; typically, all that is needed is to unzip and run a single integration step. With many builds, even that integration step is automatic.
-   Allows overrides or customizations to grow from simple to complex over time, with no increased complexity to the extension mechanism.
-   Plug-ins can be moved from version to version with an upgraded toolkit simply by unzipping again, or by copying the directory from one install to another; there is no need to re-integrate code based on updates to the core processing.
-   Plug-ins can build upon each other. If you like a plug-in provided by one user, simply install that plug-in, and then create your own that builds on that extension. The two plug-ins can then be distributed to your team as a unit, or you can even share your own extensions with the original provider.

-   **[Plug-in configuration file](../dev_ref/plugin-configfile.md)**  
The plugin.xml file controls all aspects of a plug-in, making each extension visible to the rest of the toolkit. The file uses pre-defined extension points to locate changes, and integrates those changes into the core code.
-   **[Extending the XML Catalog](../dev_ref/plugin-xmlcatalog.md)**  
The XML Catalogs extension point is used to update the XML Catalogs used to resolve DTD or Schema document types, or to add URI mappings. This is required in order to support DITA specializations or new DITA document type shells.
-   **[Adding new targets to the Ant build process](../dev_ref/plugin-anttarget.md)**  
The Ant conductor extension point is used to make new targets available to the Ant processing pipeline. This may be done as part of creating a new transform, extending pre-processing, or simply to provide Ant targets for the use of other plug-ins.
-   **[Adding Ant targets to the pre-process pipeline](../dev_ref/plugin-antpreprocess.md)**  
Every step in the pre-process pipeline defines an extension point before and after the step, to allow plug-ins to integrate additional processing. This allows a plug-in to insert a new step before any pre-processing step, as well as before or after the entire preprocess pipeline.
-   **[Integrating a new transformation type](../dev_ref/plugin-newtranstype.md)**  
Plug-ins may integrate an entirely new transformation type. The new transformation type can be very simple, such as an XHTML build that creates an additional control file; it can also be very complex, adding any number of new processing steps.
-   **[Override styles with XSLT](../dev_ref/plugin-overridestyle.md)**  
The XSLT import extension points are used to override various steps of XSLT processing. For this, the extension attribute indicates the step that the override applies to; the `file` attribute is a relative path to the override within the current plugin. The plugin installer will add an XSL import statement to the default code so that your override becomes a part of the normal build.
-   **[Modifying or adding generated text](../dev_ref/plugin-addgeneratedtext.md)**  
Generated text is the term for strings that are automatically added by the build, such as "Note" before the contents of a <note\> element.
-   **[Passing parameters to existing XSLT steps](../dev_ref/plugin-xsltparams.md)**  
Plug-ins can define new parameters to be passed from the Ant build into existing XSLT pipeline stages, usually to have those parameters available as global `<xsl:param>` values within XSLT overrides.
-   **[Adding Java libraries to the classpath](../dev_ref/plugin-javalib.md)**  
If your Ant or XSLT extensions require additional Java libraries in the classpath, you can add them to the global DITA-OT classpath with the following feature.
-   **[Adding diagnostic messages](../dev_ref/plugin-messages.md)**  
Plug-in specific warning and error messages can be added to the set of messages supplied by the DITA-OT. These messages can then be used by any XSLT override.
-   **[Managing plug-in dependencies](../dev_ref/plugin-dependencies.md)**  
The `<require>` element in a plugin.xml file is used to create a dependency on another plug-in. The `<require>` element requires the `plugin` attribute in order to reference the dependency.
-   **[Version and support information](../dev_ref/plugin-support.md)**  
The following extension points are used by convention to define version and support info within a plug-in.
-   **[Creating a new plug-in extension point](../dev_ref/plugin-newextensions.md)**  
If your plug-in needs to define its own extension point in an XML file, add the string "`_template`" to the filename before the file suffix. During integration, this file will be processed like the built-in DITA-OT templates.
-   **[Example plugin.xml file](../dev_ref/plugin-sample.md)**  
The following is a sample of a plugin.xml file. This file adds support for a new set of specialized DTDs, and includes an override for the XHTML output processor.

**Parent topic:**[DITA Open Toolkit Developer Reference](../dev_ref/index.md)

