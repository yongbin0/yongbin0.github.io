+++
author = "yb"
date = 2010-01-16T19:33:47Z
description = ""
draft = false
slug = "mail-notify-in-movabletype"
title = "Movable Type邮件提醒中文乱码的问题"

+++


切换到MT 5之后，发现评论发送的邮件提醒中文显示乱码，解决方法是修改mt-config.cgi文件，添加如下一行即可<br /><br /><blockquote>MailEncoding utf-8<br /></blockquote>

