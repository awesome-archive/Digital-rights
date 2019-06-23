<span> </span>

<span>2016年11月16日星期三</span>
---------------------------------

<span id="4245320283755345073"></span>
### Tor浏览器用户手册

<a href="#tor浏览器用户手册" id="tor浏览器用户手册"></a>Tor浏览器用户手册
=========================================================================

### <a href="#文章目录" id="文章目录"></a>文章目录

1.  [写在前面](#1)
2.  [关于Tor浏览器](#2)
3.  [下载](#3)
4.  [第一次运行Tor浏览器](#4)
5.  [绕过审查](#5)
6.  [管理身份](#6)
7.  [洋葱服务](#7)
8.  [安全连接](#8)
9.  [安全滑块](#9)
10. [更新](#10)
11. [插件，扩展及JavaScript](#11)
12. [故障排除](#12)
13. [卸载](#13)
14. [推荐阅读](#14)

不久前Tor Project发布了[Tor浏览器](https://www.torproject.org/projects/torbrowser.html.en)的[用户手册](https://tb-manual.torproject.org/windows/en-US/index.html)，其中介绍了Tor浏览器的原理及使用方法。考虑到很多同学还没听说过Tor浏览器，或在使用过程中存在着种种误区，二翔子将其翻译成了中文，并加入了一些提示，希望可以帮助各位同学更加有效地保护自己的安全及隐私。
<span id="more"></span>

<a href="#1.-写在前面" id="1.-写在前面"></a><span id="1">1. 写在前面 </span>
============================================================================

随着隐私及安全意识的提升，越来越多的同学开始使用匿名工具保护自己。然而因为相关的中文资源（数量或质量）太过有限，对于匿名工具的原理和使用，不少同学都存在着一些误区。对此，二翔子将通过努力地了解和学习，把更多、更好的普及教程献给大家。而以Tor浏览器这样一款基础却又优秀的匿名软件作为开篇，可以说是再合适不过了。文中从第二小节起是二翔子对Tor Project发布的Tor浏览器[用户手册](https://tb-manual.torproject.org/windows/en-US/index.html)的翻译，其中*斜体字*部分是二翔子自己加入的提示内容。与往常一样，由于二翔子的知识和能力有限，如果文中有没说清楚的地方，希望大家能在评论区指出，以帮助二翔子将博文写得更好。

<a href="#1.1-tor,-tor,-tor-browser,-tor-browser-bundle" id="1.1-tor,-tor,-tor-browser,-tor-browser-bundle"></a>1.1 Tor, TOR, Tor Browser, Tor Browser Bundle
-------------------------------------------------------------------------------------------------------------------------------------------------------------

在有关Tor的讨论中，很多同学没有对以上词汇进行区分，结果给问题的描述和讨论造成了困难。为了方便起见，二翔子在此先对这些词汇做个约定。

### <a href="#1.1.1-tor还是tor？" id="1.1.1-tor还是tor？"></a>1.1.1 Tor还是TOR？

Tor的规范写法只有“Tor”一种，这一点在其官网上已经明确[指出](https://www.torproject.org/docs/faq#WhyCalledTor)了：)

### <a href="#1.1.2-tor还是tor-browser？" id="1.1.2-tor还是tor-browser？"></a>1.1.2 Tor还是Tor Browser？

很多同学喜欢用“Tor”指代Tor浏览器。但实际上Tor是一个很大的词汇，其既可以指Tor匿名网络，也可以指Tor社区；既可以指Tor客户端（又称裸Tor），又可以指Tor服务端；因此，当你想指Tor浏览器时最好就写“Tor浏览器”或者“Tor Browser”。

### <a href="#1.1.3-tor-browser还是tor-browser-bundle?" id="1.1.3-tor-browser还是tor-browser-bundle?"></a>1.1.3 Tor Browser还是Tor Browser Bundle?

通常情况下这二者可以说是一回事儿，但也有例外情况：比如说，如果你能确定出问题的是浏览器，那么就没必要说“Tor Browser Bundle”怎么怎么样了；再比如，在一些高级玩法中，需要把Tor Browser Bundle拆成Tor Browser和Tor客户端两部分（[Whonix](https://2xiangzi.blogspot.com/2016/05/whonix0.html)就是这样干滴），这时候的讨论就需要对名称加以区分。

<a href="#1.2-自测问题" id="1.2-自测问题"></a>1.2 自测问题
----------------------------------------------------------

如果读完这篇博文，你能回答出以下问题，说明相关知识你已经完全掌握了。**欢迎大家在评论区中写下自己的答案**，二翔子也会在一段时间后写出自己的答案：)

1.  小明喜欢匿名地在线冲浪，但他总觉得Tor浏览器用起来“不够顺手”，因此每次都是用Tor配合自己喜欢的（Chrome/Firefox/IE/Safari）浏览器使用。请问他这样做会失去Tor浏览器提供的哪些保护措施？能否分层次的说一说？
2.  为了防止IP泄漏，小明改为在自制的隔离虚拟机中进行在线冲浪，但他仍只用了自己喜欢的（Chrome/Firefox/IE/Safari）浏览器和Tor客户端。请问他这样做的匿名性如何？为什么？
3.  小红在[Tor Check](https://check.torproject.org/)（或其它IP检测）页面点击了Torbutton中的“为此站点使用新Tor线路”，却发现重新加载后的页面所显示的IP地址和上一次一样。假如Tor浏览器和该网页都工作正常，你觉得是什么原因导致了这一现象？

<a href="#2.-关于tor浏览器" id="2.-关于tor浏览器"></a><span id="2">2. 关于Tor浏览器</span>
==========================================================================================

Tor浏览器使用Tor匿名网络保护你的隐私及匿名性。使用Tor网络有主要有两个特点：

1.  你的互联网服务提供者(ISP)，以及任何能够监控你的本地流量的人，都将无法跟踪你的网络活动，其中包括你所访问的网站的地址及名称；
2.  你所使用的网络服务或访问的网站的提供者，以及所有能监控他们的人，都只能看到你的连接来自Tor匿名网络，而无法看到你的真实IP地址。因此，除非你自己透露之，否则他们无法得知你的身份。

除此之外，Tor浏览器还被设计得能够防止网站通过你的“指纹”或浏览器设置来识别你的身份。

默认设置下，Tor浏览器不会保存你的任何浏览历史。Cookie只在单次的会话中有效（退出Tor浏览器或请求新身份后失效）。

<a href="#2.1-tor工作原理" id="2.1-tor工作原理"></a>2.1 Tor工作原理
-------------------------------------------------------------------

Tor是一个建立在虚拟隧道之上的网络，旨在提升你在互联网上的隐私性及安全性。Tor会将你的网络流量随机地通过3台架设在Tor匿名网络之内的服务器（又称节点），然后最后一个节点（又称“出口节点”）再将你的流量发送至公共互联网。

[<img src="https://3.bp.blogspot.com/-LAcmeZxvwB8/WCvOU-Qz9PI/AAAAAAAAAG4/2yvp20eDk04Wf-7FmG8A0hRk24Mt9YR2gCPcB/s640/how-tor-works.png" width="640" height="351" />](https://3.bp.blogspot.com/-LAcmeZxvwB8/WCvOU-Qz9PI/AAAAAAAAAG4/2yvp20eDk04Wf-7FmG8A0hRk24Mt9YR2gCPcB/s1600/how-tor-works.png)

上面这张图片描绘了一个用户使用Tor浏览不同的网站。绿色屏幕的电脑代表了Tor网络中的各个节点，而那三把钥匙则代表了用户及各个节点之间的加密层。

*Tor之所以拿洋葱当图标，就是因为在其数据传输过程中各节点的层层解密（加密）就像剥洋葱一样。*

<a href="#3.-下载" id="3.-下载"></a><span id="3">3. 下载</span>
===============================================================

下载Tor浏览器最安全且最简单的办法是前往Tor Project的[官方网站](https://www.torproject.org)。你与Tor官网的通讯采用[HTTPS](#8)加密，使得他人难以破坏。

然而，有时你也可能无法访问Tor Project的网站：比如，当其被你所使用的网络屏蔽时。一旦遇到这样的情况，你可以采用如下办法下载Tor浏览器。

*尽管以下的各种方法已经是Tor下载受到审查的情况下的备用之选，但由于大陆的网络封锁极为严重，因此在没有其它翻墙工具辅助的情况下，只有使用Email的方式可能有效。*

<a href="#3.1-gettor" id="3.1-gettor"></a>3.1 GetTor
----------------------------------------------------

GetTor服务可以自动回复给你最新版本Tor浏览器的下载地址，其服务器广泛分布于不同位置，比如Dropbox，Google Drive及Github。

### <a href="#3.1.1-通过email使用gettor" id="3.1.1-通过email使用gettor"></a>3.1.1 通过Email使用GetTor

1.  发送邮件给gettor@torproject.org，在邮件的正文中根据你所使用的操作系统简单地写上“windows”，“osx”或者“linux”（不要加引号）；
2.  GetTor将会自动回复你一封电子邮件，其中包含Tor浏览器下载地址、密码学签名（用来校验下载到的软件包）、对软件包进行了签名的密钥的指纹及软件包校验值。你可能会收到“32位”和“64位”两种软件包，如何选择取决于你计算机类型。

### <a href="#3.1.2-通过twitter使用gettor" id="3.1.2-通过twitter使用gettor"></a>3.1.2 通过Twitter使用GetTor

1.  假如你想获取英文版的支持OS X的Tor浏览器，则发送私信“osx en”至@get\_tor（无需follow该账户）。

### <a href="#3.1.3-通过jabber/xmpp-(tor-messenger,-jitsi,-coyim)使用gettor" id="3.1.3-通过jabber/xmpp-(tor-messenger,-jitsi,-coyim)使用gettor"></a>3.1.3 通过Jabber/XMPP (Tor Messenger, Jitsi, CoyIM)使用GetTor

1.  假如你想获取中文版的支持Linux的Tor浏览器，则发送私信“linux zh”至gettor@torproject.org。

<a href="#3.2-satori" id="3.2-satori"></a>3.2 Satori
----------------------------------------------------

Satori是一个Chrome/Chromium浏览器的扩展，其允许你通过不同的下载源，下载多个安全及隐私相关程序。

使用Satori下载Tor浏览器：

1.  从Chrome App商店安装Satori；
2.  在你浏览器的Apps菜单选中Satori；
3.  打开Satori后选择你的语言偏好。之后的菜单会列出你所选择的语言可供下载的所有程序。找到你所使用的操作系统下的Tor浏览器。程序名称后的“A”和“B”代表了不同的下载源，点击之即可开始下载；
4.  待下载完成后，在Satori的菜单中找到“Generate Hash”选项，进入后点击“选择文件”；
5.  选择下载好的Tor浏览器软件包，Satori会计算并显示出其校验值，将这个值与原始校验值进行比较（原始校验值可以在下载开始后点击“checksum”找到）。如果两个校验值匹配则证明下载成功，如不匹配，则需要你（换个下载源）重新下载。

<a href="#4.-第一次运行tor浏览器" id="4.-第一次运行tor浏览器"></a><span id="4">4. 第一次运行Tor浏览器</span>
============================================================================================================

第一次运行Tor浏览器时会看到Tor网络设置窗口。通过它你可以选择直接或通过特殊配置连接到Tor网络。

<a href="#4.1-连接" id="4.1-连接"></a>4.1 连接
----------------------------------------------

[<img src="https://1.bp.blogspot.com/-asK_dYZcPJo/WCvOUUSDR3I/AAAAAAAAAG0/Pj71OWyfZ1A3qANN0iuxoLHlae8GSf01gCPcB/s640/connect.png" width="640" height="526" />](https://1.bp.blogspot.com/-asK_dYZcPJo/WCvOUUSDR3I/AAAAAAAAAG0/Pj71OWyfZ1A3qANN0iuxoLHlae8GSf01gCPcB/s1600/connect.png)

多数情况下你只需选择“连接”即可连接到Tor网络。点击后，一个显示Tor连接过程的进度条会弹出。如果你有一个相对快速的网络连接，却在某个进度点上卡住了，那么请前往之后的[故障排除](#12)小结。

<a href="#4.2-设置" id="4.2-设置"></a>4.2 设置
----------------------------------------------

[<img src="https://1.bp.blogspot.com/-8p6pvVqsrys/WCvOURwZy-I/AAAAAAAAAGw/Y_-U6tJwcdsvQcI8FzVKAKij6y6lnlaDQCPcB/s640/configure.png" width="640" height="526" />](https://1.bp.blogspot.com/-8p6pvVqsrys/WCvOURwZy-I/AAAAAAAAAGw/Y_-U6tJwcdsvQcI8FzVKAKij6y6lnlaDQCPcB/s1600/configure.png)

如果你确定你的连接遭到了审查，或者你想使用代理连接到Tor网络，那么请选择此项。Tor浏览器会带你进行一系列的配置选择。

1.  第一个窗口会问你所在的网络是否屏蔽或审查了Tor。如果你觉得没有的话请选择“否”。如果你确定自己的连接遭到了审查，或者你尝试了各种连接到Tor网络的方法却未成功，那么请选择“是”。接下来你会被带到[绕过审查](#5)窗口进行pluggable transport相关配置。
2.  下一个页面会问你是否要通过代理连接到Tor网络。在大多数情况下这都是没必要的。你会清楚的知道自己是否需要进行代理设置，这是因为相同的设置在你的其它浏览器上也会被使用。如果可能的话，请向你的网络管理员寻求指导。如果你连接无需代理，请点击“下一步”。
    [<img src="https://1.bp.blogspot.com/-EE0jdRHM70s/WCvOVrdIATI/AAAAAAAAAHE/yjIfKvM7HL4kDSCYHKNZth55zO73q8zmgCPcB/s640/proxy_question.png" width="640" height="526" />](https://1.bp.blogspot.com/-EE0jdRHM70s/WCvOVrdIATI/AAAAAAAAAHE/yjIfKvM7HL4kDSCYHKNZth55zO73q8zmgCPcB/s1600/proxy_question.png)

    [<img src="https://1.bp.blogspot.com/-CVhJn1ypBpw/WCvOVN812MI/AAAAAAAAAHA/qPgTJj6s_IwHI1r3WYFi4_PR1CMfXBhKACPcB/s640/proxy.png" width="640" height="526" />](https://1.bp.blogspot.com/-CVhJn1ypBpw/WCvOVN812MI/AAAAAAAAAHA/qPgTJj6s_IwHI1r3WYFi4_PR1CMfXBhKACPcB/s1600/proxy.png)

<a href="#5.-绕过审查" id="5.-绕过审查"></a><span id="5">5. 绕过审查</span>
===========================================================================

直接访问Tor网络有时可能会被你的互联网提供者或政府审查。Tor浏览器包含了一些帮助你绕过审查的工具。这些工具被称作“pluggable transports”。前往[Pluggable Transports页](https://tb-manual.torproject.org/windows/en-US/transports.html)可了解更多现阶段可用的传输类型。

<a href="#5.1-使用-pluggable-transport" id="5.1-使用-pluggable-transport"></a>5.1 使用 pluggable transport
----------------------------------------------------------------------------------------------------------

1.  如需使用pluggable transports请在第一次运行Tor浏览器时点击“配置”。
    你也可以在Tor浏览器运行时进行相关设置。办法是点击地址栏附近的绿色洋葱按钮，然后选择“Tor网络设置”。

    [<img src="https://1.bp.blogspot.com/-8p6pvVqsrys/WCvOURwZy-I/AAAAAAAAAGw/Y_-U6tJwcdsvQcI8FzVKAKij6y6lnlaDQCPcB/s640/configure.png" width="640" height="526" />](https://1.bp.blogspot.com/-8p6pvVqsrys/WCvOURwZy-I/AAAAAAAAAGw/Y_-U6tJwcdsvQcI8FzVKAKij6y6lnlaDQCPcB/s1600/configure.png)

2.  当被问及你的互联网提供者是否屏蔽了Tor网络时，选择“是”。

3.  选择“使用集成的网桥连接”。当前Tor浏览器有六种pluggable transport可供选择。
    [<img src="https://2.bp.blogspot.com/-WBnQ6Eoxpv0/WCvOahHQvFI/AAAAAAAAAHI/1tZ-J5fD1JQzwUQO59h5ZQqnDabHDaHpgCPcB/s640/bridges.png" width="640" height="518" />](https://2.bp.blogspot.com/-WBnQ6Eoxpv0/WCvOahHQvFI/AAAAAAAAAHI/1tZ-J5fD1JQzwUQO59h5ZQqnDabHDaHpgCPcB/s1600/bridges.png)

<a href="#5.2-该用哪种transport？" id="5.2-该用哪种transport？"></a>5.2 该用哪种transport？
-------------------------------------------------------------------------------------------

每一种pluggable transport的工作机制不尽相同（详情见[Pluggable Transports页](https://tb-manual.torproject.org/windows/en-US/transports.html)），它们各自的有效程度取决你所在的网络环境。

如果你是第一次尝试绕过审查，那么请将所有的transports都尝试一遍：obfs3, obfs4, ScrambleSuit, fte, meek-azure, meek-amazon。

如果你尝试了所有方法却都未见效，那么请手动输入网桥地址。了解更多有关网桥及其获取办法，请前往[Bridges页](https://tb-manual.torproject.org/windows/en-US/bridges.html)。

<a href="#6.-管理身份" id="6.-管理身份"></a><span id="6">6. 管理身份</span>
===========================================================================

当你访问某个网站时，能够记录你访问数据的不止有该网站的运营者。如今的大多数网站都使用着数不清的第三方服务，其中包括社交网络的“Like”按钮，分析追踪程序及广告信标。而这些服务均可以将你在不同网站的行为活动联系起来。

使用Tor网络可以阻止追踪者获取你的真实IP和物理位置，但即使没有这些信息，追踪者仍然有能力将你在不同网站的活动联系起来。因此，Tor浏览器包含了一些额外的特性，旨在让你掌控你的哪些网络活动会被视为同一身份所为。

<a href="#6.1-地址栏" id="6.1-地址栏"></a>6.1 地址栏
----------------------------------------------------

Tor浏览器将你的网络体验放在中心。即使你所访问的两个网站使用了相同的第三方服务，Tor浏览器会选择两条不同的Tor链路分别对这两个网站进行访问，因此追踪者无法得知这两次访问源自同一个人。

但另一方面，所有对某一单一网站进行的访问都将使用相同的Tor链路，这意味着你可以在不损失任何功能的情况下，使用不同的标签页或窗口访问该网站的不同页面。

[<img src="https://4.bp.blogspot.com/-IiYamch_Eg0/WCvNcKEwgoI/AAAAAAAAAGo/-Q2NcXtRc2wUsPjm5k6d58tiU3HDjwuPQCPcB/s640/circuit_full.png" width="640" height="303" />](https://4.bp.blogspot.com/-IiYamch_Eg0/WCvNcKEwgoI/AAAAAAAAAGo/-Q2NcXtRc2wUsPjm5k6d58tiU3HDjwuPQCPcB/s1600/circuit_full.png)

你可以看到一个当前标签页中Tor所用链路的示意图。

<a href="#6.2-通过tor登录" id="6.2-通过tor登录"></a>6.2 通过Tor登录
-------------------------------------------------------------------

虽然Tor浏览器是为用户匿名上网设计的，但有些情况下也需要使用Tor登录那些需要用户名，密码或其他身份信息的网站。

在你使用普通的浏览器登录网站或发送电子邮件时时，你会暴露你真实的IP地址与地理位置。但Tor浏览器有能力让你自己选择在你登录社交网络或电子邮箱时，要透露哪些信息。在你想要登录受到审查的网站时，使用Tor浏览器同样会有帮助。

当你要通过Tor登录某个网站时，以下几点你应牢记在心：

-   查看[安全连接页](#8)，了解有关如何在登录时确保连接安全的信息。
-   Tor从来不曾真正隐藏你的连接，它只能让其看来是来自世界上另一个地方。一些网站，如银行或电子邮件服务商，可能会将其解读为你的账户遭到入侵的标志，因而冻结你的账户。解决此类问题的唯一办法是遵从网站的账户回复流程，或联系网站的运营者并说明情况。

*说到用Tor登录账户，二翔子想提醒大家：由于你应该始终假设你所访问的网站会记录其能获取到的所有信息，所以只要你之前有一次没有使用匿名技术就登录了账户，那么不管你以后使用了多么严格的匿名技术，你仍然不是匿名的。*

<a href="#6.3-更换身份和链路" id="6.3-更换身份和链路"></a>6.3 更换身份和链路
----------------------------------------------------------------------------

[<img src="https://4.bp.blogspot.com/-o-DfwCjPh6Q/WCvOU2FjfwI/AAAAAAAAAH8/SqQ9O7UEPD89e1mupbymQOfbbthiOWhqgCPcB/s640/new_identity.png" width="640" height="451" />](https://4.bp.blogspot.com/-o-DfwCjPh6Q/WCvOU2FjfwI/AAAAAAAAAH8/SqQ9O7UEPD89e1mupbymQOfbbthiOWhqgCPcB/s1600/new_identity.png)

Tor浏览器在菜单设有”新身份“和”为此站点使用新Tor线路“选项。

### <a href="#6.3.1-新身份" id="6.3.1-新身份"></a>6.3.1 新身份

这个选项可以帮助你切断你接下来的浏览行为与之前的浏览行为间的联系。点击这个选项会关闭你目前所有的标签页及窗口，清空所有的隐私信息诸如cookie和浏览历史，并为之后所有连接使用新的Tor链路。Tor浏览器会提醒你所有的活动及下载都将被停止，因此在点击之前请先考虑清楚。

### <a href="#6.3.2-为此站点使用新tor线路" id="6.3.2-为此站点使用新tor线路"></a>6.3.2 为此站点使用新Tor线路

这个选项在当前使用的出口节点无法连接或正常加载你请求的网站时十分有用。点击它会让Tor浏览器换一条新的链路来加载当前的标签页或窗口。其它已被打开的标签页或窗口也会在它们被重新加载时使用新的链路。这一选项不会清空你的任何隐私信息，不会帮助你切断接下来的浏览行为与之前的浏览行为间的联系，不会影响到当前你与其它网站间的连接。

*应该指出，Tor会将出口节点相同但中间节点不同的链路视为不同的链路（之所以这样设计与Tor浏览器的[Adersary Mode](https://www.torproject.org/projects/torbrowser/design/#adversary)有关）。因此，在极少数情况下，点击”为此站点使用新Tor线路”后，其使用的出口节点并未改变。*

<a href="#7.-洋葱服务" id="7.-洋葱服务"></a><span id="7">7. 洋葱服务</span>
===========================================================================

洋葱服务（正式名称”隐藏服务“）是一些只能通过Tor网络连接的网络服务（如网站）。

洋葱服务拥有一些其它同样设在非私人网络的网络服务所不具备的优点：

-   洋葱服务器的位置和IP地址是隐藏的，这使得攻击者难以审查或识别运营者身份。
-   Tor用户与洋葱服务间的通讯是端对端加密的，因此你无需担心使用洋葱服务的网站并未开启[HTTPS加密](#8)。
-   洋葱服务的地址是自动生成的，因此运营者无需购买域名；URL中的.onion后缀帮助Tor确保其连接到正确的地址，且连接过程不被破坏。

<a href="#7.1-如何访问洋葱服务" id="7.1-如何访问洋葱服务"></a>7.1 如何访问洋葱服务
----------------------------------------------------------------------------------

[<img src="https://4.bp.blogspot.com/-WXIV7ghLPAw/WCvVO2OWI_I/AAAAAAAAAHc/O-KaLb8BfrYAKvwTZDqr7lbb4YcLZrszgCLcB/s640/onion_url.png" width="640" height="362" />](https://4.bp.blogspot.com/-WXIV7ghLPAw/WCvVO2OWI_I/AAAAAAAAAHc/O-KaLb8BfrYAKvwTZDqr7lbb4YcLZrszgCLcB/s1600/onion_url.png)

就像其它所有的网站一样，你必须知道要访问网站的地址。洋葱服务的地址是16位几乎随机的字母或数字加上”.onion“。

<a href="#7.2-故障排除" id="7.2-故障排除"></a>7.2 故障排除
----------------------------------------------------------

如果你无法访问洋葱服务，请先确保你输入的16位洋葱地址正确：即使是一个小错误也会造成Tor浏览器无法访问该网站。

如果访问仍不成功，请稍候再试。这可能是由于暂时的连接故障或网站的运营者没有事先预警就将该服务下线造成的。

你可以通过尝试连接[DuckDuckGo的洋葱服务](http://3g2upl4pq6kufc4m.onion/)来检验自己是否可以访问其他的洋葱服务。

<a href="#8.-安全连接" id="8.-安全连接"></a><span id="8">8. 安全连接</span>
===========================================================================

当使用未经加密的互联网传输你的个人信息时，它们可被窃听者轻易读取。当你登录某个网站时，你应该确认该网站启用了防止此类窃听的HTTPS加密技术。这一点可以看地址栏确认：如果当前连接是加密的，那么地址的开头会是”[https://“，而非”http://“。](https://“，而非”http://“。)

[<img src="https://4.bp.blogspot.com/-l5vQt49hYyg/WCvVPT1WTOI/AAAAAAAAAHg/GxcvT0-VBo07VAqJOv1g5794Zu9nb8TfgCLcB/s640/https.png" width="640" height="484" />](https://4.bp.blogspot.com/-l5vQt49hYyg/WCvVPT1WTOI/AAAAAAAAAHg/GxcvT0-VBo07VAqJOv1g5794Zu9nb8TfgCLcB/s1600/https.png)

下图是对当你（没有）使用Tor浏览器和（或）HTTPS 加密时，窃听者各将获得哪些信息的说明：
<https://tb-manual.torproject.org/windows/en-US/secure-connections.html>

-   点击”Tor“按钮，可以看到当你使用Tor时，观察者能了解到哪些信息。
-   点击”HTTPS“按钮，可以看到当你使用HTTPS加密时，观察者能了解到哪些信息。
-   当两个按钮都是绿色时，可以看到当你同时使用这两种工具时，观察者能了解到哪些信息。
-   当两个按钮都是灰色时，可以看到当这两种工具都没有使用时，观察者能了解到哪些信息。

可被查看到的数据信息包括：

-   Site.com： 你所访问的网站；
-   user / pw： 你的帐号和密码；
-   data： 传输的数据；
-   location： 你所在的地理位置/IP地址；
-   Tor： 你是否正在使用Tor；

*上面说的图表需要点击给出的链接进到原始页面查看。二翔子个人觉得那个动画特别不错，直观清楚地表示出了处于网络不同位置的攻击者在你采用不同安全措施的情况下所能获得的信息。另外要是能再加上Tor浏览器访问洋葱服务的部分，就更好了。*

<a href="#9.-安全滑块" id="9.-安全滑块"></a><span id="9">9. 安全滑块</span>
===========================================================================

Tor浏览器包含一个”安全滑块“，其允许你通过禁用一些会被用来攻击你的安全性和匿名性的网页功能，达到增强安全性的目的。提升Tor浏览器的安全等级会造成一些网页无法正常使用，因此你需要权衡你所需要的安全性与易用性。

*这里二翔子教大家一个平衡安全性与易用性的小方法：在使用过程中以你期望的安全等级为“常用等级”，偶有遇到显示或功能不正常却又必须使用的网站时，再逐级降低其安全等级，直到网站能正常工作为止。用完该网页后，再将安全等级恢复为你的“常用等级”。*

<a href="#9.2-进入”安全滑块“" id="9.2-进入”安全滑块“"></a>9.2 进入”安全滑块“
----------------------------------------------------------------------------

[<img src="https://4.bp.blogspot.com/-_OmD-wLO1z4/WCvVPdrdLFI/AAAAAAAAAH8/qC4Aik6RJ9gLQeAAkuzHiwX2P0CLr7S2QCPcB/s640/slider.png" width="640" height="454" />](https://4.bp.blogspot.com/-_OmD-wLO1z4/WCvVPdrdLFI/AAAAAAAAAH8/qC4Aik6RJ9gLQeAAkuzHiwX2P0CLr7S2QCPcB/s1600/slider.png)

”安全滑块“位于Torbutton的”隐私与安全设置“菜单中。

<a href="#9.3-安全等级" id="9.3-安全等级"></a>9.3 安全等级
----------------------------------------------------------

[<img src="https://4.bp.blogspot.com/-26gg16dnFdA/WCvVPiFmIfI/AAAAAAAAAH8/2boToiYZA4gJtOkV1jtRwp5TO58PeHWFwCPcB/s640/slider_window.png" width="638" height="640" />](https://4.bp.blogspot.com/-26gg16dnFdA/WCvVPiFmIfI/AAAAAAAAAH8/2boToiYZA4gJtOkV1jtRwp5TO58PeHWFwCPcB/s1600/slider_window.png)

提升”安全滑块“的安全等级将会禁用或部分禁用特定的浏览器功能，以达到避免可能的攻击的目的。

*说到避免攻击，每次Tor出现安全漏洞后，都会加一句：安全等级使用xx及以上的用户未受影响。*

### <a href="#9.3.1-高" id="9.3.1-高"></a>9.3.1 高

在这个等级，HTML5视频和音频需要通过NoScript点击播放；禁用全部JavaScript性能优化；禁用数学方程式的某些显示机制；禁用某些字体的渲染功能；默认禁用所有网站JavaScript；禁用大部分音视频类型；某些字体和图标可能无法正常显示。

### <a href="#9.3.2-中高" id="9.3.2-中高"></a>9.3.2 中高

在这个等级，HTML5视频和音频需要通过NoScript点击播放；禁用全部JavaScript性能优化；禁用数学方程式的某些显示机制；禁用某些字体的渲染功能；禁用某些图像类型；对于非HTTPS网站，默认禁用JavaScript。

### <a href="#9.3.3-中低" id="9.3.3-中低"></a>9.3.3 中低

在这个等级，HTML5视频和音频需要通过NoScript点击播放；禁用全部JavaScript性能优化，使得一些网站脚本执行变慢；禁用数学方程式的某些显示机制。

### <a href="#9.3.4-低" id="9.3.4-低"></a>9.3.4 低

在这个等级，所有浏览器功能都将被启用。该选项可提供最佳的用户体验。

<a href="#10.-更新" id="10.-更新"></a><span id="10">10. 更新</span>
===================================================================

Tor浏览器必须保持是最新的版本。如果你使用一个过时的版本，那么你的隐私与匿名性将很容易受到利用安全漏洞的攻击。

一旦有了新的版本，Tor浏览器就会出现更新提示：Torbutton标志会多出一个黄色的小三角，你也可能在打开Tor浏览器后看到升级指示。你可以使用自动或手动的方式更新。

<a href="#10.1-自动更新tor浏览器" id="10.1-自动更新tor浏览器"></a>10.1 自动更新Tor浏览器
----------------------------------------------------------------------------------------

1.  当被提示需要更新Tor浏览器后，点击Torbutton标志，并选择”检查Tor浏览器更新“；
    [<img src="https://4.bp.blogspot.com/-NpEiMNleCtk/WCvVQBwpYqI/AAAAAAAAAHs/jFvKX-GRaPUYgAlmwIeMez3fjWtYk3S1gCLcB/s640/update1.png" width="640" height="335" />](https://4.bp.blogspot.com/-NpEiMNleCtk/WCvVQBwpYqI/AAAAAAAAAHs/jFvKX-GRaPUYgAlmwIeMez3fjWtYk3S1gCLcB/s1600/update1.png)

2.  当Tor浏览器完成更新检查，点击”更新“按钮；
    [<img src="https://4.bp.blogspot.com/-R-xGmn44k20/WCvVQMxOGrI/AAAAAAAAAH8/uMdfh98lFeA-2y1fSMsIlwaVdMvv1xkIgCPcB/s640/update3.png" width="640" height="431" />](https://4.bp.blogspot.com/-R-xGmn44k20/WCvVQMxOGrI/AAAAAAAAAH8/uMdfh98lFeA-2y1fSMsIlwaVdMvv1xkIgCPcB/s1600/update3.png)

3.  待下载及安装完成后，重启Tor浏览器。现在你运行的就是最新版本的。
    [<img src="https://3.bp.blogspot.com/-VP92QIUhJ4E/WCvVQmthkKI/AAAAAAAAAH0/BeSebl8kLjw3GEJ8_pkrNDhCu_5vdXmzQCLcB/s640/update4.png" width="640" height="431" />](https://3.bp.blogspot.com/-VP92QIUhJ4E/WCvVQmthkKI/AAAAAAAAAH0/BeSebl8kLjw3GEJ8_pkrNDhCu_5vdXmzQCLcB/s1600/update4.png)

<a href="#10.2-手动更新tor浏览器" id="10.2-手动更新tor浏览器"></a>10.2 手动更新Tor浏览器
----------------------------------------------------------------------------------------

1.  当被提示需要更新Tor浏览器后，完成当前的浏览并关闭程序；
2.  通过删除其所在的文件夹的方式移除Tor浏览器（参见[卸载](#13)）；
3.  访问[](https://www.torproject.org/projects/torbrowser.html.en)<https://www.torproject.org/projects/torbrowser.html.en>,并下载最新版本的Tor浏览器，按往常一样安装之。

<a href="#11.-插件，扩展及javascript" id="11.-插件，扩展及javascript"></a><span id="11">11. 插件，扩展及JavaScript</span>
=========================================================================================================================

<a href="#11.1-flash播放器" id="11.1-flash播放器"></a>11.1 Flash播放器
----------------------------------------------------------------------

诸如Vimeo的视频网站需要Flash播放器插件来播放视频。不幸的是，该插件的运行相对独立于Tor浏览器，并且很难让其遵从Tor浏览器的代理设置。因此它可以泄露你的真实位置或IP地址给网站的运营者和其它观察者。出于这个原因，Flash在Tor浏览器中是被默认禁用的，并且也不推荐将其手动开启。

一些视频网站（如YouTube）提供了其它无需依赖Flash的视频传输方式。这些方式也许可以与Tor浏览器兼容。

<a href="#11.2-javascript" id="11.2-javascript"></a>11.2 JavaScript
-------------------------------------------------------------------

JavaScript是一种编程语言。它可以被网站用来提供互动元素诸如视频，动画，音频，状态时间表。不幸的是，JavaScript也可以被用来攻击浏览器，已达到对匿名用户去匿名化的效果。

Tor浏览器包含一个叫NoScript的附加组件（add-on）附加组件，可以点击窗口左上角的”S“标志使用它。它允许你控制JavaScipt将在哪些页面启用，也允许你在任何页面都禁用JavaScript。

[<img src="https://1.bp.blogspot.com/-0JBi-Aq3hgk/WCvVO5nD2mI/AAAAAAAAAHY/jd_T_J2j3TUskoVGL2jm_FK3CC33bnGcgCLcB/s640/noscript_menu.png" width="640" height="258" />](https://1.bp.blogspot.com/-0JBi-Aq3hgk/WCvVO5nD2mI/AAAAAAAAAHY/jd_T_J2j3TUskoVGL2jm_FK3CC33bnGcgCLcB/s1600/noscript_menu.png)

需要高安全性的用户应将Tor浏览器的[Security Slider](#9)设为”中高“（将在为启用HTTPS的网站禁用JavaScript）或”高“（将在所有网站禁用JavaScript）。然而，禁用JavaScript可能会使许多网站无法正常显示，因此Tor浏览器的默认设置是允许其在所有网站运行的。

<a href="#11.3-浏览器附加组件（add-ons）" id="11.3-浏览器附加组件（add-ons）"></a>11.3 浏览器附加组件（Add-ons）
----------------------------------------------------------------------------------------------------------------

Tor浏览器基于火狐浏览器，兼容火狐浏览器的任何附加组件和主题都可以被安装在Tor浏览器上。

但是，只有那些现在已经被默认包括在Tor浏览器上的附加组件被测试适合与Tor浏览器一起使用。安装任何其他的浏览器附加组件都可能破坏Tor浏览器的功能或导致严重的安全和隐私问题。Tor Project强烈建议不要安装额外的附加组件，并且也不会为它们提供任何支持。

<a href="#12.-故障排除" id="12.-故障排除"></a><span id="12">12. 故障排除</span>
===============================================================================

第一次打开Tor浏览器程序，你应该只需要点击”连接“按钮即可。

[<img src="https://1.bp.blogspot.com/-asK_dYZcPJo/WCvOUUSDR3I/AAAAAAAAAG0/Pj71OWyfZ1A3qANN0iuxoLHlae8GSf01gCPcB/s640/connect.png" width="640" height="526" />](https://1.bp.blogspot.com/-asK_dYZcPJo/WCvOUUSDR3I/AAAAAAAAAG0/Pj71OWyfZ1A3qANN0iuxoLHlae8GSf01gCPcB/s1600/connect.png)

<a href="#12.1-快速修理" id="12.1-快速修理"></a>12.1 快速修理
-------------------------------------------------------------

如果Tor浏览器无法直接连接，请尝试以下措施：

-   你电脑的系统时钟必须设置正确，否则Tor无法工作；
-   确保没有另一个Tor浏览器正在运行。如果你不确定是否有Tor浏览器在运行，请重启电脑；
-   确保杀毒软件没有在阻止Tor运行。如果不知道怎么做，你也许需要查看杀毒软件的文档；
-   暂时停用你的防火墙；
-   删除Tor浏览器并重新安装。重新安装时不要只是覆盖你之前的Tor浏览器文件；重新安装前应确保旧有的文件已被删除。

<a href="#12.2-你的连接受到了审查吗？" id="12.2-你的连接受到了审查吗？"></a>12.2 你的连接受到了审查吗？
-------------------------------------------------------------------------------------------------------

如果你还是不能连接，也许是因为你的互联网提供者审查了去往Tor网络的连接。阅读[绕过审查](#5)以寻求可能的解决办法。

<a href="#12.3-已知问题" id="12.3-已知问题"></a>12.3 已知问题
-------------------------------------------------------------

Tor浏览器处于持续开发的状态，而一些已知问题仍未解决。请前往[已知问题页](https://tb-manual.torproject.org/windows/en-US/known-issues.html)查看你遇到的问题是否已被列出。

<a href="#13.-卸载" id="13.-卸载"></a><span id="13">13. 卸载</span>
===================================================================

卸载Tor浏览器不会影响到你电脑上现存的任何软件或设置。

卸载Tor浏览器的办法很简单：

1.  找到Tor浏览器所在的文件夹。Windows下的默认位置是桌面；Mac OS X下的默认位置是Applications文件夹。Linux下并没有默认位置，但如果你运行的是英文版，则文件夹的名称是”tor-browser\_en-US“；
2.  删除Tor浏览器文件夹；
3.  清空回收站。

需要注意，整个过程无需使用操作系统中标准的”卸载“工具。

<a href="#14.-推荐阅读" id="14.-推荐阅读"></a><span id="14">14. 推荐阅读</span>
===============================================================================

1.  [The Design and Implementation of the Tor Browser](https://www.torproject.org/projects/torbrowser/design/#proxy-obedience)
2.  [Torbutton Design Documentation](https://www.torproject.org/docs/torbutton/en/design/)

------------------------------------------------------------------------

**版权声明**
============

[![知识共享许可协议](https://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)](https://creativecommons.org/licenses/by-nc-sa/3.0/)
本作品采用[知识共享署名-非商业性使用-相同方式共享 3.0 未本地化版本许可协议](https://creativecommons.org/licenses/by-nc-sa/3.0/)进行许可。

<span class="post-author vcard"> 发帖者 <span class="fn" itemprop="author" itemscope="itemscope" itemtype="http://schema.org/Person"> <a href="https://plus.google.com/105144493669632558142" class="g-profile" title="author profile"><span itemprop="name">二翔子</span></a> </span> </span> <span class="post-timestamp"> 时间： <a href="https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html" class="timestamp-link" title="permanent link">上午5:00</a> </span> <span class="reaction-buttons"> </span> <span class="post-comment-link"> </span> <span class="post-backlinks post-comment-link"> </span> <span class="post-icons"> <span class="item-control blog-admin pid-309686794"> [<img src="https://resources.blogblog.com/img/icon18_edit_allbkg.gif" class="icon-action" width="18" height="18" />](https://www.blogger.com/post-edit.g?blogID=7959751325273089682&postID=4245320283755345073&from=pencil "修改帖子") </span> </span>
<a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=4245320283755345073&amp;target=email" class="goog-inline-block share-button sb-email" title="通过电子邮件发送"><span class="share-button-link-text">通过电子邮件发送</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=4245320283755345073&amp;target=blog" class="goog-inline-block share-button sb-blog" title="BlogThis!"><span class="share-button-link-text">BlogThis!</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=4245320283755345073&amp;target=twitter" class="goog-inline-block share-button sb-twitter" title="共享给 Twitter"><span class="share-button-link-text">共享给 Twitter</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=4245320283755345073&amp;target=facebook" class="goog-inline-block share-button sb-facebook" title="共享给 Facebook"><span class="share-button-link-text">共享给 Facebook</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=4245320283755345073&amp;target=pinterest" class="goog-inline-block share-button sb-pinterest" title="分享到Pinterest"><span class="share-button-link-text">分享到Pinterest</span></a>

<span class="post-labels"> 标签： [匿名](https://2xiangzi.blogspot.com/search/label/%E5%8C%BF%E5%90%8D), [信息安全](https://2xiangzi.blogspot.com/search/label/%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8), [Tor](https://2xiangzi.blogspot.com/search/label/Tor) </span>

<span class="post-location"> </span>

<span id="comments"></span>
#### 21 条评论:

1.  

    ![](//lh4.googleusercontent.com/-h4-x9kzvjA8/AAAAAAAAAAI/AAAAAAAAAaQ/dHsS60shUXI/s35-c/photo.jpg)

    [音業](https://www.blogger.com/profile/13678458541060375922)<span class="icon user"></span><span class="datetime secondary-text">[2016年11月16日 下午8:13](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479298388766#c3681475100935850095)</span>

    &gt;&gt; 就像其它所有的网站一样，你必须直到你要访问网站的地址。洋葱服务的地址是16位几乎随机的字母或数字加上”.onion“。
    翔子啊，这句话中的“直到”也许是“知道”吧？

    <span id="bc_0_1MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1990112671">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3681475100935850095)</span></span>

    <span id="bc_0_1b+seedmG-D" kind="d"></span>
    <span id="bc_0_0TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_0TA" class="thread-arrow"></span><span id="bc_0_0TN" class="thread-count"><span id="bc_0_0TNT" style="display: none;"></span><span id="bc_0_0TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:33](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479317636919#c5366634570800254010)</span>

        To 音業
        多谢指出二翔子的笔误，现在已经更正啦:)

        <span id="bc_0_0MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=5366634570800254010)</span></span>

2.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年11月17日 上午2:24](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479320688115#c4998678626299054115)</span>

    好久没看到您发文了，加油！

    <span id="bc_0_3MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1260667726">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=4998678626299054115)</span></span>

    <span id="bc_0_3b+seedmHCD" kind="d"></span>
    <span id="bc_0_2TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_2TA" class="thread-arrow"></span><span id="bc_0_2TN" class="thread-count"><span id="bc_0_2TNT" style="display: none;"></span><span id="bc_0_2TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月19日 上午12:51](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479487879054#c3742559835165341625)</span>

        To 匿名
        感谢你的鼓励，二翔子会继续写出更多、更好的博文献给大家的:)

        <span id="bc_0_2MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3742559835165341625)</span></span>

3.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年11月17日 下午4:22](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479370949358#c2759177986282114757)</span>

    订阅了才能看到最新的

    <span id="bc_0_5MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-445857993">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=2759177986282114757)</span></span>

    <span id="bc_0_5b+seedmHDD" kind="d"></span>
    <span id="bc_0_4TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_4TA" class="thread-arrow"></span><span id="bc_0_4TN" class="thread-count"><span id="bc_0_4TNT" style="display: none;"></span><span id="bc_0_4TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月19日 上午12:53](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479488017480#c3837529725716495906)</span>

        To 匿名
        请问你说的“订阅”，是指订阅啥？

        <span id="bc_0_4MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3837529725716495906)</span></span>

4.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年11月18日 下午1:07](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479445646411#c8268584000024647354)</span>

    使用TBB打开谷歌云端硬盘时显示让重新登录，但重新登录后还是这样的提示，无法使用云端硬盘，该怎么半？

    <span id="bc_0_7MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-882293916">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=8268584000024647354)</span></span>

    <span id="bc_0_7b+seedmHED" kind="d"></span>
    <span id="bc_0_6TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_6TA" class="thread-arrow"></span><span id="bc_0_6TN" class="thread-count"><span id="bc_0_6TNT" style="display: none;"></span><span id="bc_0_6TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月19日 上午12:56](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479488203600#c950135773715297582)</span>

        To 匿名
        你可以试一试在安全滑块中短暂地：
        1. 将安全等级调至“中高”；
        2. 并关闭“限制第三方cookies”选项
        应该就可以解决你遇到的问题了:)

        <span id="bc_0_6MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=950135773715297582)</span></span>

5.  

    ![](//lh4.googleusercontent.com/-48oaFCJGPPU/AAAAAAAAAAI/AAAAAAAAABo/kLvWNbW28m0/s35-c/photo.jpg)

    [赵越](https://www.blogger.com/profile/01968732663194697365)<span class="icon user"></span><span class="datetime secondary-text">[2016年11月19日 下午2:52](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479538332356#c495087199827828564)</span>

    有没有翻译工具?

    <span id="bc_0_9MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1600168392">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=495087199827828564)</span></span>

    <span id="bc_0_9b+seedmHJD" kind="d"></span>
    <span id="bc_0_8TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_8TA" class="thread-arrow"></span><span id="bc_0_8TN" class="thread-count"><span id="bc_0_8TNT" style="display: none;"></span><span id="bc_0_8TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年12月2日 下午2:56](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480661800877#c7956296755992338660)</span>

        To 赵越
        你好,请问能否把问题描述得更清楚些？

        <span id="bc_0_8MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=7956296755992338660)</span></span>

6.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年11月20日 下午3:53](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1479628389288#c4924660906724058069)</span>

    做了一件好事，你会让很多人记住的。今后希望看到更多你的文章。

    <span id="bc_0_11MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1994972561">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=4924660906724058069)</span></span>

    <span id="bc_0_11b+seedmHKD" kind="d"></span>
    <span id="bc_0_10TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_10TA" class="thread-arrow"></span><span id="bc_0_10TN" class="thread-count"><span id="bc_0_10TNT" style="display: none;"></span><span id="bc_0_10TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年12月2日 下午2:57](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480661824655#c6706006080709723618)</span>

        To 匿名
        多谢你的鼓励，二翔子会继续努力的。

        <span id="bc_0_10MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=6706006080709723618)</span></span>

7.  

    ![](//img1.blogblog.com/img/blank.gif)

    勘误<span class="icon user"></span><span class="datetime secondary-text">[2016年11月26日 上午4:00](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480104045296#c3299101560732832446)</span>

    原文：文中从第二小结起是二翔子对Tor Project发布的Tor浏览器用户手册的翻译
    正作“第二小节”。
    原文：通常情况下着二者可以说是一回事儿
    正作“这二者”。
    原文：以及所用能监控他们的人
    “所用”正作“所有”。
    原文：Cookies只在单次的会话中有效
    原文：清空所有的隐私信息诸如cookies和浏览历史
    非英文环境，cookie没必要加s。
    原文：Tor会将你的网络流量随机地通过3架设在Tor匿名网络之内的服务器
    “3”可改成“3个”。
    原文：比如，当它在你所使用的网络被屏蔽时。
    “它在”可删去。
    原文：可能只有使用Email的方式可能有效
    “可能”重复。
    原文：GetTor服务可以自动回复给你你最新版本Tor浏览器的下载地址
    “你”重复。
    原文：请向你的网络管理员寻求直到
    正作“指导”。
    原文：在你使用普通的浏览器登录网站或发送电子邮件时时
    “时”重复。
    原文：但Tor浏览器有力能让你自己选择在你登录社交网络或电子邮箱时
    “力能”正作“能力”。
    原文：洋葱服务拥有一些其它同样设在非私人网络的网络服务所不具备的有点：
    正作“优点”。
    原文：并且页不推荐将其手动开启
    原文：页允许你在任何页面都禁用JavaScript
    正作“也”。
    原文：add-ons
    火狐翻译为“附加组件”。

    <span id="bc_0_13MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1805495042">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3299101560732832446)</span></span>

    <span id="bc_0_13b+seedmHLD" kind="d"></span>
    <span id="bc_0_12TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_12TA" class="thread-arrow"></span><span id="bc_0_12TN" class="thread-count"><span id="bc_0_12TNT" style="display: none;"></span><span id="bc_0_12TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年12月2日 下午2:57](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480661858514#c3662660274441869352)</span>

        To 勘误
        真是万分感谢你这么认真的帮助二翔子校对。
        二翔子现已将上述错误修正，并且会在今后发表博文前更加仔细的校核。
        谢谢你！

        <span id="bc_0_12MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3662660274441869352)</span></span>

8.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年11月29日 下午6:30](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480415440614#c8470718046594410728)</span>

    我通常都是在工作日使用Tor，周末双休日几乎不翻墙。如果政府掌握了我的这个特征，我匿名上网是不是也很危险？

    <span id="bc_0_15MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-612776020">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=8470718046594410728)</span></span>

    <span id="bc_0_15b+seedmHMD" kind="d"></span>
    <span id="bc_0_14TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_14TA" class="thread-arrow"></span><span id="bc_0_14TN" class="thread-count"><span id="bc_0_14TNT" style="display: none;"></span><span id="bc_0_14TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年12月2日 下午2:57](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1480661879290#c4711829013208054253)</span>

        To 匿名
        仅仅从你上述描述来看，有以下几点可以考虑：
        首先，如果你使用了前置代理或其它有效的方式来掩盖自己使用Tor的事实，那么（中国）政府恐怕很难知道你使用了Tor；
        其次，上述情况的信息量很小，如果你操作得当的话，即便被政府了解到这点信息，也不足以将你的匿名身份与真实身份关联起来；
        最后，你问的问题可以归为一大类问题，即：实际中，有哪些比较有效的针对Tor的去匿名化攻击需要我们注意。这个问题非常值得一聊，一方面是因为对相关知识的掌握可以让同学们更加有效的使用Tor保护自己；另一方面是因为（至少对很多中文用户来讲），对于相关问题许多同学还存在着一些误区。举个例子，很多同学一说到Tor就想到溯源攻击，但实际上这种攻击手段并不是最为有效的，因此真这么干的攻击者非常少，几乎就没有。相反，在对一些更加有效的攻击手段(比如身份关联攻击)的防范上，很多同学却疏忽了。

        <span id="bc_0_14MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=4711829013208054253)</span></span>

9.  

    ![](//img1.blogblog.com/img/blank.gif)

    是<span class="icon user"></span><span class="datetime secondary-text">[2016年12月19日 下午10:03](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1482156238011#c500317285839765840)</span>

    1你们打开赛风后会自动打开https://www.jesselanewellness.com/ 这个网站吗？这是赛风最新的广告还是劫持？用的是最新版的赛风，比较奇怪的是我在网关虚拟机里的赛风没这个问题，在隔离虚拟机里的赛风才会弹这个网址https://www.jesselanewellness.com 我恢复了快照也没用。主机还没试过
    2现在最新版的赛风的上层代理设置那儿有5个框，是不是只要填主机名称和端口的框，其他3个乱填就好了，我试了其他3个乱填是可以连的

    <span id="bc_0_17MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1158986784">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=500317285839765840)</span></span>

    <span id="bc_0_17b+seedmHOD" kind="d"></span>
    <span id="bc_0_16TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_16TA" class="thread-arrow"></span><span id="bc_0_16TN" class="thread-count"><span id="bc_0_16TNT" style="display: none;"></span><span id="bc_0_16TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//img1.blogblog.com/img/blank.gif)

        匿名<span class="icon user"></span><span class="datetime secondary-text">[2017年3月12日 上午11:53](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1489290823442#c1913099832742552991)</span>

        本地代理端口那个框是不能乱填的，必须与你浏览器的代理端口完全一致。

        <span id="bc_0_16MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-198741818">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=1913099832742552991)</span></span>

10. 

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2017年3月12日 下午12:26](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1489292781683#c6995584840153198419)</span>

    有哪些比较有效的针对Tor的去匿名化攻击需要我们注意。这个问题非常值得一聊
    这个问题不是值得一聊，而是非常重要，需要深入探讨交流。

    <span id="bc_0_18MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-198741818">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=6995584840153198419)</span></span>

11. 

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2017年4月7日 上午9:34](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1491528867958#c2029472368988396537)</span>

    翔子哥，你要好久才更新一次博客啊？我每次去编程随想的博客都要关注你的，结果……还是没得结果。

    <span id="bc_0_19MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1632219116">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=2029472368988396537)</span></span>

12. 

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2017年4月7日 上午9:41](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html?showComment=1491529314842#c3659369441638973835)</span>

    \[b\]试试\[/b\]你这里给可以

    <span id="bc_0_20MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1632219116">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3659369441638973835)</span></span>

[添加评论](javascript:;)

[加载更多...](javascript:;)

<span id="comment-form"></span>

<a href="https://www.blogger.com/comment-iframe.g?blogID=7959751325273089682&amp;postID=4245320283755345073" id="comment-editor-src"></a>

<span id="blog-pager-older-link"> <a href="https://2xiangzi.blogspot.com/2016/09/change-gpg-public-key-1.html" id="Blog1_blog-pager-older-link" class="blog-pager-older-link" title="较早的帖子">较早的帖子</a> </span> <a href="https://2xiangzi.blogspot.com/" class="home-link">主页</a>

订阅： <a href="https://2xiangzi.blogspot.com/feeds/4245320283755345073/comments/default" class="feed-link">帖子评论 (Atom)</a>

<span class="widget-item-control"> <span class="item-control blog-admin"> <a href="//www.blogger.com/rearrange?blogID=7959751325273089682&amp;widgetType=HTML&amp;widgetId=HTML2&amp;action=editWidget&amp;sectionId=sidebar-right-1" class="quickedit" title="修改"><img src="https://resources.blogblog.com/img/icon18_wrench_allbkg.png" width="18" height="18" /></a> </span> </span>

互联网上的二翔子
----------------

-   [二翔子的博客](https://2xiangzi.blogspot.com/)
-   [二翔子的邮箱及GPG公钥](https://2xiangzi.blogspot.com/p/blog-page.html)
-   [二翔子的Google+](https://plus.google.com/105144493669632558142/posts)
-   [二翔子的Twitter](https://twitter.com/2xiangzi)
-   [翻译组成员邮箱列表](https://2xiangzi.blogspot.com/p/last-child-margin-bottom-0px-horizontal.html)

<span class="widget-item-control"> <span class="item-control blog-admin"> <a href="//www.blogger.com/rearrange?blogID=7959751325273089682&amp;widgetType=LinkList&amp;widgetId=LinkList1&amp;action=editWidget&amp;sectionId=sidebar-right-1" class="quickedit" title="修改"><img src="https://resources.blogblog.com/img/icon18_wrench_allbkg.png" width="18" height="18" /></a> </span> </span>

博客订阅
--------

[![RSS 订阅网址](https://lh5.googleusercontent.com/-6oleSG-DCYU/SZ5PE7w1kgI/AAAAAAAAAao/MTZz9nhJ2Dw/feed-icon-animated.gif)](https://feeds.feedburner.com/blogspot/2xiangzi "RSS 订阅") [![邮件订阅网址](https://lh6.googleusercontent.com/-aq_Tc06jlUM/UcMcVsTB6xI/AAAAAAAAAk8/wSTQfl9ytCQ/email-icon.png)](https://feedburner.google.com/fb/a/mailverify?uri=blogspot/2xiangzi "邮件订阅")

<span class="widget-item-control"> <span class="item-control blog-admin"> <a href="//www.blogger.com/rearrange?blogID=7959751325273089682&amp;widgetType=HTML&amp;widgetId=HTML4&amp;action=editWidget&amp;sectionId=sidebar-right-1" class="quickedit" title="修改"><img src="https://resources.blogblog.com/img/icon18_wrench_allbkg.png" width="18" height="18" /></a> </span> </span>

博客归档
--------

-   <a href="javascript:void(0)" class="toggle"><span class="zippy toggle-open"> ▼  </span></a> <a href="https://2xiangzi.blogspot.com/2016/" class="post-count-link">2016</a> <span class="post-count" dir="ltr">(7)</span>
    -   <a href="javascript:void(0)" class="toggle"><span class="zippy toggle-open"> ▼  </span></a> <a href="https://2xiangzi.blogspot.com/2016/11/" class="post-count-link">十一月</a> <span class="post-count" dir="ltr">(1)</span>
        -   [Tor浏览器用户手册](https://2xiangzi.blogspot.com/2016/11/tor-browser-user-manual.html)

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2016/09/" class="post-count-link">九月</a> <span class="post-count" dir="ltr">(2)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2016/05/" class="post-count-link">五月</a> <span class="post-count" dir="ltr">(2)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2016/04/" class="post-count-link">四月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2016/01/" class="post-count-link">一月</a> <span class="post-count" dir="ltr">(1)</span>

<!-- -->

-   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/" class="post-count-link">2015</a> <span class="post-count" dir="ltr">(7)</span>
    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/12/" class="post-count-link">十二月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/11/" class="post-count-link">十一月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/10/" class="post-count-link">十月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/09/" class="post-count-link">九月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/08/" class="post-count-link">八月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/07/" class="post-count-link">七月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2015/04/" class="post-count-link">四月</a> <span class="post-count" dir="ltr">(1)</span>

<span class="widget-item-control"> <span class="item-control blog-admin"> <a href="//www.blogger.com/rearrange?blogID=7959751325273089682&amp;widgetType=BlogArchive&amp;widgetId=BlogArchive1&amp;action=editWidget&amp;sectionId=sidebar-right-1" class="quickedit" title="修改"><img src="https://resources.blogblog.com/img/icon18_wrench_allbkg.png" width="18" height="18" /></a> </span> </span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><div id="footer-2-1" class="foot no-items section">

</div></td>
<td><div id="footer-2-2" class="foot no-items section">

</div></td>
</tr>
</tbody>
</table>

“简单”主题背景. 由 [Blogger](https://www.blogger.com) 提供支持.

<span class="widget-item-control"> <span class="item-control blog-admin"> <a href="//www.blogger.com/rearrange?blogID=7959751325273089682&amp;widgetType=Attribution&amp;widgetId=Attribution1&amp;action=editWidget&amp;sectionId=footer-3" class="quickedit" title="修改"><img src="https://resources.blogblog.com/img/icon18_wrench_allbkg.png" width="18" height="18" /></a> </span> </span>
