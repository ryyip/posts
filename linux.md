---
title: Linux command
date: 2022-07-16
tags: 
    - linux
    - linux command
categories: 
    - linux
    - linux command
---

### User & Group

切换root
sudo su

切换用户
su leo

1. chgrp：更改文件属组
   chgrp [-R] 属组名 文件名
2. chown：更改文件属主，也可以同时更改文件属组
   chown [–R] 属主名 文件名
   chown [-R] 属主名:属组名 文件名
3. chmod: 更改文件权限
   chmod [-R] 755 文件名

查看当前用户所属组: groups

查看指定用户所属组: groups leo

直接查看组文件: cat /etc/group

wget http://example.com/file.tar -O /path/to/dir/file.tar
curl http://example.com/file.tar -o /path/to/dir/file.tar


cgroups
cgroups(Control Groups) 是 linux 内核提供的一种机制，这种机制可以根据需求把一系列系统任务及其子任务整合(或分隔)到按资源划分等级的不同组内，从而为系统资源管理提供一个统一的框架。简单说，cgroups 可以限制、记录任务组所使用的物理资源。本质上来说，cgroups 是内核附加在程序上的一系列钩子(hook)，通过程序运行时对资源的调度触发相应的钩子以达到资源追踪和限制的目的。

#### Process

#lsof(list open files)是一个列出当前系统打开文件的工具。
lsof -i:端口号

#netstat -tunlp 用于显示 tcp，udp 的端口和进程等相关情况。
netstat -tunlp | grep 端口号

sudo update-alternatives --set php /usr/bin/php7.2

### File

快速创建文件
echo > test.txt

### Setting

source命令
通常用于重新执行刚修改的初始化文件，使之立即生效，而不必注销并重新登录。因为linux所有的操作都会变成文件的格式存在。
当我修改了/etc/profile文件，我想让它立刻生效，而不用重新登录；这时就想到用source命令，如:source /etc/profile
语法
source filename

### SSH

Host app-staging.local.com
  HostName app-staging
  User ubuntu
  IdentityFile ~/Personal/AWS-CN.pem
  Port 22

Host *
  IdentitiesOnly=yes
  ServerAliveInterval 60
  AddKeysToAgent yes
  IdentityFile ~/.ssh/AWS-CN.pem

### System

查看系统版本
cat /etc/os-release
lsb_release -a
hostnamectl

