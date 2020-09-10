+++
author = "yb"
date = 2014-09-25T21:44:52Z
description = ""
draft = false
slug = "disable-ssl-2-0-in-iis-6-and-7"
title = "Disable SSL 2.0 in IIS 6 and 7"

+++


在检测 SSL 证书的时候, 我们会看到提示说服务器开着并不安全的 SSL 2.0 协议

![SSL2.0](/content/images/2014/Sep/SSL2-0.JPG)

关闭也很简单,需要修改注册表:
`HKey_Local_Machine\System\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server` 新建一个名字为 enable 键, 然后类型是 DWord, 值是 0

或者一行批处理更改:

	reg add "HKLM\System\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0" /v Enabled /t REG_DWord /d 0

重启服务器后生效, 可在下边网站测试一下: 
https://www.ssllabs.com/ssltest/index.html

