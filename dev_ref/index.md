# DITA Open Toolkit Developer Reference

 The Developer Reference is designed to provide more advanced information about the DITA-OT. It is geared to an audience that needs information about the DITA-OT architecture, extending the DITA-OT, and creating DITA-OT plug-ins. 

-   **[Architecture of the DITA Open Toolkit](../dev_ref/DITA-OTArchitecture.md)**  
The DITA Open Toolkit is an open-source implementation of the OASIS specification for the Darwin Information Typing Architecture. The toolkit uses Ant, XSLT, and Java to transform DITA content \(maps and topics\) into different deliverable formats.
-   **[Extending the DITA Open Toolkit](../dev_ref/extending-the-ot.md)**  
There are several methods that can be used to extend the toolkit; not all of them are recommended or supported. The best way to create most extensions is with a plug-in; extended documentation for creating plug-ins is provided in the next section.
-   **[Creating plug-ins](../dev_ref/plugins-overview.md)**  
The DITA Open Toolkit comes with a built in mechanism for adding in extensions through plug-ins. These plug-ins may do a wide variety of things, such as adding support for specialized DITA DTDs or Schemas, integrating processing overrides, or even providing entirely new output transforms. Plug-ins are the best way to extend the toolkit in a way that is consistent, easily sharable, and easy to preserve through toolkit upgrades.
-   **[Customizing PDF output](../user-guide/dita2pdf-customization.md)**  
You can build a DITA-OT plug-in that contains a customized PDF transformation.
-   **[Migrating customizations](../dev_ref/migration.md)**  
If you have XSL transformation overrides, plugins or other customizations written prior to DITA-OT 2.2, you may need to make changes to ensure your overrides work properly with the latest toolkit versions.
-   **[Implementation dependent features](../dev_ref/DITA1.2-implementation-dependent-features.md)**  

-   **[Extended functionality](../dev_ref/extended-functionality.md)**  


