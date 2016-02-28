# Move metadata \(move-meta-entries\) and pull content into maps \(mappull\)

The `move-meta-entries` step pushes metadata back and forth between maps and topics. For example, index entries and copyrights in the map are pushed into affected topics, so that the topics can be processed later in isolation while retaining all relevant metadata. This step is implemented in Java.

**Note:** As of DITA-OT 2.2, the `move-meta-entries` and `mappull` steps have been merged. The `mappull` step has been moved into `move-meta-entries`.

The `mappull` step pulls content from referenced topics into maps, and then cascades data within maps. This step is implemented in XSLT.

The `mappull` step makes the following changes to the DITA map:

-   Titles are pulled from referenced DITA topics. Unless the @locktitle attribute is set to "yes", the pulled titles replace the navigation titles specified on the <topicref\> elements.
-   The <linktext\> element is set based on the title of the referenced topic, unless it is already specified locally.
-   The <shortdesc\> element is set based on the short description of the referenced topic, unless it is already specified locally.
-   The @type attribute is set on <topicref\> elements that reference local DITA topics. The value of the @type attribute is set to value of the root element of the topic; for example, a <topicref\> element that references a task topic is given a @type attribute set to "task"".
-   Attributes that cascade, such as @toc and print, are made explicit on any child <topicref \>elements. This allows future steps to work with the attributes directly, without reevaluating the cascading behavior.

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:** [Resolve code references \(coderef\)](../dev_ref/preprocess-coderef.md)

**Next topic:** [Chunk topics \(chunk\)](../dev_ref/preprocess-chunk.md)

