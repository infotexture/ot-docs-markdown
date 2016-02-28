# Prerequisite software

The prerequisite software that the DITA-OT requires depends on the types of transformations that you want to use.

## Software required for core DITA-OT processing

The DITA-OT requires the following software applications:

 JRE or JDK, version 7 or later
 :   Provides the basic environment for the DITA-OT. You can download the Oracle JRE or JDK from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

    **Note:** This is the *only* prerequisite software that you need to install. The remaining required software is included in the distribution packages.

  Ant, version 1.7.1 or later
 :   Provides the standard setup and sequencing of processing steps. You can download Ant from [http://ant.apache.org/](http://ant.apache.org/).

  XSLT processor
 :   Provides the main transformation services. It must be compliant with XSLT 2.0. The DITA-OT is tested with Saxon. You can download Saxon, version 9.1.0.8 from [http://saxon.sourceforge.net/](http://saxon.sourceforge.net/).

 ## Software required for specific transformations

Depending on the type of output that you want to generate, you might need the following applications:

 ICU for Java
 :   ICU for Java is a cross-platform, Unicode-based, globalization library. It includes support for comparing locale-sensitive strings; formatting dates, times, numbers, currencies, and messages; detecting text boundaries; and converting character sets. You can download ICU for Java from [http://www.icu-project.org/download/](http://www.icu-project.org/download/).

  Microsoft Help Workshop
 :   Required for generating HTML help. You can download the Help Workshop from [http://msdn.microsoft.com/en-us/library/windows/desktop/ms669985%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/ms669985%28v=vs.85%29.aspx).

  XSL-FO processor
 :   Required for generating PDF output. You can download FOP from [http://xmlgraphics.apache.org/fop/download.html](http://xmlgraphics.apache.org/fop/download.html); you also can use Antenna House Formatter or RenderX.

 See [Tested platforms and tools](tested-tools.md) for detailed information about versions of the prerequisite applications that have been tested with the current DITA-OT release.

**Parent topic:** [Installing the DITA Open Toolkit](../user-guide/installing.md)

