# Passing parameters to existing XSLT steps

Plug-ins can define new parameters to be passed from the Ant build into existing XSLT pipeline stages, usually to have those parameters available as global `<xsl:param>` values within XSLT overrides.

To create new parameters, create a file named insertParameters.xml, which contains one or more Ant `<param>` elements. It also needs a `<dummy>` wrapper element around the parameters. For example, the following parameter will be passed in to the XSLT file with a value of `${antProperty}`, but only if that parameter is defined:

```
<dummy>
  <!-- Any Ant code allowed in xslt task is possible. Common example: -->
  <param name="paramNameinXSLT" expression="${antProperty}" if="antProperty"/>
</dummy>
```

Pass the value using the following extensions:

 `dita.conductor.html.param`
 :   Pass parameters to HTML and HTML Help XSLT

  `dita.conductor.xhtml.param`
 :   Pass parameters to XHTML and Eclipse Help XSLT

  `dita.conductor.xhtml.toc.param`
 :   Pass parameters to XHTML TOC XSLT

  `dita.conductor.eclipse.toc.param`
 :   Pass parameters to Eclipse Help TOC XSLT

  `dita.preprocess.conref.param`
 :   Pass parameters to conref XSLT

  `dita.preprocess.mapref.param`
 :   Pass parameters to mapref XSLT

  `dita.preprocess.mappull.param`
 :   Pass parameters to mappull XSLT

  `dita.preprocess.topicpull.param`
 :   Pass parameters to topicpull XSLT

  `dita.conductor.pdf2.param`
 :   Pass parameters to PDF2 XSLT

 ## Example

The following plug-in will pass the parameters defined in the insertParameters.xml file as input to the XHTML process. Generally, an additional XSLT override will make use of the parameter to do something new with the generated content.

```
<plugin id="com.example.newparam">
  <feature extension="dita.conductor.xhtml.param" file="insertParameters.xml"/>
</plugin>
```

