---
# type: docs 
title: 区块链学习--BTC网络
date: 2022-12-07T11:34:27+08:00
featured: false
draft: true
comment: true
toc: true
reward: true
pinned: false
carousel: false
series: Blockchain
categories: [Blockchain]
tags: [Blockchain]
images: []
---

在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍BTC网络。


## 词条

- The BitCoin  Network
- Super Node
- Master Node
- Seed Node
- simple robust ，but not efficient
- flooding
- best effort

# BTC 架构

```
application layer: BTC block chain
------------------------------
network layer: P2P overlay network
```


## BTC 节点

BTC网络所有的节点是对等的，没有超级节点。在BTC网络中至少要一个种子节点（Seed node），它会告知它知道的BTC节点。节点间使用TCP链接，离开的时候不用通知其他节点，过一段时间别的节点没有你的消息会把离线节点删除。

## BTC网络特点

- 简单
- 鲁棒性
- 效率较低

每个节点维护一个邻居节点集合，消息传播采取flooding方式，节点收到消息会传播给所以邻居节点，同时记录该消息已经接收过了。
邻居节点的选举是随机的，不是拓扑结构，也不是物理距离，这样设计的目的是增强鲁棒性。

BTC中每个节点维护一个等待上链的交易集合，当节点收到一个交易信息，先验证交易合法性，然后会广播给邻居节点，如果消息收到过，会记录，且不会转发给邻居节点。

BTC区块发布和交易发布类似，BTC block大小有1M限制。
