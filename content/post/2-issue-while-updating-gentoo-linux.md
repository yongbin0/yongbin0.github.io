+++
author = "yb"
date = 2010-02-21T08:21:57Z
description = ""
draft = false
slug = "2-issue-while-updating-gentoo-linux"
title = "升级系统的两个小问题"

+++


攒了些日子没有更新系统了，这次在emerge -uDN world的过程中碰到了两个问题，特此记录一下<br /><br />1. <br />问题描述: dev-util/intltool-0.41.0 编译的时候报错<br />   报错信息: Configure fails with message "XML::Parser perl module is required for intltool"<br />   解决方法: emerge XML-Parser<br /><br />2. <br />问题描述: sys-apps/help2man-1.37.1 编译报错<br />   报错信息: configure: error: perl module Locale::gettext required<br />   解决方法: emerge USE="-nss" help2man (标准做法当然是修改/etc/portage/package.use)<br /><br />

