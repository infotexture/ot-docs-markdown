# Example plugin.xml file

The following is a sample of a plugin.xml file. This file adds support for a new set of specialized DTDs, and includes an override for the XHTML output processor.

This plugin.xml file would go into a directory such as DITA-OT/plugins/music/ and referenced supporting files would also exist in that directory. A more extensive sample using these values is available in the actual music plug-in, available at the [DITA-OT download page](http://sourceforge.net/projects/dita-ot/files/) at SourceForge.

```
<plugin id="org.metadita.specialization.music">
  <feature extension="dita.specialization.catalog.relative" file="catalog-dita.xml">
  <feature extension="dita.xsl.xhtml" file="xsl/music2xhtml.xsl"/>
</plugin>
```

**Related information**  


[Plug-in configuration file](../dev_ref/plugin-configfile.md)

