+++
author = "yb"
categories = ["ecrypt", "ecryptfs", "gentoo", "linux"]
date = 2009-12-01T16:35:51Z
description = ""
draft = false
slug = "start-to-use-ecryptfs"
tags = ["ecrypt", "ecryptfs", "gentoo", "linux"]
title = "开始使用ecryptfs来加密文件夹"

+++


记得Ubuntu Linux安装过程中在设置登录账号的时候有一个选项让你选择是否加密主目录，其实这个功能就是通过<a class="" href="https://launchpad.net/ecryptfs">ecryptfs</a>这个软件来实现的。<br><br><a class="" href="https://launchpad.net/ecryptfs">eCryptfs</a> 是一个功能强大的企业级加密文件系统，为应用程序提供透明、安全的加密功能其设计受到OpenPGP 规范的影响，使用了两种方法来加密单个文件：
<br><br><blockquote>1. eCryptfs 先使用一种对称密钥加密算法来加密文件的内容，推荐使用 AES-128 算法，密钥 FEK（File Encryption
Key）随机产生<br><br>2. eCryptfs 使用用户提供的口令（Passphrase）、公开密钥算法（如 RSA 算法）或 TPM（Trusted Platform Module）的公钥来加密保护刚才提及的 FEK<br></blockquote><br>现在我想也用上它来加密我的一个包含很多账号信息的文件夹，这样可以保护你的重要数据，防止由于硬盘，电脑丢失造成的机密信息泄漏。软件已经安装到了我的Gentoo系统上了，不过还有一些问题没有解决，继续研究之....<br><br>

