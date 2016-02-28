# Integrating a new transformation type

Plug-ins may integrate an entirely new transformation type. The new transformation type can be very simple, such as an XHTML build that creates an additional control file; it can also be very complex, adding any number of new processing steps.

The transtype extension point is used to define a new transformation type, which makes use of targets in your Ant extensions. When a transformation type is defined, the build expects Ant code to be integrated to define the transform process. The Ant code must define a target based on the name of the transformation type; if the transformation type is "mystuff", the Ant code must define a target named dita2mystuff.

 `dita.conductor.transtype.check`
 :   Add a new value to the list of valid transformation type names.

  `dita.transtype.print`
 :   Declare the transformation type as a print type.

 The `<transtype>` element is used to define a new transformation type with the parameters that are supported.

## Example

The following feature defines a transformation type of "newtext" and declares it as a print type; using this transformation type will cause the build to look for a target `dita2newtext`, defined in a related Ant extension from the third feature:

```
<plugin id="com.example.newtext">
  **<feature extension="dita.conductor.transtype.check" value="newtext"/\>**
  **<transtype name="newtext"/\>**
  <feature extension="dita.transtype.print" value="newtext"/>
  <feature extension="dita.conductor.target.relative" file="antWrapper.xml"/>
</plugin>
```

The following example shows how the org.dita.html5 plugin uses the `<transtype>` element to extend the common HTML transformation with a new html5 transformation type and define a new nav-toc parameter with three possible values:

```
**<transtype name="html5" extends="common-html" desc="HTML5"\>**
  <param name="nav-toc" type="enum" 
         desc="Specifies whether to generate a navigation TOC in topic pages.">
    <val default="true" desc="No TOC">none</val>
    <val desc="Partial TOC that shows the current topic">partial</val>
    <val desc="Full TOC">full</val>
  </param>
</transtype>
```

**Related information**  


[Plug-in configuration file](../dev_ref/plugin-configfile.md)

