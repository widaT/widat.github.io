---
# type: docs 
title: 区块链学习--BTC中的数据结构
date: 2022-12-05T12:40:33+08:00
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

在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍BTC中的数据结构。

<!--more-->

## 词条

- hash pointers
- genesis block
- most recent block
- Merkle tree
- binary tree
- merkle proof
- sorted merkle tree

# Hash指针

Hash指针除了存结构体地址，还有存结构体的hash值。这样子可以不仅仅可以找到结构体位置，判断结构体是否被修改。

BTC是区块链，使用Hash指针代替普通指针。区块链上任何block内容发生变化，后面的指针就会对不上。

最后一个block的hash值，就可以检查之前链上的区块是不是有变化。

# Merkle tree

Merkle tree 最底层是data blocks，上层是hash pointers。 根hash值就可以检测block上的内容是否被修改。

每一个区块分为， block header和block body。 block header只存储根hash值。

Merkle tree可以提供Merkle proof。

BTC分轻节点和全节点，轻节点只保存block header.轻节点验证交易需要使用merkle proof，轻节点向任意一个全节点请求验证，全节点返回相应hash指针，轻节点从下往上验证
hash值，直到根节点hash值和block header的值一样，才能证明交易在某个block中。


# Hash指针

Hash指针需要有向无环，有环的会有循环依赖问题。