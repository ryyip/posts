---
title: Yarn
date: 2022-05-05 10:20:12 
tags: 
    - Yarn
    - Dependent
categories: 
    - Tools
    - Yarn
---

***Yarn: 依赖包管理工具***

[官方文档](http://yarnpkg.top/WorkFlow.html)

#### 项目初始化

```
yarn init
```

#### 管理依赖

##### 新增依赖

```
yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]
```

##### 更新依赖

```
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[dist-tag]
```

##### 删除依赖

```
yarn remove [package]
```

#### 安装依赖

```
yarn install
```

[`yarn install`](http://yarnpkg.top/Cli-install.html)命令用来安装一个项目的全部依赖。项目的这些依赖是在项目的`package.json`文件中描述的，并被储存在`yarn.lock`文件中

通常在下面两种情况下需要安装依赖

1. 一个全新的项目刚刚被下载

2. 依赖有了更新

   

---



#### Yarn的优点

- **速度快** 。速度快主要来自以下两个方面：

1. 并行安装：无论 npm 还是 Yarn 在执行包的安装时，都会执行一系列任务。npm 是按照队列执行每个 package，也就是说必须要等到当前 package 安装完成之后，才能继续后面的安装。而 Yarn 是同步执行所有任务，提高了性能。
2. 离线模式：如果之前已经安装过一个软件包，用Yarn再次安装时之间从缓存中获取，就不用像npm那样再从网络下载了。

- 安装**版本统一**：为了防止拉取到不同的版本，Yarn 有一个锁定文件 (lock file) 记录了被确切安装上的模块的版本号。每次只要新增了一个模块，Yarn 就会创建（或更新）yarn.lock 这个文件。这么做就保证了，每一次拉取同一个项目依赖时，使用的都是一样的模块版本。npm 其实也有办法实现处处使用相同版本的 packages，但需要开发者执行 npm shrinkwrap 命令。这个命令将会生成一个锁定文件，在执行 npm install 的时候，该锁定文件会先被读取，和 Yarn 读取 yarn.lock 文件一个道理。npm 和 Yarn 两者的不同之处在于，Yarn 默认会生成这样的锁定文件，而 npm 要通过 shrinkwrap 命令生成 npm-shrinkwrap.json 文件，只有当这个文件存在的时候，packages 版本信息才会被记录和更新。
- **更简洁的输出**：npm 的输出信息比较冗长。在执行 npm install 的时候，命令行里会不断地打印出所有被安装上的依赖。相比之下，Yarn 简洁太多：默认情况下，结合了 emoji直观且直接地打印出必要的信息，也提供了一些命令供开发者查询额外的安装信息。
- **多注册来源处理：**所有的依赖包，不管他被不同的库间接关联引用多少次，安装这个包时，只会从一个注册来源去装，要么是 npm 要么是 bower, 防止出现混乱不一致。
- **更好的语义化**： yarn改变了一些npm命令的名称，比如 yarn add/remove，感觉上比 npm 原本的 install/uninstall 要更清晰。



#### Yarn和npm命令对比

```text
npm install === yarn 
npm install taco --save === yarn add taco
npm uninstall taco --save === yarn remove taco
npm install taco --save-dev === yarn add taco --dev
npm update --save === yarn upgrade
```