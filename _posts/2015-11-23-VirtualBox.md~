---
layout: post
title: Compile the kenel of VBox
categories: Ubuntu
tags: VirtualBox

---

VirtualBox

Recently，I installed the latest version of VirtualBox by downloading the deb file from virtualbox.org
on Ubuntu 14.04,The installation goes fine,but today it reports the follow error after updating the 
sysytem.

> Kernel driver not installed (rc=-1908)

> The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

> '/etc/init.d/vboxdrv setup'

> as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Looks like some kernel driver has to be compiled for Virtualbox to run properly. But this is easy enough on Ubuntu and does not require a lot of effort. And here are the steps to do the necessary.

First install the kernel headers and build tools.

    $ sudo apt-get install build-essential module-assistant 
    $ sudo m-a prepare

And now compile virtualbox kernel driver with the commanded as reported by the error message earlier.

    $ sudo /etc/init.d/vboxdrv setup

The compilation should go fine and finish within a few minutes with an output similar to what is shown below.

    $ sudo /etc/init.d/vboxdrv setup
    Stopping VirtualBox kernel modules ...done.
    Recompiling VirtualBox kernel modules ...done.
    Starting VirtualBox kernel modules ...done.

Now run Virtualbox again and it should run fine. 
