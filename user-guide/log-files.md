# Log files

When you run the DITA-OT, key information is logged on the screen. This information can also be written to a log file. If you encounter a problem, you can analyze this information to determine the source of the problem and then take action to resolve it.

The logging behavior varies depending on whether you use the dita command, DITA-OT command-line tool, or Ant to invoke a toolkit build.

 dita command
 :   By default, only warning and error messages are written to the screen. If you use the -v option, logging will be more verbose and informative messages are also written out. The -l option can be used to write the log messages into a file.

  Ant
 :   By default, status information is written to the screen. If you issue the -l parameter, the build runs silently and the information is written to a log file with the name and location that you specified. \(You also can use other Ant loggers; see the Ant documentation for more information.\)

 **Parent topic:** [Error messages and troubleshooting](../user-guide/troubleshooting-overview.md)

