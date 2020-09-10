+++
author = "yb"
date = 2010-03-19T11:56:12Z
description = ""
draft = false
slug = "sound-issue-in-virtualbox"
title = "VirtualBox的声卡问题"

+++


在启动VirtualBox里的虚拟机的时候，弹出个如下报错：<br><br><span style="font-size: 12px;" tag="span" class="yui-tag-span yui-tag">No audio device could be opened.Select the NULL audio backend with the consequence that no sound is audible.</span><br style="font-family: yui-tmp;"><span style="font-size: 12px;" tag="span" class="yui-tag-span yui-tag">Error ID: HostAudioNotResponding</span><br style="font-family: yui-tmp;"><span style="font-size: 12px;" tag="span" class="yui-tag-span yui-tag">Severity: Warning</span><br><br><a class="" target="" href="http://i773.photobucket.com/albums/yy16/yongbin0/Screenshot/vbox-sound-error.png"><img alt="" title="" class="yui-img" src="http://i773.photobucket.com/albums/yy16/yongbin0/Screenshot/vbox-sound-error.png"></a><br><br>启动之后就是虚拟机里没有声音，原来是 media-libs/libsdl 造成的，解决办法就是在/etc/portage/package.mask里把高于<b>1.2.14</b>屏蔽掉，然后重新emerge<br><br>

