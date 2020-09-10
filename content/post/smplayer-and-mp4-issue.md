+++
author = "yb"
date = 2010-02-06T07:49:38Z
description = ""
draft = false
slug = "smplayer-and-mp4-issue"
title = "Smplaer播放mp4格式文件的问题"

+++


电脑里有几个mp4格式和3gp格式的文件，用smplayer播放的时候很不流畅，用mplayer来播放却正常，这就排除了视频驱动和vpdau的问题<br /><br />看到网上说可以尝试一下三种办法：<br /><br />1. 在smplayer的属性 - 高级设置里把 correct pts 改成 no<br /><br />2. 把 demuxer 改成mov<br /><br />3. 在属性 - 性能里把 cache for local files设置为 0 <br /><br /><a href="http://i773.photobucket.com/albums/yy16/yongbin0/Screenshot/smplayer.png" target="_blank"><img src="http://i773.photobucket.com/albums/yy16/yongbin0/Screenshot/smplayer.png" alt="smplayer" style="width: 512px;" border="0" /></a><br /><br />最终生效的是第三种办法，再把cache改成0后，Smplayer也可以流畅的播放mp4文件了<br />

