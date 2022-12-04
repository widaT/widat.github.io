---
# type: docs 
title: 区块链学习--BTC中的密码学原理
date: 2022-12-04T21:39:33+08:00
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
在B站看北京大学肖臻老师《区块链技术与应用》公开课。这边做一下学习笔记，这一节肖老师介绍，BTC的密码学原理。

<!--more-->

## 词条
- crypto-currency
- cryptographic hash fuction
- collision resistance
- burte-force
- hiding
- digital commitment(digital equivalent of a sealed envelope)
- puzzle friendly
- difficult to solve,but easy to verify

# Hash

Btc利用的密码学原理有两个功能，一个是hash，另一个是签名。

Hash三特性

- collision resistance

    Hash碰撞不可避免，输入空间远远大于输出空间，例如256hash，输出空间为2的256次方，输入空间可以是无限。
    collision resistance不是说不会发生hash碰撞，而是说不能人为制造碰撞。 

- hiding
    x->H(x)过程的单向的，无法通过H(x)推算出x。 hiding特性需要输入空间足够大，而且取值结果要足够均匀，使得蛮力求解计算量非常大。

    hiding和collision resistance 可以实现digital equivalent of a sealed envelope，可以预测一个内容，把内容hash，公布hash值，然后后面来验证预测结果。hash值可以保证预测的内容不可能被篡改，预测内容在验证前也不会有人知道。

    如果输入空间不够大，可以使用拼接随机数方案H(x||nonce)
- puzzle friendly

    一个输入不好预测输出结果，你只能一个一个算。如何你先得等前面7个0的hash，你想知道什么样的输入满足这样的hash结果，其实无法实现，只能一个一个去实验，没有捷径。    

# 签名

Btc中的账户管理：创立(public key ,private key)公私钥对。

加密用公钥，解密使用私钥。

btc账户签名用的是私钥，验证用的是公钥。