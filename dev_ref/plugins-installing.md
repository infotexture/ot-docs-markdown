# Manually installing plug-ins

Plug-ins are generally distributed as zip files. There are two steps to installing a plug-in: unzipping and integrating.

It is possible to define a plug-in so that it may be installed anywhere, although most expect to be placed in plugins/ directory inside of the DITA-OT. Most plug-ins do not require a specific install directory and can go in either of the default locations, but some may come with instructions for a particular install directory.

1.   The unzip the plug-in file to plugins subdirectory. The plug-in directory should be named after plug-in ID and version, for example plugins/com.example.xhtml\_1.0.0.
2.   Run plug-in integration process. 

    -   From the toolkit directory, run the following command to integrate all installed plug-ins:

        ```
        ant -f integrator.xml 
        ```

    -   Any build that uses the Java command line interface automatically runs the integrator before processing begins.
    -   Ant based builds may import the `integrator.xml` file, and add `integrate` to the start of the dependency chain for the build.

        **Note:** The integration process in considered part of the installation process and running it before each conversion will incur a performance penalty.

    The integration process has two modes, lax and strict. In the strict mode the integration process will immediately fail if it encounters errors in plug-in configurations or installation process. In the lax mode, the integration process will continue to finish regardless of errors; the lax mode does not imply error recovery and may leave the DITA-OT installation into a broken state. The default mode is lax due to backwards compatibility, to run the integration in strict mode:

    ```
    ant -f integrator.xml strict
    ```

    To get more information about the integration process, run Ant in verbose mode:

    ```
    ant -f integrator.xml -verbose strict
    ```


**Parent topic:** [Extending the DITA Open Toolkit](../dev_ref/extending-the-ot.md)

