## 在线匿名FAQ - Online Anonymity FAQ

**更新日期：2016-12-19**  

> 前言：在线匿名不但是一门技术，更包含一些使用习惯、非技术的软技巧。如Whonix wiki的首页上说：“but staying anonymous is not just a technological problem. Anonymity is a complex problem without an easy solution. The more you know, the safer you can be. ”  
本人（@mdrights) 现总结一下关于这方面的常见问题。这些有的来自我经常混迹的Telegram群组：[Tor/Whonix/Tails匿踪隐私保护](https://telegram.me/joinchat/Cg4fLT2ZrhHeiRyj5N55cQ)（*在此向群友表示感谢*）；以及来自[Whonix文档](https://www.whonix.org/wiki/Documentation)、[Tails文档](https://tails.boum.org/)；其他的相关资源还有（英文）：EFF的[自我防卫指南](https://ssd.eff.org)、[prism-break.org](https://prism-break.org/en/)，[securityinabox.org](https://securityinabox.org/)，等等。  

0. 什么是“在线匿名”？它的原理是什么？  
仅仅使用化名绝对不能称为我们说的匿名（anonymity），自己的社交帐号、邮箱名称使用化名是无法对付国家机器的。因为当前的主流的互联网结构（暂不讨论BT等p2p网络）会记录每台联网的设备的唯一的身份信息，包括：IP地址、浏览器指纹印记(user-agent)、设备唯一编码（如网卡的MAC地址、SIM卡IMSI码、手机IMEI码）等。在线匿名的技术就是要伪装这些信息，让网络那边的有意无意的记录者无法知道某台设备的浏览/访问踪迹，或者说无法将某台设备的流量内容与真实设备对应起来，也就无法确定某些信息来自这台设备的使用者。

1. 我真的需要在线匿名吗？/ 谁需要在线匿名？  
简单回答：需要。网上言论和访问地址不被追踪是人的基本自由，就好像在物理世界里每个人也都有不被跟踪和监视的自由一样。  
深入回答：看你的实际需求是什么。由于目前的互联网技术本身没有为匿名而设计，因此在线匿名显得需要额外的技术和时间/学习成本，或许使用上还不大方便、或速度减慢。因此根据自己的实际需求/困境/受威胁模式，来确定/优化自己的匿名方案。
请看下一个问题。  

2. 什么是“威胁模式”（Threat Modes）  
从上一个问题我们可以知道，我们需要具体需求具体安排匿名技术的使用。具体需求具体分析，也就是说你的需求来自于你遇到怎样的风险/危险。
从需要隐匿的对象来看，我们有两类要隐匿的对象：一是本地网络网管和ISP，二是你所访问的（远端）服务器（如网站、聊天工具、邮件服务等）。如果你觉得你需要真正在物理位置上匿名，那你需要同时对付ISP和所访问的服务器，因为这两者都会与国家机器合作，泄漏你的具体地点。当然ISP（包括本地网管）更能帮忙定位你的具体位置，对付他们的重要性可能更大（修改你设备的Mac地址（手机还有IMSI码、IMEI码））；而对付远端服务器你只需要Tor就够了。
举个栗子，假如，你认为只要你一上网有关部门就会盯着你，或你正在躲避抓捕，流浪在某个地方，你需要全套的高度的匿名措施：eg. ss(R)+Tails+TorBrowser+Pidgin/OTR或Tox+MAC随机地址+无需实名的公共网络，或更多前置/后置代理……；如果你认为只要相关敏感网站上没有你的痕迹，你的目标应是防你所访问的网站等服务的记录和分析，你只需要个Torbrowser就够了。
这些都还要配上严谨的使用规范（如不能在匿名后登录自己的非匿名帐号等）。  

3. 加密还是匿名？  
这个问题背后似乎还是需求分析的问题。**加密可以让你的真正数据不被其他人看到，匿名是为了不让人知道这些数据是你的**。 一般认为，**需要匿名的地方通常是需要在公共/半公共的场合发表言论/信息的地方（因此没有必要加密嘛）；而加密更多是为了防止在个体间或封闭的群体之间通讯中被窃听**。后者通常需要确认双方的真实身份（所以有时需求是矛盾的）。当然也可能出现非常高安全的需求，那就两者都用上。   
一般我们认为，在墙国这样的形势（手机、网络通通实名）下，想（在ISP层面）匿名是很难的（当然你可以说你去找别人的手机/WIFI去用，但……你真的忍心去让朋友/陌生人替你去背你的锅么？另一方面，长时间使用另一个人的帐号上网，也会被关联到你自己，如果是朋友的话，关联可能性更高；如果是同时携带匿名的移动设备和非匿名的移动设备，这也会被分析你的物理移动轨迹而让匿名的设备成为徒劳）。  
所以，对大多数人来说，一个对策是把你的物理机器的信息与在网络远端留下信息做成不一样的。  

4. 在线匿名的基础技术有哪些？  
无需多说肯定是著名的 [Tor项目](https://torproject.org)，又称洋葱路由，它的主要功效是隐藏（伪装）你的真实IP地址（即显示出来的是个别的IP）。已经有不少中文的介绍了，见[这里](http://chinadigitaltimes.net/chinese/2016/01/tor-5-0-7-%E4%B8%AD%E6%96%87%E7%89%88%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B/)。Tor本身可以在命令行里运行，但更多的用户是使用Tor浏览器（在墙内需要用前置代理先翻墙，或找个安全的信赖的网桥）才是好的。  
当然，配备个[Tails Linux](https://tails.boum.org/)系统（所有流量走Tor的系统）也是好的。为什么？请看下一个问题。
除了Tor外，还有一些别的匿名技术，如Freenet，JonDonym，但它们都不够Tor成熟和实用，暂且不表。此外，隐匿了自己机器的IP地址，不等于就做到匿名了，请看[这个问题](#在线匿名我只需要Tor就够了吗？)。

5. 为什么要用Tails？  
Tails仍然值得推荐是因为它，一是基于自由开源的Debian GNU/linux+专业志愿社区审计和加固+Live USB载体。自由开源的代码为免去恶意代码提供了很大可能性；Live USB的形式可以做到所有修改不写入系统，重启恢复原来状态。更重要的是，它在多方面为广大非技术用户做了一站式隐私安全处理，包括可以设置MAC地址伪装，浏览器UA伪装，当然还有：所有流量走Tor。  
二是对非技术小白有容易上手的操作性（自带中文输入法虽然好像不大好用，具体请看我曾写过一篇[介绍](https://mdrights.github.io/os-observe/posts/2015/11/Tails-%E4%B8%AD%E6%96%87%E6%95%99%E7%A8%8B.html)）。

6. Tails在墙内如何把Tor用起来？  
常听到有人问这个问题。我分享我的做法是，用Raspberry Pi（比较小巧便携）做前置代理（eg ss+resocks全局），当然你也可以用其他设备（电脑、openWRT路由器或安卓手机）。另外的做法是你也可以用网桥，有两种：Tails/Tor提供的网桥（通常一公开出来很容易被墙/封）；其它网桥（建议最好自己自建网桥服务器VPS，用他人的网桥容易有风险，流量泄露的可能性高；当然前置翻墙用的代理（vps）最好也是自建的，且不分享给没有安全措施的设备使用）。对了，第三个方法是把Tails放进虚拟机里（如 Virtualbox），如果Host机不是VPN等全局代理的话，仍需要开http proxy让整个虚拟机走代理。但这有个风险就是如果Host机没做好安全措施的话，直接降低了Tails的安全性（_所以更加复杂而不推荐_)。
 Tails仍然值得推荐是因为它，一是基于自由开源的Debian GNU/linux+专业志愿社区审计和加固+Live USB载体；二是对非技术小白有容易上手的操作性（自带中文输入法虽然好像不大好用，具体请看我曾写过一篇[介绍](https://mdrights.github.io/os-observe/posts/2015/11/Tails-%E4%B8%AD%E6%96%87%E6%95%99%E7%A8%8B.html)）。

### 在线匿名我只需要Tor就够了吗？
不够。只伪装IP地址顶多可以做到：不让人知道你的当下物理地点，但很难不让人发现来自这台机器的流量/网络身份是你的。因为确定你的身份，除了用物理位置外，还有很多东西可以帮助确定/定位到某个特定的人（那个人特点越多越容易～）。EFF有过一个[研究](https://panopticlick.eff.org/)，从数学的角度来解释讲只要知道少至几个（如6个）属性/特点，就能定位世界上任何一个人。而当你用你的机器在网络浏览，留下的特质性信息还是蛮多的。
网卡MAC地址，浏览器User-Agent，就是两个应该伪装的地方。[EFF的网站](https://panopticlick.eff.org/)上可以看到你的浏览器的 User-Agent 跟多少其他访客的是一模一样的，你就理解了。

8. MAC地址伪装，浏览器UA伪装   
（本人略知一些方法，但要么不方便，要么效果不好，如果你有什么好的方法/工具，欢迎告诉我（issue/PR) :)。
MAC地址伪装方法
- on Linux 命令行：
`$ openssl rand -hex 6 | sed 's/\(..\)/\1:/g; s/./0/2; s/.$//'     # 生成随机MAC格式的字串（注意有效的MAC字串的首两位数必须是偶数）`
`# ip link set dev interface down                         # 先把网卡关闭`
`# ip link set dev interface address XX:XX:XX:XX:XX:XX  # X就是你刚才上面生成的随机字串`
`# ip link set dev interface up`

- on macOS 命令行：
```
$ sudo /System/Library/PrivateFrameworks/Apple80211.framework/Resources/airport -z
- $ sudo ifconfig en0 ether $(openssl rand -hex 6 | sed 's/\(..\)/\1:/g; s/./0/2; s/.$//')
- $ networksetup -detectnewhardware
```
或，
```
- $ openssl rand -hex 6 | sed 's/\(..\)/\1:/g; s/./0/2; s/.$//'     # 生成随机MAC格式的字串
- $ sudo ifconfig eth0 down hw ether XX:XX:XX:XX:XX:XX && ifconfig eth0 up
```

on Android：
（欢迎补充……我没用Android）

在自由的Linux上，还有不少方法，如用 macchanger，ArchWiki[收集的方法](https://wiki.archlinux.org/index.php/MAC_Address_Spoofing)也会是你的必读。

- 浏览器UA伪装：
请参考这篇[文章](http://www.howtogeek.com/113439/how-to-change-your-browsers-user-agent-without-installing-any-extensions/) （英文）（略复杂）；
再就是火狐浏览器插件[Switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/) ；[Chrome插件](https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg)（效果不好且可能有隐私隐患——理论上是插件都能看到/过滤所有浏览器上的内容）


9. 那，在线匿名需要做到那些非技术性的措施？  
这篇[Whonix wiki文章](https://www.whonix.org/wiki/DoNot)做了详细的介绍，匿名时*不要*做以下事情：

```
* 我匿名的时候我的网站是啥样子我想去看看
* 登录你的反映真实社会关系的（实名）社交帐号，并觉得自己在隐匿
* 坚决不要登录你之前不用tor登陆的帐号
* 不要登录你的银行帐号、淘宝或其他重要个人帐号，除非……
* 不要以为公共WIFI 有Tor一样的功效
* 防止 Tor中带Tor这样的情况
* 没有端对端加密就不要传送敏感信息了
* 不要透露关于你自己的身份信息
* 不要同一时间使用不同的网络身份
* 无事少登推特、非死不可、谷歌等
* 不要把不同匿名模式混着用：
    * 模式1: 自己匿名，任意接受者（公开）；
    * 模式2: 自己知道接受者是谁，双方都用Tor；
    * 模式3: 自己用Tor但是不匿名，任意接受者（公开）
    * 模式4: 自己不匿名，任意接受者（公开）
    
* 如果你不清楚后果就不要修改设置
* 不要把明网和Tor一起混着用
* 不要同时用匿名和非匿名技术连接同一个服务器／网站
* 不要将匿名和化名混为一谈
* 不要让自己成为第一个传播自己（网站）链接的人
* 不要打开陌生／随机文件或链接
* 不要用手机（移动设备）做验证方面的事  
```
（全文翻译正在本repo进行……）  


7. 手机上如何做到在线匿名？  
这也是很多朋友的疑问。  
简单回答：带移动模块的移动设备的（ISP层面）的隐匿性是非常差的。
参见 [EFF：手机的问题](https://ssd.eff.org/en/module/problem-mobile-phones)）：
深入回答：  
  - 国行/国产安卓手机您就放弃吧；
  - 苹果手机，唔，对匿名的需求也是不给力，因为非越狱的iOS系统不让用户进行深度设置（hack）；苹果也会发送用户/账户信息去它的服务器（虽然它征得了用户的同意）；
  - 大部分（90%？）的手机都是墙国生产制造，即使操作系统你深度定制，但硬件固件仍可以由设备制造商控制，喏，前几天不还有[新闻爆出后门](http://www.solidot.org/story?sid=50401)，悄悄发送用户的短信、位置等信息来么？
  - 移动运营商会记录SIM卡和其相关联的设备的信息（各种唯一编码），如果SIM卡实名，与其关联的设备也就无法匿名。因此如果想用手机匿名匿踪的话，非实名地买一台手机，不插自己用过的SIM卡，不装不信任的软件（比较流氓的软件也能出卖你），一次只做一件事。
  - 只要是手机（带移动信号模块），都难以排除它跟信号基站的通讯联络，即使飞行模式、拔掉Sim卡，也能定位。主要因为当前的移动网络系统（ss7）不开源，大多数人是不深入懂其中的坑并做审计。比如短信是可以被劫持、SIM卡是容易被复制的。已经有相关报道显示Telegram用的接受验证码的短信被有关部门[劫持并远程登录](http://www.solidot.org/story?sid=48167)。因此不要使用带短信验证码的服务（如果可以，用OTP/OAUTH等，随机一次性密码，如谷歌的Authenticator、UbikeyU盘、密钥U盘等）
  - 因此您还不如用一台没有移动信号模块的安卓平板，经过刷机等安全措施后，在不需手机验证等实名的网络下匿名上网。
  - 如果您不在乎ISP层面的匿名，可以参考Tor项目的 [Tor-Android尝试](https://blog.torproject.org/blog/mission-improbable-hardening-android-security-and-privacy)（其从远端的角度来伪装本机但无法防止ISP层面的匿名；但尊重用户选择和自由、大幅减少攻击面”，让其仍有很大可能成为一个安全加固的定制安卓系统——毕竟有机会让更多的人低成本地接触到网络也很重要。）
  - 只要可能，选择非 `made In China` 的手机，如台湾、韩国、印度制造，并且能选到低端手机的话（在你预算之内），时而更换手机也是极好的。
  
 
======

Copyleft  
This article is first published from [MDrights@github](https://github.com/mdrights/) under the GNU Free Document License.  
https://www.gnu.org/licenses/licenses.html#FDL  
Please keep this part reserved and unchanged.  

======
