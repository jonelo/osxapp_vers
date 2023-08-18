osxapp_vers
===========

What the project is for
-----------------------
The script called osxapp_vers finds the product name, the complete product version, and build version in an `Install*OS X*.app` package, in an `Install macOS*.app` package or in a mounted CD/DVD image called `Mac OS X Install *` and prints the info out like the macOS' `/usr/bin/sw_vers` does for an installed macOS product.

The idea for this has been described at [my blog](https://loefflmann.blogspot.de/2015/03/finding-os-x-version-and-build-in-install-os-x-app.html).


What are the system requirements
--------------------------------
* At least Mac OS X 10.6.8 (Snow Leopard) in order to run the bash script, older releases haven't been tested.


What are the input requirements
-------------------------------
* `Install macOS Ventura.app`, `Install macOS Monterey.app`, `Install macOS Big Sur.app`, `Install macOS Catalina.app`, `Install macOS Mojave.app`, `Install macOS High Sierra.app`, `Install macOS Sierra.app`, `Install OS X El Capitan.app`, `Install OS X Yosemite.app`, `Install OS X Mavericks.app`, `Install OS X Mountain Lion.app`, or `Install Mac OS X Lion.app` from the Apple App Store (1st public version or any update release) or on a bootable macOS install media that has been created by Apple's `createinstallmedia`
* Alternatively, a mounted Mac OS X Install CD/DVD image such as `Mac OS X Install DVD`, `Mac OS X Install CD` or `Mac OS X Install Disk`

See also "How to create a bootable installer for macOS?" at https://support.apple.com/en-us/HT201372


How to configure and install it
-------------------------------
Download the osxapp_vers file from GitHub to a folder of your choice.

```bash
% curl -Ls https://bit.ly/osxapp_vers > osxapp_vers
```

Set execute permissions.

```bash
% chmod +x ./osxapp_vers
```

In order to bypass a check that prevents the script from investigating an unknown macOS release, you can set the NOCHECK environment variable.

```bash
% export NOCHECK=1
```

In order to see details from the mount actions and additional messages, you can enable debug output by exporting the DEBUG environment variable. Usually there is no need to do that.

```bash
% export DEBUG=/dev/stdout
```
 
If you want to disable debug mode, enter

```bash
% export DEBUG=
```


How to run it without installing it
-----------------------------------
```
% curl -Ls https://bit.ly/osxapp_vers | bash
```


Examples of how to use it or get it running
-------------------------------------------
By default, if you don't specify any program parameters, the script reads all `Install*OS X*.app`, and `Install macOS X*.app` known to Spotlight and all `/Volumes/Mac OS X Install *` and prints out product name, product version and build version for each macOS that those installers are loaded with.

Example output from runs without any program parameters:

```bash
/Volumes/Mac OS X Install DVD:
ProductName:    Mac OS X
ProductVersion: 10.5
BuildVersion:   9A581

/Applications/Install Mac OS X Lion.app:
ProductName:    Mac OS X
ProductVersion: 10.7.5
BuildVersion:   11G63

/Applications/Install OS X Mountain Lion.app:
ProductName:    Mac OS X
ProductVersion: 10.8.5
BuildVersion:   12F45

/Applications/Install OS X Mavericks.app:
ProductName:    Mac OS X
ProductVersion: 10.9.4
BuildVersion:   13E28

/Applications/Install OS X Yosemite.app:
ProductName:    Mac OS X
ProductVersion: 10.10.2
BuildVersion:   14C109

/Applications/Install OS X El Capitan.app:
ProductName:    Mac OS X
ProductVersion:	10.11.5
BuildVersion:   15F34

/Applications/Install macOS Sierra.app:
ProductName:    Mac OS X
ProductVersion:	10.12
BuildVersion:   16A323

/Applications/Install macOS High Sierra.app:
ProductName:	Mac OS X
ProductVersion:	10.13
BuildVersion:	17A365

/Applications/Install macOS Mojave.app:
ProductName:	Mac OS X
ProductVersion:	10.14
BuildVersion:	18A391

/Applications/Install macOS Catalina.app:
ProductName:	Mac OS X
ProductVersion:	10.15
BuildVersion:	19A583

/Applications/Install macOS Big Sur.app:
ProductName:	macOS
ProductVersion:	11.1
BuildVersion:	20C69

/Applications/Install macOS Monterey.app:
ProductName:	macOS
ProductVersion:	12.0.1
BuildVersion:	21A559

/Applications/Install macOS Ventura.app:
ProductName:	macOS
ProductVersion:	13.0
BuildVersion:	22A380
```

If you specify program parameters, the script prints out product name, product version and build version for each Install OS X .app folder that you have specified.

```bash
% ./osxapp_vers '/Applications/Install OS X Mavericks.app'

/Applications/Install OS X Mavericks.app:
ProductName:    Mac OS X
ProductVersion: 10.9.4
BuildVersion:   13E28
```

If you have created a bootable macOS install media with `createinstallmedia` (that command line tool is provided by Apple as part of the OS X installer starting with Mavericks), you could also find out the version of macOS version that is on the install media by specifying the path to the .app folder.

```bash
% ./osxapp_vers '/Volumes/Install OS X Mavericks/Install OS X Mavericks.app/'

/Volumes/Install OS X Mavericks/Install OS X Mavericks.app/:
ProductName:    Mac OS X
ProductVersion: 10.9.2
BuildVersion:   13C64
```


The license
-----------
The license that the project is offered under is the [Apache 2.0 license](http://choosealicense.com/licenses/apache-2.0/).


References
----------
* https://loefflmann.blogspot.de/2015/03/finding-os-x-version-and-build-in-install-os-x-app.html
