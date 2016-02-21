# Rebuilding the DITA-OT documentation

The DITA-OT ships with Ant scripts that enable you to rebuild the toolkit documentation. This is especially helpful if your environment contains plug-ins that integrate additional messages into the toolkit.

1.  Change to the docsrc directory.
2.  Run the following command:

    ```
    ant -f build.xml target
    ```

    The target parameter is optional and specifies a specific transformation type. It takes the following values:

    -   html
    -   htmlhelp
    -   pdf
    If you do not specify an Ant target, all three output formats \(HTML5, HTML help, and PDF\) are generated.


**Parent topic:** [Extending the DITA Open Toolkit](../dev_ref/extending-the-ot.md)

