+++
author = "yb"
categories = ["450d", "cannon", "dc", "firmware"]
date = 2009-11-20T20:17:08Z
description = ""
draft = false
slug = "updated-the-firmware-for-450d"
tags = ["450d", "cannon", "dc", "firmware"]
title = "升级450D的firmware"

+++


闲来无事，网上逛游的时候看到450D的固件已经到1.1.0，增加了新款闪光灯Speedlite&nbsp;270EX的自动对焦辅助光功能。<br />之前一个版本1.0.9也有3个改进：<br /><blockquote><ol><li>在AEB（自动包围曝光）模式下，修正写入存储卡的第三张照片会出现不能写入结束的情况</li><li>
修正了实时取景的一个曝光模拟警告的不正确显示问题</li><li>
修正了连接打印机和其他终端的时候，连续拍摄不能回放照片的问题</li></ol></blockquote>再一看我的机器还是出厂的1.0.4，那就开始升级吧<br /><br />

<!--more-->
Canon只提供了Windows和MAC的两种格式的固件软件包，没有linux格式的。经我验证最终的软件包里的fir文件的md5值，完全可以下载windows的这个，然后在linux上解压缩这个exe文件，就会得到最后要拷贝到sd卡里的fir文件，然后就可以网站上的提示来操作了。<br /><br />下面大概写下刷新过程：<br /><ol><ol><li>从Cannon官方网站下载最新的windows格式firmware的软件包，<a href="http://web.canon.jp/imaging/eosd/firm-e/eosdigital4/firmware.html">http://web.canon.jp/imaging/eosd/firm-e/eosdigital4/firmware.html</a><br /><br /></li><li>在linux里用unzip命令解压缩这个软件包，就会得到e5kr4110.fir这个文件<br />unzip e5kr4110.exe<br /><br /></li><li>在相机上格式化sd卡<br /><br /></li><li>复制解压的fir文件到sd卡的根目录<br />sudo mount /dev/mmcblk0p1 /mnt<br />sudo cp e5kr4110.fir /mnt<br /><br /></li><li>sd卡插入相机，就可以刷了，整个刷机过程也就两三分钟而已<br /><img src="http://farm3.static.flickr.com/2613/4136961128_e9390daf8a_o.jpg" /><img src="http://farm3.static.flickr.com/2777/4136961136_8b5256d014_o.gif" /><br /></li></ol></ol><br /><font style="font-size: 1em;"><b><font style="font-size: 1.25em;">固件升级有一定的风险，请谨慎。</font></b></font><br />

