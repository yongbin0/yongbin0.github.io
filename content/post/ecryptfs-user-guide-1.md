+++
author = "yb"
categories = ["ecrypt", "gentoo", "加密"]
date = 2009-12-09T22:23:13Z
description = ""
draft = false
slug = "ecryptfs-user-guide-1"
tags = ["ecrypt", "gentoo", "加密"]
title = "ecryptfs的用法 - (1)"

+++


上一篇说过了<a class="" href="http://blog.yongbin.org/archives/2009/12/install-ecryptfs-on-gentoo.html">在Gentoo上安装ecryptfs</a>，现在说一下怎么来用这个软件。常见的用ecryptfs加密目录有两种方式：加密用户主目录和加密~/Private 文件夹，其实原理都是大同小异的，只不过挂载点不同并且加密主目录要稍麻烦一些。ecryptfs支持PAM，这样的话可以用开机密码来解密，这个过程是透明的，非常方便当然也可以设置成另外的密码，在需要的时候在解密。<br><br>1. 确认已经加载了ecryptfs 模块，如果没有那么请 sudo modprobe ecryptfs<br><br>2. 运行命令 ecryptfs-setup-private来建立一个加密的私人目录，这个命令需要你输入一些密码和密钥，请牢记你的这些密码密钥并妥善保存。<br><br>&nbsp;&nbsp;&nbsp; login passphrase: 输入开机登录的密码<br><br>&nbsp;&nbsp;&nbsp; mount passphrase [leave blank to generate one]: 挂载加密目录的密钥（建议这里直接回车让系 统直接随机生成，这样强度会高些）<br><br>&nbsp;&nbsp;&nbsp; 这个命令运行之后会生成3个文件夹：Private，.Private和.ecryptfs。其中Private只是一 个用来&nbsp; 挂载的目录而已，.Private为存放加密的数据真实目录, .ecryptfs存放的是配置文件<br>

<!--more-->
3. 正常情况下运行完上面这个命令后，会自动挂载加密目录到~/Private，可以用mount命令来查看，<br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a. 如果没有的话是因为 /usr/bin/ecryptfs-mount-private 的权限问题，需要手动设置suid<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ sudo chmod +s /usr/bin/ecryptfs-mount-private<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 如果是gentoo的话，可以添加"suid"这个USE然后重新 sudo emerge ecryptfs-utils<br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b. 如果不愿意设置suid的话，可以下边一行到 /etc/fstab 这个文件，这个是推荐的做法,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
/home/yongbin/.Private /home/yongbin/Private ecryptfs
rw,user,noauto,ecryptfs_sig=aaaaaa,ecryptfs_fnek_sig=bbbbbb,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs
0 0<br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 其中
ecryptfs_sig和ecryptfs_fnek_sig这两个值可以从~/.ecryptfs/Private.sig中得到，分别对应该文件中
的第一行和第二行，直接把相应字符串填入即可，这样的话普通用户也可以随时mount和umount这个~/Private目录<br><br>4. 手动挂载该加密目录：<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ ecryptfs-insert-wrapped-passphrase-into-keyring 输入第2步输入的login pasphrase，<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ mount -i ~/.Private ~/Private<br><br>&nbsp;&nbsp;&nbsp; 手动卸载该目录<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $umount ~/Private<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 或者$ ecryptfs-umount-private<br><br>5. 如果要配置成开机登录的时候自动挂载该目录，那就需要简单修改一下/etc/pam.d/system-auth这个文件，把pam_ecryptfs.so添加到相应位置，如图所示<br>&nbsp;&nbsp;
<a class="" href="http://farm3.static.flickr.com/2507/4172700375_74e4f39b6e_o.jpg" title="pam by im_yb, on Flickr"><img class="yui-img" src="http://farm3.static.flickr.com/2507/4172700375_74e4f39b6e_o.jpg" alt="pam" height="211" width="500"></a><br>
这样，在自己的主目录的底下有一个存放加密文件的.Private目录（并且其中文件名也是加密的），该目录会在开机登录后自动挂载到Private目
录，然后在该用户注销的时候，其他用户包括root是访问不了你的实际数据的，最重要的是保护你的硬盘丢失后的重要数据丢失。<br>
<br><br><b>note：</b><br>1. ~/.private存放的是加密后的数据，需要保存好，切勿随意删除，要不然数据就找不到了<br>&nbsp;&nbsp;&nbsp; ~/.ecryptfs尽可能也要备份，这样如果系统重装会很容易恢复加密数据<br><br>2. 保存好第二步创建的挂载密钥，如果是系统自动生成的，那么可以通过下面这个命令得到这个密钥<br>&nbsp;$ ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase<br>输入开机的密码就会得到一组字符串，慎重保存该字符串，在数据恢复的时候是用得着的，一旦丢失，恢复数据基本不可能（如果wrapped-passphrase还在的话还是可以的）<br>
<br>

