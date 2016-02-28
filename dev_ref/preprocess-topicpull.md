# Pull content into topics \(topicpull\)

The `topicpull` step pulls content into <xref\> and <link\> elements. This step is implemented in XSLT.

If an <xref\> element does not contain link text, the target is examined and the link text is pulled. For example, a reference to a topic pulls the title of the topic; a reference to a list item pulls the number of the item. If the <xref\> element references a topic that has a short description, and the <xref\> element does not already contain a child <desc\> element, a <desc\> element is created that contains the text from the topic short description.

The process is similar for <link\> elements. If the <link\> element does not have a child <linktext\> element, one is created with the appropriate link text. Similarly, if the <link\> element does not have a child <desc\> element, and the short description of the target can be determined, a <desc\> element is created that contains the text from the topic short description.

