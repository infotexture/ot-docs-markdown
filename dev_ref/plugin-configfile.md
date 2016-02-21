# Plug-in configuration file

The plugin.xml file controls all aspects of a plug-in, making each extension visible to the rest of the toolkit. The file uses pre-defined extension points to locate changes, and integrates those changes into the core code.

The root element of the plugin.xml file is `<plugin>`, and must specify an `id` attribute. The `id` attribute is used to identify the plug-in, as well as to identify whether pre-requisite plug-ins are available. The `id` attribute should follow the syntax rules:

```
id    ::= token('.'token)*
token ::= ( [0..9] | [a..zA..Z] | ’_’ | ’-’ )+
```

The `<plugin>` element supports the following child elements:

-   The `<feature>` element defines an *extension* to contribute to a defined *extension point*. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`extension`**|extension point identifier|yes|
    |**`value`**|comma separated string value of the extension|either `value` or `file`|
    |**`file`**|file path value of the extension, relative to plugin.xml|either `value` or `file`|
    |**`type`**|type of the `value` attribute|no|

-   The `<extension-point>` element defines new a *extension point* that can be used by other plug-ins. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`id`**|extension point identifier|yes|
    |**`name`**|extension point description|no|

-   The `<require>` element defines plug-in dependencies. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`plugin`**|vertical bar separated list of plug-ins that are required|yes|
    |**`importance`**|flag whether plug-in is required or optional|no|

-   The `<template>` element defines files that should be treated as *templates*. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`file`**|file path to the template, relative to plugin.xml|yes|

-   The `<meta>` element defines metadata. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`type`**|metadata name|yes|
    |**`value`**|metadata value|yes|

-   The `<transtype>` element defines an output format \(transformation type\). The following attributes are supported for transformations:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`name`**|transformation name|yes|
    |**`desc`**|description|no|
    |**`abstract`**|defines an abstract transformation type that cannot be used directly|no|
    |**`extends`**|specifies the name of the transformation type being extended|no|

    The `<transtype>` element may define additional parameters for the transformation type using `<param>` child elements. The following parameter attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`name`**|parameter name|yes|
    |**`desc`**|description|no|
    |**`type`**|parameter type \(enum, file, string\)|yes|

    Enumeration parameters \(`<param>` elements of type enum\) define enumeration values with `<val>` child elements. The following attributes are supported:

    |Attribute|Description|Required|
    |---------|-----------|--------|
    |**`default`**|defines an enumeration value as the default value \(default="true"\)|yes|


Any extension that is not recognized by the DITA-OT is ignored; all elements other than `<plugin>` are optional. Since version 1.5.3 multiple extension definitions within a plug-in configuration file are combined; in older versions only the last extension definition is used.

**Parent topic:** [Creating plug-ins](../dev_ref/plugins-overview.md)

**Related information**  


[Integrating a new transformation type](../dev_ref/plugin-newtranstype.md)

[Example plugin.xml file](../dev_ref/plugin-sample.md)

