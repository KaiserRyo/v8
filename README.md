#V8

The _**v8**_ repository holds the v3.8.9 sources for the open source V8 JavaScript Engine for BlackBerry QNX based platforms.


### Prerequisites:

* Linux or Mac OS X (it may be possible to build on Windows with cygwin or MinGW)
* Python 2.6 or higher and Scons
* BlackBerry Native SDK 2.0
* bbndk-env.sh sourced into your shell


### Building:

    ./qnxbuild.sh [arm|ia32] [v8 build options]


The qnxbuild.sh script wraps calling scons and sets up the cross compilation environment, etc.
The V8 build options are passed directly to the v8 build.

To build the interactive JS shell executable that can be loaded onto a device for example, type:

    ./qnxbuild.sh arm d8

Then load the d8 binary onto the device and run it.

