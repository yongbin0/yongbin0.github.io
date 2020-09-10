+++
author = "yb"
categories = ["mpalyer", "nvidia"]
date = 2010-01-09T15:23:18Z
description = ""
draft = false
slug = "vdpau_in_nvidia-drivers-19053"
tags = ["mpalyer", "nvidia"]
title = "vdpau in nvidia-drivers-190.53"

+++


<font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2"></font></font><font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2">nvidia-drivers升级到190.53后，发现mplayer在使用vdpau作为视频驱动的时候播放视频报错"</font></font><font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2">Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared</font></font><font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2"> object file: No such file or directory</font></font>"<br><br>google了一番发现是nvidia-drivers190.53，libvdpau-0.3中把<font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2">libvdpau_nvidia.so从原来位置/usr/lib64/给挪到了/usr/lib64/vdpau/中<br><br>直接解决方法就是做个链接<br>$ sudo ln -s /usr/lib64/</font></font><font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2">vdpau/libvdpau_nvidia.so /usr/lib64/</font></font><br><font color="black" face="Verdana,Arial,Helvetica" size="2"><font color="black" face="Verdana,Arial,Helvetica" size="2"><br>更多细节：<a class="" title="" target="" href="http://www.nvnews.net/vbulletin/showthread.php?p=2156911#post2156911">http://www.nvnews.net/vbulletin/showthread.php?p=2156911#post2156911</a><br></font></font>

