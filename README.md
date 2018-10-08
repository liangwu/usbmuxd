# usbmuxd-win32

[![Build Status](https://dev.azure.com/libimobiledevice-win32/imobiledevice-net/_apis/build/status/libimobiledevice-win32.usbmuxd)](https://dev.azure.com/libimobiledevice-win32/imobiledevice-net/_build/latest?definitionId=6)

Provides native Windows, Linux and macOS builds (using the Visual C++ compiler) of [usbmuxd](http://libimobiledevice.org).

> **NOTE**: This is work in progress; usbmuxd requires special USB drivers which work with libusb and are able to select a configuration which is not the default configuration. These drivers are not available yet.

## Where to report issues

For general questions about usbmuxd, see http://github.com/libimobiledevice/usbmuxd.
For questions specific to Visual C++, feel free to use the GitHub issue tracker

## How to get the latest binaries

The binaries for usbmuxd are added as an artifact to each AppVeyor build. Check the status of the [latest build](https://ci.appveyor.com/project/qmfrederik/usbmuxd/branch/master-msvc) and download the .zip file.

On Windows, you'll need to install the following dependencies:
* [Microsoft Visual C++ Redistributable Packages for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
* [Microsoft Visual C++ Redistributable Packages for Visual Studio 2012 Update 4](http://www.microsoft.com/en-us/download/details.aspx?id=30679)

## Building on Windows
You can open `usbmuxd.sln` in Visual Studio and restore the packages and build from there, or from the commandline:
```
nuget restore
msbuild usbmuxd.sln
```

## Building on Ubuntu
Compatibility with Linux is important, so here's how you can build on Ubuntu 16.04.

Make sure you've built and installed `libplist` and `libusbmuxd` first.

```
apt-get install libusb-1.0-0 libusb-1.0-0-dev
./autogen.sh
make
sudo make install
```
