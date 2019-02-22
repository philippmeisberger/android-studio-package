Android Studio Package
======================

[![Build Status](https://travis-ci.org/philippmeisberger/android-studio-package.svg?branch=master)](https://travis-ci.org/philippmeisberger/android-studio-package)

Utility to build Debian package from Android Studio binary distribution.

Installation
------------

There are two ways of installing Android Studio Package: Installation of the stable or latest version. The stable version is distributed through the PM Code Works APT repository and is fully tested but does not contain the latest changes.

### Installation of the stable version

Add PM Code Works repository

    `~# echo "deb http://apt.pm-codeworks.de stretch main" | tee /etc/apt/sources.list.d/pm-codeworks.list`

Add PM Code Works signing key

    ~# wget -qO - http://apt.pm-codeworks.de/pm-codeworks.de.gpg | apt-key add -
    ~# apt-get update

Install the package

    ~# apt-get install android-studio-package

### Installation of the latest version

The latest version contains the latest changes that may not have been fully tested and should therefore not be used productively. It is recommended to install the stable version.

Install required packages for building

    ~# apt-get install git devscripts

Clone this repository

    ~$ git clone https://github.com/philippmeisberger/android-studio-package.git

Build the package

    ~$ cd ./android-studio-package/
    ~$ dpkg-buildpackage -uc -us

Install the package

    ~# dpkg -i ../android-studio-package*.deb

Usage
-----

Download Android Studio IDE .zip archive file from <https://developer.android.com/studio/index.html> and execute `make-aspkg` with the downloaded file as argument. The Debian package is built in the current directory.

### Building on 32-bit Debian

To build Android Studio on a 32-bit Debian the 64-bit version of `libc6` library is required. Otherwise following error will occur `dpkg-shlibdeps: error: couldn't find library libc.so.6`. Use [Multiarch](https://wiki.debian.org/Multiarch/HOWTO) capabilities of Debian and enable installation of 64-bit packages:

    ~# dpkg --add-architecture amd64

Install 64-bit version of `libc6`

    ~# apt-get install libc6:amd64

Then building will succeed on 32-bit Debian.

Installation of Android Studio
------------------------------

If Android Studio should be installed on 64-bit Debian some 32-bit libraries are required. It is recommended to use [Multiarch](https://wiki.debian.org/Multiarch/HOWTO) capabilities of Debian and enable installation of 32-bit packages:

    ~# dpkg --add-architecture i386

Then install Android Studio

    ~# dpkg -i android-studio_*.deb

Finally install missing dependencies

    ~# apt-get install -f

Please remind that Android Studio requires at least Java 8.

Questions and suggestions
-------------------------

If you have any questions to this project just ask me via email:

<team@pm-codeworks.de>
