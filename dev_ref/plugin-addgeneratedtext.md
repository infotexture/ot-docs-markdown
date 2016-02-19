# Modifying or adding generated text

Generated text is the term for strings that are automatically added by the build, such as "Note" before the contents of a <note\> element.

The generated text extension point is used to add new strings to the default set of generated text. There are several reasons you may want to use this:

-   It can be used to add new text for your own processing extensions; for example, it could be used to add localized versions of the string "User response" to aid in rendering troubleshooting information.
-   It can be used to override the default strings in the toolkit; for example, it could be used to reset the English string "Figure" to "Fig".
-   It can be used to add support for new languages \(for non-PDF transforms only; PDF requires more complicated localization support\). For example, it could be used to add support for Vietnamese or Gaelic; it could also be used to support a new variant of a previously supported language, such as Australian English.

`dita.xsl.strings`
:   Add new strings to generated text file.

## Example: adding new strings

First copy the file xsl/common/strings.xml to your plug-in, and edit it to contain the languages that you are providing translations for \("en-US" must be present\). For this sample, copy the file into your plug-in as xsl/my-new-strings.xml. The new strings file will look something like this:

```
<?xml version="1.0" encoding="utf-8"?>
<!-- Provide strings for my plug-in; this plug-in supports
     English, Icelandic, and Russian. -->
<langlist>
  <lang xml:lang="en"     filename="mystring-en-us.xml"/>
  <lang xml:lang="en-US"  filename="mystring-en-us.xml"/>
  <lang xml:lang="is"     filename="mystring-is-is.xml"/>
  <lang xml:lang="is-IS"  filename="mystring-is-is.xml"/>
  <lang xml:lang="ru"     filename="mystring-ru-ru.xml"/>
  <lang xml:lang="ru-RU"  filename="mystring-ru-ru.xml"/>
</langlist>
```

Next, copy the file xsl/common/strings-en-us.xml to your plug-in, and replace the content with your own strings \(be sure to give them unique name attributes\). Do the same for each language that you are providing a translation for. For example, the file mystring-en-us.xml might contain:

```
<?xml version="1.0" encoding="utf-8"?>
<strings xml:lang="en-US">
  <str name="String1">English generated text</str>
  <str name="Another String">Another String in English</str>
</strings>
```

Use the following extension code to include your strings in the set of generated text:

```
<plugin id="com.example.strings">
  <feature extension="dita.xsl.strings" file="xsl/my-new-strings.xml"/>
</plugin>
```

The string is now available to the "getString" template used in many DITA-OT XSLT files. For example, if processing in a context where the xml:lang value is "en-US", the following call would return "Another String in English":

```
<xsl:call-template name="getString">
  <xsl:with-param name="stringName" select="'Another String'"/>
</xsl:call-template>

```

**Note:** If two plug-ins define the same string, the results will be non-deterministic, so multiple plug-ins should not try to create the same generated text string. One common way to avoid this problem is to ensure the name attributes used to look up the string value are related to the ID or purpose of your plug-in.

## Example: modifying existing strings

The process for modifying existing generated text is exactly the same as for adding new text, except that the strings you provide override values that already exist. To begin, set up the xsl/my-new-strings.xml file in your plug-in as in the previous example.

Next, copy the file xsl/common/strings-en-us.xml to your plug-in, and choose the strings you wish to change \(be sure to leave the name attribute unchanged, because this is the key used to look up the string\). Create a strings file for each language that needs to modify existing strings. For example, the new file mystring-en-us.xml might contain:

```
<?xml version="1.0" encoding="utf-8"?>
<strings xml:lang="en-US">
  <str name="Figure">Fig</str>
  <str name="Draft comment">ADDRESS THIS DRAFT COMMENT</str>
</strings>
```

To integrate the new strings, use the same method as above to add these strings to your plugin.xml file. Once this plug-in is integrated, where XHTML output previously generated the term "Figure", it will now generate "Fig"; where it previously generated "Draft comment", it will now generate "ADDRESS THIS DRAFT COMMENT". The same strings in other languages will not be modified unless you also provide new versions for those languages.

**Note:** If two plug-ins override the same string in the same language, the results will be non-deterministic \(either string may be used under different conditions\). Multiple plug-ins should not override the same generated text string for a single language.

## Example: adding a new language

The process for adding a new language is exactly the same as for adding new text, except you are effectively just translating an existing strings file. To begin, set up the xsl/my-new-strings.xml file in your plug-in as in the previous examples. In this case, the only difference is that you are adding a mapping to new languages; for example, the following file would be used to set up support for Vietnamese:

```
<?xml version="1.0" encoding="utf-8"?>
<!-- Map languages with xml:lang="vi" or xml:lang="vi-vn"
     to the translations in this plug-in. -->
<langlist>
  <lang xml:lang="vi"     filename="strings-vi.xml"/>
  <lang xml:lang="vi-VN"  filename="strings-vi.xml"/>
</langlist>
```

Next, copy the file xsl/common/strings-en-us.xml to your plug-in, and rename it to match the language you wish to add. For example, to support Vietnamese strings you may want to pick a name like strings-vi.xml. In that file, change the `xml:lang` attribute on the root element to match your new language.

Once the file is ready, translate the contents of each `<str>` element \(be sure to leave the name attribute unchanged\). Repeat this process for each new language you wish to add.

To integrate the new languages, use the same method as above to add these strings to your plugin.xml file. Once this plug-in is integrated, non-PDF builds will include support for Vietnamese; instead of generating the English word "Caution", the element `<note type="caution" xml:lang="vi">` may generate something like "chú ý".

**Note:** If two plug-ins add support for the same language using different values, the results will be non-deterministic \(translations from either plug-in may be picked up under different conditions\).

**Parent topic:**[Creating plug-ins](../dev_ref/plugins-overview.md)

**Related information**  


[Languages supported by the core toolkit](../user-guide/DITA-globalization-xhtml.md)

[Globalizing DITA content](../user-guide/DITA-globalization.md)

