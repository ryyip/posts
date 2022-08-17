---
title: Git
date: 2022-07-21
tags: 
    - Git
categories: 
    - Tools
---

#### Generate ssh key

该命令将在~/.ssh目录下生成两个文件，私钥id_rsa，公钥id_rsa.pub
ssh-keygen -t rsa -b 4096 -C "leo.ye@gmail.com"
ssh-keygen -t rsa -b 4096
cat ~/.ssh/id_rsa.pub
生成后，将公钥内容复制到 git / bitbucket 代码托管站点

```
ERROR:
Git on Bitbucket: Always asked for password, even after uploading my public SSH key
vim .git/config
[remote "origin"]
        fetch = +refs/heads/*:refs/remotes/origin/*
        url = https://Nicolas_Raoul@bitbucket.org/Nicolas_Raoul/therepo.git
to
[remote "origin"]
        fetch = +refs/heads/*:refs/remotes/origin/*
        url = git@bitbucket.org:Nicolas_Raoul/therepo.git

Using the command:
git remote set-url origin git@github.com:username/repo.git
```

#### Command

#Normal

```
git log
git status
git add .
git commit 'desc'
git pull
git push
git push --set-upstream origin feature/ST-8498-Supplier-Assembly-Sku
git checkout branchName
git checkout -b feature/ST-13074-Shipsage-Api origin/feature/ST-13074-Shipsage-Api
```

#Stash

```
git stash
git stash list
git stash apply
git stash drop
git stash pop stash@{1} #apply & drop
```

#GitHub 撤销某次 commit

```
git reset {commitId}：回滚到某次提交。
git reset --soft {commitId}：此次提交之后的修改会被退回到暂存区。
git reset --hard {commitId}：此次提交之后的修改不做任何保留，git status 查看工作区是没有记录的。
git revert {commitId}：放弃某次提交。git revert 之前的提交仍会保留在 git log 中，而此次撤销会做为一次新的提交。要撤销中间某次提交时，只需要对应的commitId即可。
git rebase：当两个分支不在一条线上，需要执行 merge 操作时使用该命令。
```
