# XHTML migration for flagging updates in DITA-OT 1.7

This topic is primarily of interest to developers with XHTML transform overrides written prior to DITA-OT 1.7. Due to significant changes in the flagging process with the 1.7 release, some changes may be needed to make overrides work properly with DITAVAL based flagging. The new design is significantly simpler than the old design; in many cases, migration will consist of deleting old code that is no longer needed.

## Which XHTML overrides need to migrate?

If your override does not contain any code related to DITAVAL flagging, then there is nothing to migrate.

If your builds do not make use of DITAVAL based flagging, but calls the deprecated flagging templates, then you should override but there is little urgency. You will not see any difference in the output, but those templates will be removed in a future release.

If you do make use of DITAVAL based flagging, try using your override with 1.7. Check the elements you override:

1.  In some cases flags may be doubled. This will be the case if you call routines such as `"start-flagit"`.
2.  In some cases flags may be removed. This will be the case if you call shortcut routines such as `"revtext"` or `"revblock"`.
3.  In other cases, flags may still appear properly, in which case migration is less urgent

For any migration that needs migration, please see the instructions that follow.

## Deprecated templates in DITA-OT 1.7

All of the old DITAVAL based templates are deprecated in DITA-OT 1.7. If your overrides include any of the following templates, they should be migrated for the new release; in many cases the templates below will not have any effect on your output, but all instances should be migrated.

-   The `"gen-style"` template used to add CSS styling
-   The `"start-flagit"` and `"end-flagit"` templates used to generate image flags based on property attributes like @audience
-   The `"start-revflag"` and `"end-revflag"` templates, used to generate images for active revisions
-   Shortcut templates that group these templates into a single call, such as:
    -   `"start-flags-and-rev"` and `"end-flags-and-rev"`, used to combine flags and revisions into one call
    -   `"revblock"` and `"revtext"`, both used to output start revisions, element content, and end revisions
    -   The modes `"outputContentsWithFlags"` and `"outputContentsWithFlagsAndStyle"`, both used to combine processing for property/revision flags with content processing
-   All other templates that make use of the `$flagrules` variable, which is no longer used in any of the DITA-OT 1.7 code
-   All templates within flag.xsl that were called from the templates listed above
-   Element processing handled with mode="elementname-fmt", such as `mode="ul-fmt"` for processing unordered lists and `mode="section-fmt"` for sections.

## What replaces the templates?

The new flagging design described in the preprocess design section now adds literal copies of relevant DITAVAL elements, along with CSS based flagging information, into the relevant section of the topic. This allows most flags to be processed in document order; in addition, there is never a need to read the DITAVAL, interpret CSS, or evaluate flagging logic. The htmlflag.xsl file contains a few rules to match and process the start/end flags; in most cases, all code to explicitly process flags can be deleted.

For example, the common logic for most element rules before DITA-OT 1.7 could be boiled down to the following:

Match element  
     Create `"flagrules"` variable by reading DITAVAL for active flags  
     Output start tag such as `<div>` or `<span>`  
         Call `"commonattributes"` and ID processing  
         Call `"gen-style"` with `$flagrules`, to create DITAVAL based CSS  
         Call `"start-flagit"` with `$flagrules`, to create start flag images  
         Call `"start-revflag"` with `$flagrules`, to create start revision images  
         Output contents  
         Call `"end-revflag"` with `$flagrules`, to create end revision images  
         Call `"end-flagit"` with `$flagrules`, to create end flag images  
     Output end tag such as `</div>` or `</span>`

In DITA-OT 1.7, style and images are typically handled with XSLT fallthrough processing. This removes virtually all special flag coding from element rules, because flags are already part of the document and processed in document order. The sample above is reduced to:

Match element  
    Output start tag such as `<div>` or `<span>`  
       Call `"commonattributes"` and ID processing  
       Output contents  
    Output end tag such as `</div>` or `</span>`

## Migrating `"gen-style"` named template

Calls to the `"gen-style"` template should be deleted. There is no need to replace this call for most elements.

The `"gen-style"` template was designed to read a DITAVAL file, find active style-based flagging \(such as colored or bold text\), and add it to the generated @style attribute in HTML.

With DITA-OT 1.7, the style is calculated in the pre-process flagging module. The result is created as @outputclass on a `<ditaval-startprop>` sub-element. The `"commonattributes"` template now includes a line to process that value; the result is that for every element that calls `"commonattributes"`, DITAVAL style will be processed when needed. Because virtually every element includes a call to this common template, there is little chance that your override needs to explicitly process the style. The new line in `"commonattributes"` that handles the style is:

```
<xsl:apply-templates select="*[contains(@class,' ditaot-d/ditaval-startprop ')]/@outputclass" mode="add-ditaval-style"/>
```

## Migrating `"start-flagit"`, `"start-revflag"`, `"end-flagit"`, and `"end-flagit"` named templates

Calls to these templates fall into two general groups.

If the flow of your element rule is to create a start tag like `<div>`, `"start-flagit"`/`"start-revflag"`, process contents, `"end-revflag"`/`"end-flagit"`, end tag - you just need to delete the calls to these templates. Flags will be generated simply by processing the element contents in document order.

If the flow of your element rule processes flags outside of the normal document-order. There are generally two reasons this is done. The first case is for elements like `<ol>`, where flags must appear before the `<ol>` in order to create valid XHTML. The second is for elements like `<section>`, where start flags are created, followed by the title or some generated text, element contents, and finally end flags. In either of these cases, support for processing flags in document order is disabled, so they must be explicitly processed out-of-line. This is done with the following two lines \(one for start flag/revision, one for end flag/revision\):

```
Create starting flag and revision images:
<xsl:apply-templates select="*[contains(@class,' ditaot-d/ditaval-startprop ')]" mode="out-of-line"/>

Create ending flag and revision images:
<xsl:apply-templates select="*[contains(@class,' ditaot-d/ditaval-endprop ')]" mode="out-of-line"/>
```

For example, the following lines are used in DITA-OT 1.7 to process the `<ul>` element \(replacing the 29 lines used in DITA-OT 1.6\):

```
<xsl:template match="*[contains(@class,' topic/ul ')]">
  **<xsl:apply-templates select="\*\[contains\(@class,' ditaot-d/ditaval-startprop '\)\]" mode="out-of-line"/\>**
  <xsl:call-template name="setaname"/>
  <ul>
    <xsl:call-template name="commonattributes"/>
    <xsl:apply-templates select="@compact"/>
    <xsl:call-template name="setid"/>
    <xsl:apply-templates/>
  </ul>
  **<xsl:apply-templates select="\*\[contains\(@class,' ditaot-d/ditaval-endprop '\)\]" mode="out-of-line"/\>**
  <xsl:value-of select="$newline"/>
</xsl:template>
```

## Migrating `"start-flags-and-rev"` and `"end-flags-and-rev"`

-   `"start-flags-and-rev"` is equivalent to calling `"start-flagit"` followed by `"start-revflag"`; it should be migrated as in the previous section.
-   `"end-flags-and-rev"` is equivalent to calling `"end-revflag"` followed by `"end-flagit"`; it should be migrated as in the previous section.

## Migrating `"revblock"` and `"revtext"`

Calls to these two templates can be replaced with a simple call to `<xsl:apply-templates/>`.

## Migrating modes `"outputContentsWithFlags"` and `"outputContentsWithFlagsAndStyle"`

Processing an element with either of these modes can be replaced with a simple call to `<xsl:apply-templates/>`.

## Migrating `mode="elementname-fmt"`

Prior to DITA-OT 1.7, many elements were processed with the following logic:

```
Match element
    Set variable to determine if revisions are active and $DRAFT is on
    If active
        create division with rev style
            process element with mode="elementname-fmt"
        end division
    Else
        process element with mode="elementname-fmt"

Match element with mode="elementname-fmt"
    Process as needed
```

Beginning with DITA-OT 1.7, styling from revisions is handled automatically with the `"commonattributes"` template. This means there is no need for the extra testing, or the indirection to `mode="elementname-fmt"`. These templates are deprecated, and element processing will move into the main element rule. Overrides that include this indirection may remove it; overrides should also be sure to match the default rule, rather than matching with `mode="elementname-fmt"`.

**Parent topic:** [Migrating to Release 1.7](../dev_ref/migrating-to-1.7.md)

