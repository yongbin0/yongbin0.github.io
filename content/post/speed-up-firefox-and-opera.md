+++
author = "yb"
categories = ["firefox", "gentoo", "linux", "opera", "tempfs"]
date = 2009-12-04T16:48:46Z
description = ""
draft = false
slug = "speed-up-firefox-and-opera"
tags = ["firefox", "gentoo", "linux", "opera", "tempfs"]
title = "加速你的Firefox和Opera浏览器"

+++


在使用glibc 2.2或者更高的Linux系统上，相信你也该看到你的系统挂在了/dev/shm，这是tempfs（虚拟内存文档系统），使用内存的一部分容量在开机时自动挂载，因为是存储到内存里，所有这里的数据访问速度飞快，并且关机或者重启的时候不会保存其数据，所以非常适合作为缓存（不可放置个人文件），这里我们可以把浏览器的缓存放到这个虚拟内存里加快浏览速度<br /><br />1. Firefox<br /><br /><blockquote>打开一页面在地址栏输入<b>about:config</b>,然后在页面上鼠标邮件<b> New</b> - <b>String</b>，新填如下两行内容<i>browser.cache.disk.parent_directory</i>和 <i>browser.cache.offline.parent_directory</i>，在紧接着的Value里都输入<i> /dev/shm/ff-cache </i>(ff-cache可随意)，设置完之后重启firefox即生效，也可以从about:cache页面看到是否生效。<br /></blockquote>2. Opera<br /><br /><blockquote>打开一空白页面输入<b>opera:config</b>, 然后在 User Prefs 里找到 <b>Cache Directory4</b>, 把这行内容改成 <i>/dev/shm/opera-cache</i>,重启opera即生效<br /></blockquote>

