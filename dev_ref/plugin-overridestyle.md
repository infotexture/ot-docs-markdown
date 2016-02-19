# Override styles with XSLT

The XSLT import extension points are used to override various steps of XSLT processing. For this, the extension attribute indicates the step that the override applies to; the `file` attribute is a relative path to the override within the current plugin. The plugin installer will add an XSL import statement to the default code so that your override becomes a part of the normal build.

The following XSLT steps are available to override in the core toolkit:

`dita.xsl.xhtml`
:   Overrides default \(X\)HTML output \(including HTML Help and Eclipse Help\). The referenced file is integrated directly into the XSLT step that generates XHTML.

`dita.xsl.xslfo`
:   Overrides default PDF output \(formerly known as PDF2\). The referenced file is integrated directly into the XSLT step that generates XSL-FO for PDF.

`dita.xsl.docbook`
:   Overrides default DocBook output.

`dita.xsl.rtf`
:   Overrides default RTF output.

`dita.xsl.eclipse.plugin`
:   Overrides the step that generates plugin.xml for Eclipse.

`dita.xsl.conref`
:   Overrides the preprocess step that resolves conref.

`dita.xsl.topicpull`
:   Overrides the preprocess step "topicpull" \(the step that pulls text into <xref\> elements, among other things\).

`dita.xsl.mapref`
:   Overrides the preprocess step "mapref" \(the step that resolves references to other maps\).

`dita.xsl.mappull`
:   Overrides the preprocess step "mappull" \(the step that updates navtitles in maps and causes attributes to cascade\).

`dita.xsl.maplink`
:   Overrides the preprocess step "maplink" \(the step that generates map-based links\).

`dita.xsl.troff-ast`
:   Overrides the intermediate block-and-phrase format generated as input to troff processing.

`dita.xsl.troff`
:   Overrides the XSL that converts block-and-phrase intermediate markup into troff.

## Example – Overriding XHTML header processing

The following two files represent a complete, simple style plug-in.

The plugin.xml file declares an XSLT file that extends XHTML processing:

```
<?xml version="1.0" encoding="UTF-8"?>
<plugin id="com.example.brandheader">
  <feature extension="dita.xsl.xhtml" file="xsl/header.xsl"/>
</plugin>
```

The xsl/header.xsl XSLT file referenced above in plugin.xml overrides the default header processing to provide a \(theoretical\) banner:

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" 
                xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template name="gen-user-header">
    <div><img src="http://www.example.com/company_banner.jpg" 
              alt="Example Company Banner"/></div>
  </xsl:template>
</xsl:stylesheet>
```

## Example – Overriding troff formatting

To apply custom formatting for your own domain to the intermediate markup generated as input to troff processing, create a plugin that extends `dita.xsl.troff-ast` and specify the path to your custom XSL as follows:

```
<feature extension="dita.xsl.troff-ast" file="xsl/your-domain.xsl"/>
```

**Parent topic:**[Creating plug-ins](../dev_ref/plugins-overview.md)

