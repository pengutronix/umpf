umpf from the Inside
====================

Series commands
---------------

The following commands are parsed from a ``useries`` file, or the commit
message of a *utag*:

umpf-base: <rev>
  Specifies ``<rev>`` as the base of the umpf, equivalent to the ``--base``
  command line argument.

  Must be the first command in *useries* or *utag*.

umpf-name: <name>
  Specifies ``<name>`` as the name of the umpf, equivalent to the ``--name``
  command line argument.

umpf-version: <version>
   The version of the *utag*. It is created from the umpf-name, the date and
   a version number (1 or explicitly set with the ``-v`` command line
   argument).

umpf-topic: <topic>
   A branch that will be added to the umpf.

umpf-squash-topic: <topic>
   Similar to umpf-topic but all commits in this branch will be squashed
   into a single commit in a *utag*.

umpf-hashinfo: <rev>
  Following an *umpf-topic* or *umpf-squash-topic* command, ``<rev>`` specifies
  the commit to which that topic branch pointed when the umpf was created.

umpf-topic-range: <rev1>..<rev2>
   The rebased commits of the branch in a *utag*. This will be used to create
   patches.

umpf-release: <version>
   The version is the same as in umpf-version. For supported projects, this
   will be followed by an umpf-topic-range that contains a single commit.
   It patches the project version to include the version of this *utag*.

umpf-end
  Must be the last command in *useries* or *utag*.


The following commands are parsed from the commit messages of a *umerge*:

umpf-merge-topic: <name>
   An indicator which branch was merged here. It allows umpf to find the
   correct branch when creating a *utag* (or a new *umerge*) from an existing
   *umerge*.

umpf-squash-topic
   An indicator that umpf-squash-topic should be used for this branch
   instead of umpf-topic.

umpf-build-note: <base> <name>
   Used to remember the base commit and umpf name in a *umerge*.

