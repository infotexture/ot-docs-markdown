# Map based linking \(maplink\)

This step collects links based on a map and moves those links into the referenced topics. The links are created based on hierarchy in the DITA map, the @collection-type attribute, and relationship tables. This step is implemented in XSLT and Java.

The `maplink` module runs an XSLT stylesheet that evaluates the map; it places all the generated links into a single file in memory. The module then runs a Java program that pushes the generated links into the applicable topics.

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:**[Chunk topics \(chunk\)](../dev_ref/preprocess-chunk.md)

**Next topic:**[Pull content into topics \(topicpull\)](../dev_ref/preprocess-topicpull.md)

