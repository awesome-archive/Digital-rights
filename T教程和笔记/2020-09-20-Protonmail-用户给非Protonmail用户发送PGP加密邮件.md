---
date: 2020-09-20
title: Protonmail 用户给非 Protonmail 用户发送PGP加密邮件
---

# Protonmail 用户给非 Protonmail 用户发送PGP加密邮件

## 缘起

大家已经知道， Protonmail 用户之间的邮件肯定是用 PGP 端对端技术加密了的。但有时为了充分利用好 email 这种古老通讯方式优越的好处，我们仍需要跟其他邮件服务商的用户进行私密通讯。这时邮件到了对方那里，默认就是没有加密了的。

> 所谓 email 古老但优越的地方，就是它的去中心化。正如 Protonmail 的一篇[博客](https://protonmail.com/blog/address-verification-pgp-support/)（以及本人的[翻译](https://github.com/mdrights/Digital-rights/blob/master/M%E9%82%AE%E4%BB%B6%E5%AE%89%E5%85%A8/%E9%82%AE%E7%AE%B1%E5%9C%B0%E5%9D%80%E7%A1%AE%E8%AE%A4%E6%9C%BA%E5%88%B6%E5%92%8C%E5%85%A8%E9%9D%A2PGP%E6%94%AF%E6%8C%81-Protonmail_zh.md#%E5%85%B3%E4%BA%8E%E5%BC%80%E6%94%BE%E6%A0%87%E5%87%86%E5%92%8C%E9%82%A6%E8%81%94%E5%BD%A2%E5%BC%8F%E7%9A%84%E6%80%BB%E7%BB%93)）所说：

> ……电子邮件系统的美妙就在于它的邦联性(federated)，意思就是任何一个人都可以自己搭建/实现/使用它。这门技术不会由某个实体来把持，它不是中心化的……不像其他加密通讯系统，比如 Signal 或Telegram，PGP 不属于任何一个人所有，一个中央服务器都没有，而也没有人强迫你使用某家的服务而不让用其他家的。  

也就是说它的精妙就在于使用 email 的你可以选择你信任的邮件服务商（甚至可以自己搭建，如果你都不信任的话）。但今时今日，互联网这么发达，人们似乎忘了或放弃了这项选择的自由，宁愿依赖一些巨头而换取一些便利。而就像大家都只用三两个邮件服务商的话，那 email 作为 email 的意义也就不存在了，邮件服务商其实成了网盘服务商，大家其实只是同一家公司的网盘里互相发文件而已。  


## 怎么办

还好 Protonmail 为我们提供了 [Address Verification]() 功能（据我所知，[Mailfence](mailfence.com) 也有类似功能）—— 其实就是把 openPGP 的常用功能都在 Protonmail 页面呈现出来，方便大家直接使用 PGP 与其他也使用了 PGP 加密/签名的同学进行通讯。

以下介绍一下用法（参照 Protonmail [官方文档](https://protonmail.com/support/knowledge-base/address-verification/)）：  

- 这里假设大家对 PGP 这种加密方式有基本的了解，比如：  
```
	给对方发加密邮件需要使用对方的公钥，解密对方发来的邮件则只需要有自己的私钥（在 Protonmail，你的私钥都是 Proton 为你设置好了，当然也可以导出来）。
```

- 给对方发加密邮件我们需要先得到对方的公钥，可以叫对方通过别的方式给你，比如对方一般会在邮件附件里附上ta的公钥。

- 把对方的公钥加入到自己的通讯录里  
	- 去到 Contacts  
	- 选择你的对方好友  
	- 点击「Advanced Settings」（高级设置）  
![](https://protonmail.com/support/wp-content/uploads/2018/05/Contact-Details-Advanced-Settings-e1525392504605-920x257.png)  
	- 进入你可能发现 Public Keys 那里是空的，点击「Upload Key」上传对方的公钥  
![](https://protonmail.com/support/wp-content/uploads/2018/05/Contact-Advanced-Settings-920x837.png)  
	- 然后记得把「Configure External PGP」下方的两个开关**开启**，分别是「Encrypt」和 「Sign」。  

大功告成！

这时你再给对方发邮件的话，Protonmail 会自动使用对方的 PGP 公钥，准备发送加密邮件了（在收件人地址旁边会显示一个绿色带勾的小锁头）。  

如果收到对方发来的加密邮件，会显示蓝色带勾的小锁头（表示不但对方不但用了你的公钥加密，而且还用ta的私钥做了签名以证明是ta！）。 

![](https://protonmail.com/support/wp-content/uploads/2018/05/End-to-end-encrypted-from-verified-Protonmail-user-920x142.png)  

如果对方发来的邮件，显示一个蓝色小锁头但带了个叹号警告，说明对方可能为你加密了但ta没有给自己签名（有可能不是真的ta发出的）；如果小锁头是灰色的，说明对方没有使用 PGP 加密（而只是退一步用了 Proton 自己的服务器上存储加密）。 

![](https://protonmail.com/support/wp-content/uploads/2018/05/Sender-verification-failed.png)  


## 把你的公钥给对方

最后记得也要把你的公钥给到对方哦，这样人家才能给你发加密邮件。方法很简单，Protonmail 已经为你准备好了，只需在发邮件的页面如下操作：  

![](https://protonmail.com/support/wp-content/uploads/2018/05/Compose-Attach-Public-Key-600x513.png)  

若你想在每封邮件都默认带上自己的公钥，则可以在设置 ——> 安全页面勾选：  

![](https://protonmail.com/support/wp-content/uploads/2018/05/Advanced-Default-encryption-Settings-1024x215.png)    


## 注意事项

- Proton 把你的邮箱登录密码跟你的私钥相关联，如果**你的密码更改**了，你之前导入的对方的公钥会出现验证失效。当然 Protonmail 会提示你是否要进行 resign（再签名）—— 如果你确认对方的公钥无误，resigin 就好了。  

- 如果你改了你的密码，你可能需要把你的公钥重新导出来，给到想给你发邮件的人咯。  


