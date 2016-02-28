# Open Document Format processing modules

The odt transformation creates a binary file using the OASIS Open Document Format.

The odt transformation begins with pre-processing. It then runs either the `dita.odt.package.topic` or `dita.odt.package.map` target, depending on whether the input to the transformation is a DITA topic or a DITA map. The following description focuses on the map process, which is made up of the following targets:

 `dita.map.odt`
 :   Converts the map into a merged XML file using the Java-based `topicmerge` module. Then an XSLT process converts the merged file into the content.xml file.

  `dita.map.odt.stylesfile`
 :   Reads the input DITA map, and then uses XSLT to create a styles.xml file in the temporary directory.

  `dita.out.odt.manifest.file`
 :   Creates the manifest.xml file

 Once these targets have run, the generated files are zipped up together with other required files to create the output ODT file.

**Parent topic:** [Architecture of the DITA Open Toolkit](../dev_ref/DITA-OTArchitecture.md)

