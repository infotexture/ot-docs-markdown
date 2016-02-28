# Common HTML-based processing

After the pre-processing operation runs, HTML-based builds each run a common series of Ant targets to generate HTML file. Navigation may be created before or after this set of common routines.

After the pre-processing is completed, the following targets are run for all of the HTML-based builds:

-   If the arg.css parameter is passed to the build to add a CSS file, the `copy-css` target copies the CSS file from its source location to the relative location in the output directory.
-   If a DITAVAL file is used, the `copy-revflag` target copies the default start- and end-revision flags into the output directory.
-   The DITA topics are converted to HTML files. Unless the @chunk attribute was specified, each DITA topic in the temporary directory now corresponds to one HTML file. The `dita.inner.topics.xhtml` target is used to process documents that are in the map directory \(or subdirectories of the map directory\). The `dita.outer.topics.xhtml` target is used to process documents that are outside of the scope of the map, and thus might end up outside of the designated output directory. Various DITA-OT parameters control how documents processed by the `dita.outer.topics.xhtml` target are handled.

