+++
author = "yb"
categories = ["browser", "firefox", "opera"]
date = 2009-04-21T21:43:10Z
description = ""
draft = false
slug = "firefox"
tags = ["browser", "firefox", "opera"]
title = "Firefox里的翻页浏览建失效"

+++


最近这几天发现在Firefox里翻页键和Home,End键都失效了, 刚开始还以为跟最近换的evdev驱动或者HAL有关,
后来发现在其他程序OpenOffice和Opera里正常, google了一下,原来是一个叫做Caret Browsing的功能给启用了,
Caret Browsing启用之后会使光标在网页里就像在word里一样,嵌入在文字之间。关闭这个功能可以按F7,或者Edit - Preferences - advanced - general: 关掉Always use the
cursor keys to navigate within the pages即可.<br /><br />  <br />要看Mozilla知识库里关于Caret Browsing的文档，请<a href="http://kb.mozillazine.org/Scrolling_with_arrow_keys_no_longer_works">转向...</a><br />

