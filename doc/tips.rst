Tips and Tricks
===============

How do I…

Let umpf prompt for the remote for every single branch
------------------------------------------------------

Call ``umpf --remote=foo`` where ``foo`` is a remote that does not exist.
This way you can test if some local branch leads to merge conflicts when
umpfed without needing to force-push it to a remote.
Of course, this should only be done to test an umpf run, and should **not**
be the default case – your coworkers will be confused when they try to
reproduce an umpf!

Use ``--identical`` only for specific branches (but use tip-of-head for others)
-------------------------------------------------------------------------------

By default, ``--identical`` will always use the hashinfo for all branches.
This can be overridden case by case with the ``--override`` option.
For example, to use the local state of only the ``v4.19/topic/imx-poweroff``
branch, but use ``acme`` remote for everything else::

  umpf --identical --remote acme --override v4.19/topic/imx-poweroff build series

In cases, where the local branch is named differently, this can be made
explicit::

  umpf --identical --remote acme --override \
    v4.19/topic/imx-poweroff=v4.19/topic/poweroff-rework build series

Normally, this state is needed for future umpfs and thus ``--override`` should
be a temporary measure until the remote branches are updated and future
umpfs yield the same result without ``--override``.

If the topic branches are shared between different project and a branch needs
to be stabilized, a separate branch in the ``vX.Y/customers/`` namespace can
be created pointing at the desired commit.
This can then be referred to in the *useries* file or with ``umpf merge``.
Example (with ``umpf-topic: v4.19/customers/foobar/topic/imx-poweroff``)::

  $ git log --oneline --decorate ${base}^..origin/v4.19/topic/imx-poweroff
  * f845a5df665c (origin/v4.19/topic/imx-poweroff) ARM: dts: imx6: RIoTboard provide standby on power off option
  * 21f8a3c69a05 (origin/v4.19/customers/foobar/topic/imx-poweroff) regulator: pfuze100-regulator: provide pm_power_off_prepare handler
  * 76b9fc78a7b1 regulator: pfuze100: add fsl,pmic-stby-poweroff property
  * b2686f99abc5 kernel/reboot.c: export pm_power_off_prepare
  * ba0390a910e7 ARM: imx6q: provide documentation for new fsl,pmic-stby-poweroff property
  * c63ee2939dc1 (tag: v4.19.85) Linux 4.19.85

This way renewed umpfs are independent of future updates of the
``v4.19/topic/imx-poweroff`` topic branch.

Create branches based on other branches
---------------------------------------

Sometimes it is necessary to separate changes from an existing branch into
specfific bits for a single project. These changes should not be applied to all
projects, but are necessary changes for this project to work. Additionally they
are usually based on previous changes from another branch.

To ensure that ``umpf tag`` is able to resolve the branch dependencies, the
required base branch needs to be merged in via ``umpf merge`` to ensure that the
merge commit contains the correct ``umpf-merge-topic`` line. This way umpf can
rebase your branch correctly during a tag operation.
