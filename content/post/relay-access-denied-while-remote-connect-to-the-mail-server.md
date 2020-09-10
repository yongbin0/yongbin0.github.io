+++
author = "yb"
categories = ["cisco", "firewall", "mail", "network", "pix", "smtp"]
date = 2009-05-03T19:32:56Z
description = ""
draft = false
slug = "relay-access-denied-while-remote-connect-to-the-mail-server"
tags = ["cisco", "firewall", "mail", "network", "pix", "smtp"]
title = "relay access denied while remote connect to the mail server"

+++


一台内网的邮件服务器(postfix)已经启用了mysql用户认证，内网收发正常，网关是Cisco PIX 501，发布到外网之后，webmail正常，只是在使用邮件客户端发邮件的时候发信失败，错误信息是Relay access denied.。在mail server和firewall检查了日志之后，发现是PIX的mailguard功能对esmtp的通讯进行了保护，所以禁用这个功能就好了<p><br /></p>
<p>登录Cisco PiX的config模式然后<br /></p>&nbsp;<b>
<code>no fixup protocol smtp 25</code></b><br /><p></p><p><br /></p><p>关于mailguard的更多信息:</p><p><a href="http://www.cisco.com/en/US/products/hw/vpndevc/ps2030/products_tech_note09186a00800b2ecb.shtml">http://www.cisco.com/en/US/products/hw/vpndevc/ps2030/products_tech_note09186a00800b2ecb.shtml</a></p><p><a href="http://support.microsoft.com/?scid=kb%3Ben-us%3B320027&amp;x=17&amp;y=9">http://support.microsoft.com/?scid=kb%3Ben-us%3B320027&amp;x=17&amp;y=9</a><br /><b></b></p>

