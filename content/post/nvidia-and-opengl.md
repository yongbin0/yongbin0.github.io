+++
author = "yb"
categories = ["gentoo", "nvidia", "opengl"]
date = 2009-12-30T14:31:25Z
description = ""
draft = false
slug = "nvidia-and-opengl"
tags = ["gentoo", "nvidia", "opengl"]
title = "Nvidia的opengl加速"

+++


不知从什么时候起，Gentoo里的opengl只能工作在xorg-x11，没有nvidia的opengl 3D加速了，glxgears只能到400FPS，如果eselect opengl set xorg-x11的话glxgears报错 Fatal: glXCreateContext failed，起先还以为是nvidia的驱动升级的原因，后来发现是设置上的问题造成的<br /><br />1. 添加以下两行到<i>/etc/X11/xorg.conf</i>的<i>Section "Files"</i>里<br /><br /><blockquote>&nbsp;&nbsp;&nbsp; ModulePath&nbsp;&nbsp; "/usr/lib64/xorg/modules/extensions/nvidia"<br />&nbsp;&nbsp;&nbsp; ModulePath&nbsp;&nbsp; "/usr/lib64/xorg/modules"<br /></blockquote>2. 选择nvidia的#D加速<br /><br /><blockquote>&nbsp;$sudo eselect opengl set nvidia<br /></blockquote>然后重启X，可以看到已经用上nvidia的opengl加速了，glxgears已经上到5000左右了<br />

