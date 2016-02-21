# Adding Ant targets to the pre-process pipeline

Every step in the pre-process pipeline defines an extension point before and after the step, to allow plug-ins to integrate additional processing. This allows a plug-in to insert a new step before any pre-processing step, as well as before or after the entire preprocess pipeline.

The group of preprocessing steps defines extension points before and after the full preprocessing chain.

`depend.preprocess.pre`
:   Preprocessing pre-target; extending this target runs your Ant target before the full preprocess routine begins.

`depend.preprocess.post`
:   Preprocessing post-target; extending this target runs your Ant target after the full preprocess routine completes.

In addition, there are extension points to execute an Ant target before individual preprocessing steps.

`depend.preprocess.clean-temp.pre`
:   Clean temp pre-target

`depend.preprocess.gen-list.pre`
:   Generate list pre-target

`depend.preprocess.debug-filter.pre`
:   Debug and filter pre-target

`depend.preprocess.conrefpush.pre`
:   Content reference push pre-target

`depend.preprocess.move-meta-entries.pre`
:   Move meta entries pre-target

`depend.preprocess.conref.pre`
:   Content reference pre-target

`depend.preprocess.coderef.pre`
:   Code reference pre-target

`depend.preprocess.mapref.pre`
:   Map reference pre-target

`depend.preprocess.keyref.pre`
:   Resolve key reference pre-target

`depend.preprocess.mappull.pre`
:   Map pull pre-target

`depend.preprocess.chunk.pre`
:   Chunking pre-target

`depend.preprocess.maplink.pre`
:   Map link pre-target

`depend.preprocess.topicpull.pre`
:   Topic pull pre-target

`depend.preprocess.copy-files.pre`
:   Copy files pre-target

`depend.preprocess.copy-image.pre`
:   Copy images pre-target

`depend.preprocess.copy-html.pre`
:   Copy HTML pre-target

`depend.preprocess.copy-flag.pre`
:   Copy flag pre-target

`depend.preprocess.copy-subsidiary.pre`
:   Copy subsidiary pre-target

`depend.preprocess.copy-generated-files.pre`
:   Copy generated files pre-target

## Example

The following feature adds "myAntTargetBeforeChunk" Ant target to be executed before the chunk step in preprocessing. It assumes that an Ant file defining that target has already been integrated.

```
<plugin id="com.example.extendchunk">
  <feature extension="depend.preprocess.chunk.pre" value="myAntTargetBeforeChunk"/>
</plugin>
```

When integrated, the Ant target "myAntTargetBeforeChunk" will be added to the Ant dependency list so that it always runs immediately before the Chunk step.

**Parent topic:** [Creating plug-ins](../dev_ref/plugins-overview.md)

