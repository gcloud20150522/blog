---
title: 多Git账户生成多个id_rsa私钥保存路径冲突问题解决办法
date: 2017-11-31 23:54:51
tags: git github 
categories: 版本控制
---

1.四.1步回车后, 重命名id_rsa为id_rsa_springboot、id_rsa_project1

2.此时/c/Users/wangzaiplus/.ssh/目录下生成文件如下
      
    id_rsa_springboot
    id_rsa_springboot.pub
    id_rsa_project1
    id_rsa_project1.pub

3.新建config文件, 注意, 无扩展名, 内容如下

    Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_springboot

    Host gitee.com
        HostName gitee.com
        User git
        IdentityFile ~/.ssh/id_rsa_project1

4.再把对应的公钥添加至对应的网站上面即可, 如GitHub, gitee

5.说明: 未加入配置文件的网站会自动应用/.ssh目录下的id_rsa