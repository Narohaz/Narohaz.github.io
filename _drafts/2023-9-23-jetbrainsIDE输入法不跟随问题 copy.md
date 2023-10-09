---
layout: post
title : kde fctix输入法在部分窗口下不能使用 问题
author : Narohaz
date : 2023-10-10 1:05:49 +0800
description: 问题记录
tags : 
- post
- manjaro
- 搜狗输入法
- fctix
---

# 1. 安装经过修改的依赖  

    Linux x64: https://cache-redirector.jetbrains.com/intellij-jbr/jbr_jcef-17.0.8-linux-x64-b1000.37.tar.gz

    Linux AArch64: https://cache-redirector.jetbrains.com/intellij-jbr/jbr_jcef-17.0.8-linux-aarch64-b1000.37.tar.gzx

# 2. 替换ide允许依赖的jbr
    在ide中双击shift-choose jar-runtime-选中解压后的1中解压后的目录  
    或者    
    将解压之后的内容替换ide中jar包内的所有文件(位置 /opt/clion/jar) 其他ide同理
    另，在snap中下载的软件会有snap专有的写保护