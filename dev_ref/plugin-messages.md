# Adding diagnostic messages

Plug-in specific warning and error messages can be added to the set of messages supplied by the DITA-OT. These messages can then be used by any XSLT override.

 `dita.xsl.messages`
 :   Add new messages to diagnostic message file.

 ## Example

To add your own messages, create the new messages in an XML file such as myMessages.xml:

```
<dummy>
  <!-- See resources/messages.xml for the details. -->
  <message id="DOTXmy-msg-numW" type="WARN">
    <reason>Message text</reason>
    <response>How to resolve</response>
  </message>
</dummy>
```

There are three components to the message ID:

1.  The prefix DOTX is used by all DITA-OT XSLT transforms, and must be part of the ID.
2.  This is followed by the message number \("my-msg-num" in the sample above\). By convention, this should be a three digit integer.
3.  Finally, a letter corresponds to the severity. This should be one of:
    -   I = Informational, used with type="INFO"
    -   W = Warning, used with type="WARN"
    -   E = Error, used with type="ERROR"
    -   F = Fatal, used with type="FATAL"

Once the message file is defined, it is incorporated with this extension:

```
<plugin id="com.example.newmsg">
  <feature extension="dita.xsl.messages" file="myMessages.xml"/>
</plugin>
```

XSLT modules can then generate the message using the following call:

```
<xsl:call-template name="output-message">
  <xsl:with-param name="msgnum">my-msg-num</xsl:with-param>
  <xsl:with-param name="msgsev">W</xsl:with-param>
</xsl:call-template>

```

