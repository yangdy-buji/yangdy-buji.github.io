---
layout: post
title: "git 配置多个SSH-Key"
date: 2017-09-30 08:00:00 +0800
categories: 学无止境
tag: [git, ssh]
---
* content
{:toc}

作为一名键盘侠（程序员），git 是我最常用的SCM工具，日常工作和生活中会涉及gitlab、github以及阿里云RDC的仓库。登录涉及多个ssh key那怎么办呢？

<!-- more -->

# Quick Start
## 创建ssh秘钥对
```cmd
$ ssh-keygen -t rsa -C "youremail@yourcompany.com” -f ~/.ssh/gitlab_rsa
```
在~/.ssh/目录会生成gitlab_rsa(私钥)和gitlab_rsa.pub(公钥)。 我们将gitlab_rsa.pub中的内容粘帖到公司gitlab服务器的SSH-key的配置中。
## 注册私钥
```cmd
$ ssh-add ~/.ssh/gitlab_rsa
```
如果执行ssh-add时提示"Could not open a connection to your authentication agent"，可以先执行命令：
```cmd
$ ssh-agent bash
```
然后再运行ssh-add命令。
同样方法创建第二个key，eg github_rsa

```cmd
# 可以通过 ssh-add -l 来确私钥列表
$ ssh-add -l
# 可以通过 ssh-add -D 来清空私钥列表
$ ssh-add -D
```

## 添加配置文件
```cmd
touch config
```
添加如下内容
```cmd
# gitlab
Host gitlab.com
    HostName gitlab.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/gitlab_rsa
# github
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_rsa
```

## 设置账号名
Setting your Git username for all repositories
```cmd
$ git config --global user.name "Mona Lisa"
$ git config --global user.name
> Mona Lisa
$ git config user.email "邮箱"
```
Setting your Git username for a single repository
```cmd
$ git config user.name "Mona Lisa"
$ git config user.name
> Mona Lisa
$ git config user.email "邮箱"
```


## 测试
```cmd
ssh -T git@github.com

# for debug
ssh -vT git@github.com
```

`<EOF>`