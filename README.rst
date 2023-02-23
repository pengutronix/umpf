=========================================
UMPF - Universal Magic Patch Functionator
=========================================

umpf is a tool that helps you manage git branches and combine them into a
software release. It can create tags and export the changes as a patch
stack. umpf was originally designed for the Linux kernel but it can be used
for other projects as well.

Motivation
==========

There are several reasons why commits are split into multiple branches:

* Some but not all features may be shared among multiple projects.
  Separate branches make it possible to avoid unnecessary changes to a
  specific release.

* A set of commits are developed for upstream. Keeping the commits on a
  separate branch makes further development and upstreaming easier.

* A branch may be created from a patch series collected from a mailing
  list. Keeping it separate makes it easier to update to a new version.

So working with multiple branches makes patch handling and further
development easier. But combining those branches to a release can be
tedious and error prone.

This is where umpf comes in. It automates the process of creating releases.
It creates tags in a reproducible way. And it can create patch series from
those tags.

Installation
============

umpf is a bash script, so no installation is necessary. It just needs a few
command line tools such as sed, grep and of course git.

To enable bash completion, make sure umpf is in your ``$PATH``, then::

    $ mkdir -p ~/.local/share/bash-completion/completions
    $ ln -s /path/to/umpf/bash_completion ~/.local/share/bash-completion/completions/umpf

Documentation
=============

``umpf -h`` gives a basic description of the command line arguments.
More details about umpf can be found in the documentation.

* `What is an umpf?`_
* `Getting Started`_
* `umpf from the Inside`_
* `Tips and Tricks`_

.. _`What is an umpf?`: doc/what-is-an-umpf.rst
.. _`Getting Started`: doc/getting-started.rst
.. _`Tips and Tricks`: doc/tips.rst
.. _`umpf from the Inside`: doc/inner-workings.rst

