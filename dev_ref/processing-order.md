# Processing order

The order of processing is often significant when evaluating DITA content. Although the DITA specification does not mandate a specific order for processing, the DITA-OT has determined that performing filtering before conref resolution best meets user expectations. Switching the order of processing, while legal, may give different results.

The DITA-OT project has found that filtering first provides several benefits. Consider the following sample that contains a <note\> element that both uses conref and contains a @product attribute:

```
<note conref="documentA.dita#doc/note" product="MyProd"/>
```

If the @conref attribute is evaluated first, then documentA must be parsed in order to retrieve the note content. That content is then stored in the current document \(or in a representation of that document in memory\). However, if all content with product="MyProd" is filtered out, then that work is all discarded later in the build.

If the filtering is done first \(as in the DITA-OT\), this element is discarded immediately, and documentA is never examined. This provides several important benefits:

-   Time is saved by discarding unused content as early as possible; all future steps can load the document without this extra content.
-   Additional time is saved case by not evaluating the @conref attribute; in fact, documentA does not even need to be parsed.
-   Any user reproducing this build does not need documentA. If the content is sent to a translation team, that team can reproduce an error-free build without documentA; this means documentA can be kept back from translation, preventing accidental translation and increased costs.

If the order of these two steps is reversed, so that conref is evaluated first, it is possible that results will differ. For example, in the code sample above, the @product attribute on the reference target will override the product setting on the referencing note. Assume that the referenced <note\> element in documentA is defined as follows:

```
<note id="note" product="SomeOtherProduct">This is an important note!</note>
```

A process that filters out product="SomeOtherProduct" will remove the target of the original conref before that conref is ever evaluated, which will result in a broken reference. Evaluating conref first would resolve the reference, and only later filter out the target of the conref. While some use cases can be found where this is the desired behavior, benefits such as those described above resulted in the current processing order used by the DITA-OT.

**Parent topic:** [Architecture of the DITA Open Toolkit](../dev_ref/DITA-OTArchitecture.md)

