+++
author = "yb"
categories = ["media", "streaming", "vlc"]
date = 2009-05-05T19:39:19Z
description = ""
draft = false
slug = "2_parameters_of_vlc_for_the_streaming"
tags = ["media", "streaming", "vlc"]
title = "2 parameters of vlc for the streaming"

+++


<p>I use vlc to read the video file and then generate a http stream to
another system. But the stream will stop for nearly 3 seconds and I
need re-connect this stream.</p>
<p>To fix this, we can use "-sout-keep", for example:</p>
<p><code> $ cvlc -vvv ***.avi --sout '#standard{access=http,mux=ts,dst=:1234}' --sout-keep --repeat</code><br />
-sout-keep, -no-sout-keep: Keep sout open (default disabled) : use the
same sout instance across the various playlist items, if possible.</p>
<p>-repeat: repeat the current video file</p>
<p>-loop:&nbsp; repeat all</p>

