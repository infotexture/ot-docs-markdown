# Creating plug-ins

The DITA Open Toolkit comes with a built in mechanism for adding in extensions through plug-ins. These plug-ins may do a wide variety of things, such as adding support for specialized DITA DTDs or Schemas, integrating processing overrides, or even providing entirely new output transforms. Plug-ins are the best way to extend the toolkit in a way that is consistent, easily sharable, and easy to preserve through toolkit upgrades.

A plug-in consists of a directory, typically stored directly within the plugins/ directory inside of the DITA-OT. Every plug-in is controlled by a file named plugin.xml, located in the plug-in's root directory.

Benefits of extending the toolkit through plug-ins include:

-   Plug-ins are easily sharable with other users, teams, or companies; typically, all that is needed is to unzip and run a single integration step. With many builds, even that integration step is automatic.
-   Allows overrides or customizations to grow from simple to complex over time, with no increased complexity to the extension mechanism.
-   Plug-ins can be moved from version to version with an upgraded toolkit simply by unzipping again, or by copying the directory from one install to another; there is no need to re-integrate code based on updates to the core processing.
-   Plug-ins can build upon each other. If you like a plug-in provided by one user, simply install that plug-in, and then create your own that builds on that extension. The two plug-ins can then be distributed to your team as a unit, or you can even share your own extensions with the original provider.

