# Configuration properties

The DITA-OT uses .properties files that store configuration settings for the toolkit and its plug-ins. The configuration properties are available to both Ant and Java processes, but unlike argument properties, they cannot be set at run time.

-   **[plugin.properties file](../parameters/lib-plugin-properties.md)**  
The plugin.properties file is used to store configuration properties that are set by the integration process. The file is located in the lib/org.dita.dost.platform directory; it is regenerated each time the integration process is run and so should not be edited manually.
-   **[configuration.properties file](../parameters/lib-configuration-properties.md)**  
The lib/configuration.properties file controls certain common properties, as well as some properties that control PDF processing.

**Parent topic:**[DITA Open Toolkit Parameter Reference](../parameters/index.md)

