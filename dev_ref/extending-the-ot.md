# Extending the DITA Open Toolkit

There are several methods that can be used to extend the toolkit; not all of them are recommended or supported. The best way to create most extensions is with a plug-in; extended documentation for creating plug-ins is provided in the next section.

-   Creating a plug-in can be very simple to very complex, and is generally the best method for changing or extending the toolkit. Plug-ins can be used to accomplish almost any modification that is needed for toolkit processing, from minor style tweaks to extensive, complicated new output formats.
-   The PDF process was initially developed independently of the toolkit, and created its own extension mechanism using customization directories. Many \(but not quite all\) of the capabilities available through PDF customization directories are now available through plug-ins.
-   Using a single XSL file as an override by passing it in as a parameter. For example, when building XHTML content, the XSL parameter allows users to specify a single local XSL file \(inside or outside of the toolkit\) that is called in place of the default XHTML code. Typically, this code imports the default processing code, and overrides a couple of processing routines. This approach is best when the override is very minimal, or when the style varies from build to build. However, any extension made with this sort of override is also possible with a plug-in.
-   Editing DITA-OT code directly may work in some cases, but is not advised. Modifying the code directly significantly increases the work and risk involved with future upgrades. It is also likely that such modifications will break plug-ins provided by others, limiting the function available to the toolkit.

-   **[Manually installing plug-ins](../dev_ref/plugins-installing.md)**  
Plug-ins are generally distributed as zip files. There are two steps to installing a plug-in: unzipping and integrating.
-   **[Manually removing plug-ins](../dev_ref/plugins-removing.md)**  
Plug-ins can be installed by removing the plug-in and running integration process.
-   **[Rebuilding the DITA-OT documentation](../dev_ref/rebuilding-the-dita-ot-documentation.md)**  
The DITA-OT ships with Ant scripts that enable you to rebuild the toolkit documentation. This is especially helpful if your environment contains plug-ins that integrate additional messages into the toolkit.

**Parent topic:** [DITA Open Toolkit Developer Reference](../dev_ref/index.md)

**Related information**  


[Installing plug-ins](../user-guide/plugins-installing.md)

[Removing plug-ins](../user-guide/plugins-removing.md)

