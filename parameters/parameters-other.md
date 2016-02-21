# Other parameters

These parameters enable you to reload style sheets that the DITA-OT uses for specific pre-processing stages.

dita.preprocess.reloadstylesheet
dita.preprocess.reloadstylesheet.conref
dita.preprocess.reloadstylesheet.mapref
dita.preprocess.reloadstylesheet.mappull
dita.preprocess.reloadstylesheet.maplink
dita.preprocess.reloadstylesheet.topicpull
:   Specifies whether the DITA-OT reloads the XSL style sheets that are used for the transformation. The allowed values are true and false; the default value is false.

    **Tip:** Set the parameter to true if you want to use more than one set of style sheets to process a collection of topics. The parameter also is useful for large projects that generate Java out-of-memory errors during transformation. Alternatively, you can adjust the size of your Java memory heap if setting `dita.preprocess.reloadstylesheet` for this reason.

**Parent topic:** [DITA-OT parameters](../parameters/parameters_intro.md)

