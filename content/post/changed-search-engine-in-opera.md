+++
author = "yb"
categories = ["google", "opera", "search", "搜索"]
date = 2009-12-09T18:21:47Z
description = ""
draft = false
slug = "changed-search-engine-in-opera"
tags = ["google", "opera", "search", "搜索"]
title = "更改Opera的搜索引擎为google.com"

+++


机器上的Opera为英文版，虽然不常用，但还是发现它的默认搜索是google.cn，遂改之。只需要添加一个hl=en就可以让google变为英文界面的<br><br>打开Tools - Preferences - Search 选择google 然后 Edit - Details，最终的搜索字符串为：<br><br>http://www.google.com/search?hl=en&amp;q=%s&amp;sourceid=opera&amp;num=%i&amp;ie=utf-8&amp;oe=utf-8<br>

