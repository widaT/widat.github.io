---
# type: docs 
title: Hugo
date: 2022-11-28T21:39:33+08:00
featured: false
draft: true
comment: true
toc: true
reward: true
pinned: false
carousel: false
series: Hugo
categories: [Hugo]
tags: [Hugo]
images: []
---

最近一两个月开始研究Hugo，有点心得和大家分享下。

<!--more-->

Hugo是基于Go开发的静态网站生成工具，相较于传统的cms的网站管理和生成方式相比，Hugo没有依赖数据库，它的数据来自配置文件和`markdown`文档.

Hugo现在最场景的场景是用在个人Blog搭建，导航类网站搭建。本人的Blog就是基于Hugo搭建的，另外本来还用Hugo开始批量制作了一批导航站群。

# Hugo的优点

- Hugo简单低代码，生成静态文件速度快

    使用hugo基本上写很少的代码，基本上就是维护配置文件和维护`markdown`文档。

- Hugo静态站低成本

    因为生成静态网站，你部署的时候非常简单，直接把整个生成的文件夹部署到线上即可。如果你没有自己的服务器，你可以免费部署在Github `netlify`上，`netlify`不限制网站数量，如果你有自己的域名还可以绑定自己的域名，非常方便。

- Hugo目前有些不错主题

    Hugo的主题相较于Wordpress那是少好几个数量级，但是现在已经有一些比较好用的Blog主题和一些好用的导航站主题，对我来说这些已经够用了。如果有同学对我的Blog主题感兴趣或者对我的导航站主题感兴趣，可以加我微信联系我。

# Hugo的缺点

- 使用的场景比较少

    Hugo的缺点也很明细，就是所有的数据需要自己组织，没有数据库，没有管理后台，无法做到大规模编辑提交和发布，更无法做到传统cms那样子权限管理，和审核机制。

- 做大型静态站比较力不从心

    Hugo的页面生成基于Go的`template`语法，每一个页面都需要一个模板，一般情况下主题会提供这类模板。如果你做大型静态站，还要考虑数据源的格式，然后根据数据源格式定制各种模板，相较于传统cms固定的数据源格式，Hugo这个步骤相当繁琐。