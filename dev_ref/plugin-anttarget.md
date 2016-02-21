# Adding new targets to the Ant build process

The Ant conductor extension point is used to make new targets available to the Ant processing pipeline. This may be done as part of creating a new transform, extending pre-processing, or simply to provide Ant targets for the use of other plug-ins.

`dita.conductor.target.relative`
`dita.conductor.target`
:   Add Ant import to main Ant build file.

    **Remember:** The `dita.conductor.target` extension is deprecated. Use `dita.conductor.target.relative` instead.

## Example

To extend Ant processing, first place your extensions in an Ant project file within your plug-in, such as myAntStuff.xml. Next, create a small wrapper file myAntStuffWrapper.xml in the same directory:

```
<dummy> <import file="myAntStuff.xml"/> </dummy>
```

Then create the following feature:

```
<plugin id="com.example.ant">
  <feature extension="dita.conductor.target.relative" file="myAntStuffWrapper.xml"/>
</plugin>
```

When the plug-in is integrated, the imports from myAntStuffWrapper.xml will be copied into build.xml \(using the correct path\). This makes targets in myAntStuff.xml available to any other processing.

**Parent topic:** [Creating plug-ins](../dev_ref/plugins-overview.md)

