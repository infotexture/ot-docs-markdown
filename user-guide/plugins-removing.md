# Removing plug-ins

Plug-ins can be removed by running the uninstallation process.

1.   Run plug-in uninstallation process. 
    -   Using the dita command line tool, run the uninstallation command:

        ```
        dita -uninstall plug-in-id
        ```

    -   Using Ant, from the toolkit directory run the uninstallation target:

        ```
        ant -f integrator.xml uninstall -Dplugin.id=plug-in-id
        ```


