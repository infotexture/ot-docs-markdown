# Installing plug-ins

Plug-ins are distributed as zip files and can be installed using either the command line tool or Ant.

1.   Run plug-in installation process. 

    -   Using the dita command line tool, run the installation command:

        ```
        dita -install plug-in-zip
        ```

    -   Using Ant, from the toolkit directory run the installation target:

        ```
        ant -f integrator.xml install -Dplugin.file=plug-in-zip
        ```

    The plug-in-zip can be either a local file path or a URL.


**Parent topic:** [Extending the DITA Open Toolkit](../user-guide/extending-the-dita-ot.md)

