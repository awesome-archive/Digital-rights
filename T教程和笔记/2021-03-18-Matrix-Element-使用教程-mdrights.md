---
title: Matrix Element 使用教程
author: mdrights
---

# Matrix Element 使用教程

## 什么是 Matrix ？以及 Element？  

[Matrix](https://matrix.org) 是一种新型去中心化通讯网络，它让互相通讯的客户端可以不再依赖唯一的中心化的服务器，实现的是多中心的自选或自建的服务器作为服务端。目前在这个网络上的客户端软件有很多，其中最流行的是 [Element](https://element.io/)，在各操作系统平台均有版本，也有PC桌面和網頁版: https://app.element.io   

用最最简单的（人）话来说，就是 Matrix 这玩意其实借鉴了 Email 的连结方式。大家可曾记得每人的电子邮件地址：`abc@xyz.com` —— xyz.com 就是自己可以选择的邮件服务商，不同人可以选择不同的服务商，互相之间都可以通信。这就是古老但有效的去中心化的方式（只是到了现代，很多通讯软件都只允许用户使用官方的服务了，不能选择别人的，因为都不可能自己搭建该软件的服务器～呵呵）  

因此，在使用和注册 Matrix 的时候，请大家不要怕麻烦，选择其中一家服务者的服务器进行注册和登录，之后的互相通讯就没什么特别的了（服务器列表在下文的链接）。顺便说一句，只有这样，才能抵抗无论是政府的封锁和软件服务商自己的原因拒绝提供服务了。  

那么如果你还想问 Matrix 和 Element 的关系时，可以拿 Email 来帮忙理解：Email vs Gmail vs Outlook 客户端。 小明想使用 Email，于是她去 Gmail 注册了一个邮箱，然后她再在自己的电脑上打开了 Outlook 客户端，登录自己的 Gmail 账号，愉快地接收邮件了。所以 Matrix 好比 Email，下面的众多服务器（home server）就相当于 Gmail，Protonmail，Element 就好比邮件客户端（如 Outlook，Apple Mail，Thunderbird，QQ），三种东西基本都可以互相组合使用不会有什么例外。    

### 注册一个账号

那么由于服务端可以自选/自建，就不必一定用官方的 matrix.org 注册账号了（而且也被墙了）。  
目前有这些公开的他人运营的 Matrix 服务端（其实大多都是非营利组织的）：    
```  
https://www.hello-matrix.net/public_servers.php   
```  

启动 app 或桌面/网页版时应该都可见注册的入口，旁边可自行选择 `Other homeserver` 然后输入上面其中一个服务器地址作为自己帐号的所在服务器。  

![element-register](https://shitpost.to/i/wakknbccvu31kpez.png?key=ZJCyyeA8v7CVKJ7SHczPm0xxtXQflsSY)

### 加入一个房间

手机版请点击右下角「+」；桌面/网页版点击 Filter 输入框旁边的小指南针图标（看到了吗？是的我承认这UI的设计……），搜索关键词如`csobot` 应该能见到该房间，点击进入。 注意：只有公开的房间才能搜索到，不开放的房间可以通过邀请直接进入。  

![enter and find](https://shitpost.to/i/2uptfkqeln7vyiug.png?key=lilubSYvNhJWGWuSXdvcH3RPLp1HcVvj)

![join a room（样式略有差异）](https://assets.matters.news/processed/1080w/embed/57b482de-fcf5-401c-9ebd-f63e954651d4/screenshot-2019-7-29-riot.webp)

### 创建一个房间

手机版直接点击「+」就可选择「创建房间」选项；桌面/网页版也和加入房间时差不多，只是在进入之后的输入框上方点击文字超链接：`create a new room`。  

（由于 Matrix 和 Element 还在不断开发中，因此此文对应的是 2021年初的版本）  

祝自由地聊天顺利！
