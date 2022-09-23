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

Currently, ``--identical`` will always use the hashinfo for all branches.

Workround 1: reset all local topic branches that are included in the umpf to their
desired commit, then let umpf prompt for the remote for every single branch
(see above), and select the local branch.

Workaround 2: If the same state is needed on future umpfs (e.g. with stable workflows),
create a separate branch in the ``vX.Y/customers/`` namespace on the desired commit,
which you can then refer to in your *useries* file or with ``umpf merge``.
Example (with ``umpf-topic: v4.19/customers/foobar/topic/imx-poweroff``)::

  $ git log --oneline --decorate ${base}^..origin/v4.19/topic/imx-poweroff
  * f845a5df665c (origin/v4.19/topic/imx-poweroff) ARM: dts: imx6: RIoTboard provide standby on power off option
  * 21f8a3c69a05 (origin/v4.19/customers/foobar/topic/imx-poweroff) regulator: pfuze100-regulator: provide pm_power_off_prepare handler
  * 76b9fc78a7b1 regulator: pfuze100: add fsl,pmic-stby-poweroff property
  * b2686f99abc5 kernel/reboot.c: export pm_power_off_prepare
  * ba0390a910e7 ARM: imx6q: provide documentation for new fsl,pmic-stby-poweroff property
  * c63ee2939dc1 (tag: v4.19.85) Linux 4.19.85

This way you are independent of future updates of the
``v4.19/topic/imx-poweroff`` topic branch.
