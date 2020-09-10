+++
author = "yb"
date = 2015-07-16T23:49:43Z
description = ""
draft = false
slug = "a-windows-firewall-problem-on-win8"
title = "Windows Firewall启动问题"

+++


一台电脑在重启完之后就再也无法通过远程桌面连上了, 这台机器没有接显示器键盘鼠标, 平常只能远程登录上去.只能接上显示器看一下, 登录之后发现电脑访问外网正常, 只是局域网内的机器不能访问它, ping也不通. Widows自带的防火墙也没法启动, 系统日志里有如下报错"

> 
Event ID: 7024
Source: Service Control Manager
Message: 
The Windows Firewall service terminated with the following service-specific error: 
Access is denied.

这应该是跟防火墙相关的权限出问题了
解决方法:

* 一种是手动修改注册表
打开注册表, 找到一下四个键, 然后给 **NT Service\MpsSVC** 这个用户加上完全控制权限
HKLM\SYSTEM\CurrentControlSet\Services\SharedAccess\Defaults\FirewallPolicy
HKLM\CurrentControlSet\Services\SharedAccess\Epoch
HKLM\SYSTEM\CurrentControlSet\Services\SharedAccess\Epoch2
HKLM\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy”

* 或者用批处理操作:
SUBINACL需要从[微软网站下载.](http://www.microsoft.com/en-au/download/details.aspx?id=23510)
`SUBINACL /verbose=1 /keyreg “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Defaults\FirewallPolicy” /grant=”NT Service\MpsSvc”=QSCEYDA
SUBINACL /verbose=1 /keyreg “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Epoch” /grant=”NT Service\MpsSvc”=QS
SUBINACL /verbose=1 /keyreg “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Epoch2″ /grant=”NT Service\MpsSvc”=QS
SUBINACL /verbose=1 /keyreg “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy” /grant=”NT Service\MpsSvc”=QSCEYDA`

