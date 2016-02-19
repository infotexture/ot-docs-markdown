# Pre-processing modules

The pre-processing operation is a set of steps that typically runs at the beginning of every DITA-OT transformation. Each step or stage corresponds to an Ant target in the build pipeline; the preprocess target calls the entire set of steps.

1.  [Generate lists \(gen-list\)](../dev_ref/preprocess-genlist.md)  
The `gen-list` step examines the input files and creates lists of topics, images, document properties, or other content. These lists are used by later steps in the pipeline. For example, one list includes all topics that make use of the conref attribute; only those files are processed during the conref stage of the build. This step is implemented in Java.
2.  [Debug and filter \(debug-filter\)](../dev_ref/preprocess-debugfilter.md)  
The `debug-filter` step processes all referenced DITA content and creates copies in a temporary directory. As the DITA content is copied, filtering is performed, debugging information is inserted, and table column names are adjusted. This step is implemented in Java.
3.  [Resolve map references \(mapref\)](../dev_ref/preprocess-mapref.md)  
The `mapref` step resolves references from one DITA map to another. This step is implemented in XSLT.
4.  [Copy related files \(copy-files\)](../dev_ref/preprocess-copyfiles.md)  
The `copy-files` step copies non-DITA resources to the output directory, such as HTML files that are referenced in a map or images that are referenced by a DITAVAL file.
5.  [Resolve keyref \(keyref\)](../dev_ref/preprocess-keyref.md)  
The `keyref` step examines all the keys that are defined in the DITA source and resolves the key references. Links that make use of keys are updated so that any @href value is replaced by the appropriate target; key-based text replacement is also performed, and the key definition list file is written to the temporary directory. This step is implemented in Java.
6.  [Conref push \(conrefpush\)](../dev_ref/preprocess-conrefpush.md)  
The `conrefpush` step resolves "conref push" references. This step only processes documents that use conref push or that are updated due to the push action. This step is implemented in Java.
7.  [Conref \(conref\)](../dev_ref/preprocess-conref.md)  
The `conref` step resolves conref attributes, processing only the DITA maps or topics that use the @conref attribute. This step is implemented in XSLT.
8.  [Resolve code references \(coderef\)](../dev_ref/preprocess-coderef.md)  
The `coderef` step resolves references made with the <coderef\> element. This step is implemented in Java.
9.  [Move metadata \(move-meta-entries\) and pull content into maps \(mappull\)](../dev_ref/preprocess-metadata.md)  
The `move-meta-entries` step pushes metadata back and forth between maps and topics. For example, index entries and copyrights in the map are pushed into affected topics, so that the topics can be processed later in isolation while retaining all relevant metadata. This step is implemented in Java.
10. [Chunk topics \(chunk\)](../dev_ref/preprocess-chunk.md)  
The `chunk` step breaks apart and assembles referenced DITA content based on the @chunk attribute in maps. This step is implemented in Java.
11. [Map based linking \(maplink\)](../dev_ref/preprocess-maplink.md)  
This step collects links based on a map and moves those links into the referenced topics. The links are created based on hierarchy in the DITA map, the @collection-type attribute, and relationship tables. This step is implemented in XSLT and Java.
12. [Pull content into topics \(topicpull\)](../dev_ref/preprocess-topicpull.md)  
The `topicpull` step pulls content into <xref\> and <link\> elements. This step is implemented in XSLT.
13. [Flagging in the toolkit](../dev_ref/preprocess-flagging.md)  
Beginning with DITA-OT 1.7, flagging support is implemented as a common preprocess module. The module evaluates the DITAVAL against all flagging attributes, and adds DITA-OT–specific hints to the topic when flags are active. Any extended transformation type may use these hints to support flagging without adding logic to interpret the DITAVAL.

**Parent topic:**[Architecture of the DITA Open Toolkit](../dev_ref/DITA-OTArchitecture.md)

