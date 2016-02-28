# Resolve keyref \(keyref\)

The `keyref` step examines all the keys that are defined in the DITA source and resolves the key references. Links that make use of keys are updated so that any @href value is replaced by the appropriate target; key-based text replacement is also performed, and the key definition list file is written to the temporary directory. This step is implemented in Java.

**Parent topic:** [Pre-processing modules](../dev_ref/DITA-OTPreprocess.md)

**Previous topic:** [Copy related files \(copy-files\)](../dev_ref/preprocess-copyfiles.md)

**Next topic:** [Conref push \(conrefpush\)](../dev_ref/preprocess-conrefpush.md)

