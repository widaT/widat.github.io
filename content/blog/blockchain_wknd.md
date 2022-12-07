---
# type: docs 
title: BTC挖矿
date: 2022-12-07T20:38:12+08:00
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

在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍BTC挖矿。

# 词条

- 51% attack


# BTC挖矿

BTC挖矿指的是不断调整block header中 nonce，使得 block header的hash值小于等于给定的目标阈值(H(block header) <= target)。

H(block header) <= target,BTC使用 sha256 hash算法。

# BTC出块难度

BTC为什么要调出块难度？-- 随着旷工越来阅读，算力越来越强，出块时间会越来越短。

出块时间越短会有什么问题？ -- BTC会大量的分叉，系统的总算力会分散，系统的共识有难度。

BTC的出块时间是10分钟。

BTC每出2016个块（大概14天)会调整出块难度，调整出块难道的代码是写在btc的代码里头。

# 矿池

矿池解决收益不稳定的问题。 矿池会降低挖矿难度，旷工挖到类似难度的nonce，提交到矿主，用来做工作量证明。