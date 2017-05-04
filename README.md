Android Studio Package
======================

Android Studio Package builds a Debian package from Android Studio binary distribution.

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

First you have to download the Android Studio IDE .zip file from <https://developer.android.com/studio/index.html> and execute `make-aspkg` with the downloaded file as argument. The Debian package is built in the current directory.

Questions and suggestions
-------------------------

If you have any questions to this project just ask me via email:

<team@pm-codeworks.de>
