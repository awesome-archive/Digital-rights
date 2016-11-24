## 在线匿名FAQ - Online Anonymity FAQ

> 前言：在线匿名不但是一门技术，更包含一些使用习惯、“社会学”的软技巧。如Whonix wiki的首页上说：“but staying anonymous is not just a technological problem. Anonymity is a complex problem without an easy solution. The more you know, the safer you can be. ”  
本人（@mdrights) 现总结一下关于这方面的常见问题。这些有的来自我经常混迹的Telegram群组：[Tor/Whonix/Tails匿踪隐私保护](https://telegram.me/joinchat/Cg4fLT2ZrhHeiRyj5N55cQ)（*在此向群友表示感谢*）；以及来自[Whonix文档](https://www.whonix.org/wiki/Documentation)、[Tails文档](https://tails.boum.org/)；其他的相关资源还有（英文）：EFF的[自我防卫指南](https://ssd.eff.org)、[prismbreak.org](https://prism-break.org/en/), [securityinabox.org](https://securityinabox.org/)，等等。  

0. 什么是“在线匿名”？  
仅仅使用化名绝对不能称为我们说的匿名（anonimity），自己的社交帐号、邮箱名称使用化名是无法对付国家机器的。我们需要用专门的技术来：隐匿自己的真实IP地址、真实的浏览器指纹印记、设备唯一编码（如网卡的MAC地址、SIM卡IMSI码、手机IMEI码）。一台普通的Windows、安卓系统上的软件就能轻松获取这些信息。

1. 我真的需要在线匿名吗？/ 谁需要在线匿名？  
简单回答：需要。网上言论和访问地址不被追踪是人的基本自由，就好像在物理世界里每个人也都有不被跟踪和监视的自由一样。  
深入回答：看你的实际需求是什么。由于目前的互联网技术本身没有为匿名而设计，因此在线匿名显得需要额外的技术和时间/学习成本，或许使用上还不大方便、或速度减慢。所以你可以根据你的实际情况酌情使用。请看下一个问题。
[待拓展……]

2. 清楚了解自己的“受威胁模式”（Threat Modes），明确需求  
从上一个问题我们可以知道，我们需要具体需求具体安排匿名技术的使用。具体需求具体分析，比如假如你正在躲避抓捕，流浪在某个地方，你需要全套的高度的匿名措施：eg. ss(R)+Tails+TorBrowser+Pidgin/OTR+无需实名的公共网络，或更多前置/后置代理……；如果你认为你的目标是防你所访问的网站等服务的记录和分析，你只需要个Torbrowser或只要代理就够了；如果你担心ISP（及其背后的国家机器）对你的定位那你需要的修改你设备的Mac地址（手机还有IMSI码、IMEI码）。这些都还要配上严谨的使用规范（如不能登录自己的帐号等）。  

3. 在线匿名的最基础技术是什么？  
无需多说肯定是著名的 [Tor项目](https://torproject.org)，又称洋葱路由，已经有不少中文的介绍了，见[这里](http://chinadigitaltimes.net/chinese/2016/01/tor-5-0-7-%E4%B8%AD%E6%96%87%E7%89%88%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B/)。因此至少配备个Tor浏览器（在墙内需要用前置代理先翻墙，或找个安全的信赖的网桥）才是好的。  
当然，配备个Tails Linux系统也是好的，请看下一个问题。

4. Tails在墙内如何把Tor用起来？  
常听到有人问这个问题。我分享我的做法是，用Raspberry Pi（比较小巧便携）做前置代理（eg ss+resocks全局），当然你也可以用其他设备（电脑、openWRT路由器或安卓手机）。另外的做法是你也可以用网桥，有两种：Tails/Tor提供的网桥（通常一公开出来很容易被墙/封）；其它网桥（建议最好自己自建网桥服务器VPS，用他人的网桥容易有风险，流量泄露的可能性高；当然前置翻墙用的代理（vps）最好也是自建的，且不分享给没有安全措施的设备使用）。  
Tails仍然值得推荐是因为它，一是基于自由开源的Debian GNU/linux+专业志愿社区审计和加固+Live USB载体；二是对非技术小白有容易上手的操作性（自带中文输入法虽然好像不大好用，具体请看我曾写过一篇[介绍](https://mdrights.github.io/os-observe/)）。

5. 那，在线匿名需要做到那些非技术性的措施？  
这篇[Whonix wiki文章](https://www.whonix.org/wiki/DoNot)做了详细的介绍：

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
（待深入翻译……）  

6. 手机上如何做到在线匿名？  
这也是很多朋友的疑问。我的理解（参见 [EFF：手机的问题](https://ssd.eff.org/en/module/problem-mobile-phones)）：
  - 国行/国产安卓手机您就放弃吧；
  - 苹果手机，唔，对匿名的需求也是不给力，因为非越狱的iOS系统不让用户进行深度设置（hack）；苹果也会发送用户/账户信息去它的服务器（虽然它征得了用户的同意）；
  - 大部分（90%？）的手机都是墙国生产制造，即使操作系统你深度定制，但硬件固件仍可以由设备制造商控制，喏，前几天不还有[新闻爆出后门](http://www.solidot.org/story?sid=50401)，悄悄发送用户的短信、位置等信息来么？
  - 只要是手机（带移动信号模块），都难以排除它跟信号基站的通讯联络，即使飞行模式、拔掉Sim卡。主要因为当前的移动网络系统（ss7）不开源，大多数人是不深入懂其中的坑并做审计。比如短信是可以被劫持、SIM卡是容易被复制的。已经有相关报道显示Telegram用的接受验证码的短信被有关部门[劫持并远程登录](http://www.solidot.org/story?sid=48167)。
  - 因此您还不如用一台没有移动信号模块的安卓平板，经过刷机等安全措施后，在不需手机验证等实名的网络下匿名上网。
  - 至于仍然希望致力于用安卓手机在线匿名的朋友，建议参考Tor项目的 [Tor-Android尝试](https://blog.torproject.org/blog/mission-improbable-hardening-android-security-and-privacy)（但可能只是“尊重用户选择和自由、大幅减少攻击面”；但仍不失为有意义的安全加固的安卓系统——毕竟开源的安卓有机会让更多的人低成本地接触到网络。）
  - 只要可能，选择非 `made In China` 的手机，如台湾、韩国、印度制造，并且能选到低端手机的话（在你预算之内），时而更换手机也是极好的。
  
 
======

Copyleft  
This article is first published from @MDrights under the GNU Free Document License.  
https://www.gnu.org/licenses/licenses.html#FDL  
Please keep this part reserved and unchanged.  

======
