+++
author = "yb"
date = 2014-09-28T19:19:42Z
description = ""
draft = false
slug = "fix-wcf-4-service-load-error"
title = "Fix WCF 4 service load error"

+++


Description: An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code. 

Exception Details: System.TypeLoadException: Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.

![](/content/images/2014/Sep/loaderror.JPG)

解决办法:

	c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe -iru

