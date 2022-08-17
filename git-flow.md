---
title: Git Flow
date: 2022-07-21
tags: 
    - Git Flow
categories: 
    - Tools
---

## *GIT Flow*

### Initial

[master]$ git flow init
[develop]$ git push --set-upstream origin develop

### Release

[develop]$ git pull # Pull first and then choose an intial version number like V1.0.0.0 or V0.1.0.0 ...
[develop]$ git flow release start V0.0.1.0 # VMajor.Minor.Release.Hotfix
[release/V0.0.1.0]$ git flow release finish V0.0.1.0
[master]$ git push
[master]$ git push --tags

### Feature

[master]$ git flow feature start ST-6319-DEV-Workflow-V2.0 # ST-JiraNo-feature-Name-Version
[feature]$ git add .
[feature]$ git commit -m 'ST-6774: Code Review Doc-Init' # ST-TaskJiraNo: Task Name-Action(Init/Update/Done/Fix Bug/Approved/Rejected...)
[feature]$ git push --set-upstream origin feature/ST-10185-Purchase-Permission
root/client/ERP yarn generate

#### 1. Feature Release

Mode 1:
[feature]$ git flow feature finish ST-8284-EstimatedPaymentDate
Mode 2:
[feature]$ git flow feature publish ST-6319-DEV-Workflow-V2.0 # The new unpublished feature
[feature]$ git push # The published feature

#### 2. Feature Testing

[staging\][develop]$ git pull
[staging\][develop]$ git checkout feature/ST-6319-DEV-Workflow-V2.0

#### 3. Feature Release

[develop]$ git pull # Pull first
[develop]$ git flow release start V0.0.2.0 # VMajor.Minor.Release.Hotfix
[release/V0.0.2.0]$ git flow release finish V0.0.2.0
[master]$ git push
[master]$ git push --tags

### Hotfix

[develop]$ git pull # Pull first
[develop]$ git flow hotfix start V0.0.2.1 # VMajor.Minor.Release.Hotfix
[hotfix/V0.0.2.1]$ git add .
[hotfix/V0.0.2.1]$ git commit -m 'ST-6774: Code Review Doc-Fix Bug'
[hotfix/V0.0.2.1]$ git flow hotfix finish V0.0.2.1
[master]$ git push
[master]$ git push --tags

