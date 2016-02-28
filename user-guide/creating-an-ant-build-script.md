# Creating an Ant build script

Instead of typing the DITA-OT parameters at the command prompt, you might want to create an Ant build script that contains all of the parameters.

1.   Create an XML file that contains the following content: 

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    <project name="%project-name%" default="%default-target%" basedir=".">
    
      <property name="dita.dir" location="%path-to-DITA-OT%"/>
     
      <target name="%target-name%">
        <ant antfile="${dita.dir}/build.xml">
          <property name="args.input" value="%DITA-input%"/>
          <property name="transtype" value="html5"/>
        </ant>
      </target>
    
    </project>
    ```

    You will replace the placeholder content \(indicated by the % signs\) with content applicable to your environment.

2.   Specify project information: 
    1.   Set the value of the @name attribute to the name of your project. 
    2.   Set the value of the @default attribute to the name of a target in the build script. If the build script is invoked without specifying a target, this target will be run.
3.   Set the value of the dita.dir property to the location of the DITA-OT. This can be a fully qualified path, or you can specify it relative to the location of the Ant build script that you are writing.
4.   Create the Ant target: 
    1.   Set the value of the @name attribute. 
    2.   Specify the value for the args.input property. 
    3.   Specify the value of the transtype property. 
5.   Save the build script. 

The following Ant build script generates CHM and PDF output for the userguide.ditamap file.

```
<?xml version="1.0" encoding="UTF-8" ?>
<project name="Toolkit-documentation" default="all" basedir=".">
    
  <property name="dita.dir" location="C:\dita-ot"/>
  
  <target name="all" description="build CHM and PDF" depends="chm,pdf"/>
  
  <target name="chm" description="build CHM">
    <ant antfile="${dita.dir}\build.xml">
      <property name="args.input" value="C:\dita-ot\src\main\doc\userguide.ditamap"/>
      <property name="args.gen.task.lbl" value="YES"/>   
      <property name="output.dir" value="C:\temp\out"/>
      <property name="transtype" value="htmlhelp"/>
    </ant>
  </target>
  
  <target name="pdf" description="build PDF">
    <ant antfile="${dita.dir}\build.xml">
      <property name="args.input" value="C:\dita-ot\src\main\doc\userguide.ditamap"/>
      <property name="args.gen.task.lbl" value="YES"/>   
      <property name="args.rellinks" value="nofamily"/>   
      <property name="output.dir" value="C:\temp\out"/>
      <property name="transtype" value="pdf"/>
    </ant>
  </target>
    
</project>
```

In addition to the mandatory parameters \(args.input and transtype\), the chm and pdf targets each specify some optional parameters:

-   The args.gen.task.lbl property is set to YES, which ensures that headings are automatically generated for the sections of task topics.
-   The output.dir property specifies where the DITA-OT writes the output of the transformations.

The pdf target also specifies that related links should be generated in the PDF, but only those links that are created by relationship tables and <link\> elements.

Finally, the all target simply specifies that both the chm and pdf target should be run.

Another resource for learning about Ant scripts are the files in the samples/ant\_samples directory. This directory contains the Ant build files used by the demo build, as well as templates that you can use to create Ant scripts.

**Parent topic:** [Publishing DITA content from Ant](../user-guide/publishing-with-ant.md)

**Related information**  


[Building output using Ant](../user-guide/building-with-ant.md)

[Ant](../user-guide/ant.md)

[DITA-OT parameters](../parameters/parameters_intro.md)

[Apache Ant documentation](http://ant.apache.org/manual/index.html)

