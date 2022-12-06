---
# type: docs 
title: 区块链学习--BTC中协议
date: 2022-12-06T12:37:04+08:00
featured: false
draft: true
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
series: Blockchain
categories: [Blockchain]
tags: [Blockchain]
images: []
---

在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍，BTC中协议。

# 词条

- double spending attack
- create coin （铸币交易）
- coinbase transaction
- bitcoin script
- distributed consensus
- distributed hash table
- impossibility  result
- CAP theorem
- Paxos
- consensus in Bitcoin
- sybil attack (女巫攻击)
- longest valid chain
- forking attack
- orphan  block
- block reward

# 思考

1. 央行用央行的私钥签发一个100元数字货币，普通人用央行的公钥去验证真伪。这样的货币是否可行？   -- 不可行，存在双发攻击（double spending attack），数字货币不能伪造，但是可以被复制，这样就可以发多次。
2. 上面的法案加上每个数字货币有编号在央行记录每个编号在谁手里，支付的时候到央行确认。 -- 方案可行，但是每次交易都要央行确认太繁琐。 

3. 有没有办法解决每次要和央行确认的中心化方式 ，而又可以解决，双花攻击的问题？ -- 区块链可以，区块链可以追踪一个币的所有交易。

# BTC的交易过程

1. BTC交易包含两个部分，输出和输入，输入部分需要币的来源，输出部分需要给出收款人公钥的hash。在链上除了指向上一个区块的hash指针，还有指向前面某个交易的hash指针，来说明币的来源，这样子可以防止double spending。


2. 转账交易,A需要有签名，还要给出公钥，还需要有B的地址。BTC中没有直接找到某人的地址的功能。B要知道A的公钥，区块链都需要知道A的公钥，用公钥计算出hash和来源的输出部分hash要一致，这个过程使用btc脚本验证。


# 区块结构

- Block Header
    - revsion
    - hash of previous block header
    - merkle root hash
    - target 
    - nonce

- Block Body
    - transaction list

取hash只需要对Block header 取hash就可以。

# BTC中的共识协议

BTC中假设大部分节点是合法的。

BTC使用算力投票机制，H(block header)<= target，只有取得规范的Hash值，节点才有记账权，由于取得合法区块比较难，Btc出块通常比较慢。

BTC要求在最长合法链上接收区块。

当两个节点同时发布一个合法区块，这样子的区块会保持一段时间，当下一个区块出来，最长的链会保持，另外一个会丢弃。


# 出块奖励

每过21w区块，出块奖励就减半。