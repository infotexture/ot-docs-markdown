# Adding Java libraries to the classpath

If your Ant or XSLT extensions require additional Java libraries in the classpath, you can add them to the global DITA-OT classpath with the following feature.

`dita.conductor.lib.import`
:   Add Java libraries to DITA-OT classpath.

## Example

The following plug-in adds the compiled Java code from myJavaLibrary.jar into the global DITA-OT classpath. XSLT or Ant code can then make use of the added code.

```
<plugin id="com.example.addjar">
  <feature extension="dita.conductor.lib.import" file="myJavaLibrary.jar"/>
</plugin>
```

Now assume that in this case myJavaLibrary.jar performs some validation step in the middle of processing, and you always want it to run immediately before the conref step. In that case you need to make use of several features in this plug-in

-   The JAR file must be added to the classpath.
-   An Ant target must be created that uses this class, and the Ant wrapper integrated into the code.
-   The Ant target must be added to the dependency chain for conref.

In this extended example, the files might look something like this.

```
plugin.xml:
<?xml version="1.0" encoding="UTF-8"?>
<plugin id="com.example.samplejava">
  <!-- Add the JAR file to the DITA-OT CLASSPATH -->
  **<feature extension="dita.conductor.lib.import" file="com.example.sampleValidation.jar"/\>**
  <!-- Integrate the Ant code -->
  <feature extension="dita.conductor.target.relative" file="antWrapper.xml"/>
  <!-- Define the Ant target that is called, and the location (before conref) -->
  <feature extension="depend.preprocess.conref.pre" value="validateWithJava"/>
</plugin>

antWrapper.xml imports the new Ant code:
<?xml version="1.0" encoding="UTF-8"?>
<dummy>
  <import file="calljava-antcode.xml"/>
</dummy>

calljava-antcode.xml:
<?xml version="1.0" encoding="UTF-8"?>
<project default="validateWithJava">
  <target name="validateWithJava">
    <java classname="com.example.sampleValidation">
      <!-- The class was added to dost.class.path (the DITA-OT classpath) -->
      <classpath refid="dost.class.path"/>
    </java>
  </target>
</project>
```

**Parent topic:**[Creating plug-ins](../dev_ref/plugins-overview.md)

