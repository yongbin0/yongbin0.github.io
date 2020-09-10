+++
author = "yb"
date = 2010-01-13T01:17:14Z
description = ""
draft = false
slug = "upgrading-to-movabletype-5"
title = "升级到Movable Type 5"

+++


今天终于下定决心去升级<a title="Movable Type" href="http://www.movabletype.com/" id="bq6z">Movable Type</a>了，MT5
中新引入website的概念，website是blog的父集合，在MT
5中可以创建多个website，在每个website里又可以创建多个blog，其中每个blog的域名地址是和其所属的website网址的子域名或
者其下的目录；对发布的页面文档可以进行版本控制，这样可以把文章随时回滚到某一特定的revision，倒是很方便了<br />
<br />安装的过程就是首先尽可能的备份网站数据：<br />1. mysql数据库的备份可以用mysqldump命令或者使用phpmyadmin的export功能，导出所有的表打包下载<br /><blockquote>$ mysqldump -u <i>username</i> -p -h <i>mysql.xxx.com</i> <i>databasename</i> &gt; mt.mysql<br /></blockquote>2. 登录到网站服务器，打包网站文件<br /><blockquote>$ tar zcvf blog.tar.gz blog.yongbin.org<br /></blockquote>3. 登录MT的后台，用MT后台自带的备份和导出功能分别备份网站数据<br /><br />安装过程按照MT的<a title="Detailed Step-by-Step Guide to Movable Type Installation" href="http://www.movabletype.org/documentation/installation/install-movable-type.html#install-new-version" id="r_nm">文档</a>进行全新安装<br />1. 上传MT-5.01-en.tar.gz到服务器并且解压缩<br />
<blockquote>tar zxvf MT-5.01-en.tar.gz <br />
mv MT-5.01-en blog.yongbin.org/mt5<br />
</blockquote>
2. 打开http://blog.yongbin.org/mt5/填入mysql信息然后会自动进行升级安装<br />
3. 安装结束然后调整模板，插件，重新发布，升级过程就结束了

