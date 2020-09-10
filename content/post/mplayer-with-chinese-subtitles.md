+++
author = "yb"
date = 2010-02-04T15:31:16Z
description = ""
draft = false
slug = "mplayer-with-chinese-subtitles"
title = "mplayer的中文字幕问题"

+++


眼下，Lost - 迷失第六季归来，趁此时机准备从头认真看一下这部美剧，遂从网上拽下来720P bluray版本的，也找来了srt格式的字幕，结果发现中文字幕在mplayer里播放是乱码的

后来发现网上下载下来的字幕文件都是UTF-16或者ISO8859编码的，需要先转化为UTF-8格式才可以正常显示，可以采用以下任意一种办法：

1. 用iconv转化文件格式

		iconv -f iso8859-1 -t utf8 -c 1.srt > new.srt

	* -f 指定当前文件编码
	* -t 指定要转化成的编码 
	* -c 指定字幕文件

2. 用vim打开字幕文件执行以下命令然后保存即可

		set fileencoding=utf8


###常见问题：
Q: 中文字幕显示还是不出来

A: 修改`~/.mplayer/conig` 文件添加一行 

	subcp=utf8

Q: 中文字幕显示成横线

A: 修改~/.mplayer/conig 文件，添加一行 

	fontconfig=0

Q: ass格式字幕在smplayer下正常，在mplayer下却不能正确识别ass字幕其格式信息

A: 如果想启用mplayer对ass格式字幕的渲染效果，将 `ass=1` 添加到`~/.mplayer/config` 即可

其中mplayer还需要进一步配置才能达到更好的播放效果，，备份一下我的~/.mplayer/config 文件

	autosync=0
	mc=0
	ao=alsa 
	vo=vdpau,xv
	stop-xscreensaver=no
	monitoraspect=1440:900
	zoom=yes 
	subcp=utf8
	unicode=yes
	#Displaye Chinese subtitles if available
	slang=chs
	#设置自动缩放字幕，0－不自动缩放，1－按电影高度缩放，2－按电影宽度缩放，3－按电影对角线缩放(默认值)
	subfont-autoscale=1
	#设置字幕文本的自动缩放系数(屏幕尺寸的百分比)，值范围为0～100
	subfont-text-scale=4
	subfont-osd-scale=2
	#font=/usr/share/fonts/Truetype/msyh.ttf #选择字幕用的字体
	overlapsub=1
	# Load all subtitles containing the movie name
	sub-fuzziness=1
	osdlevel=3 
	# set 8MB input cache
	cache = 8192
	fontconfig=0
	#set 1 to enable the ass subtitles
	ass=0
	ass-font-scale=0.8

