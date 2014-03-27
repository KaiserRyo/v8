#V8

QNX is now an officially supported platform in the V8 project on the trunk branch. We now recommend using the upstream project.

The **v8-3.8.9-qnx** branch holds the previous v3.8.9 sources for QNX and is still available in this repository.


### Getting the Code and Dependencies

 Follow the instructions at https://code.google.com/p/v8/wiki/BuildingWithGYP to get the code and install the dependences. After doing this, please follow the QNX and cross-compilation instructions below.


### Prerequisites

* Linux
* Python 2.6 or higher
* BlackBerry NDK or QNX SDP


### Patching GYP

The GYP build tool needs to be patched to work with the QNX toolchain. Please download and apply the **qnx-gyp.patch** patch above in this repository in the root of your GYP installation directory:

    cd $V8_DIR/build/gyp
    patch -p0 -i qnx-gyp.patch


### Building For QNX ARM

    export CXX="${QNX_HOST}/usr/bin/qcc -Vgcc_ntoarmv7le_cpp-ne"
    export LINK="${QNX_HOST}/usr/bin/qcc -Vgcc_ntoarmv7le_cpp-ne"
    export HOST_OS=`uname -s | sed -e 's/Linux/linux/;s/Darwin/mac/'`
    export GYP_DEFINES="OS=qnx host_os=${HOST_OS} target_arch=arm v8_target_arch=arm arm_version=7 arm_neon=1"
    make arm.release -j16

To test, you can then load the d8 binary onto the device and run it.

