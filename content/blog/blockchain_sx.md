---
# type: docs 
title: 区块链学习--BTC实现
date: 2022-12-06T21:43:43+08:00
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

在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍，BTC的实现。

# 词条

- transaction-base ledger
- UTXO: unspent transaction output
- total inputs = total outps
- transaction fee
- accout-base ledger
- Bernoulli trial: a random experiment with binary outcome 
- Bernoulli process: a sequence of independent Bernoulli trial memoryless
- Poisson process
- Bitcoin is sucured by mining
- selfish mining 

# UTXO

utxo的作用验证币在谁手里。

btc平均10分钟出一个块，平均4年出块奖励减半。

# BTC

btc所有总量为2100w。

## BTC安全

- 恶意节点是否能伪造交易 -- 不能A->M需要A的签名。
- 恶意节点是否能对一个B发两次 -- 可以多等几个区块确认（BTC需要6个块，大概需要1个小时）