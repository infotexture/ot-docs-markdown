# Debug and filter \(debug-filter\)

The `debug-filter` step processes all referenced DITA content and creates copies in a temporary directory. As the DITA content is copied, filtering is performed, debugging information is inserted, and table column names are adjusted. This step is implemented in Java.

The following modifications are made to the DITA source:

-   If a DITAVAL file is specified, the DITA source is filtered according to the entries in the DITAVAL file.
-   Debug information is inserted into each element using the @xtrf and @xtrc attributes. The values of these attributes enable messages later in the build to reliably indicate the original source of the error. For example, a message might trace back to the fifth <ph\> element in a specific DITA topic. Without these attributes, that count might no longer be available due to filtering and other processing.
-   The table column names are adjusted to use a common naming scheme. This is done only to simplify later conref processing. For example, if a table row is pulled into another table, this ensures that a reference to "column 5 properties" will continue to work in the fifth column of the new table.

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:** [Generate lists \(gen-list\)](../dev_ref/preprocess-genlist.md)

**Next topic:** [Resolve map references \(mapref\)](../dev_ref/preprocess-mapref.md)

