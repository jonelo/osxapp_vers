osxapp_vers
===========

What the project is for
-----------------------
The script called osxapp\_vers finds the complete product version and build version of OS X in an `Install*OS X*.app` package and prints it out like the OS X's /usr/bin/sw_vers does for a installed OS X product.

The idea for this has been described at [my blog](http://loefflmann.blogspot.de/2015/03/finding-os-x-version-and-build-in-install-os-x-app.html).

What are the system requirements
--------------------------------
* At least Mac OS X 10.6.8 (Snow Leopard) in order to run the script
* `Install Mac OS X Lion.app`,  `Install OS X Mountain Lion.app`, `Install OS X Mavericks.app`, `Install OS X Yosemite.app` or `Install OS X El Capitan.app` from the Apple App Store (1st public version or any update release)

How to configure and install it
-------------------------------
Download the osxapp_vers file from github to a folder of your choice and set execute permissions.

```bash
$ chmod +x ./osxapp_vers
```

In order to see details from the mount actions, you can enable debug output by exporting the DEBUG environment variable. Usually there is no need to do that.

```bash
$ export DEBUG=/dev/stdout
```

An example of how to use it or get it running
---------------------------------------------
By default, if you don't specify any program parameters, the script reads all `/Applications/Install*OS X*.app` and prints out both product version and build version for each OS X that the installer is loaded with.

```bash
$ ./osxapp_vers

/Applications/Install Mac OS X Lion.app:
ProductVersion: 10.7.5
BuildVersion:   11G63

/Applications/Install OS X Mavericks.app:
ProductVersion: 10.9.4
BuildVersion:   13E28

/Applications/Install OS X Mountain Lion.app:
ProductVersion: 10.8.5
BuildVersion:   12F45

/Applications/Install OS X Yosemite.app:
ProductVersion: 10.10.2
BuildVersion:   14C109
```

If you specify program parameters, the script prints out both product version and build version for each Install OS X .app folder that you have specified.

```bash
$ ./osxapp_vers '/Applications/Install OS X Mavericks.app'

/Applications/Install OS X Mavericks.app:
ProductVersion: 10.9.4
BuildVersion:   13E28
```

The license
-----------
The license that the project is offered under is the [Apache 2.0 license](http://choosealicense.com/licenses/apache-2.0/).

References
----------
* http://loefflmann.blogspot.de/2015/03/finding-os-x-version-and-build-in-install-os-x-app.html
