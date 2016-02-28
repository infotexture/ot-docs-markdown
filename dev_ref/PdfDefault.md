# PDF processing modules

The PDF \(formerly known as PDF2\) transformation process runs the pre-processing routine and follows it by a series of additional targets. These steps work together to create a merged set of content, convert the merged content to XSL-FO, and then format the XSL-FO file to PDF.

The PDF process includes many Ant targets. During a typical conversion from map to PDF, the following targets are most significant.

 `map2pdf2`
 :   Creates a merged file by calling a common Java merge module. It then calls the `publish.map.pdf` target to do the remainder of the work.

  `publish.map.pdf`
 :   Performs some initialization and then calls the `transform.topic2pdf` target to do the remainder of processing.

  `transform.topic2pdf`
 :   Converts the merged file to XSL-FO, generates the PDF, and deletes the topic.fo file, unless instructed to keep it.

 The `transform.topic2pdf` target uses the following targets to perform those tasks:

 `transform.topic2fo`
 :   Convert the merged file to an XSL-FO file. This process is composed of several Ant targets.

    |Ant target|Description|
    |----------|-----------|
    |`transform.topic2fo.index`|Runs a Java process to set up index processing, based on the document language. This step generates the file stage1.xml in the temporary processing directory.|
    |`transform.topic2fo.flagging`|Sets up preprocessing for flagging based on a DITAVAL file. This step generates the file stage1a.xml in the temporary processing directory.|
    |`transform.topic2fo.main`|Does the bulk of the conversion from DITA to XSL-FO. It runs the XSLT based process that creates stage2.fo in the temporary processing directory|
    |`transform.topic2fo.i18n`|Does additional localization processing on the FO file; it runs a Java process that converts stage2.fo into stage3.fo, followed by an XSLT process that converts stage3.fo into topic.fo.|

  `transform.fo2pdf`
 :   Converts the topic.fo file into PDF using the specified FO processor \(Antenna House, XEP, or Apache FOP\).

  `delete.fo2pdf.topic.fo`
 :   Deletes the topic.fo file, unless otherwise specified by setting an Ant property or command-line option.

 