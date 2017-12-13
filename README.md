# Passbolt debian package

## What is this repository?

This repository contains the required files to build a debian package of passbolt api v2.

## Requirements

Operating system:
* A debian stretch/stable at least to build the package

Packages:
* devscripts: provide tools such as debuild to compile the package
* Passbolt dependencies: php extensions required by passbolt

Source:
* passbolt_api v2 source code in a tar.gz with the following naming convention:

```passbolt_<version_number>.orig.tar.gz```

This source tarball has to contain all the composer dependencies already installed before building the package.

## How to create the debian package

Unpack the tar.gz file

```
$ tar zxvf passbolt_<version_number>.orig.tar.gz
$ cd passbolt-<version_number>
$ git clone https://bitbucket.org/passbolt/debian_package debian
$ cd debian
$ rm -rf .git # <--- we don't want the git binary files to build the package
$ mv debian/* . && rm -rf debian
$ cd ..
$ debuild -us -uc
```

This should create a .deb package on the same directory as the .orig.tar.gz is located.

## Installation

To a dependency managed install use:

```apt install ./passbolt_<version_number>-<build_number>_<architecture>.deb```

Using dpkg you will have to manage dependencies yourself:

```dpkg -i ./passbolt_<version_number>-<build_number>_<architecture>.deb```
