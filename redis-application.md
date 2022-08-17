---
title: Redis应用场景
date: 2022-08-05
tags: 
    - redis
categories: 
    - redis
---

Redis是一款内存高速缓存数据库。Redis全称为：Remote Dictionary Server（远程数据服务），使用C语言编写，Redis是一个key-value存储系统（键值存储系统），支持丰富的数据类型，如：String、list、set、zset、hash。

Redis是一种支持key-value等多种数据结构的存储系统。可用于缓存，事件发布或订阅，高速队列等场景。使用C语言编写，支持网络，提供字符串，哈希，列表，队列，集合结构直接存取，基于内存，可持久化。

1、热点数据的缓存

由于redis访问速度块、支持的数据类型比较丰富，所以redis很适合用来存储热点数据，另外结合expire，我们可以设置过期时间然后再进行缓存更新操作，这个功能最为常见，我们几乎所有的项目都有所运用。

2、限时业务的运用

redis中可以使用expire命令设置一个键的生存时间，到时间后redis会删除它。利用这一特性可以运用在限时的优惠活动信息、手机验证码等业务场景。

3、计数器相关问题

redis由于incrby命令可以实现原子性的递增，所以可以运用于高并发的秒杀活动、分布式序列号的生成、具体业务还体现在比如限制一个手机号发多少条短信、一个接口一分钟限制多少请求、一个接口一天限制调用多少次等等。

4、排行榜相关问题

关系型数据库在排行榜方面查询速度普遍偏慢，所以可以借助redis的SortedSet进行热点数据的排序。

5、分布式锁

主要利用redis的setnx命令进行，setnx："set if not exists"就是如果不存在则成功设置缓存同时返回1，否则返回0。

6、延时操作

7、分页、模糊搜索

redis的set集合中提供了一个zrangebylex方法，语法如下：

ZRANGEBYLEX key min max[LIMIT offset count]

通过ZRANGEBYLEX zset-+LIMIT 0 10可以进行分页数据查询，其中-+表示获取全部数据

zrangebylex key min max这个就可以返回字典区间的数据，利用这个特性可以进行模糊查询功能，这个也是目前我在redis中发现的唯一一个支持对存储内容进行模糊查询的特性。

8、点赞、好友等相互关系的存储

Redis set对外提供的功能与list类似是一个列表的功能，特殊之处在于set是可以自动排重的，当你需要存储一个列表数据，又不希望出现重复数据时，set是一个很好的选择

9、队列

由于redis有list push和list pop这样的命令，所以能够很方便的执行队列操作。

*转载至：https://www.huaweicloud.com/zhishi/Redis.html*
