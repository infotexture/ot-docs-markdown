# Version and support information

The following extension points are used by convention to define version and support info within a plug-in.

-   `package.support.name`
-   `package.support.email`
-   `package.version`

**Note:** The toolkit does not currently do anything with these values, but may do so in the future.

The `package.version` value should follow the syntax rules:

```
version   ::= major ( '.' minor ( '.' micro ( '.' qualifier )? )? )?

major     ::= number
minor     ::= number
micro     ::= number
qualifier ::= ( [0..9] | [a..zA..Z] | ’_’ | '-' )+
```

The default value is `0.0.0`.

## Example

```
<plugin id="com.example.WithSupportInfo">
  <feature extension="package.support.name" value="Joe the Author"/>
  <feature extension="package.support.email" value="joe@example.com"/>
  <feature extension="package.version" value="1.2.3"/>
</plugin>
```

**Parent topic:** [Creating plug-ins](../dev_ref/plugins-overview.md)

