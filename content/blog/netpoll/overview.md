---
# type: docs 
title: Netpoll介绍
date: 2023-01-09T08:43:08+08:00
featured: false
draft: true
comment: true
toc: true
reward: true
pinned: false
carousel: false
series: Netpoll
categories: [Golang]
tags: [Golang,Netpoll]
images: []
---

超高连接数场景下，越来越多的第三方库开始使用裸的epoll来实现，相继出现了Evio,Gnet和本系列主要讨论的Netpoll。

<!--more-->

随着Go语言的运用越来越广，Go原生的net组件在一些场景下逐渐开始乏力。比如一个需要超高连接数服务的场景下，我们如果使用Go自动的net库，每一个新Client Go net库会分配一个goroutine。我们知道goroutine的默认栈是2k，在超大连接数等于有超高的goroutine，会产生很大的内存占用。而且超多的goroutine会让go调度器调度难度增大。

为了解决这个问题，Go社区里开始出现了抛开go原生net，使用裸epoll的解决方案。比较受欢迎的有[evio](https://github.com/tidwall/evio),[gnet](https://github.com/panjf2000/gnet),以及本系列专栏想讨论的字节跳动开源的[netpoll](https://github.com/cloudwego/netpoll/)。


## 在Go中如何使用裸的epoll？

[1m-go-websockets](https://github.com/eranyanay/1m-go-websockets) 这个项目有比较简洁易懂的代码实现。也可以参考笔者的练手项目[poller](https://github.com/widaT/poller)。

## Reactor模型

epoll最终反馈到用户态的是一个事件数组，我们根据事件数组处理各个事件，这种基于事件的处理模型我们称之为`Reactor`模型。

![reactor](/images/reactor.png)

## Netpoll

 [Netpoll](https://github.com/cloudwego/netpoll)是字节开源的基于Reactor模型的纯golang实现的网络库。字节基于Netpoll开发出了[Kitex](https://github.com/cloudwego/kitex)RPC框架和[Hertz](https://github.com/cloudwego/hertz)http框架，从官方的基准测试结果来看，其性能还是比较出众的。


## Netpoll 核心组件

- [LinkBuffer](https://github.com/cloudwego/netpoll/blob/develop/nocopy_linkbuffer.go)提供可以流式读写的 nocopy API
- [gopool](https://github.com/bytedance/gopkg/tree/develop/util/gopool) 提供高性能的`goroutine`池
- [mcache](https://github.com/bytedance/gopkg/tree/develop/lang/mcache) 提供高效的内存复用



 本系列会从Netpoll源码角度分析，Netpoll的实现细节。