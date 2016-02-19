# Managing plug-in dependencies

The `<require>` element in a plugin.xml file is used to create a dependency on another plug-in. The `<require>` element requires the `plugin` attribute in order to reference the dependency.

If the current plug-in requires a plug-in with `id="plugin-id"` before it can be installed, it would include the following:

```
<require plugin="*plugin-id*">
```

Prerequisite plug-ins are integrated before the current plug-in is integrated. This does the right thing with respect to XSLT overrides. If your plug-in is a specialization of a specialization, it should `<require>` its base plug-ins, in order from general to specific.

If a prerequisite plug-in is missing, a warning will be printed during integration. To suppress this, but keep the integration order if both plug-ins are present, add `importance="optional"` to the `<require>` element.

If your plug-in can depend on any one of several optional plug-ins, separate the plug-in ids with a vertical bar. This is most useful when combined with importance="optional":

## Example

The following plug-in will only be installed if the plug-in with id="com.example.primary" is available. If that one is not available, a warning will be generated during the integration process.

```
<plugin id="com.example.builds-on-primary">
  <!-- ...extensions here -->
  <require plugin="com.example.primary"/>
</plugin>
```

The following plug-in will only be installed if either the plug-in with id="pluginA" or the plug-in with id="pluginB" are available. If neither of those are installed, the current plug-in will be ignored.

```
<plugin id="pluginC">
  <!-- ...extensions here -->
  <require plugin="pluginA|pluginB" importance="optional"/>
</plugin>
```

**Parent topic:**[Creating plug-ins](../dev_ref/plugins-overview.md)

