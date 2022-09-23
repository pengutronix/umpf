What is an umpf?
----------------

This is *umpf*, the Universal Magic Patch Functionator.

The term *umpf* is not only used for the tool itself, but also for the resulting artefacts
built by this tool:
An *umpf* is basically a git branch merged from different topic branches.
It can come in different forms for different use cases, which are described below.
An umpf can be fully qualified, which means that umpf has all information needed to
convert it to any other form of umpf,
but some forms of umpfs are not fully qualified.

umerge
~~~~~~

A *umerge* is a git branch containing merges from topic branches.
Generally every merged tree can be a *umerge*, but umpf needs additional information to make
a merged tree a fully qualified umpf.
For this reason it is recommended to use ``umpf merge`` rather than ``git merge`` to built
a *umerge*.

utag
~~~~

A *utag* is a git tag with multiple parents.
The range ``origin/master..utag^1`` contains a linear branch of all topic branches,
whereas ``origin/master..tag^n`` contains the (n-1)th topic branch.
A *utag* by definition is a fully qualified umpf, and it is the highest form
of an umpf, as it not only contains the topic branches but also a linear
branch which can be easily transformed into a *useries*.

useries
~~~~~~~

A *useries* is a stack of patch files together with a series file.
The series file is a regular series file which contains additional
information for umpf, which can be used to reconstruct the corresponding
*umerge* in git.
*useries* are usually used in BSPs and not in the daily developers workflow.
