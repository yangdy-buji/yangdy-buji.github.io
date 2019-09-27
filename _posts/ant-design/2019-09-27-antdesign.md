---
layout: post
title: "ant design 学习摘要"
date: 2019-09-27 20:00:00 +0800
categories: 学无止境
tag: [react, ant-design]
---
* content
{:toc}

作为一名全栈GeekCoder，怎么能不知道ant-design呢？ant-design 是基于React的，所以我们也要了解一点React的东东。

<!-- more -->

# Quick Start
## React
React是一个基于组件的前端开发框架，可以把网页看成一个由组件构成的状态机，状态的变化会导致UI的变化，正所谓相由心生。
![React生命周期](https://cdn.nlark.com/yuque/0/2019/png/87519/1569585675692-7fbf04db-ebb0-48dd-8ec9-1a00554f8cd7.png?x-oss-process=image/resize,w_746)

## umi

umi 是ant-design团队开发的构建工具，可以通过npm安装，由于不可描述的原因，国内访问npm默认仓库比较慢，可以使用淘宝的镜像进行加速。
```cmd
npm config set registry https://registry.npm.taobao.org
```
然后安装umi
```cmd
npm i -g umi
```
更多umi的信息可以查看 [查看umi](https://umijs.org/)

`<EOF>`