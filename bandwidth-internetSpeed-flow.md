---
title: 带宽、网速、流量之间有什么关系 
date: 2022-06-15
tags: 
    - bandwidth
categories: 
    - Computer
---

### 区别

1、带宽的统计单位是：比特/秒（bps）：100M=100Mbps；

2、网速是数据传输的速度，单位是：字节/秒（B/s KB/s MB/s）：1MB/s=1024KB/s ；1KB/s=1024B/s。

3、流量是用户上网发送和接收的数据量总和，单位是：字节（Byte）；

比特是信息的最小单位：1字节=8比特（1B=8bit或者1B=8b）；1字节/秒=8比特/秒（1B/s=8bps）

### 如何换算

我们这里来用实例看下：比如200M宽带下载速度是多少？

首先，运营商所说的200M宽带光纤，完整单位是200Mbps，而我们电脑中所说的下载速度单位是：MB。因此200M宽带下载速度并不代表下载速度就是200Mb/s，而是需要按照如下公式进行换算：

1Mbps=1024Kbps=1024/8KBps=128KB/s

也就是说 1M 的宽带下载速度不会超过 128KB/s ，也就是理论上1秒钟，可以下载128K的内容，实际上1M宽带，下载速度100k/s就属于正常，毕竟理论值不一定能达到。

200M宽带的下载速度理论上为：128KB/s x 200 = 25600 KB/s = 25.6MB/s

正常的下载速度是：25M；当然，这是理论上的下载速度，在实际使用的过程中，可能会略低于/高于25M，一般来说上下浮动1M都属于正常的，即24-26都属于正常的。

如果你家网速测试小于25M太多的话，要么是连的假200M带宽，要么就是其它的路由器、光猫没有使用千兆的。