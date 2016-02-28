# Flagging in the toolkit

Beginning with DITA-OT 1.7, flagging support is implemented as a common preprocess module. The module evaluates the DITAVAL against all flagging attributes, and adds DITA-OT–specific hints to the topic when flags are active. Any extended transformation type may use these hints to support flagging without adding logic to interpret the DITAVAL.

## Evaluating the DITAVAL flags

Flagging is implemented as a reusable module during the preprocess stage. If a DITAVAL file is not used with a build, this step is skipped with no change to the file.

When a flag is active, relevant sections of the DITAVAL itself are copied into the topic as a sub-element of the current topic. The active flags are enclosed in a pseudo-specialization of the `<foreign>` element \(referred to as a pseudo-specialization because it is used only under the covers, with all topic types; it is not integrated into any shipped document types\).

 `<ditaval-startprop>`
 :   When any flag is active on an element, a `<ditaval-startprop>` element will be created as the first child of the flagged element:

    ```
    <ditaval-startprop class="+ topic/foreign ditaot-d/ditaval-startprop ">
    ```

    The `<ditaval-startprop>` element will contain the following:

    -   If the active flags should create a new style, that style is included using standard CSS markup on the @outputclass attribute. Output types that make use of CSS, such as XHTML, can use this value as-is.
    -   If styles conflict, and a `<style-conflict>` element exists in the DITAVAL, it will be copied as a child of `<ditaval-startprop>`.
    -   Any `<prop>` or `<revprop>` elements that define active flags will be copied in as children of the `<ditaval-startprop>` element. Any `<startflag>` children of the properties will be included, but `<endflag>` children will not.

  `<ditaval-endprop>`
 :   When any flag is active on an element, a `<ditaval-endprop>` element will be created as the last child of the flagged element:

    ```
    <ditaval-endprop class="+ topic/foreign ditaot-d/ditaval-endprop ">
    ```

    CSS values and `<styleconflict>` elements are not included on this element.

    Any `<prop>` or `<revprop>` elements that define active flags will be copied in as children of `<ditaval-prop>`. Any `<endflag>` children of the properties will be included, but `<startflag>` children will not.

 ## Supporting flags in overrides or custom transformation types

For most transformation types, the `<foreign>` element should be ignored by default, because arbitrary non-DITA content may not mix well unless coded for ahead of time. If the `<foreign>` element is ignored by default, or if a rule is added to specifically ignore `<ditaval-startprop>` and `<ditaval-endprop>`, then the added elements will have no impact on a transform. If desired, flagging support may be integrated at any time in the future.

The processing described above runs as part of the common preprocess, so any transform that uses the default preprocess will get the topic updates. To support generating flags as images, XSLT based transforms can use default fallthrough processing in most cases. For example, if a paragraph is flagged, the first child of `<p>` will contain the start flag information; adding a rule to handle images in `<ditaval-startprop>` will cause the image to appear at the start of the paragraph content.

In some cases fallthrough processing will not result in valid output; for those cases, the flags must be explicitly processed. This is done in the XHTML transform for elements like `<ol>`, because fallthrough processing would place images in between `<ol>` and `<li>`. To handle this, the code processes `<ditaval-startprop>` before starting the element, and `<ditaval-endprop>` at the end. Fallthrough processing is then disabled for those elements as children of `<ol>`.

## Example DITAVAL

Assume the following DITAVAL file is in use during a build. This DITAVAL will be used for each of the following content examples.

```
<?xml version="1.0" encoding="UTF-8"?>
<val>
  <!-- Define what happens in the case of conflicting styles -->
  <style-conflict background-conflict-color="red"/>

  <!-- Define two flagging properties that give styles (no image) -->
  <prop action="flag" att="audience" style="underline" val="user" backcolor="green"/>
  <prop action="flag" att="platform" style="overline" val="win" backcolor="blue"/>

  <!-- Define a property that includes start and end image flags -->
  <prop action="flag" att="platform" val="linux" style="overline" backcolor="blue">
    <startflag imageref="startlin.png"><alt-text>Start linux</alt-text></startflag>
    <endflag imageref="endlin.png"><alt-text>End linux</alt-text></endflag>
  </prop>

  <!-- Define a revision that includes start and end image flags -->
  <revprop action="flag" style="double-underline" val="rev2">
    <startflag imageref="start_rev.gif"><alt-text>ssssssssssstart</alt-text></startflag>
    <endflag imageref="end_rev.gif"><alt-text>eeeeeeeeeeeeeend</alt-text></endflag>
  </revprop>
</val>
```

## Content example 1: adding style

Now assume the following paragraph exists in a topic. Class attributes are included, as they would normally be in the middle of the preprocess routine; @xtrf and @xtrc are left off for clarity.

```
<p audience="user">Simple user; includes style but no images</p>

```

Based on the DITAVAL above, audience="user" results in a style with underlining and with a green background. The interpreted CSS value is added to @outputclass on `<ditaval-startprop>`, and the actual property definition is included at the start and end of the element. The output from the flagging step looks like this \(with newlines added for clarity, and class attributes added as they would appear in the temporary file\):

The resulting file after the flagging step looks like this; for clarity, newlines are added, while @xtrf and @xtrc are removed:

```
<p audience="user" class="- topic/p ">
  **<ditaval-startprop class="+ topic/foreign ditaot-d/ditaval-startprop " 
           outputclass="background-color:green;text-decoration:underline;"\>
    <prop action="flag" att="audience" style="underline" val="user" backcolor="green"/\>
  </ditaval-startprop\>**
  Simple user; includes style but no images
  **<ditaval-endprop class="+ topic/foreign ditaot-d/ditaval-endprop "\>
    <prop action="flag" att="audience" style="underline" val="user" backcolor="green"/\>
  </ditaval-endprop\>**
</p>
```

## Content example 2: conflicting styles

This example includes a paragraph with conflicting styles. When the audience and platform attributes are both evaluated, the DITAVAL indicates that the background color is both green and blue. In this situation, the `<style-conflict>` element is evaluated to determine how to style the content.

```
<p audience="user" platform="win">Conflicting styles (still no images)</p>
```

The `<style-conflict>` element results in a background color of red, so this value is added to @outputclass on `<ditaval-startprop>`. As above, active properties are copied into the generated elements; the `<style-conflict>` element itself is also copied into the generated `<ditaval-startprop>` element.

The resulting file after the flagging step looks like this; for clarity, newlines are added, while @xtrf and @xtrc are removed:

```
<p audience="user" platform="win" class="- topic/p ">
  **<ditaval-startprop class="+ topic/foreign ditaot-d/ditaval-startprop " 
           outputclass="background-color:red;"\>
    <style-conflict background-conflict-color="red"/\>
    <prop action="flag" att="audience" style="underline" val="user" backcolor="green"/\>
    <prop action="flag" att="platform" style="overline" val="win" backcolor="blue"/\>
  </ditaval-startprop\>**
  Conflicting styles (still no images)
  **<ditaval-endprop class="+ topic/foreign ditaot-d/ditaval-endprop "\>
    <prop action="flag" att="platform" style="overline" val="win" backcolor="blue"/\>
    <prop action="flag" att="audience" style="underline" val="user" backcolor="green"/\>
  </ditaval-endprop\>**
</p>
```

## Content example 3: adding image flags

This example includes image flags for both @platform and @rev, which are defined in DITAVAL `<prop>` and `<revprop>` elements.

```
<ol platform="linux" rev="rev2">
  <li>Generate images for platform="linux" and rev="2"</li>
</ol>
```

As above, the `<ditaval-startprop>` and `<ditaval-endprop>` nest the active property definitions, with the calculated CSS value on @outputclass. The `<ditaval-startprop>` drops the ending image, and `<ditaval-endprop>` drops the starting image. To make document-order processing more consistent, property flags are always included before revisions in `<ditaval-startprop>`, and the order is reversed for `<ditaval-endprop>`.

The resulting file after the flagging step looks like this; for clarity, newlines are added, while @xtrf and @xtrc are removed:

```
<ol platform="linux" rev="rev2" class="- topic/ol ">
  **<ditaval-startprop class="+ topic/foreign ditaot-d/ditaval-startprop " 
           outputclass="background-color:blue;text-decoration:underline;text-decoration:overline;"\>
    <prop action="flag" att="platform" val="linux" style="overline" backcolor="blue"\>
      <startflag imageref="startlin.png"\><alt-text\>Start linux</alt-text\></startflag\>
    </prop\>
    <revprop action="flag" style="double-underline" val="rev2"\>
      <startflag imageref="start\_rev.gif"\><alt-text\>ssssssssssstart</alt-text\></startflag\>
    </revprop\>
  </ditaval-startprop\>**
  <li class="- topic/li ">Generate images for platform="linux" and rev="2"</li>
  **<ditaval-endprop class="+ topic/foreign ditaot-d/ditaval-endprop "\>
    <revprop action="flag" style="double-underline" val="rev2"\>
      <endflag imageref="end\_rev.gif"\><alt-text\>eeeeeeeeeeeeeend</alt-text\></endflag\>
    </revprop\>
    <prop action="flag" att="platform" val="linux" style="overline" backcolor="blue"\>
      <endflag imageref="endlin.png"\><alt-text\>End linux</alt-text\></endflag\>
    </prop\>
  </ditaval-endprop\>**
</ol>
```

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:** [Pull content into topics \(topicpull\)](../dev_ref/preprocess-topicpull.md)

