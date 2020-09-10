+++
author = "yb"
date = 2010-01-16T19:17:32Z
description = ""
draft = false
slug = "recovery-the-data-from-xfs-partition"
title = "恢复移动硬盘xfs分区的数据"

+++


笔记本的Gentoo Linux已经<a class="" title="" target="" href="http://blog.yongbin.org/archives/2010/01/gentoo-dmcrypt-lvm2.html">切换到了dm-crypt加密的LVM</a>里，正好也想顺便把那个1 TB移动硬盘也给重新整理下分区，然后把其中一个分区加密一下存放一些比较重要的之前的工作文档。这样的话数据的安全性也会有很好的保证。<br><br>之前的移动硬盘分区<br>/dev/sdb1&nbsp;&nbsp;&nbsp; 600 GB&nbsp;&nbsp;&nbsp; NTFS <br>/dev/sdb2&nbsp;&nbsp;&nbsp; 400 GB&nbsp;&nbsp;&nbsp; XFS&nbsp;&nbsp;&nbsp; #for linux<br>调整之后的移动硬盘分区<br>/dev/sdb1&nbsp;&nbsp;&nbsp; 300 GB&nbsp;&nbsp;&nbsp; NTFS<br>/dev/sdb2&nbsp;&nbsp;&nbsp; 700 GB&nbsp;&nbsp;&nbsp; XFS&nbsp;&nbsp;&nbsp; # dm-crypt加密该分区<br>

<!--more-->
由于那个硬盘里已经存放了好几百GB的资料，得先备份出来，然后再减小sdb1的容量，因为电脑上没有那么大空间来备份那么的数据，所以准备先把sdb1
里的全部文件备份到电脑里，然后调整sdb1的分区和格式化，然后把sdb2里的数据复制到sdb1里，再对sdb2分区进行操作。在对sdb1进行分区
的时候为了随后的数据复制的效率把这个分区暂时格式化成了xfs分区（在linux下，ntfs-3g占用资源高些），然后把sdb2的数据复制到了
sdb1的xfs分区里，然后再把移动硬盘的剩余空间全部划归到sdb2,之后为了使新的分区生效，重新接上移动硬盘，结果出问题了....sdb1分区
mount的时候报错"mount: /dev/sdb1: can't read superblock"
,这个分区上刚捣过去207个G的数据，虽说这些数据不是最重要的，只是些操作系统的ISO和常需要用的windows平台上的软件，但如果这次丢了，以
后用到的话再去下载也是很麻烦的，再说刚才还是好好的，那就尝试恢复数据吧<br>
<br>
首先尝试xfs_check没有作用，<br>
xfs_repair运行了若干个小时之后未果<br>
编译了testdisk之后，对移动硬盘扫描分区，识别到了对sdb1减容之后的分区表，写入分区，未果<br>
不太甘心，又一次运行了testdisk，扫描硬盘，再次写入分区表，然后重新挂载，great，207 GB的数据又回来了，只不过分区的顺序颠倒了，数据都在就好，下次一定要备份好分区表，这样类似的问题就简单多了<br><img alt="" title="" style="width: 600px; height: 361px;" class="yui-img" src="http://i773.photobucket.com/albums/yy16/yongbin0/Screenshot/sdb2-partition.png"><br>
<br>
然后继续按照之前的过程倒腾数据，加密sdb2分区，在格式化sdb2的时候选择了reiserfs格式(对xfs后怕啊)，很顺利

