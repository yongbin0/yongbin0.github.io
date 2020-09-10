+++
author = "yb"
categories = ["linux", "p2p", "stream", "tv", "tvuplayer", "video", "vlc"]
date = 2009-12-02T09:14:54Z
description = ""
draft = false
slug = "use-tvuplayer-in-windows"
tags = ["linux", "p2p", "stream", "tv", "tvuplayer", "video", "vlc"]
title = "介绍一个windows上的电视播放器 TVUPlayer"

+++


TVUPlayer是一个基于P2P技术的网络电视播放器，可以运行在Windows和Mac上，通过互联网观看电视节目，有很多国内和国外的频道。同时，它在播放的同时也会在本地产生一个视频流，这样在局域网里你就可以在其他的电脑上连接这个网络视频流达到观看电视，比如你可以在Linux的电脑或者智能手机上通过VLC来同时观看这一个频道的电视节目<br /><br />vlc访问http视频流的命令：<br />&nbsp;$ vlc http://x.x.x.x:8901&nbsp; (8901是TVUPlayer产生视频流的端口号)<br />或者通过窗口菜单 File - open network，然后选择http协议，输入IP地址和端口号就可以播放了。<br />

