# Building output using the dita command

DITA-OT includes a dita command-line tool. You can invoke the DITA-OT from the command-line tool and generate output.

1.   At the command-line prompt, enter the following command: 

    ```
    install-dir/bin/dita -i input-file -f format -Dparameter-name=value -o output-dir
    ```

    where:

    -   install-dir is the DITA-OT installation directory path.
    -   input-file is the DITA map or DITA file that you want to process.
    -   format is the output format \(transformation type\).
    -   parameter-name is the name of an optional parameter.
    -   value is an applicable value for the optional parameter.
    -   output-dir is the output directory path for generated output.
    If processing is successful, nothing is printed in the terminal window.

    If you do not specify an output directory, the dita command writes output to the out subdirectory of the current directory.

    **Tip:** If you add the absolute path for the DITA-OT install-dir/bin directory to the PATH environment variable, you can run the dita command from any location on the file system.


The following command generates HTML5 output for the sequence.ditamap file and writes the output to the test directory:

```
dita -i samples/sequence.ditamap -f html5 -o test
```

**Parent topic:** [Publishing DITA content](../user-guide/transforming-dita-content.md)

**Related information**  


[Arguments and options for the dita command](../parameters/dita-command-arguments.md)

