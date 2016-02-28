# Extending the XML Catalog

The XML Catalogs extension point is used to update the XML Catalogs used to resolve DTD or Schema document types, or to add URI mappings. This is required in order to support DITA specializations or new DITA document type shells.

To do this, first create a catalog with only your new values, using the OASIS Catalog format, and place that in your plug-in. Local file references in the catalog should be relative to the location of the catalog. The following extension points are available to work with catalogs.

 `dita.specialization.catalog.relative`
 `dita.specialization.catalog`
 :   Adds the content of the catalog file defined in `file` attribute to main DITA-OT catalog file.

    **Remember:** The `dita.specialization.catalog` extension is deprecated. Use `dita.specialization.catalog.relative` instead.

  `org.dita.pdf2.catalog.relative`
 :   Adds the content of the catalog file defined in `file` attribute to main PDF plug-in catalog file.

 ## Example

This example assumes that "catalog-dita.xml" contains an OASIS catalog for any DTDs or Schemas inside this plug-in. The catalog entries inside of catalog-dita.xml are relative to the catalog itself; when the plug-in is integrated, they will be added to the core DITA-OT catalog \(with the correct path\).

```
<plugin id="com.example.catalog">
  <feature extension="dita.specialization.catalog.relative" file="catalog-dita.xml"/>
</plugin>
```

