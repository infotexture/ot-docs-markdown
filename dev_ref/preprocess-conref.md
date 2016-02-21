# Conref \(conref\)

The `conref` step resolves conref attributes, processing only the DITA maps or topics that use the @conref attribute. This step is implemented in XSLT.

The values of the @id attribute on referenced content are changed as the elements are pulled into the new locations. This ensures that the values of the @id attribute within the referencing topic remain unique.

If an element is pulled into a new context along with a cross reference that references the target, both the values of the @id and @xref attributes are updated so that they remain valid in the new location. For example, a referenced topic might include a section as in the following example:

```
<topic id="referenced_topic">
  <title>...</title>
  <body>
    <section id="sect"><title>Sample section</title>
      <p>Figure <xref href="#referenced_topic/fig"/> contains an code sample that demonstrates ... .</p>
      <fig id="fig"><title>Code sample</title>
        <codeblock>....</codeblock>
      </fig>
    </section>
  </body>
</topic>
```

When the section is referenced using a @conref attribute, the value of the @id attribute on the <fig\> element is modified to ensure that it remains unique in the new context. At the same time, the <xref\> element is also modified so that it remains valid as a local reference. For example, if the referencing topic has an @id set to "new\_topic", then the conrefed <section\> element may look like this in the intermediate document.

```
<section id="sect"><title>Sample section</title>
    <p>Figure <xref href="#new_topic/d1e25"/> contains an code sample that demonstrates ... .</p>
    <fig id="d1e25"><title>Code sample</title>
        <codeblock>....</codeblock>
    </fig>
</section>
```

In this case, the value of the @id attribute on the <fig\> element has been changed to a generated value of "d1e25". At the same time, the <xref\> element has been updated to use that new generated ID, so that the cross reference remains valid.

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:**[Conref push \(conrefpush\)](../dev_ref/preprocess-conrefpush.md)

**Next topic:**[Resolve code references \(coderef\)](../dev_ref/preprocess-coderef.md)

