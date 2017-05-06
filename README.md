Android Studio Package
======================

Utility to build Debian package from Android Studio binary distribution.

Installation
------------

Add PM Codeworks repository

    ~# wget http://apt.pm-codeworks.de/pm-codeworks.list -P /etc/apt/sources.d/

Add PM Codeworks key

    ~# wget -O - http://apt.pm-codeworks.de/pm-codeworks.de.gpg | apt-key add -
    ~# apt-get update

Install the package

    ~# apt-get install android-studio-package

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
