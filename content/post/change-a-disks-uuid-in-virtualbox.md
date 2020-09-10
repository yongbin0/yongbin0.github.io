+++
author = "yb"
date = 2014-09-25T22:05:54Z
description = ""
draft = false
slug = "change-a-disks-uuid-in-virtualbox"
title = "Change a disk's UUID in VirtualBox"

+++


在把之前的备份VBox的磁盘镜像文件挂到一台信的机器上的启动虚拟机的时候会提示磁盘的uuid不对而无法启动. 可以是由VirtualBox的内部命令金星修改, 其中61ea0339-8c0e-4807-9e39-5d28d410695b是新建虚拟机里的磁盘UUID
  

 	cd "c:\Program Files\Oracle\VirtualBox"
	 VBoxManage.exe internalcommands sethduuid E:\WinXP\WinXP.vdi 61ea0339-8c0e-4807-9e39-5d28d410695b

