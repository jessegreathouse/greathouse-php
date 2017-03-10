#greathouse-php
A PHP version manager which will allow you to install, update and change between multiple versions of PHP with minimal setup

This attempts to build PHP, per individual version, into a single location on your system without spreading out the app over multiple locations on your file system.

For instance: When you install some application packages in Linux or some other Unix-like oerating system, you end up with the app putting its linked libraries is /usr/local/lib or /usr/local/share, its executables in /usr/local/bin, or /usr/bin, its configuration files in /etc, and dozens of other tendrils spreading out all over. Typically this presents a problem if you want to maintain multiple versions of the same software on the same system. 

In the case of PHP, I may need to develop several different apps, one using PHP 7.0.x, another using PHP 7.1.x , and another using PHP 5.6.x .This PHP version managing system attempts to keep multiple different versions in isolated locations to make sure it's easy to switch between different PHP versions. By default it installs PHP 7.1.2 into /usr/local/greathouse-php/7.1.2 and every sub folder required is contained within that version's root instead of spread out all over your system. You can change the key path variables with command line arguments outlide in the following section.

##Usage info

If you want to execute PHP from the command line then be sure to add the bin to your PATH variable. By default it's /usr/local/greathouse-php/bin. The easiest way to do it is to add this line to your .bash_profile.
`vim ~/.bash profile`

add the line:
* export PATH=/usr/local/greathouse-php/bin:$PATH

**install-osx**

installs a specific version of PHP

`$ install-osx [--version 7.1.2] [--prefix-root /usr/local/greathouse-php] [--config-path /etc/php7`]

* --version/-v [optional] indicates which php version to install
    * default: 7.1.2
* --prefix-root/-p [optional] complete path to where you want it to be built
    * default: /user/local/greathouse-php
    * the php version will be added as a sub directory e.g. /usr/local/greathouse-php/7.1.2
* --config-path/-c [optional] where the php.ini should be
    * default: /usr/local/greathouse-php/etc
    
**list**

Lists the currently available versions that have been installed.

`$ list [--prefix-root /usr/local/greathouse-php]`

--prefix-root/-p [optional] specific location of php installs
    * default: /user/local/greathouse-php

**use**

Specifies which version of PHP to use

`$ use [--prefix-root /usr/local/greathouse-php] --version 7.1.2`
--prefix-root/-p [optional] specific location of php install
    * default: /user/local/greathouse-php
* --version/-v [required] the specific version number to use

**unpack**

Unpacks an archive of a specific PHP source version without installing it. (Typically not needed except to inspect the contents or do manual builds.)

`$ unpack [--version 7.1.2]`
* --version/-v [required] the specific version number to download and unpack

##Supported platforms
At this point it only supports OSX (with homebrew) but can possibly support other platforms in future iterations

## How to use
Currently this is just a very simple set of bash scripts

## FAQ
* Where is Apache, NGINX, MySQL etc... ?
    * This only installs PHP. If you want an all-in-one web platform installer this is not meant for that.

* I need this and this changed, can you do it?
    * Submit a PR or fork it.

* why not use homebrew?
    * I've always found homebrew PHP packages to be too involved and difficult to switch between multiple versions. This manager simply installs PHP from source for whatever version specified and updates symlinks to the various versions on-demand.
    * If homebrew is working fine for you, then keep using it. For me, homebrew php packages have always been a hassle.
    

