+++
author = "yb"
categories = ["dhcp", "network", "server", "windows"]
date = 2009-05-04T17:14:31Z
description = ""
draft = false
slug = "dhcp-scope-options-are-missing"
tags = ["dhcp", "network", "server", "windows"]
title = "DHCP服务器的作用域选项设置丢失"

+++


一台windows 2003的服务器上运行着dhcp的服务，长时间的运行一直是很正常的，在一次大厦线路维护之后就发现了作用域选项的设置全都清空了，造成了网内电脑上不上网的现象。因为网关，时间服务器，dns的地址都是在这个作用域选项李置顶的，所以手动配置上之后就都恢复正常了，但一次重启服务器的时候发现这个作用域又一次被清空了。<br /><br />经过查询微软的知识库<a href="http://support.microsoft.com/kb/930142">KB930142</a>，发现了产生这个问题的原因是因为以下两种清空之一：<br /><br /><ol><li>不正确或者不准确的保留地址，比如：192.168.1._</li><li>保留的地址和作用域的ID相同，比如作用域的ID是192.168.1.0,而恰好你的保留地址里也有这个192.168.1.0</li></ol>

<!--more-->
这些问题可能造成以下3中问题的发生：<br /><br /><ul><li>一些作用域选项丢失</li><li>租约时间变为0</li><li>客户端得不到正确的dhcp信息</li></ul><br />解决的方法也很简单，找出有问题的保留地址删除掉就可以了<br /><br /><br />

