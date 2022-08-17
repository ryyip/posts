---
title: 快速创建自己的VPN服务
date: 2022-06-10
tags: 
    - VPN
categories: 
    - Tools
---

本文介绍的是来自github的开源项目[setup-ipsec-vpn](https://github.com/hwdsl2/setup-ipsec-vpn)，想要全面了解项目的各项设置，可查看其详尽的说明文档。

### Step 1. 服务端安装

首先，在你的 Linux 服务器* 上全新安装 Ubuntu, Debian 或者 CentOS。

使用以下命令快速搭建 IPsec VPN 服务器：

```
wget https://get.vpnsetup.net -qO vpn.sh && sudo sh vpn.sh
```

你的 VPN 登录凭证将会被自动随机生成，并在安装完成后显示。

VPN客户端有两种，所用登录凭证都在安装完成时，展示在界面上，记得保存

a. IPsec/L2TP

通过在客户端设置VPN的用户名，密码，IPsec PSK. 这种方式不需要下载相应文件，仅需要配置即可使用，但这种方式比较繁琐的是，期间有可能遇到各种各样的报错，手机端（Android 12+）不支持。推荐使用下面这种

b. IKEv2

/root/vpnclient.p12 (for Windows & Linux)
/root/vpnclient.sswan (for Android)
/root/vpnclient.mobileconfig (for iOS & macOS)

### Step 2. 客户端安装

[IKEv2 VPN 配置和使用指南](https://github.com/hwdsl2/setup-ipsec-vpn/blob/master/docs/ikev2-howto-zh.md)

#### Windows:  

1. [ikev2_config_import.cmd](https://github.com/hwdsl2/vpn-extras/releases/latest/download/ikev2_config_import.cmd) 下载cmd文件，并将cmd文件与上面的 .p12放在同个目录下，
2. 选择 **以管理员身份运行** 并按提示操作，输入账号名，IP地址即可。
3. 其中遇到一个错误并且没有列入官方的报错列表中，顺便记录下来 “parameter is incorrect” 相应的解决方案再 [github issue](https://github.com/trailofbits/algo/issues/1051) 中找到。

Android, OS X (macOS), IOS 等手机端的，官方文档更加详细。



***Linux 服务器购买渠道：**

1. [vultr.com](https://vultr.com) 最低配置服务器，费用是$6/month。（首次注册赠送100美金的优惠，仅有14天有效期）
2. [搬瓦工（国内）](https://www.bwgyhw.cn/recommend) [搬瓦工（国外）](https://bwh81.net/vps-hosting.php) 最优惠的 $49.99/year，有常用优惠码减 5 ~ 6%，黑五、双11，元旦优惠码减 11 ~ 12%，服务器IP被baned后，需购买更换IP服务（$8/次）

