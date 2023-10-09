---
layout: post
title : 解决ubuntu下搜狗输入法不跟随问题
author : Narohaz
date : 2023-9-23 13:02:30 +0800
description: 问题记录
tags : 
- post
- ubuntu
- 搜狗输入法
- jetbrains,idea,clion,pychatm
---

# 1. 安装经过修改的jbr

    [Linux x64](https://cache-redirector.jetbrains.com/intellij-jbr/jbr_jcef-17.0.8-linux-x64-b1000.37.tar.gz)

    Linux AArch64: https://cache-redirector.jetbrains.com/intellij-jbr/jbr_jcef-17.0.8-linux-aarch64-b1000.37.tar.gzx


# 2. 在ide中双击shift-choose jar-runtime-选中解压后的1中解压后的目录  
或者    
  
    将解压之后的内容替换ide中jar包内的所有文件(位置 /opt/clion/jar) 其他ide同理
    另，在snap中下载的软件会有snap专有的写保护
    又另，貌似这个问题在windows中也有但是早被修复了