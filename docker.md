---
title: Docker & Docker Compose
date: 2022-08-03
tags: 
    - docker
    - docker compose
categories: 
    - docker
---

​		上个月将系统更换成了Manjaro，期间顺理了相关软件推荐，命令的简要使用等，今天总结一下docker的使用及遇到的问题。

## Docker

#### 简介

- image (相当于镜像，里面各项配置)
- container (相当与一台台虚拟机)
- docker-compose (多容器合作，App容器，数据库容器)
- Portainer (容器可视化管理软件)

#### 文件

dockerfile (自动化脚本，用于创建镜像)

docker-compose.yml (docker compose 配置文件)

#### 镜像源地址修改

```
mkdir -p /etc/docker
tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
EOF

#重启docker
systemctl daemon-reload
systemctl restart docker

#腾讯云的镜像地址
https://mirror.ccs.tencentyun.com

#网易的镜像地址
http://hub-mirror.c.163.com

#阿里云镜像地址，需要到自己的阿里云"容器镜像服务->镜像加速器"去复制自己的镜像地址
https://xxxx.mirror.aliyuncs.com

#daocloud发布的镜像地址
http://f1361db2.m.daocloud.io
```

#### 命令

```
#创建container (第一次会先下载对应的镜像)
docker run -itd -v /sys/fs/cgroup:/sys/fs/cgroup:ro --privileged=true --name=lnmp 2233466866/lnmp
#查看容器信息
docker inspect lnmp | grep IPAddress
#进入容器console(*部分容器支持/bin/bash,部分支持/bin/sh)
docker exec -it lnmp /bin/bash
docker exec -it cgi /bin/bash
docker exec -it proxy /bin/sh
#在宿主机直接运行 指定容器 的命令
docker exec -it cgi /bin/bash -c "cd /var/www/html/app.gaatu.com && php artisan migrate"
#复制容器内的文件或文件夹到宿主机
docker cp cgi:/usr/local/etc/php/php.ini ~/docker-compose/docker-leo/docker/config/cgi/php.ini

#查询所有container
docker ps -a
#查询所有image
docker images
#停止container
docker stop containerName
docker stop $(docker ps -a -q)
#删除container
docker rm containerName
docker rm $(docker ps -a -q)
#删除image
docker rmi imageName
docker rmi $(docker images -q)

#Docker Composer
docker-compose -f docker-compose.yml up -d 
docker-compose up -d
docker-compose down -d

#Docker仓库
docker login
docker tag <IMAGE_ID>|<IMAGE_NAME> <REGISTRY_HOST>/<APPNAME>:<APPVERSION>
docker push <REGISTRY_HOST>/<APPNAME>:<APPVERSION>

Example:
docker tag 92bd352be65f ryyip/php7.2-fpm:1.1
docker tag docker-leo_php72 ryyip/php7.2-fpm:1.1
docker push ryyip/php7.2-fpm:1.1
```

#### Container Problems

```
#image: mysql:8.0.29
error: the server requested authentication method unknown to the client

$ docker-compose exec mysql bash
$ mysql -u root -p
(login as root)
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';
ALTER USER 'default'@'%' IDENTIFIED WITH mysql_native_password BY 'secret';
```

```
#image: php:7.2-fpm

#重启php服务(该容器自带的特定命令)
kill -USR2 1
```

#### Project

```
https://github.com/ryyip/docker-leo
```

