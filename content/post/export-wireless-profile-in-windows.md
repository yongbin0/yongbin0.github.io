+++
author = "yb"
categories = ["network", "windows", "wireless", "无线"]
date = 2009-09-07T18:51:39Z
description = ""
draft = false
slug = "export-wireless-profile-in-windows"
tags = ["network", "windows", "wireless", "无线"]
title = "windows系统里导出无线网络的配置"

+++


在要重装系统或者要换一台电脑的时候，我们应该都会希望新电脑或者新的系统的设置跟以前一样，不需要再一个个设置的去调整以适应自己的习惯。桌面设置，拨号连接，显示DPI，快速启动栏，IE的收藏夹以及设置等等我们可以通过"windows文件和设置转移向导"来完成，很遗憾它不能转移无线网络的配置。<br /><br />如果你的电脑里有若干网线网络的配置文件，而恰好你又想不起来密码或者你不希望再一个个的输入SSID选择认证类型来添加这些网络，这时候我们可以在命令行下试试netsh这个命令。<br /><br />显示当前系统所有的无线配置文件：<br />&nbsp; netsh wlan show profiles<br />

<!--more-->
导出某个配置文件到c盘，文件名将会是"Wireless Network Connection-<i>profilename</i>.xml"<br />&nbsp; netsh wlan export profile name="yb-home" folder=C:\"<br /><br />导出所有配置文件<br />&nbsp; netsh wlan export profile folder=C:\<br /><br />导入无线网络的配置文件到系统里<br />&nbsp; netsh wlan add profile filename="c:\Wireless Network Connection-<i>profilename</i>.xml" user=all"

