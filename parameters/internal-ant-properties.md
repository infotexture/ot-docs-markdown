# Internal Ant properties

Reference list of Ant properties used by DITA-OT internally.

`include.rellinks`
:   A space-separated list of link roles to be output; the `#default` value token represents links without an explicit role \(those for which no `@role` attribute is defined\). Defined by `args.rellinks`, but may be overridden directly. Valid roles include:

    -   parent
    -   child
    -   sibling
    -   friend
    -   next
    -   previous
    -   cousin
    -   ancestor
    -   descendant
    -   sample
    -   external
    -   other

**Parent topic:**[DITA Open Toolkit Parameter Reference](../parameters/index.md)

