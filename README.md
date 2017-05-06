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

Installation of Android Studio
------------------------------

If Android Studio should be installed on 64-bit Debian some 32-bit libraries are required. It is recommended to use [Multiarch](https://wiki.debian.org/Multiarch/HOWTO) capabilities of Debian:

    ~# dpkg --add-architecture i386

This will enable installation of 32-bit packages. Then install Android Studio:

    ~# dpkg -i android-studio_*.deb

Install missing dependencies

    ~# apt-get install -f

Please remind that Android Studio requires at least Java 8.

Questions and suggestions
-------------------------

If you have any questions to this project just ask me via email:

<team@pm-codeworks.de>
