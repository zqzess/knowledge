---
title: Hexo NextT主题博客美化
date: 2020-10-13 21:54:01
tags: [Hexo,博客]
categories:
- 博客
- Hexo
password: "0210"
description: 由于我使用的NextT版本是7.8比较新，从7.3开始删除了好多东西，而网上很多教程都无法使用了，所以分享并记录一下我自己的美化过程
top:
keywords: 
related_posts: true
---

## 环境

| name | version |
| -------     | ------- |
| Git          | 2.27.0 |
| Node      | 12.19.0 |
| npm        | 6.14.8  |
| hexo      | 5.2.0    |
| hexo-cli | 4.2.0    |
| NextT   | 7.8.0    |

## 说明
在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。

**前者一般称为 站点配置文件， 后者称为 主题配置文件**

## 下载主题

```
mkdir themes/next
curl -L https://api.github.com/repos/theme-next/hexo-theme-next/tarball/v7.8.0 | tar -zxv -C themes/next --strip-components=1
```
更多安装方法请参考[官方github说明](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/INSTALLATION.md)


## 参考资料
[NextT中文Readme.md](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/README.md)

## 启用主题
下载好后在打开**站点配置文件**,在最后几行找到``theme``字段，并将值改为``next``

```yml
# Extensions
# Plugins: hexo-generate-feed
## Themes: https://hexo.io/themes/
theme: next
```

## 设置语言
编辑**站点配置文件**,更改``language``值
```yml
language: zh-Hans
```

## 选择主题样式Scheme
Scheme 是 NexT 提供的一种特性，借助于 Scheme，NexT 为你提供多种不同的外观。同时，几乎所有的配置都可以 在 Scheme 之间共用。目前 NexT 支持四种 Scheme
- Muse - 默认 Scheme，上下布局，这是 NexT 最初的版本，黑白主调，大量留白
- Mist - Muse 的紧凑版本，整洁有序的单栏外观
- Pisces - 双栏 Scheme，小家碧玉似的清新
- Gemini

Scheme 的切换通过更改**主题配置文件**，搜索 scheme 关键字，将你需用启用的 scheme 前面注释 # 去除即可

```yml
# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
# scheme: Muse
scheme: Mist
# scheme: Pisces
# scheme: Gemini
```
## 基本信息配置
打开**站点配置文件** ，找到Site模块

```yml
# Site
title:      #标题
subtitle: ''    #副标题
description: ''    #描述
keywords:     #关键词
author:     #作者
language: zh-CN    #语言
timezone: 'Asia/Shanghai'
```

# 未完待续