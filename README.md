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

## How to create the debian package

Unpack the tar.gz file

```
$ tar zxvf passbolt_<version_number>.orig.tar.gz
$ cd passbolt-<version_number>
$ git clone https://bitbucket.org/passbolt/debian_package .
$ rm -rf .git # <--- we don't want the git binary files to build the package
$ debuild -us -uc
```

This should create a .deb package on the same directory as the .orig.tar.gz is located.

## Installation

```apt install ./passbolt_<version_number>-<build_number>_<architecture>.deb```

Or:

```dpkg -i ./passbolt_<version_number>-<build_number>_<architecture>.deb```
