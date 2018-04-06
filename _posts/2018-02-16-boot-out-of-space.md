---
title: Boot out of space
date: '2018-02-16 14:11:44 -0700'
tags: linux
---

/boot is out of space. uh oh.

## Error: filesystem mounted at /boot has no free disk space

From [AskUbuntu](https://askubuntu.com/a/259092):
```bash
$ dpkg -l linux-{image,headers}-"[0-9]*" | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e '[0-9]' | xargs sudo apt-get -y purge
```

### If the above returns errors:

From [help.ubuntu.com](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels):

Get currently unning kernel:
```bash
$ uname -r
4.4.0-104-generic
```

List all kernels, including the current:
```bash
$ dpkg -l linux-image-\* | grep ^ii

ii  linux-image-4.4.0-101-generic       4.4.0-101.124 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-103-generic       4.4.0-103.126 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-104-generic       4.4.0-104.127 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-109-generic       4.4.0-109.132 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-112-generic       4.4.0-112.135 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic        4.4.0-96.119  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic        4.4.0-97.120  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-98-generic        4.4.0-98.121  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-101-generic 4.4.0-101.124 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-103-generic 4.4.0-103.126 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-104-generic 4.4.0-104.127 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic  4.4.0-96.119  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic  4.4.0-97.120  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-98-generic  4.4.0-98.121  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
```

To free space in /boot, remove an initrd.img for an _old_ kernel manually:
```
$ sudo update-initramfs -d -k 4.2.0-98-generic
```

Now go back to the top command and try again.
