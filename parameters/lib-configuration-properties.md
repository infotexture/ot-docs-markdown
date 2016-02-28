# configuration.properties file

The lib/configuration.properties file controls certain common properties, as well as some properties that control PDF processing.

 default.language
 :   Specifies the language that is used if the input file does not have the @xml:lang attribute set on the root element. By default, this is set toen. The allowed values are those that are defined in IETF BCP 47, [Tags for Identifying Languages](https://tools.ietf.org/html/bcp47).

  org.dita.pdf2.i18n.enabled
 :   \(PDF transformation only\) Enables I18N font processing. The following values are allowed:

    -   true \(default\) — Enables I18N processing
    -   false — Disables I18N processing

  plugindirs
 :   A semicolon-separated list of directory paths that the DITA-OT searches for plug-ins to integrate; any relative paths are resolved against the DITA-OT base directory. Any immediate subdirectory that contains a plugin.xml file is integrated

  plugin.ignores
 :   A semicolon-separated list of directory names to be ignored during plug-in integration; any relative paths are resolved against the DITA-OT base directory.

 