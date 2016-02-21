# DITA 1.2 support

DITA Open Toolkit 2.2 supports the DITA 1.2 specification. Initial support for this specification was added in version 1.5 of the toolkit; versions 1.5.1 and 1.5.2 contain minor modifications to keep up with the latest drafts. The specification itself was approved at approximately the same time as DITA-OT 1.5.2, which contained the final versions of the DTD and Schemas. DITA-OT 1.6 updated the DITA 1.2 XSDs to address minor errata in the standard; the DTDs remain up to date.

Earlier versions of the DITA Open Toolkit contained a subset of the specification material, including descriptions of each DITA element. This material was shipped in source, CHM and PDF format. This was possible in part because versions 1.0 and 1.1 of the DITA Specification contained two separate specification documents: one for the architectural specification, and one for the language specification.

In DITA 1.2, each of these has been considerably expanded, and the two have been combined into a single document. The overall document is much larger, and including the same set of material would double the size of the DITA-OT package. Rather than include that material in the package, we’ve provided the links below to the latest specification material.

Highlights of DITA 1.2 support in the toolkit include:

-   Processing support for all new elements and attributes
-   Link redirection and text replacement using keyref
-   New processing-role attribute in maps to allow references to topics that will not produce output artifacts
-   New conref extensions, including the ability to reference a range of elements, to push content into another topic, and to use keys for resolving a conref attribute.
-   The ability to filter content with controlled values and taxonomies, using the new Subject Scheme Map
-   Processing support for both default versions of task \(original, limited task, and the general task with fewer constraints on element order\)
-   Acronym and abbreviation support with the new <abbreviated-form\> element
-   New link grouping abilities available with headers in relationship tables
-   OASIS Subcommittee specializations from the learning and machine industry domains \(note that the core toolkit contains only basic processing support for these, but can be extended to produce related artifacts such as SCORM modules\)

To find detailed information about any of these features, see the specification documents at OASIS. The DITA Adoption Technical Committee has also produced several papers to describe individual new features. In general, the white papers are geared more towards DITA users and authors, while the specification is geared more towards tool implementors, though both may be useful for either audience. The DITA Adoption papers can be found from that TC’s main web page.

**Parent topic:** [DITA specification support](../user-guide/DITA_spec-support.md)

**Related information**  


[DITA 1.2 Specification \(XHTML\)](http://docs.oasis-open.org/dita/v1.2/spec/DITA1.2-spec.html)

[DITA 1.2 Specification \(PDF\)](http://docs.oasis-open.org/dita/v1.2/spec/DITA1.2-spec.pdf)

[DITA 1.2 Specification \(zip of the DITA source\)](http://docs.oasis-open.org/dita/v1.2/spec/DITA1.2-spec.zip)

[DITA 1.2 Specification \(zip of the HTML Help\)](http://docs.oasis-open.org/dita/v1.2/spec/DITA1.2-spec-chm.zip)

[DITA Adoption Technical Committee](http://www.oasis-open.org/committees/tc_home.php?wg_abbrev=dita-adoption)

[Building subsets of the specification](http://dita.xml.org/wiki/dita-12-specification-building-specification-subsets)

