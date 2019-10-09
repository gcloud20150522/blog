---
title: git常用命令
date: 2017-10-3 23:54:51
tags: 
  - git 
  - github 
categories: 版本控制
---

![pic1](/images/1.webp)

### git 流程
   - git status
   - git add .
   - git commit
   - git pull
   - git push origin branchName:refs/for/branchName
   - git pull

### create branch
- git checkout -b featureOne
- git push —set-upstream origin  featureOne
- git add .
- git commit -m ‘msg'
- git pull
- git push origin featureOne:refs/for/featureOne
- git pull

### merge to master
- git checkout master
- git merge featureOne
- git add .
- git commit -m ‘merge'
- git pull
- git push origin master:refs/for/master
- git pull