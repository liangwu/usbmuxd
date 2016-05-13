# usbmuxd-win32

[![Build status](https://ci.appveyor.com/api/projects/status/dka6taye67ww57vf/branch/master-msvc?svg=true)](https://ci.appveyor.com/project/qmfrederik/usbmuxd/branch/master-msvc)
[![Build Status](https://travis-ci.org/libimobiledevice-win32/usbmuxd.svg?branch=master-msvc)](https://travis-ci.org/libimobiledevice-win32/usbmuxd)

Provides a native Windows build (using the Visual C++ compiler) of [usbmuxd](http://libimobiledevice.org).

> **NOTE**: This is work in progress; usbmuxd requires special USB drivers which work with libusb and are able to select a configuration which is not the default configuration. These drivers are not available yet.


## Where to report issues



For general questions about usbmuxd, see http://github.com/libimobiledevice/usbmuxd.
For questions specific to Visual C++, feel free to use the GitHub issue tracker



## How to get the latest binaries



The binaries for usbmuxd are added as an artifact to each AppVeyor build. Check the status of the [latest build](https://ci.appveyor.com/project/qmfrederik/usbmuxd/branch/master-msvc) and download the .zip file.
