+++
author = "yb"
categories = ["bank", "e60", "mobile", "nokia", "ucweb", "手机", "银行"]
date = 2009-11-27T17:43:36Z
description = ""
draft = false
slug = "payment-by-mobile-phone"
tags = ["bank", "e60", "mobile", "nokia", "ucweb", "手机", "银行"]
title = "尝试招行的手机支付"

+++


今天试用了一次招商银行的手机支付功能，大体上就是在网上购物（如淘宝），在付款的时候选择招行，然后再选手机支付，输入输入卡的四位尾号，系统就会给当初绑定的手机发一个短信，里面有一个链接，在手机上打开这个链接（可以使用wifi或者cmnet）就会打开招行的手机支付的页面，在手机上输入信用卡的的支付密码有效期，输入卡背面的3位安全码（cvv或者cvc，此码应妥善保护），这样就可以付款了。手机支付在某些条件下是非常安全方便的，比如在网吧，或者一个临时使用的电脑上，免去了安装网上银行软件或者证书的过程，让你能安全的购物。<br /><br />只不过在我的Nokia E60上，因为把手机的固件升级到了3.0633.09.04，这个版本是没有中文支持的，好在安装了一些字体之后，显示和输入中文的问题都得到了解决，只是问题在于你直接打开短信里的链接地址的话会自动调用手机自带的浏览器，而这个浏览器是没有gb2312等中文编码的，改成UTF-8打开这个网上支付的页面依然乱码，好在咱们可以变通的解决这个问题：<br />

<!--more-->
<ol><li>打开招行发的这个带链接的短信然后选择转发</li><li>按一下手机上的笔型键（1上面那个），然后选择 1.Select</li><li>选中链接地址</li><li>再按一下笔形键，选择 2.copy 这个时候我们就复制了链接地址</li><li>把这个地址粘贴进ucweb这个手机浏览器，然后就可以正常的访问这个支付页面了</li></ol>
附上几张截图：<br /><br /><img src="http://farm3.static.flickr.com/2489/4143917186_0f7069e53f_m.jpg" alt="cmb01" height="240" width="203" />&nbsp;&nbsp;&nbsp;&nbsp; <img src="http://farm3.static.flickr.com/2594/4143917192_92dc2d34be_m.jpg" alt="cmb02" height="240" width="203" /><br /><br /><img src="http://farm3.static.flickr.com/2749/4143917194_16ac3863b6_m.jpg" alt="cmb03" height="240" width="203" />&nbsp;&nbsp;&nbsp;&nbsp; <img src="http://farm3.static.flickr.com/2790/4143917196_0504558523_m.jpg" alt="cmb04" height="240" width="203" />

