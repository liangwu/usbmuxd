# usbmuxd-win32

[![Build Status](https://dev.azure.com/libimobiledevice-win32/imobiledevice-net/_apis/build/status/libimobiledevice-win32.usbmuxd)](https://dev.azure.com/libimobiledevice-win32/imobiledevice-net/_build/latest?definitionId=6)

Provides a native Windows build (using the Visual C++ compiler) of [usbmuxd](http://libimobiledevice.org),
a socket daemon to multiplex connections from and to iOS devices.

> **NOTE**: This is work in progress; usbmuxd requires special USB drivers which work with libusb and are able to select a configuration which is not the default configuration. These drivers are not available yet.

## Background

usbmuxd stands for "USB multiplexing daemon". This daemon is in charge of
multiplexing connections over USB to an iOS device.

To users, it means you can sync your music, contacts, photos, etc. over USB.

To developers, it means you can connect to any listening localhost socket on the
device. usbmuxd is not used for tethering data transfer which uses a dedicated
USB interface as a virtual network device.

Multiple connections to different TCP ports can happen in parallel.
The higher-level layers are handled by libimobiledevice.

When usbmuxd is running (normally started or stopped as a result of _udev_
auto-insertion messages, or by _systemd_) it provides a socket interface in
`/var/run/usbmuxd` that is designed to be compatible with the socket interface
that is provided on macOS.

You should also create an `usbmux` user that has access to USB devices on your
system. Alternatively, just pass a different username using the `-U` argument.

The daemon also manages pairing records with iOS devices and the host in
`/var/lib/lockdown` (Linux) or `/var/db/lockdown` (macOS).

Ensure proper permissions are setup for the daemon to access the directory.

## Requirements

Development Packages of:
* libimobiledevice
* libplist
* libusb

Software:
* make
* autoheader
* automake
* autoconf
* libtool
* pkg-config
* gcc or clang
* udev (Linux only)

Optional:
* systemd (Linux only)

## Installation

To compile run:
```bash
./autogen.sh
make
sudo make install
```

The daemon is automatically started by udev or systemd depending on what you
have configured it on hotplug of an iOS device and exits if the last device
was unplugged.

For debugging purposes it is helpful to start usbmuxd using the foreground `-f`
argument and enable verbose mode `-v` to get suitable logs.

## Who/What/Where?

* Home: https://libimobiledevice.org/
* Code: `git clone https://git.libimobiledevice.org/usbmuxd.git`
* Code (Mirror): `git clone https://github.com/libimobiledevice/usbmuxd.git`
* Tickets: https://github.com/libimobiledevice/usbmuxd/issues
* Mailing List: https://lists.libimobiledevice.org/mailman/listinfo/libimobiledevice-devel
* Twitter: https://twitter.com/libimobiledev

## Credits

The initial usbmuxd daemon implementation was authored by Hector Martin.

Apple, iPhone, iPod, and iPod Touch are trademarks of Apple Inc.

usbmuxd is an independent software application and has not been
authorized, sponsored, or otherwise approved by Apple Inc.

README Updated on: 2020-06-08

For general questions about usbmuxd, see http://github.com/libimobiledevice/usbmuxd.
For questions specific to Visual C++, feel free to use the GitHub issue tracker

## How to get the latest binaries

The binaries for usbmuxd are added as an artifact to each Azure Pipeline build. Check the status of the [latest build](https://dev.azure.com/libimobiledevice-win32/imobiledevice-net/_apis/build/status/libimobiledevice-win32.usbmuxd) and download the .zip file.

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

## Consulting, Training and Support


This repository is maintained by [Quamotion](http://quamotion.mobi). Quamotion develops test software for iOS and

Android applications, based on the WebDriver protocol.



Quamotion offers various technologies related to automating iOS devices using

computers running Windows or Linux.

This includes:

* The ability to remotely control iOS devices

* Extensions to libimobiledevice with support for the Instruments protocol

* Running Xcode UI Tests and Facebook WebDriverAgent tests



In certain  cases, Quamotion also offers professional services - such as consulting, training and support - related

to imobiledivice-net and libimobiledevice.



Contact us at [info@quamotion.mobi](mailto:info@quamotion.mobi) for more information.