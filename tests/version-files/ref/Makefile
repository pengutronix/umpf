# SPDX-License-Identifier: GPL-2.0
VERSION = 6
PATCHLEVEL = 7
SUBLEVEL = 0
EXTRAVERSION = -rc5-20221209-2
NAME = Hurr durr I'ma ninja sloth

# Read KERNELRELEASE from include/config/kernel.release (if it exists)
KERNELRELEASE = $(call read-file, include/config/kernel.release)
KERNELVERSION = $(VERSION)$(if $(PATCHLEVEL),.$(PATCHLEVEL)$(if $(SUBLEVEL),.$(SUBLEVEL)))$(EXTRAVERSION)
export VERSION PATCHLEVEL SUBLEVEL KERNELRELEASE KERNELVERSION
