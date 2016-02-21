# Creating Change Bars

The PDF2 transform can generate change \(revision\) bars with XSL-FO engines that support the fo:change-bar formatting object.

**Note:**

As of July 2015 the Antenna House Formatter and RenderX XEP FO engines support change bar generation but FOP 1.1 does not.

You can request revision bars in your PDF output by using the @changebar attribute of the DITAVAL <revprop\> element. The DITA specification for @changebar simply says:

> @changebar
:   > When flag has been set, specify a changebar color, style, or character, according to the changebar support of the target output format. If flag has not been set, this attribute is ignored.

The PDF2 syntax for @changebar is a sequence of semicolon-delimited name/value pairs:

```
<revprop action="flag" val="rev01"
 **changebar="color:black;style:solid;width:0.5pt"**
/>
```

Each name/value corresponds to an attribute of the [XSL-FO fo:change-bar-begin element](http://www.w3.org/TR/xsl/#fo_change-bar-begin). The available attributes and values are:

style
:   The style to use for the line, as for other XSL-FO rules \([@change-bar-style](http://www.w3.org/TR/xsl/#change-bar-style)\). The value "solid" produces a solid rule. The default is "none".

color
:   Any color value recognized by XSL-FO, including the usual color names or a hex color value. The default is "black".

offset
:   The space as a measurement value \(e.g., points \(pt\) or millimeters \(mm\)\) to offset the bar from the edge of the text column.

placement
:   The side of the text column on which to place the change bar, one of "start" \(left side for left-to-right languages\) or "end" \(right side for left-to-right languages\). The default is "start".

width
:   The width of the rule as a measurement value. Typical values are "1pt" and "0.5pt" \(hairline rule\).

To get a rule at all you must specify a value for style, e.g. "style:solid" and should specify a value for width so you get an appropriately-sized rule, e.g., "width:0.5pt".

Note that XSL-FO 1.1 does not provide for revision "bars" that are not rules, so there is no standard way to get text revision indicators instead of rules, e.g. using a number in place of a rule. Antenna House Formatter does provide a proprietary extension to allow this but the PDF2 transform does not take advantage of it.

**Parent topic:** [DITA to PDF \(PDF2\)](../user-guide/dita2pdf.md)

