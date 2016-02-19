# Extended functionality

**Parent topic:**[DITA Open Toolkit Developer Reference](../dev_ref/index.md)

## Code reference processing

### Charset definition

DITA-OT supports defining the code reference target file encoding using the `format` attribute. The supported format is:

```
format (";" space* "charset=" charset)?
```

If charset is not defined system default charset will be used. If charset is not recognized or supported, DOTJ052E error is thrown and system default charset is used as a fall-back.

```
<coderef href="unicode.txt" format="txt; charset=UTF-8"/>
```

### Line range extraction

Code reference can extract only a given line ranges with `line-range` pointer in the URI fragment. The format is:

```
uri ("#line-range(" start ("," end)? ")" )?
```

Start and end line numbers start from 1 and are inclusive. If end range is omitted, range ends in last line of the file.

```
<coderef href="Parser.scala#line-range(5, 10)" format="scala"/>
```

Only lines from 5 to 10 will be included in the output.

### RFC 5147

DITA-OT implements line position and range from [RFC 5147](http://tools.ietf.org/html/rfc5147). The format for line range is:

```
uri ("#line=" start? "," end? )?
```

Start and end line numbers start from 0 and are inclusive and exclusive, respectively. If the start range is omitted, range starts from the first line; if end range is omitted, range ends in last line of the file. The format for line position is:

```
uri ("#line=" position )?
```

Position line number starts from 0.

```
<coderef href="Parser.scala#line=4,10" format="scala"/>
```

Only lines from 5 to 10 will be included in the output.

