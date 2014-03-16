---
layout: post
title: "iOS内存管理"
date: 2014-03-16 17:14:04 +0800
comments: true
categories: 
---
###### 内存管理

* [Apple's Memory management](https://developer.apple.com/library/ios/documentation/general/conceptual/devpedia-cocoacore/MemoryManagement.html)

##### 规则描述1

1. 当你使用new,alloc或copy创建对象时，对象的count retain到1。你一定要负责把这个对象release 或 autolease掉。这样当它的生命周期结束时，它才能清空。

2. 当你使用 其他方法获得一个对象时，你可以认为它已经retain了一个count，并且autolease掉了。你不用考虑和它相关的清理问题 。但是如果你想保留这个对象，那么你需要retain它，并且要确保之后你release了这个对象。

3. 如果你retain一个对象，你最终总是需要release或者autolease它。

4. 如果这个对象是你alloc或者new出来的，你就需要调用release。如果使用autorelease，那么仅在发生过retain的时候release一次


##### 规则描述2

1. "谁创建,谁释放".如果通过alloc,new,(mutable)copy来创建一个对象,你必须调用release或autorelease来释放.反之,你不创建,则不释放.方法内返回对象一般用autorrelease.
2. 谁retain,谁release.只要你调用了retain,无论这个对象是如何生成的,都必须调用release
3. 一般来说,出了alloc,new或copy之外的方法创建的对象都被声明了autorelease.(参看autorelease 链接1)




##### Autorelease
1. [iOS Memory Management: Using Autorelease](http://www.asgteach.com/blog/?p=73)

　


