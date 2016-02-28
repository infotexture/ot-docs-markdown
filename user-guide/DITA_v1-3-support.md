# DITA 1.3 support

DITA Open Toolkit 2.2 provides processing support for the OASIS DITA 1.3 specification. Initial preview support for this specification was added in version 2.0 of the toolkit; version 2.2 extends this foundation to support key scopes and branch filtering along with additional DITA 1.3 features.

Because DITA 1.3 is fully backwards compatible with previous DITA DTDs and schemas, DITA-OT 2.2 provides the 1.3 materials as the default DTDs for processing. The XML Catalog resolution maps any references for unversioned DITA doctypes to the 1.3 DTDs. All processing ordinarily dependent on the 1.0, 1.1, or 1.2 definitions continues to work as usual, and any documents that make use of the newer DITA 1.3 elements or attributes will be supported with specific new processing.

## Initial Preview Support for DITA 1.3 in DITA-OT 2.0

The following DITA 1.3 features were implemented in version 2.0 of the toolkit. Issue numbers correspond to the tracking number in the  [GitHub issues tracker](https://github.com/dita-ot/dita-ot/issues).

-   Support DITA 1.3 link syntax \(milestone 2\) [\#1649](https://github.com/dita-ot/dita-ot/issues/1649)
-   Support DITA 1.3 cascade attribute \(milestone 2\) [\#1636](https://github.com/dita-ot/dita-ot/issues/1636)
-   Implement DITA 1.3 profiling \(milestone 2\) [\#1635](https://github.com/dita-ot/dita-ot/issues/1635)
-   Add new DITA 1.3 highlighting elements \(milestone 4\) [\#1651](https://github.com/dita-ot/dita-ot/issues/1651)
-   Add DITA 1.3 markup and xml domain support \(milestone 4\) [\#1652](https://github.com/dita-ot/dita-ot/issues/1652)
-   Add DITA 1.3 div element \(milestone 4\) [\#1654](https://github.com/dita-ot/dita-ot/issues/1654)

## Additional DITA 1.3 support in DITA-OT 2.2

The following DITA 1.3 features were implemented in version 2.2 of the toolkit.

**Important:** The DITA 1.3 grammars are now used as the default DTDs for processing [\#2094](https://github.com/dita-ot/dita-ot/issues/2094)

-   Initial implementation of DITA 1.3 branch filtering [\#1969](https://github.com/dita-ot/dita-ot/pull/1969), [\#1637](https://github.com/dita-ot/dita-ot/issues/1637) 

    The implementation is a separate module that is run before keyref processing. The process

    -   Splits branches so that each branch contains a single ditavalref
    -   Generates `@copy-to` attributes for each branch-generated <topicref\>
    -   Filters the map based on branch filters
    -   Rewrites duplicate generated copy-to targets with a numbered `-#` suffix
    -   Copies and filters generated copy-to targets
    -   Filters topics that were not branch-generated
-   Initial support for DITA 1.3 key scopes, including multiple scope names in a single `@keyscope` attribute [\#1979](https://github.com/dita-ot/dita-ot/pull/1979), [\#1648](https://github.com/dita-ot/dita-ot/issues/1648), [\#2004](https://github.com/dita-ot/dita-ot/issues/2004) 
-   The `@keyref` attribute is now supported on `object` elements [\#1783](https://github.com/dita-ot/dita-ot/issues/1783) 
-   Processing order has been revised to process any same topic fragments used in conrefs before the conref phase, to enable content references to elements in the same topic using a reference such as `<p conref="#./ID"/>` as reported in [\#1649](https://github.com/dita-ot/dita-ot/pull/1649). [\#1968](https://github.com/dita-ot/dita-ot/pull/1968) 

**Note:** For the latest status information on DITA 1.3-related features, see the [DITA 1.3 label](https://github.com/dita-ot/dita-ot/issues?q=label%3A%22DITA+1.3%22+is%3Aclosed) in the GitHub issues tracker.

**Related information**  


[DITA Version 1.3 Part 3: All-Inclusive Edition \(HTML\)](http://docs.oasis-open.org/dita/dita/v1.3/os/part3-all-inclusive/dita-v1.3-os-part3-all-inclusive.html)

[DITA Version 1.3 Part 3: All-Inclusive Edition \(PDF\)](http://docs.oasis-open.org/dita/dita/v1.3/os/part3-all-inclusive/dita-v1.3-os-part3-all-inclusive.pdf)

[DITA Version 1.3 \(Distribution ZIP of the DITA source\)](http://docs.oasis-open.org/dita/dita/v1.3/os/dita-v1.3-os.zip)

[DITA Adoption Technical Committee](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=dita-adoption)

