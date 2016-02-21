# Eclipse Help parameters

Certain parameters are specific to the Eclipse help transformation.

args.eclipse.provider
:   Specifies the name of the person or organization that provides the Eclipse help.

:   The default value is DITA.

    **Tip:** The toolkit ignores the value of this parameter when it processes an Eclipse map.

args.eclipse.symbolic.name
:   Specifies the symbolic name \(aka plugin ID\) in the output for an Eclipse Help project.

:   The @id value from the DITA map or the Eclipse map collection \(Eclipse help specialization\) is the symbolic name for the plugin in Eclipse. The default value is org.sample.help.doc.

    **Tip:** The toolkit ignores the value of this parameter when it processes an Eclipse map.

args.eclipse.version
:   Specifies the version number to include in the output.

:   The default value is 0.0.0.

    **Tip:** The toolkit ignores the value of this parameter when it processes an Eclipse map.

args.eclipsehelp.country
:   Specifies the region for the language that is specified by the args.

:   For example, us, ca, and gb would clarify a value of en set for the args.eclipsehelp.language parameter. The content will be moved into the appropriate directory structure for an Eclipse fragment.

args.eclipsehelp.language
:   Specifies the base language for translated content, such as en for English.

:   This parameter is a prerequisite for the args.eclipsehelp.country parameter. The content will be moved into the appropriate directory structure for an Eclipse fragment.

args.eclipsehelp.toc
:   Specifies the name of the TOC file.

**Parent topic:** [DITA-OT parameters](../parameters/parameters_intro.md)

**Related information**  


[Eclipse help transformation](../user-guide/dita2eclipsehelp.md)

[Common parameters](../parameters/parameters-base.md)

[HTML-based output parameters](../parameters/parameters-base-html.md)

