---
layout: post
title : 解决ubuntu下搜狗输入法不跟随问题
author : Narohaz
date : 2023-9-33 13:02:30 +0800
tags : 
- post
- ubuntu
- 
---

# 运行环境dosbox，编译器masm

源程序代表.asm文件， debug程序是dos提供的程序。

## 1.是segment而不是segement

## 2.在源程序中，不能以字母开头， 比如ffffh应该表示为0ffffh

## 3.数据需要显式指明进制 比如使用0001h而不是0001表示16进制的1

## 4.操作内存需要使用寄存器作为段地址或偏移地址,

如

`mov ds:[0], ax`

`mov ds:[bx], ax`

直接写 mov ax, [0]在源程序中会被当成立即数， 即mov ax,0 ，这和debug下不同

(debug程序下是可以这样写的)\

## 5.通用寄存器AX,BX,CX,DX不能作为段基址寄存器

## 6.以栈指针0为起始地址，则要存多少字节，sp就是多大，要存16字节，sp就是0010h

## 7.mov ss, ax会给变（ax）处的内容

`stacksg segment`
  `dw 6h,7h,5h,7h ;用栈保存字符对应的长度`
`stacksg ends`

`codesg segment`
  `start:`
`;设置栈指针`
	`mov ax, stacksg`
	`mov ss, ax`
	`mov sp, 8`

在代码中，当你使用`mov ss, ax`将`ax`的值赋给栈段寄存器`ss`后，栈段寄存器指向的栈段地址发生了变化。之前`ax`寄存器中的值指向的内存地址被标识为栈顶，但现在指向的地址变了，也就是栈顶的地址也变了，导致之前在栈顶位置的数据被覆盖。

因此，建议在操作栈时，先将栈段寄存器设置好，再将需要入栈的数据压入栈中。而不是在定义栈段时就写入数据，以避免数据被意外覆盖。

### 8.只用bx,si,di,bp这四个寄存器可以作为偏移地址使用，比如使用es:[dx]会提示Must be index or base register

### 9.使用word ptr 或者 byte ptr 指明内存长度，结合mov可以对内存修改

