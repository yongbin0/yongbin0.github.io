+++
author = "yb"
date = 2014-09-25T21:57:00Z
description = ""
draft = false
slug = "get-the-check-in-history-with-tf-exe"
title = "Get the check-in history with tf.exe"

+++


得到某一个时间段某人提交所有的check in代码立标

	tf history  /recursive /format:brief /version:D"09/03/2014"~D"09/04/2014" /noprompt /server:https://TFS:8080/tfs $/"ProjectName" /user:userName



得到某一具体changeset版本修改的文件列表

	tf history /recursive /format:detailed /version:5139 /stopafter:1 /noprompt /server:https://TFS:8080/tfs $/"ProjectName"

