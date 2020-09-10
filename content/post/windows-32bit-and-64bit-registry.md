+++
author = "yb"
date = 2014-06-25T16:08:00Z
description = ""
draft = false
slug = "windows-32bit-and-64bit-registry"
title = "Windows 32bit and 64bit Registry"

+++


在测试之前某个程序往从32位(Windows Server 2003)向64位(Windows Server 2008 R2)迁移过程中， 需要导入一个这册表， 其中需要注意的是64位系统中32位程序p配置是存在
`HKLM\Software\WOW6432Node`

微软为了让32位程序不做任何修改就能运行在64的操作系统上，添加了一个十分重要的WOW64子系统来实现这个功能，WOW64是Windows-32-on-Windows-64的简称。为了防止注册表键冲突，64位机器注册表信息分成了两个部分。一部分是专门给64位系统（即：64位程序）访问的，另一部分是专门给32位系统（即：32位程序）访问的，放在Wow6432Node下面。

* 本机模式64位程序运行在纯模式下，并且访问键和存储在以下注册表子键中的值：HKLM\Software

* 32位程序运行在 WOW64 模式下，并且访问键和值存储在以下注册表子项中：HKLM\Software\WOW6432Node

Windows 64 bit 版本中的 registry也有32和64位之分

* C:\Windows\regedit.exe #可以查看32位和64位注册表，32位节点在HKLM\Software\WOW6432Node

* C:\Windows\SysWOW64\regedit.exe #查看32位注册表

