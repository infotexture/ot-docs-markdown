# DITA to Rich Text Format

The wordrtf transformation produces an RTF file for use by Microsoft Word.

The structure of the generated RTF file is the same as the navigation structure in the DITA map. To avoid losing files in the final output, make sure the DITA map contains all topics that are referenced from any individual topics.

The wordrtf transformation has the following limitations:

-   Flagging, filtering, and revision bars are not supported.
-   Style attributes for tables are not supported.
-   Tables within list items are not supported.
-   Certain output styles supported by other DITA-OT transformations are not supported.

**Parent topic:** [DITA-OT transformations \(output formats\)](../user-guide/AvailableTransforms.md)

