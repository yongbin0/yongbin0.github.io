+++
author = "yb"
date = 2014-06-23T13:21:00Z
description = ""
draft = false
slug = "backup-your-google-authenticator-secrets"
title = "备份Google Authenticator的密钥"

+++


Google Authenticator 身份验证器是用来在手机上生成二次登录验证码的. 比如说我们可一打开Gmail, lastpass的两步验证, 这样在安全性上有了一定保障. 

那我们换了手机以后怎么把之前的设置导到新手机里呢? 
好的方法是直接登录相应的网站去重新生成密钥然后在新手机里重新绑定就可以了.

还有没有别的更好的方法呢,如果我们绑定了很多网站的二次验证那一个个重新绑定岂不是很麻烦.

已经root的Android手机可以按照在电脑上执行:

`adb pull /data/data/com.google.android.apps.authenticator2/databases/databases`

然后用sqlite3打开这个数据库文件运行一个简单查询就可以查看账号了

	sqlite3 ./databases
	select * from accounts;`

![](/content/images/2014/Jun/sqlite.png)

