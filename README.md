COMDIRAC
========

Package to supply a comprehensive list of UNIX-like commands for the DIRAC user interface

Provided commands can serve several purposes:

User Client Configuration
=========================

Users can customize their client behaviour. The configuration file lies in $HOME/.dirac/dcommands.conf

This file is a ConfigParser formatted file (see: http://docs.python.org/2/library/configparser.html).

Here is a sample configuration file:
################
# dcommands.conf
################

# global client configuration (mainly default profile)
[global]
default_profile = frangrilles_user

# frangrilles_user profile
[frangrilles_user]
# DIRAC group name for this profile
group_name = frangrilles_user
# Home directory
home_dir = /vo.france-grilles.fr/user/p/pgay
# default destination for commanddput
default_se = M3PEC-disk
# default options for command drepl
replication_scheme = all()
replication_ses = LAL-disk,CPPM-disk,MSFG-disk

# other profile
[dirac_user]
home_dir = /
group_name = dirac_user

################
# end of dcommands.conf
################

It contains a [global] section and some named profile sections. Profiles sections are used by "dinit" command to configure session with some user profile.

commands:
* dconfig - get and set configuration options from configuration file

Session Environment Commands
============================

COMDIRAC sessions are built from a user profile (see User client configuration).

Sessions are used by all commands to remember client state (think of shell environment variables)

Each session is applicable to the Unix process calling the COMDIRAC command.

commands:
* dinit - initialize a session from a profile (with proxy creation)
* dgetenv - get session environment options
* dsetenv - set session environment options
* dunsetenv - delete session environment options

File Catalog Files And Directories
==================================

commands:
* dpwd - print File Catalog working directory
* dcd - change File Catalog working directory
* dls - list File Catalog files and directories
* dreplicas - liste File Catalog file replicas
* dmkdir - create File Catalog directory
* drmdir - delete File Catalog directory


Data Management
===============

commands:
* dput - register local file in the File Catalog (and copies replica to a Storage Element)
* dget - retrieves a local copy of a File Catalog file
* drepl - replicates a File Catalog file
* dchmod - change access rights of a File Catalog file

File Catalog Metadata Management
================================

commands:
* dmeta - manipulates File Catalog metadata
* dfind - find files with File Catalog metadata
