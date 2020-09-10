+++
author = "yb"
date = 2015-08-13T19:11:31Z
description = ""
draft = false
slug = "exe-file-execute-problem-in-win8"
title = "exe执行文件打开问题"

+++


操作系统是Windows 8.1, 双击任何exe文件都弹出以下选择文件打开方式的对话框:

![](/content/images/2015/08/open_exe.PNG)

解决方法也很简单, 找到`C:\Windows\regedit.exe`,然后右键用管理员运行, 就可以打开注册表了, 找到`HKEY_CLASSES_ROOT\exefile\shell\open\command`,然后看一下default的值, 把它g改成 **"%1" %***

![](/content/images/2015/08/exefile-problem.PNG)

