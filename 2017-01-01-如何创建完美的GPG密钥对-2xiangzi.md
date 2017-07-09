<span> </span>

<span>2016年9月6日星期二</span>
-------------------------------

<span id="6125275056611834563"></span>
### 如何创建完美的GPG密钥对

<a href="#如何创建完美的gpg密钥对" id="如何创建完美的gpg密钥对"></a>如何创建完美的GPG密钥对
===========================================================================================

### <a href="#文章目录" id="文章目录"></a>文章目录

1.  [写在前面](#1)
2.  [使用副签名密钥的好处及原理](#2)
3.  [创建完美的GPG密钥对](#3)
4.  [简单回顾](#4)
5.  [使用日常密钥对](#5)
6.  [意外发生后的应对措施](#6)
7.  [推荐阅读](#7)

[GnuPG](https://www.gnupg.org/)是一款非常优秀加密软件，它在我们的数字生活中扮演了极其重要的角色。越来越多的同学都开始尝试用它进行日常的签名、验证、加密和解密等工作。虽然与其相关的中文教程已经有很多，但一篇详细介绍如何更好的使用它的教程却没有被二翔子找到。于是乎，二翔子就参考了数篇与其相关的优秀英文资源（具体资源第七节*推荐阅读*有列出），写出这篇博文，希望大家都能够用加密技术保护好自己的隐私及生命。
<span id="more"></span>

<a href="#1.-写在前面" id="1.-写在前面"></a><span id="1">1. 写在前面 </span>
============================================================================

开始正文之前，有几点想和大家说明：

1.  此篇博文并非是关于对非对称加密算法或GnuPG基本操作的教程（相关教程已在*推荐阅读*中列出）；
2.  虽然本文的操作会涉及到命令行，但跟着二翔子会手把手的将每一步写的尽量清楚，因此同学们不要有畏难心理；
3.  文中生成的GPG密钥只做演示之用，不是二翔子日常所用的[GPG密钥](https://2xiangzi.blogspot.com/p/blog-page.html)；
4.  由于二翔子的知识和能力有限，如果文中有没说清楚的地方，希望大家能在评论区指出，以帮助二翔子将博文写得更好。

<a href="#2.-使用副签名密钥的好处及原理" id="2.-使用副签名密钥的好处及原理"></a><span id="2">2. 使用副签名密钥的好处及原理</span>
=================================================================================================================================

想象有一天，你的私钥被远程地或物理地盗取了。拿到你私钥的人，不仅可以将别人发给你的加密信息解密，而且可以用你的签名密钥（即私钥）冒充你本人发信息。此时你的唯一选择就是撤回你的全部密钥（包括*主密钥*），但如此做法会使得你*主签名密钥*长期积累到的其他人的认证（参加[Web Of Trust机制](https://www.gnupg.org/gph/en/manual/x547.html)）一起作废。

这个问题实际上可以通过使用*副密钥（subkeys）*取代*主密钥*进行日常操作来缓解。其背后的原理如下：

1.  生成一个常规的GPG密钥对，该密钥对包含一个用来签名和解密的私钥和一个用来加密要发给你的信息的公钥；
2.  使用GPG添加一个副的私钥到你的密钥对中，此时我们有了三个密钥；
3.  这三个密钥密钥组成的密钥串被称作*主密钥*，其应该被保存在一个非常安全的地方；
4.  将在第一步中生成的那个私钥移除出密钥串，只剩下新添加的那个私钥和原来的公钥；
5.  把此时的留下的两个密钥称作*日常密钥*，其被留在你的电脑上进行日常的签名、加密、解密等工作；

此后，即使你的“日常密钥”丢失或被盗，你的*主密钥*仍然安全。你可以用*主密钥*撤回已经丢失或被盗的“日常密钥”。虽然这不能阻止已经获得你*日常密钥*的人查看你过往的加密信息，但起码*主签名密钥*长期积累到的其他人的认证保住了。

<a href="#3.-创建完美的gpg密钥对" id="3.-创建完美的gpg密钥对"></a><span id="3">3. 创建完美的GPG密钥对</span>
============================================================================================================

现在二翔子就手把手的带着大家创建完美的GPG密钥对。此处二翔子使用的GnuPG软件版本是1.4.18，操作系统为debian 8。因为每个人使用的GnuPG版本和操作系统可能会有差异，所以如果你发现有与二翔子的操作过程或命令有出入，希望可以在评论区告知二翔子，二翔子这里现行告谢了：）

<a href="#3.1-创建初始密钥对" id="3.1-创建初始密钥对"></a>3.1 创建初始密钥对
----------------------------------------------------------------------------

`user@temp:~$` **gpg - -gen-key**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    gpg: directory `/home/user/.gnupg' created
    gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
    gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
    gpg: keyring `/home/user/.gnupg/secring.gpg' created
    gpg: keyring `/home/user/.gnupg/pubring.gpg' created
    Please select what kind of key you want:
       (1) RSA and RSA (default)
       (2) DSA and Elgamal
       (3) DSA (sign only)
       (4) RSA (sign only)

`Your selection?` **1**

    RSA keys may be between 1024 and 4096 bits long.

这里询问你所要创建的密钥对的长度。密钥对的长度越长，加密的强度越大。随着硬件和软件技术的发展，计算机的性能越来越强，同时也意味着破解加密的难度越来越小。今天不能被破解的加密，不意味着将来不可以。因此二翔子在此强烈建议大家都使用GnuPG所提供的最长长度(当前为4096位)的密钥。

`What keysize do you want? (2048)` **4096**

    Requested keysize is 4096 bits
    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years

这里询问你要把这个密钥对设置为多久后过期。将密钥设置一定的有效期是一种有效的保护措施：即使你的私钥丢失，或者忘记了passphrase，只要等到过期时间，别人就都会知道你不再用这个密钥啦。密钥过期后基本有两种选择：一种是选择重新创建一个新的密钥，并且（如果可能的话）保留旧有密钥以解密原来的电子邮件等；另一种是选择向后延长密钥的过期时间。这里二翔子选择 “**1y**”，意味着密钥将在创建后的一年后过期。

`Key is valid for? (0)` **1y**

    Key expires at Tue 05 Sep 2017 00:00:39 PM UTC

`Is this correct? (y/N)` **y**

    You need a user ID to identify your key; the software constructs the user ID
    from the Real Name, Comment and Email Address in this form:
        "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

由于Real name这一项不能以数字开头，所以二翔子只好把 “2”该写成汉语拼音的 “er”。

`Real name:` **erxiangzi**
`Email address:` **2xiangzi-blog@riseup.net**
`Comment:`

    You selected this USER-ID:
        "erxiangzi <2xiangzi-blog@riseup.net>"

`Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?` **o**

    You need a Passphrase to protect your secret key.

此处需要你设置一个密码（Passphrase），设置好以后，每一次使用GPG私钥都会要求你输入密码，起到一定的保护作用。顺便说一句，这种保护其实并不十分有效，现在有一种比较高级的玩法叫[Split GPG](https://www.qubes-os.org/doc/split-gpg/),感兴趣的同学不妨了解一下。

&lt;在此输入密码(Passphrase)&gt;

    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    ....+++++
    ....+++++
    gpg: /home/user/.gnupg/trustdb.gpg: trustdb created
    gpg: key AB7BB174 marked as ultimately trusted
    public and secret key created and signed.

    gpg: checking the trustdb
    gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
    gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
    gpg: next trustdb check due at 2017-09-05
    pub   4096R/AB7BB174 2016-09-05 [expires: 2017-09-05]
          Key fingerprint = 9FAF 11FB 58E3 1E5F 4A4D  DF31 4FF8 F994 AB7B B174
    uid                  erxiangzi <2xiangzi-blog@riseup.net>
    sub   4096R/AB64DCD1 2016-09-05 [expires: 2017-09-05]

<a href="#3.2-添加图片" id="3.2-添加图片"></a>3.2 添加图片
----------------------------------------------------------

创建好初始的密钥对后，你还可以在其中附上一个JPGE格式的图片。但要知道，你可能会将你的公钥散布到很多地方，加入图片后会使公钥的体积增大，造成一些不便。二翔子在此不做推荐，不想加入图片的同学请在看完下一自然段后，略过此小结。

此处同学们看到输入的指令中有“**AB7BB174**”字样，这是你刚才生成的短GPG公钥ID，每个人短GPG公钥ID,除非[蓄意碰撞](https://ixquick-proxy.com/do/spg/proxy2?ep=4b78704d457a4d444f77736e475131614957425a6346735356525a584b6e39505551354e416d4a47417a784e574356656153674455574238414439785257395658516738546a736a644177754277515457306b3343424d314544456649326f424143393144475578416d52365958466651794a55436b4a564d6b38395158317055776376536a464e474642574a31454952676f725241596144316f4c4e67516349695579624456654f523134517a5150474263734479304a49556c43495673414531454e586e4566556e4d4c58425a774a6b4556425552524c30685750525a2b456a637255306f4f5430417443567351586842524b55396255536b42586d4e53636d39574a4634584447316766774e534b51317353416873645856655856706a51456c305341685564546c6d4958355156316f58465641734368465855464d57416b3963476934545743554d426855684a5734565a6c494851473855425763434d686f4258533964617855444b4555545a524a774e78462f4155743646514241426c6f6a516e5949476770585154525546306376413239444d4159584648673d&epile=4q6n41784r6n45784q5467784r3138304r5335725n586o3q&edata=6f7ceee3262ee9dbe1e5a5ca6886e230&ek=536r4n784r56382o586q5641645751705355593654544r3063335532586o49344r477872633138325n45786q6657427054476o7864434n4q4n58704859465n6r6544463561456p505358684249585n365033523653313936516q56516344354r553246474s564637554441794q6952354o30346p4r796s68526n394s65314n474n4842595n45493565534969567n4276497952494o327331617n556o5257463955455n61536p6771535731465n566p37614764655930343056535n6o56475n6s5n79563965304n656430464r6553513255545n694o7n632o51794579556q4n516655564q646r68495044524365794931625659695143742o596q30315n314267536o6o6n5144396n6256425554574533537n6p5n4o54395n516o3174625468566369684r4o6n4667523170535230316o4r44776p63585n65656r346o62574577646n7868563370436132705956794675635373684o795569637973784r694q6o51576s384s557476574359785369456p565352475533644p4r334n434n5456774r7n3541636o51784o32746864413q3q&ekdata=aec108a2ec825c28046f33db7f0efe09),否则几乎不可能一样，你可以在上一小结最后的输出结果中找到你自己的。

`user@temp:~$` **gpg - -edit-key AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Secret key is available.

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>

`gpg>` **addphoto**

    Pick an image to use for your photo ID.  The image must be a JPEG file.
    Remember that the image is stored within your public key.  If you use a
    very large picture, your key will become very large as well!
    Keeping the image close to 240x288 is a good size to use.

`Enter JPEG filename for photo ID:` **/home/user/me.jpg**

`is this photo correct (y/N/q)?` **y**

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **save**

<a href="#3.3-增强hash偏好" id="3.3-增强hash偏好"></a>3.3 增强Hash偏好
----------------------------------------------------------------------

现在我们让刚生成的密钥对偏好强Hash算法。

`user@temp:~$` **gpg - -edit-key AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Secret key is available.

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **setpref SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP**

    Set preference list to:
         Cipher: AES256, AES192, AES, CAST5, 3DES
         Digest: SHA512, SHA384, SHA256, SHA224, SHA1
         Compression: ZLIB, BZIP2, ZIP, Uncompressed
         Features: MDC, Keyserver no-modify

`Really update the preferences? (y/N)` **y**

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **save**

<a href="#3.4-添加一个新的签名副钥（signing-subkey）" id="3.4-添加一个新的签名副钥（signing-subkey）"></a>3.4 添加一个新的签名副钥（signing subkey）
----------------------------------------------------------------------------------------------------------------------------------------------------

`user@temp:~$` **gpg - -edit-key AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Secret key is available.

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **addkey**

    Key is protected.

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    Please select what kind of key you want:
       (3) DSA (sign only)
       (4) RSA (sign only)
       (5) Elgamal (encrypt only)
       (6) RSA (encrypt only)

`Your selection?` **4**

    RSA keys may be between 1024 and 4096 bits long.

`What keysize do you want? (2048)` **4096**

    Requested keysize is 4096 bits
    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years

`Key is valid for? (0)` **1y**

    Key expires at Tue 05 Sep 2017 00:10:17 PM UTC

`Is this correct? (y/N)` **y**
`Really create? (y/N)` **y**

    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    ......+++++
    +++++

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **save**

<a href="#3.5-创建一个撤销证书（revocation-certificate）" id="3.5-创建一个撤销证书（revocation-certificate）"></a>3.5 创建一个撤销证书（revocation certificate）
----------------------------------------------------------------------------------------------------------------------------------------------------------------

现在咱们来创建一个*撤销证书*。一旦你的*主密钥对*丢失或被盗，这个证书是你告诉外界“请忽略掉我丢失的密钥”的唯一方法。

`user@temp:~$` **gpg - -output revocation.cert - -gen-revoke AB7BB174**

    sec  4096R/AB7BB174 2016-09-05 erxiangzi <2xiangzi-blog@riseup.net>

`Create a revocation certificate for this key? (y/N)` **y**

    Please select the reason for the revocation:
      0 = No reason specified
      1 = Key has been compromised
      2 = Key is superseded
      3 = Key is no longer used
      Q = Cancel
    (Probably you want to select 1 here)

`Your decision?` **0**

    Enter an optional description; end it with an empty line:

`>`

    Reason for revocation: No reason specified
    (No description given)

`Is this okay? (y/N)` **y**

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    ASCII armored output forced.
    Revocation certificate created.

    Please move it to a medium which you can hide away; if Mallory gets
    access to this certificate he can use it to make your key unusable.
    It is smart to print this certificate and store it away, just in case
    your media become unreadable.  But have some caution:  The print system of
    your machine might store the data and make it available to others!

<a href="#3.6-导出主密钥对及撤销证书" id="3.6-导出主密钥对及撤销证书"></a>3.6 导出主密钥对及撤销证书
----------------------------------------------------------------------------------------------------

创建私钥备份：

`user@temp:~$` **gpg - -export-secret-keys - -armor AB7BB174 &gt; erxiangzi\_gpg\_private.key**

创建公钥备份：

`user@temp:~$` **gpg - -export - -armor AB7BB174 &gt; erxiangzi\_gpg\_public.key**

将*私钥*、*公钥*及*撤销证书*打包：（Windows操作系统的操作与此不同）

`user@temp:~$` **tar -cf gpg\_master\_keys.tar erxiangzi\_gpg\*.key revocation.cert**

理论上讲，当你打包后，除了特殊情况（如密钥丢失需要撤回或者需要将他人的密钥签名），你不会再用到这个打包文件了。介于这个打包文件非常重要，二翔子建议将其转移到一个强加密的移动介质（如U盘或CD）当中，再把这个移动介质藏好。选择移动介质来存储，一方面是因为其隐藏性好（比如你可以将刻好的CD丢进一箱子的盗版碟中）；另一方面也是为了防止如果存储 在笔记本电脑上，密钥会随着笔记本的丢失或被盗一同消失。

完成上述步骤后别忘了把刚才导出的*私钥*、*公钥*及*撤销证书*都擦除（注意：不仅仅是删除）掉：

`user@temp:~$` **shred -u erxiangzi\*.key revocation.cert**

<a href="#3.7-将主密钥对替换为日常使用的密钥对" id="3.7-将主密钥对替换为日常使用的密钥对"></a>3.7 将主密钥对替换为日常使用的密钥对
----------------------------------------------------------------------------------------------------------------------------------

这个日常使用的密钥对（以下简称*日常密钥对*）之中不应该包含你的*主签名密钥*。*日常密钥对*可以暴露在不受信任的环境（如你的手机、联网的虚拟机）之中。

### <a href="#3.7.1-导出主、副两个签名密钥" id="3.7.1-导出主、副两个签名密钥"></a>3.7.1 导出主、副两个签名密钥

将主、副两个签名密钥导出到一个叫做subkeys的临时文件中：

`user@temp:~$` **gpg - -export-secret-subkeys AB7BB174 &gt; subkeys**

需要注意: 如果你当初没有设置密码（Passphrase）(这种情况在Split-GPG用户中很常见)，由于GnuPG软件的设计，你的私钥不会被导出。这就需要你临时设置一个密码，等到导出完成，再将密码设置回空值。具体步骤如下（没有遇到此问题的同学请直接跳过）：

`user@temp:~$` **gpg - -edit-key AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Secret key is available.

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **passwd**

    Secret parts of primary key are not available.

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB64DCD1, created 2016-09-05

&lt;在此输入原密码(Passphrase)&gt;

    Enter the new passphrase for this secret key.

&lt;在此输入新密码(Passphrase)&gt;

`Do you really want to do this? (y/N)` **y**

`gpg>` **save**

### <a href="#3.7.2-删除主签名密钥" id="3.7.2-删除主签名密钥"></a>3.7.2 删除主签名密钥

因为之前已经将*主签名密钥*打包备份到安全的移动介质中，你现在可以大胆的将其从密钥串中删除掉：

`user@temp:~$` **gpg - -delete-secret-keys AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.


    sec  4096R/AB7BB174 2016-09-05 erxiangzi <2xiangzi-blog@riseup.net>

`Delete this key from the keyring? (y/N)` **y**
`This is a secret key! - really delete? (y/N)` **y**

### <a href="#3.7.3-导入副签名密钥" id="3.7.3-导入副签名密钥"></a>3.7.3 导入副签名密钥

因为刚才已经将*主签名密钥*删除掉了，所以现在只有*副签名密钥*被导入回电脑：

`user@temp:~$` **gpg - -import subkeys**

    gpg: key AB7BB174: secret key imported
    gpg: key AB7BB174: "erxiangzi <2xiangzi-blog@riseup.net>" 1 new signature
    gpg: Total number processed: 1
    gpg:         new signatures: 1
    gpg:       secret keys read: 1
    gpg:   secret keys imported: 1

`user@temp:~$` **gpg - -list-secret-keys**

    /home/user/.gnupg/secring.gpg
    -----------------------------
    sec#  4096R/AB7BB174 2016-09-05 [expires: 2017-09-05]
    uid                  erxiangzi <2xiangzi-blog@riseup.net>
    ssb   4096R/AB64DCD1 2016-09-05
    ssb   4096R/0D65E7C7 2016-09-05

这里我们注意到，sec后面多了一个“\#”，这表示*主签名密钥*已经不在密钥串中了。

### <a href="#3.7.4-擦除subkeys文件" id="3.7.4-擦除subkeys文件"></a>3.7.4 擦除subkeys文件

`user@temp:~$` **shred - -remove subkeys**

<a href="#4.-简单回顾" id="4.-简单回顾"></a><span id="4">4. 简单回顾</span>
===========================================================================

到了这里，你很可能会问：我们刚才都干了啥？

1.  首先咱们使用能够利用的最强设置生成了一个密钥对；
2.  然后咱们向这个密钥对中加入了一个副签名密钥，使之成为一个密钥串；
3.  接着咱们导出了密钥串并将其与撤销证书一起打包并存储在了安全的移动介质上。那个打包文件就是*主密钥对*；
4.  最后咱们将*主签名密钥*从本机的密钥串中删掉了，此时的密钥串被称之为*日常密钥对*。

<a href="#5.-使用日常密钥对" id="5.-使用日常密钥对"></a><span id="5">5. 使用日常密钥对</span>
=============================================================================================

现在你可以用这个*日常密钥对*进行加密、解密、签名了。

但如果你要认证他人的密钥，或者撤回这个*日常密钥对*，则需要用到*主密钥对*了。

<a href="#6.-意外发生后的应对措施" id="6.-意外发生后的应对措施"></a><span id="6">6. 意外发生后的应对措施</span>
===============================================================================================================

一旦日常密钥对丢失或被盗，由于事先做足了准备工作，我们不必将整个密钥串全部撤回，这意味着长期积累在*主签名密钥*上的[Web Of Trust签名](https://www.gnupg.org/gph/en/manual/x547.html)被保住了。

<a href="#6.1-导入主密钥" id="6.1-导入主密钥"></a>6.1 导入主密钥
----------------------------------------------------------------

首先我们要找到事先藏好的移动介质，将*主密钥对*压缩包解压缩：

`[user@temp ~]$` **tar xvf gpg\_master\_keys.tar**

    erxiangzi_gpg_private.key
    erxiangzi_gpg_public.key
    revocation.cert

然后导入主密钥：

`[user@temp ~]$` **gpg - -import alice\_gpg\_p\*.key**

    gpg: directory `/home/user/.gnupg' created
    gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
    gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
    gpg: keyring `/home/user/.gnupg/secring.gpg' created
    gpg: keyring `/home/user/.gnupg/pubring.gpg' created
    gpg: key AB7BB174: secret key imported
    gpg: /home/user/.gnupg/trustdb.gpg: trustdb created
    gpg: key AB7BB174: public key "erxiangzi <2xiangzi-blog@riseup.net>" imported
    gpg: key AB7BB174: "erxiangzi <2xiangzi-blog@riseup.net>" 1 new signature
    gpg: Total number processed: 2
    gpg:               imported: 1  (RSA: 1)
    gpg:         new signatures: 1
    gpg:       secret keys read: 1
    gpg:   secret keys imported: 1

验证一下我们的导入结果：

`user@temp:~$` **gpg - -edit-key AB7BB174**

    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Secret key is available.

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

-   可以看到最重要的主密钥显示：SC（“sign”&“certify”，代表可以签名和认证其它密钥）
-   第一个副密钥显示：E（“encrypt”，加密）
-   第二个副密钥显示：S（“sign”，签名）

<a href="#6.2-撤回被盗取或丢失的副密钥" id="6.2-撤回被盗取或丢失的副密钥"></a>6.2 撤回被盗取或丢失的副密钥
----------------------------------------------------------------------------------------------------------

`gpg>` **list**

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **key 1**

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub*  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **key 2**

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    sub*  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    sub*  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **revkey**

`Do you really want to revoke the selected subkeys? (y/N)` **y**

    Please select the reason for the revocation:
      0 = No reason specified
      1 = Key has been compromised
      2 = Key is superseded
      3 = Key is no longer used
      Q = Cancel

`Your decision?` **1**

    Enter an optional description; end it with an empty line:

`>`

    Reason for revocation: Key has been compromised
    (No description given)

`Is this okay? (y/N)` **y**

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created: 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    You need a passphrase to unlock the secret key for
    user: "erxiangzi <2xiangzi-blog@riseup.net>"
    4096-bit RSA key, ID AB7BB174, created: 2016-09-05

&lt;在此输入密码(Passphrase)&gt;

    pub  4096R/AB7BB174  created: 2016-09-05  expires: 2017-09-05  usage: SC  
                         trust: ultimate      validity: ultimate
    This key was revoked on 2016-09-05 by RSA key AB7BB174 erxiangzi <2xiangzi-blog@riseup.net>
    sub  4096R/AB64DCD1  created: 2016-09-05  expires: 2017-09-05  usage: E   
    This key was revoked on 2016-09-05 by RSA key AB7BB174 erxiangzi <2xiangzi-blog@riseup.net>
    sub  4096R/0D65E7C7  created: 2016-09-05  expires: 2017-09-05  usage: S   
    [ultimate] (1). erxiangzi <2xiangzi-blog@riseup.net>
    [ unknown] (2)  [jpeg image of size 5032]

`gpg>` **save**

<a href="#6.3-告知外界你撤回密钥的消息" id="6.3-告知外界你撤回密钥的消息"></a>6.3 告知外界你撤回密钥的消息
----------------------------------------------------------------------------------------------------------

### <a href="#6.3.1-导出被撤回的密钥到-ascii-文件" id="6.3.1-导出被撤回的密钥到-ascii-文件"></a>6.3.1 导出被撤回的密钥到 ASCII 文件

`[user@temp ~]$` **gpg - -export -a &gt; revoked\_keys.asc**

之后将 ASCII文件中的内容贴到互联网上。二翔子此次[撤回密钥](https://2xiangzi.blogspot.nl/2016/09/change-gpg-public-key-1.html)就是用了这种方法。

### <a href="#6.3.2-使用key-server" id="6.3.2-使用key-server"></a>6.3.2 使用key server

如果你之前将自己的公钥上传到了某个key server上（此处以*sks.keyservers.net*为例），那么你需要使用如下命令告知服务器你撤回了密钥：
`[user@temp ~]$` **gpg - -keyserver sks.keyservers.net - -send-keys AB7BB174**

    gpg: sending key AB7BB174 to hkp server sks.keyservers.net

`［user@temp ~]$` **gpg - -keyserver sks.keyservers.net - -send-keys AB7BB174**

    gpg: sending key AB7BB174 to hkp server sks.keyservers.net

<a href="#7.-推荐阅读" id="7.-推荐阅读"></a><span id="7">7. 推荐阅读</span>
===========================================================================

1.  [Using GnuPG with QubesOS](https://apapadop.wordpress.com/2013/08/21/using-gnupg-with-qubesos/)
2.  [Creating the perfect GPG keypair](https://alexcabal.com/creating-the-perfect-gpg-keypair/)
3.  [RSA算法原理（一）](https://ixquick-proxy.com/do/spg/proxy2?ep=4b5630564d45412f4b796834444463554f556b5a52426c62426d31525357516e5146352f4467565a6368514e4e77457961546f7143575a5344313554556d6f345230345643554534455673344755783051537779424367624367734a4b77785665414e314967383059573553467838315755343946414a514a674d63496c7367496a746a465834484f5630585568314c45524d7858687357456d786d574567494a56684c63424e714c79307846475a544342384f4d58314d636c774444417769516b672f424268655a513461654155344b6e78334969454d4a6c305a5252354d424270485868415742783930547a644b637745694e776f774b4373734543734e466b7064425377685730555256556f6b576b56334342565a644146415a414e756447776e563346554c46384a5132736441427844485563305645307a53306b424e51524f4e3135784e796f3257584a475a6c7856477a3151553146534331456a43686833446745465a67556259464530496d736a555852564b6c7866524435494445314d54454e6f557842675442634d4d31686249685671436730555677346144454e794452464d656e705253475a3142473133447746586331314d&epile=4q6n41784r6n41354q4459774q6p387n4r7935725n586o3q&edata=73039fc10a735e13ebd307c8e0d88c5f&ek=536q4239566q5n5852316p465n454r6753546s386431682o4r43743065794n514r796p5266584534&ekdata=afb5c5f92853fe94eeb19c12bf43da89)
4.  [RSA算法原理（二）](https://ixquick-proxy.com/do/spg/proxy2?ep=4b5630564d45412f4b796834444463554f556b5a52426c62426d31525357516e5146352f4467565a6368514e4e77457961546f7143575a5344313554556d6f345230345643554534455673344755783051537779424367624367734a4b77785665414e314967383059573553467838315755343946414a514a674d63496c7367496a746a465834484f5630585568314c45524d7858687357456d786d574567494a56684c63424e714c79307846475a544342384f4d58314d636c774444417769516b672f424268655a513461654155344b6e78334969454d4a6c305a5252354d424270485868415742783530547a644b637745694e776f774b4373734543734e466b7064425377685146776256556f6b576b56334342565a644146415967426a6457353856334e5366566c5a4557394e427830564742466c4252686b546b49505a6c464d595646784e796f3257584a475a6c7856477a3151553146534331456a4368683344674546596c41635977493049573538566e70514b77355a4657425056306757544551304242347947454261596c5a6249685671436730555677346144454e794452464e656d705253475a3142473133447746586331314d&epile=4q6n41784r6n41354q4459774q6p387n4r7935725n586o3q&edata=2b2ff8ec727de04a98daa1f1c8a1ccd2&ek=536q4239566q5n5852316p465n454r6753546s386431682o4r43743065794n514r796p5266584534&ekdata=15928467ece72dbc79b7ae7ddba653e0)
5.  [GPG(pgp)加解密中文完整教程](https://ixquick-proxy.com/do/spg/proxy2?ep=4831685459417458466973424e694164446c454f6345346461515143555256554869514d635130474d684d61566e596e6633736f513055724f6c454d595159505146424547696b4559313844593155735158565759327863494564636142513966564e4746323545437945504d6e5a494e41745850516f6f4832386344784e514157513341445577616d52744c78566d4d774259415434384f78597a6643454346306f464f56494c5046314d436c39554447685a644645634d68634c464342494f53594453524d43596b63494b675952526b4146466a4a6163464d504d6c6f64466964414e7a306546686b4863425a644f6c6f4c55567854586e56724a51496f5931557342444952644367434177384b4c456c564c41674f4142706c535859614f52566341466462566e63676148314c5644454b5055466566534646554578434479635859674665666c594c53694651596e6b4e556b594c4c45564e4b6c396245457758516e49594e46454e64674e4d4154554a4b58526651414d6563477376486c517359586c624e6a78424e48302f59315175566e596966446f655730414f4c6b56504c51554245556b57485863664d46554c6356396152794e535969774d556856646442524d615145525652555358545a5a63773166&epile=4q6n41784r6n45784q4459774r6p38794q6935725n586o3q&edata=fdc6f99debc3d6406056cd5fc69341de&ek=666n4275526q64716330566q576o6p755n6r647454535n375432646n4n53676n65305971&ekdata=1b4f0bc9ad832dfe93e726b8ad204693)
6.  [Using OpenPGP subkeys in Debian development](https://wiki.debian.org/Subkeys?action=show&redirect=subkeys)

------------------------------------------------------------------------

**版权声明**
============

[![知识共享许可协议](https://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)](https://creativecommons.org/licenses/by-nc-sa/3.0/)
本作品采用[知识共享署名-非商业性使用-相同方式共享 3.0 未本地化版本许可协议](https://creativecommons.org/licenses/by-nc-sa/3.0/)进行许可。

<span class="post-author vcard"> 发帖者 <span class="fn" itemprop="author" itemscope="itemscope" itemtype="http://schema.org/Person"> <a href="https://plus.google.com/105144493669632558142" class="g-profile" title="author profile"><span itemprop="name">二翔子</span></a> </span> </span> <span class="post-timestamp"> 时间： <a href="https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html" class="timestamp-link" title="permanent link">上午12:00</a> </span> <span class="reaction-buttons"> </span> <span class="post-comment-link"> </span> <span class="post-backlinks post-comment-link"> </span> <span class="post-icons"> <span class="item-control blog-admin pid-309686794"> [<img src="https://resources.blogblog.com/img/icon18_edit_allbkg.gif" class="icon-action" width="18" height="18" />](https://www.blogger.com/post-edit.g?blogID=7959751325273089682&postID=6125275056611834563&from=pencil "修改帖子") </span> </span>
<a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=6125275056611834563&amp;target=email" class="goog-inline-block share-button sb-email" title="通过电子邮件发送"><span class="share-button-link-text">通过电子邮件发送</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=6125275056611834563&amp;target=blog" class="goog-inline-block share-button sb-blog" title="BlogThis!"><span class="share-button-link-text">BlogThis!</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=6125275056611834563&amp;target=twitter" class="goog-inline-block share-button sb-twitter" title="共享给 Twitter"><span class="share-button-link-text">共享给 Twitter</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=6125275056611834563&amp;target=facebook" class="goog-inline-block share-button sb-facebook" title="共享给 Facebook"><span class="share-button-link-text">共享给 Facebook</span></a><a href="https://www.blogger.com/share-post.g?blogID=7959751325273089682&amp;postID=6125275056611834563&amp;target=pinterest" class="goog-inline-block share-button sb-pinterest" title="分享到Pinterest"><span class="share-button-link-text">分享到Pinterest</span></a>

<span class="post-labels"> 标签： [软件推荐](https://2xiangzi.blogspot.com/search/label/%E8%BD%AF%E4%BB%B6%E6%8E%A8%E8%8D%90), [信息安全](https://2xiangzi.blogspot.com/search/label/%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8) </span>

<span class="post-location"> </span>

<span id="comments"></span>
#### 14 条评论:

1.  

    ![](//img1.blogblog.com/img/blank.gif)

    Docomo<span class="icon user"></span><span class="datetime secondary-text">[2016年9月6日 上午11:31](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1473132702554#c6735851377019932590)</span>

    前排支持

    <span id="bc_0_1MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-2128498893">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=6735851377019932590)</span></span>

    <span id="bc_0_1b+seedutuD" kind="d"></span>
    <span id="bc_0_0TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_0TA" class="thread-arrow"></span><span id="bc_0_0TN" class="thread-count"><span id="bc_0_0TNT" style="display: none;"></span><span id="bc_0_0TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:30](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317446762#c1903446732654066013)</span>

        To Docomo
        多谢支持:)

        <span id="bc_0_0MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=1903446732654066013)</span></span>

2.  

    ![](//lh4.googleusercontent.com/-h4-x9kzvjA8/AAAAAAAAAAI/AAAAAAAAAaQ/dHsS60shUXI/s35-c/photo.jpg)

    [音業](https://www.blogger.com/profile/13678458541060375922)<span class="icon user"></span><span class="datetime secondary-text">[2016年9月7日 上午2:12](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1473185567853#c1126147904393820455)</span>

    后排围观。

    <span id="bc_0_3MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1990112671">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=1126147904393820455)</span></span>

    <span id="bc_0_3b+seedutvD" kind="d"></span>
    <span id="bc_0_2TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_2TA" class="thread-arrow"></span><span id="bc_0_2TN" class="thread-count"><span id="bc_0_2TNT" style="display: none;"></span><span id="bc_0_2TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:31](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317469321#c4316449813143262318)</span>

        To 音業
        多谢音業支持:)

        <span id="bc_0_2MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=4316449813143262318)</span></span>

3.  

    ![](//lh4.googleusercontent.com/-h4-x9kzvjA8/AAAAAAAAAAI/AAAAAAAAAaQ/dHsS60shUXI/s35-c/photo.jpg)

    [音業](https://www.blogger.com/profile/13678458541060375922)<span class="icon user"></span><span class="datetime secondary-text">[2016年9月7日 上午2:13](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1473185581580#c6476805768337859221)</span>

    <span class="deleted-comment">此评论已被作者删除。</span>

    <span id="bc_0_4MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=6476805768337859221)</span></span>

4.  

    ![](//img1.blogblog.com/img/blank.gif)

    fserw<span class="icon user"></span><span class="datetime secondary-text">[2016年9月8日 上午9:19](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1473297572508#c1689234924288216675)</span>

    虚拟号的教程写不写？这非常重要，现在国内外网站注册都要手机号了，即使不用国内网站，谷歌，微软邮箱动不动就要人手机号。保存缓存有时候都没用。

    <span id="bc_0_7MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1653377336">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=1689234924288216675)</span></span>

    <span id="bc_0_7b+seedutwD" kind="d"></span>
    <span id="bc_0_5TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_5TA" class="thread-arrow"></span><span id="bc_0_5TN" class="thread-count"><span id="bc_0_5TNT" style="display: none;"></span><span id="bc_0_5TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:31](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317493424#c8725670731880197154)</span>

        To fserw
        多谢你的提醒：)在手机实名制加几乎所有网络服务都需要电话号码的时代，虚拟号确实对在线匿名有很大帮助。一旦二翔子找到合适的方法，就会写博文告诉大家。

        <span id="bc_0_5MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=8725670731880197154)</span></span>

    2.  

        ![](//img1.blogblog.com/img/blank.gif)

        匿名<span class="icon user"></span><span class="datetime secondary-text">[2017年4月6日 下午2:24](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1491459862272#c758496189339826064)</span>

        http://receivefreesms.com/
        据说是个伪造现实手机专门供注册用的管理网站，如果有其他类似的在网站专门放个位置让初学者使用吧
        在那些网站你可以注册个手机专门注册各种网站用，避免被现实的警察寻找到你

        <span id="bc_0_6MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-157338243">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=758496189339826064)</span></span>

5.  

    ![](//img1.blogblog.com/img/blank.gif)

    fserw<span class="icon user"></span><span class="datetime secondary-text">[2016年9月8日 上午9:21](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1473297696263#c6916078198639079383)</span>

    虚拟号网站是很多，但很多号都被屏蔽掉，不能用了，博主能不能找到能用的，免费的方法？
    还有你这个网站字体大小怎么变了，看着不舒服最好换回来

    <span id="bc_0_9MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1653377336">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=6916078198639079383)</span></span>

    <span id="bc_0_9b+seedutxD" kind="d"></span>
    <span id="bc_0_8TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_8TA" class="thread-arrow"></span><span id="bc_0_8TN" class="thread-count"><span id="bc_0_8TNT" style="display: none;"></span><span id="bc_0_8TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:31](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317517957#c2896844889228525399)</span>

        To fserw
        虽然时隔很久才回复，但你发表评论的当天，二翔子就对网站字体进行了调整，不知你觉得现在的界面如何？

        <span id="bc_0_8MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=2896844889228525399)</span></span>

6.  

    ![](//img1.blogblog.com/img/blank.gif)

    匿名<span class="icon user"></span><span class="datetime secondary-text">[2016年9月29日 上午11:11](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1475118676452#c975584522863334472)</span>

    终于看到教程了，为你的辛勤劳动和奉献精神点赞。

    <span id="bc_0_11MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-1991422011">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=975584522863334472)</span></span>

    <span id="bc_0_11b+seedutyD" kind="d"></span>
    <span id="bc_0_10TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_10TA" class="thread-arrow"></span><span id="bc_0_10TN" class="thread-count"><span id="bc_0_10TNT" style="display: none;"></span><span id="bc_0_10TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:32](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317541371#c1367313987093532647)</span>

        To 匿名
        谢谢你的鼓励，二翔子会继续努力，写出更多、更好的博文献给大家:)

        <span id="bc_0_10MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=1367313987093532647)</span></span>

7.  

    ![](//lh5.googleusercontent.com/-7o3heqRbo_Q/AAAAAAAAAAI/AAAAAAAAADE/70KBucF4aq4/s35-c/photo.jpg)

    [ヨイツの賢狼ホロ](https://www.blogger.com/profile/08993242292265159106)<span class="icon user"></span><span class="datetime secondary-text">[2016年10月29日 上午10:23](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1477707782635#c2602988839801790330)</span>

    后排围观。

    <span id="bc_0_13MN" class="comment-actions secondary-text" kind="m">[回复](javascript:;)<span class="item-control blog-admin pid-543271033">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=2602988839801790330)</span></span>

    <span id="bc_0_13b+seedutzD" kind="d"></span>
    <span id="bc_0_12TT" class="thread-toggle thread-expanded" kind="g"><span id="bc_0_12TA" class="thread-arrow"></span><span id="bc_0_12TN" class="thread-count"><span id="bc_0_12TNT" style="display: none;"></span><span id="bc_0_12TNU" style="display: none;"></span>[回复](javascript:;)</span></span>
    <span class="thread-drop"></span>

    1.  

        ![](//lh3.googleusercontent.com/zFdxGE77vvD2w5xHy6jkVuElKv-U9_9qLkRYK8OnbDeJPtjSZ82UPq5w6hJ-SA=s35)

        [二翔子](https://www.blogger.com/profile/14852933540775977859)<span class="icon user blog-author"></span><span class="datetime secondary-text">[2016年11月17日 上午1:33](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html?showComment=1479317580456#c3694519688763194401)</span>

        To ヨイツの賢狼ホロ
        多谢ヨイツの賢狼ホロ的支持:)

        <span id="bc_0_12MN" class="comment-actions secondary-text" kind="m"><span class="item-control blog-admin pid-309686794">[删除](https://www.blogger.com/delete-comment.g?blogID=7959751325273089682&postID=3694519688763194401)</span></span>

[添加评论](javascript:;)

[加载更多...](javascript:;)

<span id="comment-form"></span>

<a href="https://www.blogger.com/comment-iframe.g?blogID=7959751325273089682&amp;postID=6125275056611834563" id="comment-editor-src"></a>

<span id="blog-pager-newer-link"> <a href="https://2xiangzi.blogspot.com/2016/09/change-gpg-public-key-1.html" id="Blog1_blog-pager-newer-link" class="blog-pager-newer-link" title="较新的帖子">较新的帖子</a> </span> <span id="blog-pager-older-link"> <a href="https://2xiangzi.blogspot.com/2016/05/whonix1.html" id="Blog1_blog-pager-older-link" class="blog-pager-older-link" title="较早的帖子">较早的帖子</a> </span> <a href="https://2xiangzi.blogspot.com/" class="home-link">主页</a>

订阅： <a href="https://2xiangzi.blogspot.com/feeds/6125275056611834563/comments/default" class="feed-link">帖子评论 (Atom)</a>

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
    -   <a href="javascript:void(0)" class="toggle"><span class="zippy"> ►  </span></a> <a href="https://2xiangzi.blogspot.com/2016/11/" class="post-count-link">十一月</a> <span class="post-count" dir="ltr">(1)</span>

    <!-- -->

    -   <a href="javascript:void(0)" class="toggle"><span class="zippy toggle-open"> ▼  </span></a> <a href="https://2xiangzi.blogspot.com/2016/09/" class="post-count-link">九月</a> <span class="post-count" dir="ltr">(2)</span>
        -   [关于二翔子更换GPG公钥的说明](https://2xiangzi.blogspot.com/2016/09/change-gpg-public-key-1.html)
        -   [如何创建完美的GPG密钥对](https://2xiangzi.blogspot.com/2016/09/perfect-gpg-keypair.html)

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
