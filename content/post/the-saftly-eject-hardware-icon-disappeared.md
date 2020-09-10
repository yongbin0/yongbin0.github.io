+++
author = "yb"
categories = ["windows", "xp"]
date = 2009-04-30T19:20:54Z
description = ""
draft = false
slug = "the-saftly-eject-hardware-icon-disappeared"
tags = ["windows", "xp"]
title = "Win XP下安全删除硬件的图标消失"

+++


使用完移动硬盘或者u盘的时候，结果发现在右下角找不到安全删除硬件的小图标了，直接硬拔的话又怕损坏设备，其解决方法很简单<br /><br />&nbsp;&nbsp; 1. 命令行或者运行里执行命令<b> regsvr32 stobject.dll</b><br />&nbsp;&nbsp; <br />&nbsp;&nbsp; 2. 重启计算机或者强行重启explore.exe进程即可<br />

