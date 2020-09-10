+++
author = "yb"
categories = ["ecryptfs", "gentoo", "加密"]
date = 2009-12-09T19:06:06Z
description = ""
draft = false
slug = "install-ecryptfs-on-gentoo"
tags = ["ecryptfs", "gentoo", "加密"]
title = "在Gentoo上安装ecryptfs"

+++


内核从2.6.19开始引入了ecryptfs这个堆叠式加密文件系统，要想使用它，首先在内核中启用该模块，然后安装用户态的工具ecryptfs-utils，在然后就可以使用了<br><br>1. 配置内核，加密的算法可以按需要再多选择几个，当然你可以全部编译成模块，编译安装新的内核<br>&nbsp;&nbsp;&nbsp; Security options&nbsp; ---&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp; &lt;×&gt; Enable access key retention support<br>&nbsp;&nbsp;&nbsp; File systems&nbsp; ---&gt;<br>&nbsp;&nbsp;&nbsp; Miscellaneous filesystems&nbsp; ---&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;M&gt; eCrypt filesystem layer support<br>&nbsp;&nbsp;&nbsp; &nbsp; Cryptographic options&nbsp; ---&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp; &lt;×&gt;&nbsp;&nbsp; MD5 digest algorithm<br>&nbsp;&nbsp;&nbsp;&nbsp; &lt;×&gt;&nbsp;&nbsp; AES cipher algorithms<br>&nbsp;&nbsp;&nbsp; 对应的这几项为<br>&nbsp;&nbsp;&nbsp;&nbsp; CONFIG_KEYS=y&nbsp; <br>
&nbsp;&nbsp;&nbsp;&nbsp; CONFIG_ECRYPT_FS=m<br>&nbsp;&nbsp;&nbsp;&nbsp; CONFIG_CRYPTO_MD5=y<br>&nbsp;&nbsp;&nbsp;&nbsp; CONFIG_CRYPTO_AES=y<br><br>2.&nbsp; 加载模块<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ sudo modprobe ecryptfs<br><br>3. 添加ecryptfs到/etc/conf.d/modules文件，这样这个模块可以开机自动加载<br><br>4. 安装用户态工具<br>&nbsp;&nbsp;&nbsp; $ sudo emerge ecryptfs-utils<br><br>这样，已经完成了ecryptfs的安装，可以使用它来加密的你的重要文档了<br>
<br>
<br>

