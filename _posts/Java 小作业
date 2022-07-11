---
layout: post
title : Java 小作业
author : Narohaz
date : 2022-5-23 12:41:38 +0800
tags : 日志
---

记录一个上学期java小作业里遇到的问题。(我不知道该怎么命名比较好...)


{% highlight js linenos %}
import java.util.Scanner;

public class test {
	public static void main(String args[]) {
		int testint=0;//申请的字符串数组长度
		Scanner input= new Scanner(System.in);
		
		System.out.println("输入字符串长度: ");
		testint=input.nextInt();
		String teststr[]=new String[testint];
		
		System.out.println("输入一系列字符串: ");
		for(int i=0;i<=testint;i++)
			teststr[i]=input.nextLine();
		
		for(String i:teststr) {
			int c=0;
			System.out.printf("这是第%d个字符串:",c);
			System.out.println(i);
			c++;
		}
		input.close();
	}
}


输入字符串长度: 
3
输入一系列字符串: 
字符串0
字符串1
字符串2
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
	at Example4/Example4.test.main(test.java:16)

手动将string数组设置为4，即
String teststr[]=new String[testint];
改为
String teststr[]=new String[4];
结果如下

{% endhighlight %}

