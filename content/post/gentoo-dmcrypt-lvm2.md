+++
author = "yb"
date = 2010-01-14T10:34:50Z
description = ""
draft = false
slug = "gentoo-dmcrypt-lvm2"
title = "安装Gentoo到基于dm-crypt加密的LVM分区"

+++


最近对数据的安全性有了兴趣，正好也想试试LVM2(logical volume manager逻辑卷管理), 就想着在硬盘划出来个分区，用dm-crypt加密这个分区，然后用LVM2管理这个分区划分几个逻辑分区：/，/home，swap，<br /><br />最终的硬盘分区<br />/sda1&nbsp;&nbsp;&nbsp; 100 MB&nbsp;&nbsp;&nbsp;&nbsp; /boot<br />/sda2&nbsp;&nbsp;&nbsp; 10 GB&nbsp;&nbsp;&nbsp; # For Windows<br />/sda3&nbsp;&nbsp;&nbsp; 剩下所有空间用dm-crypt加密然后创建逻辑卷供Gentoo使用<br /><br />首先是检查kernel，把Device mapper support和Crypt target support还有相应的编译进内核（为了方便没有编译成模块)，然后备份好Gentoo和相应的数据，用liveCD启动重新划分分区<br />

<!--more-->
1. 创建一个加密的分区，需要提供一个passphrase<br /><blockquote># cryptsetup -c aes-xts-plain -y -s 512 luksFormat /dev/sda3<br /></blockquote>&nbsp;2. 挂载该分区, 会提示你输入刚才你创建的passphrase<br /><blockquote># cryptsetup luksOpen /dev/sda3 gentoo<br /></blockquote>3. 用LVM2管理/dev/mapper/gentoo，并划分pv，vg，lv<br /><blockquote>#pvcreate /dev/mapper/gentoo<br />#vgcreate gentoo /dev/mapper/gentoo<br />#lvcreate -L 10G -n root gentoo<br />#lvcreate -L 2G -n swap gentoo<br />#lvcreate -L 30G -n home gentoo<br /></blockquote>4.生成initramfs文件，<br />4.1创建一个如下层次的目录<br /><blockquote>mkdir initram
<br />cd initram<br />mkdir bin dev dev/mapper dev/vc etc newroot proc sys<br /></blockquote>4.2复制如下的命令，并创建一些需要的链接<br /><blockquote>cp /bin/busybox /sbin/cryptsetup /sbin/lvm.static /sbin/mdadm bin
<br />mv bin/lvm.static bin/lvm
<br />ln -s busybox bin/cat
<br />ln -s busybox bin/mount <br />ln -s busybox bin/sh
<br />ln -s busybox bin/switch_root <br />n -s busybox bin/umount
<br />ln -s busybox bin/sleep
<br />ln -s lvm bin/vgscan
<br />ln -s lvm bin/vgchange<br /></blockquote>4.3复制相应的device<br /><blockquote>cp -a /dev/console /dev/sda3 /dev/sda3 /dev/null /dev/urandom dev
<br />cp -a /dev/mapper/gentoo-root dev/mapper
<br />ln -s ../console dev/vc/0<br /></blockquote>4.4创建init脚本<br /><br /><blockquote>&nbsp;#!/bin/sh<br />mount -t proc proc /proc<br />CMDLINE=`cat /proc/cmdline`<br />mount -t sysfs sysfs /sys<br />#wait a little to avoid trailing kernel output<br />sleep 3<br />#dm-crypt<br />/bin/cryptsetup luksOpen /dev/sda3 gentoo <br />#lvm<br />/bin/vgchange -ay gentoo<br />#root filesystem<br />mount -r /dev/mapper/gentoo-root /newroot<br />#unmount pseudo FS<br />umount /sys<br />umount /proc<br />#root switch<br />exec /bin/busybox switch_root /newroot /sbin/init ${CMDLINE}<br /></blockquote><br />4.5执行如下命令来生成initramfs文件<br /><blockquote>chmod a+x initrd<br />find . | cpio --quiet -o -H newc | gzip -9 &gt; /boot/initramfs<br /><br /></blockquote>4.6修改如grub.conf，添加initrd条目<br /><blockquote>title Gentoo Linux AMD64<br />root (hd0,0)<br />kernel /boot/kernel video=uvesafb:1440x900-32,mtrr:3,ywrap splash=silent,fadein,theme:livecd-2007.0 console=tty1<br />initrd /boot/initramfs<br /></blockquote>以上参考了Gentoo Wiki里的<a href="http://en.gentoo-wiki.com/wiki/Root_filesystem_over_LVM2,_DM-Crypt_and_RAID#Hierarchy">Root filesystem over LVM2, DM-Crypt and RAID<br /><br /></a>5.格式化并挂载lvm2创建的pv<br /><blockquote>mount /dev/mapper/gentoo-root&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /mnt/gentoo<br />mount /dev/mapper/gentoo-home&nbsp;&nbsp;&nbsp; /mnt/gentoo/home<br /></blockquote><br />6. 恢复之前备份的Gentoo到/mnt/gentoo<br /><blockquote>tar zvjfp gentoo.tar.bz2 -C /mnt/gentoo<br /></blockquote><br />7. 修改/mnt/etc/fstab文件，更改相应的device为lvm2创建的pv<br /><br />重新启动电脑，没有问题的话会在引导kernel的时候提示你输入/devsda3的加密passphrase，如果正确就会像正常引导系统可以正常使用了，使用了dm-crypt加密之后可以保护电脑或者硬盘丢失后的数据安全(不能保证系统启动后的数据安全) <br />

