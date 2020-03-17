## 地址确认机制和PGP全面支持简介

作者: Andy Yen
日期: Wed, 25日 7月 2018 23:35:08 +0800
链接: https://protonmail.com/blog/address-verification-pgp-support/

(开场白略)

……Protonmail 现在支持“地址确认”，一起的还有对PGP的全面支持。在这篇文章里我们将讨论这两个新功能，它们将显著提升我们的邮件安全和隐私。

### (邮件)地址确认

(开场白略)

为了让加密邮件为广大使用者接受的原因 Protonmail 做的一个决定就是把很多的加解密操作步骤隐去了。这样做虽然让数百万的人们用上了加密电邮而不需要懂任何密钥是什么，但这也意味着人们要给 Protonmail 一定程度的**信任**。

当然只要你开始使用任何互联网服务你就总得拿一定程度的信任出来。然而我们的目标是将必要的信任度降到最低，进而就算哪天 Proton 被入侵了，用户的加密通讯也不会被破坏。这也是我们的端对端加密和“零访问加密”技术背后的哲学，也是“地址确认”技术的哲学。

在以前，如果 Proton被入侵了，攻击者可以给用户发送一个假的公钥（同时还得模仿或谎称这公钥就是你的发件人的——译者注），这样你跟发件人的通信虽然是端对端加密了但加密对象显然错了，攻击者可以用他自己的私钥解开你的加密邮件了（这也叫“中间人攻击，MITM）。

“地址确认”技术能优雅地解决这个问题。我们考虑到这技术可能一般用户用不上，但有很多记者和活动人士需要进行高度敏感的通信，因此我们把这技术摆在高度优先的位置。

### “地址确认技术”的工作原理

从最新版的 Protonmail 开始，当你收到你的联系人的邮件时，你能在（网页版）该发件人名的旁边见到「信任这个公钥」(Trust Public Keys) 这样的选项。选择后系统就会保存该发件人的公钥并用你的私钥对这公钥进行数字签名。因此你一旦对该发件人的公钥表示信任（即签名）后，以后就看出这个公钥是否被篡改了。

https://protonmail.com/blog/wp-content/uploads/2018/07/ProtonMail-trusted-keys.mp4[8]

这样的话当你给这个联系人发邮件时就不用担心恶意攻击者（甚至可能包括 Protonmail喔）篡改或哄骗你用了恶意的公钥了。单这种技术就已经比别的加密电邮服务高不知哪里去了。你可以在这里[6]继续学习我们的技术。

### PGP 支持

我们还全面支持了 PGP的所有功能（指从页面上，PGP本身的功能本来任何人在命令行都可以用——译者注）。要全面的用上 PGP的功能，最好联系人双方都用 Protonmail。

但如果你的联系人还在用其他形式的 PGP（如命令行里的 GnuPG——译者注），那我们对 PGP的新支持将让你的人生轻松很多。Proton 现在支持从非 Proton 用户导入他们的公钥，对他们发送 PGP 加密邮件了。其次，反过来 Proton用户也能收到任何其它 PGP 用户发来的加密电邮了。还有，你可以导出你的公钥，并跟他人分享。


如果你已经是个 PGP 用户（即你已经在用一对PGP密钥了），你也可以导入你在用的PGP密钥对到 Proton，关联现有的 Proton 账号即可。

你可以在这里找到关于支持 PGP 的功能的更多细节[12]。

### Protonmail 的公钥服务器简介

最后，我们正式发布了我们的公钥服务器，这样让公钥的交换、分享更容易了。如果你已经在用 Protonmail，你的公钥已经在公钥服务器上了，可以自动发现（同时可以结合“地址确认”功能确保你找到正确的公钥）。如果一个非 Proton 的 PGP 用户想给你发加密电邮但还没拿到你的公钥，TA需要先找到你的公钥放哪儿了。如果你不事先把你的公钥放在一个公共的地方（比如你的网站页面上，或其他公钥服务器），对方一般都找不到的。

我们的公钥服务器就解决了这个问题啦。这是个中心化的地方，让任何人查找任何 Protonmail 邮箱的公钥（也包括非 Proton邮箱的公钥但上传给 Protonmail 保管的）。

我们公钥服务器地址就是 hkps://api.protonmail.ch (该链接不是给浏览器用的，是PGP专用地址)。但你可以从浏览器这样获得你想要的邮箱的公钥（把“username@protonmail.com”替换为实际的邮箱）：https://api.protonmail.ch/pks/lookup?op=get&search=username@protonmail.com

### 关于开放标准和邦联形式的总结

Today, ProtonMail is the world’s most widely used email encryption system[13], 
and for most of our users the addition of Address Verification and PGP support 
will not change how you use ProtonMail. In particular, setting up PGP 
(generating encryption keys, sharing them, and getting your contacts to do the 
same) is simply too complicated, and it is far easier for most people to simply 
create a ProtonMail account and benefit from end-to-end encryption and 
zero-access encryption without worrying about details like key management.

(前面几句自卖自夸的文字略)这里要提的重点是电子邮件系统的美妙就在于它的邦联性(federated)，意思就是任何一个人都可以自己搭建/实现/使用它。这门技术不会由某个实体来把持，它不是中心化的，也不会出现单点故障。虽然这种形式有很多限制，它仍是这个世界上最广泛使用且最成功的一门通讯工具。

PGP，因为它是构建于电邮系统之上，因此它也是邦联化的加密系统。不像其他加密通讯系统，比如 Signal 或Telegram，PGP 不属于任何一个人所有，一个中央服务器都没有，而也没有人强迫你使用某家的服务而不让用其他家的。我们相信加密通讯应该是开放的，不是个围墙花园。Protonmail 正是在实践和维护着这样一种支持 openPGP 标准的电邮系统，且我们的实现也是开源的。

(结束语略)

谢谢你的持续支持！

Best Regards,
The ProtonMail Team


本文首刊于 Protonmail 博客[20]。

所有链接
[1]: https://protonmail.com/blog/protonmail-v3-14-release-notes/ (链接)
[2]: https://protonmail.com/fr/bridge/ (链接)
[3]: https://vimeo.com/216747532 (链接)
[4]: https://protonmail.com/blog/what-is-end-to-end-encryption/ (链接)
[5]: https://protonmail.com/blog/zero-access-encryption/ (链接)
[6]: https://protonmail.com/support/knowledge-base/address-verification/ (链接)
[7]: https://protonmail.com/blog/encrypted-contacts-manager/ (链接)
[8]: https://protonmail.com/blog/wp-content/uploads/2018/07/ProtonMail-trusted-keys.mp4 (链接)
[9]: https://protonmail.com/blog/openpgpjs-3-release/ (链接)
[10]: https://protonmail.com/business (链接)
[11]: https://protonmail.com/blog/pgp-vulnerability-efail/ (链接)
[12]: https://protonmail.com/support/knowledge-base/how-to-use-pgp/ (链接)
[13]: https://protonmail.com (链接)
[14]: https://github.com/openpgpjs/openpgpjs (链接)
[15]: https://protonmail.com/donate (链接)
[16]: https://protonmail.com/support/knowledge-base/paid-plans/ (链接)
[17]: https://protonmail.com/signup (链接)
[18]: https://protonvpn.com/ (链接)
[19]: https://protonmail.com/blog/address-verification-pgp-support/ (链接)
[20]: https://protonmail.com/blog (链接)
