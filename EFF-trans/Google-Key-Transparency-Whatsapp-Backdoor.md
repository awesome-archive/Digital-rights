[意译]

## Google Launches Key Transparency While a Trade-Off in WhatsApp Is Called a Backdoor
## 当Whatsapp的一个权宜之计被当成“后门”时，谷歌推出「密钥透明性」功能

The Guardian ran a sensational story on Friday claiming a backdoor was discovered in WhatsApp, enabling intelligence agencies to snoop on encrypted messages. Gizmodo followed up saying it's no backdoor at all, but reasonable, intended behavior. So what's really going on here?
「卫报」最近发表了一则新闻说Whatsapp被发现了个后门，能够让特工窥探到已加密的信息。Gizmodo 回应说这不是后门，是理性地有意而为之。那么这里面到底发生了什么？

### The lost phone, lost message dilemma
### 丢失的手机丢失的信息 之两难

The issue at question is WhatsApp's answer to the question of what applications should do when someone's phone number changes (or they reinstall their app, or switch phones).
出现问题的地方在 Whatsapp 应如何应对 用户的电话号码变更（或他们重装了应用，或更换了手机）。

Suppose Alice sends a message to Bob encrypted with Bob's key K1. Alice's message is stored encrypted at the server until Bob can connect and download it. This behavior is required for any app that allows asynchronous communications (meaning you can send a message to somebody while they are offline), which nearly all popular messaging apps support.
假设 Alice 给 Bob 发送了一条用Bob的密钥K1加密的信息。直到Bob连接并下载了之前，Alice的信息都是加密存储在服务器上。这个行为对任何有非实时通讯功能的应用都是必须的（也就是你可以在对方离线的时候发信息给ta）。基本上所有流行的通讯应用都有这功能。

Unfortunately, Bob just dropped his phone in a lake. Later on, Bob gets a new phone and reinstalls WhatsApp. On this new phone, the app will create a new key K2. There are two possible behaviors here:
不幸的是，Bob刚刚把自己手机掉湖里了。之后，Bob有了新手机并重装了 Whatsapp。在这新手机上，应用会生成一个新的密钥 K2。那么现在就可能出现两种做法：

-    Fail safe: The server can delete the queued message, since it was encrypted with K1, which no longer exists. Bob will never see the message. If Alice has turned on key change notifications, she will be warned that Bob is using a new key. She will be told that her message was not delivered and given the option to re-send it. This is what Signal does.
-   *「安全模式」*：服务器可以删除正在排队的信息，因为那条消息是以K1加密的，K1已经不存在了。Bob无论如何也看不到那信息的。如果 Alice 开启了密钥变更提醒，她将被警告 Bob 使用了新密钥。她会被告知她的消息发不出去，并可以选择重发。这就是 Signal 的做法。
 
-    Proceed: The server will tell Alice's phone that Bob has a new key K2, and to please re-encrypt the message for K2. Alice's phone will do this, and Bob will get the message. If Alice has turned on key change notifications, she will then be warned that Bob's key had changed. This is what WhatsApp does.
-    *「继续模式」*：服务器会告诉 Alice 那个 Bob 现在有了新密钥K2, 并会用K2重新加密一次原信息。Alice的手机会这样做，Bob就照样能收到消息。如果 ALice 开启了密钥变更提醒，她会被警告 Bob 的密钥变更了。这就是 Whatsapp的做法。

Note that the second behavior makes the service seem more reliable: it's one less way a message can fail to be delivered.
可见第二种做法可以让服务看上去更可靠：更少的可能性信息发不出去。

The issue here is that the second behavior opens a security hole: Bob need not have actually lost his phone for the server to act as if he has lost it. Acting maliciously, the server could pretend that Bob's new key is a key that the server controls. Then, it will tell Alice about this new key, but will not give Alice a chance to intervene and prevent the message from being sent. Her phone will automatically re-send the message, which the server can now read. Alice will be notified and can later attempt to verify the new fingerprint with Bob, but by then it will be too late.
所以问题就在第二种做法是安全漏洞的：Bob 不需要真的丢掉手机才让服务器以为他丢了手机。恶意地去做的话，服务器可以用一个服务器可控的密钥来当作是 Bob的新密钥。然后，它就告诉 Alice Bob有个新密钥，但不会给她机会去干涉和防止原先的信息继续被发送。她的手机仍将继续自动地重发那信息，这样服务器现在可以直接阅读了。Alice 会被通知并可以在之后尝试跟 Bob 验证新的密钥（指纹），但一切为时已晚。

By contrast, the first behavior of failing safe prevents this potential attack vector. As far as reliability, however, it also introduces a case in which messages could fail to be delivered.
相反，第一种做法就防止了这种潜在的攻击。但是至于稳定性，这就导致了信息发送不成功的情况。

### What to do if you use WhatsApp
### 如果你用 Whatsapp的话你希望怎么做？

If you are a high-risk user whose safety might be compromised by a single revealed message, you may want to consider alternative applications. As we mention in our Surveillance Self-Defense guides for Android and iOS, we don't currently recommend WhatsApp for secure communications.
如果你是高风险用户，一条暴露的信息都可能降低你的安全的话，你可能需要考虑其他的应用。就如我们在《自我防监控手册，安卓和iOS版》提到的，我们当前不推荐 Whatsapp作为安全通讯工具。

But if your threat model can tolerate being notified after a potential security incident, WhatsApp still does a laudable job of keeping your communications secure. And thanks to WhatsApp's massive user base, using WhatsApp is not immediate evidence of secretive activity.
但如果你的“威胁模式” 可以让你忍受在发生了潜在的安全事件之后才被通知的情况，Whatsapp 还是个值得称道的安全通讯工具。同时多亏 Whatsapp的大用户量，可以让它的用户不会马上被标识出在进行私密活动。

If you would like to turn on WhatsApp's key change notifications, go into Settings → Account → Security, and slide “Show security notifications” to the right.
如果你愿意开启 Whatsapp的密钥变更通知，到「设置」-> 「账户」-> 「安全」，向右划「显示安全提醒」。

### In defense of security trade-offs
### 在安全让位于可靠性中坚守

The difference between WhatsApp and Signal here is a case of sensible defaults. Signal was designed as a secure messaging tool first and foremost. Signal users are willing to tolerate lower reliability for more security. As anybody who's used Signal extensively can probably attest, these types of edge cases add up and overall the app can seem less reliable.
这里 Whatsapp和Signal 的区别其实就是是否有明智的默认选项。Signal本身就是作为安全通讯工具而优先设计。Signal用户愿意容忍更低的可靠性而让步于更多的安全性。任何深度使用 Signal的朋友都可以佐证，这些边际使用案例在整体上降低了应用的可靠性。

WhatsApp, on the other hand, was a massively popular tool before end-to-end encryption was added. The goal was to add encryption in a way that WhatsApp users wouldn't even know it was there (and the vast majority of them don't). 
而另一方面，Whatsapp 是个在加入端对端加密功能之前就大规模流行的工具。它的目标是让它的用户在没有察觉的情况下加上加密功能（当然大多数用户不想有这样的察觉）。

If encryption can cause messages to not be delivered in new ways, the average WhatsApp user will see that as a disadvantage. WhatsApp is not competing with Signal in the marketplace, but it does compete with many apps that are not end-to-end encrypted by default and don't have to make these security trade-offs, like Hangouts, Allo, or Facebook Messenger, and we applaud WhatsApp for giving end-to-end encryption to everyone whether they know it's there or not.
如果加密功能使得消息无法发送，那大多数 Whatsapp 用户会把这看成是它的缺陷。Whatsapp 在市场上不与 Signal竞争，但它于其他很多不端对端加密的应用竞争，那些应用都不做安全性上的权衡，比如 Hangouts、Allo、或脸书信使，我们赞赏 Whatsapp 把端对端加密带给了所有人，不管他们是否有这回事。

Nevertheless, this is certainly a vulnerability of WhatsApp, and they should give users the choice to opt into more restrictive Signal-like defaults.
然而不管怎样，这都是 Whatsapp 的一个弱处，他们须给用户选项，选择可以有像Signal一样更严格的默认选项。

*But it's inaccurate to the point of irresponsibility to call this behavior a backdoor.*
*但是管这种做法叫后门，是不准确且不负责任的。*

This is a classic security trade-off. Every communication system must make security trade-offs. Perfect security does no good if the resulting tool is so difficult that it goes unused. Famously, PGP made few security trade-offs early on, and it appears to be going the way of the dodo as a result.
这是经典的安全性权衡（议题）。每个通讯系统都必须做安全性权衡。如果整个工具最终因为难用而没人使用，再完美的安全性也是白搭。著名的 PGP 就是早期只做了很少的安全性让步，但结果走上了「被说三道四」的路子。

Ideally, users should be given as much control as possible. But WhatsApp has to set defaults, and their choice is defensible.
理想的话，用户应该得到尽可能多的控制。但 Whatsapp 不得不设置些默认，他们的选择是有道理/可辩驳的。

### Detecting bad behavior more easily with Key Transparency
### 通过「密钥透明性」更容易地探测不良动作

Coincidentally, Google just announced the launch of its new Key Transparency project. This project embraces a big security trade-off: given that most users will not verify their contacts' key fingerprints and catch attacks before they happen, the project provides a way to build guarantees into messaging protocols that a server's misbehavior will be permanently and publicly visible after the fact. For a messaging application, this means you can audit a log and see exactly which keys the service provider has ever published for your account and when.
正巧，谷歌刚发布了它的新「密钥透明性」项目。这个项目大大迎合了要让步安全性的考量：考虑到大部分用户不去验证他们通讯对象的密钥指纹，也不会在攻击发生之前就发现攻击，该项目提供一种思路，在通讯协议中构建担保，服务器的不当行为将会被永久和公开地可见。对一个通讯应用来说，这意味着你可以审计日志并且可以看见，你的哪个密钥服务是提供者在何时有公开过的。

This is a very powerful concept and provides additional checks on the situation above: Bob and anyone else with the appropriate permissions will know if his account has been abused to leak the messages that Alice sent to him, without having to verify fingerprints.
这是个非常强大的理念，它对以上情境提供了更多的检测：Bob和其他任何有合适权限的人都知道他的帐号是否被黑，泄露了 Alice发给他的消息，而这并不要求他们验证指纹。

It's important to note that transparency does not prevent the server from attacking: it merely ensures that attacks will be visible after the fact to more people, more readily. For a few users, this is not enough, and they should continue to demand more restrictive settings to prevent attacks at the cost of making the tool more difficult to use. But transparency can be a big win as a remedy against mass surveillance of users who won't tolerate any reduction in user experience or reliability for the sake of security.
需要知道的重点是这种「透明性」并不防止服务器被攻击：它只是确保了在攻击发生后对更多的人可见，且更快。对一小部分人来说，这还不够，他们应该会继续要求更严格的设置，来预防攻击，当然代价是工具会更难使用。但「透明性」仍会是大赢家，因为它对于那些不能忍受因安全而减损了用户体验和可靠性的用户来说，它是一种对抗大规模监控的补救措施。

Adding key transparency will not prevent a user from being attacked, but it will catch a server that's carried out an attack.
添加「密钥透明性」功能并不能防止用户被攻击，但它能够抓获那些执行攻击的服务器。

We are still a long way from building the perfect usable and secure messaging application, and WhatsApp, like all such applications, has to make tradeoffs. As the secure messaging community continues to work towards the ideal solution, we should not write off the current batch as being backdoored and insecure in their imperfect but earnest attempts.
我们距离构建完美好用且安全的通讯应用还有很长的路要走，而 Whatsapp还有所有这些应用，必须做些权衡。安全通讯社区继续往理想的解决方案努力，我们不能以所谓「后门」和「不安全」等名义抹杀当前的努力和各种还不完美但恳切的尝试。

<br />
<hr>
Copyleft by @mdrights
Released as CC-BY-SA 4.0
