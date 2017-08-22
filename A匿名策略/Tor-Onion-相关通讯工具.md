![](/sites/all/themes/zen/images/page_bg_onion_white.png)

[Tor - Home](/)

-   [Home](/blog "Go back to the Tor Blog Home")
-   [Archives](/archive "Blog Archives")
-   [About Tor](https://www.torproject.org/overview "About the Tor Project")
-   [Donate](https://www.torproject.org/donate/donate "Donate to the Tor Project today!")

Posted December 11th, 2016 by asn

in

-   [heart of Internet freedom](/category/tags/heart-internet-freedom)
-   [instant messaging](/category/tags/instant-messaging)
-   [onion services](/category/tags/onion-services)

*During the month of December, we're highlighting other organizations and projects that rely on Tor, build on Tor, or are accomplishing their missions better because Tor exists. Check out our blog each day to learn about our fellow travelers. And please support the Tor Project! We're at the heart of Internet freedom.*
 [Donate today](https://torproject.org/donate/donate-blog12)!

* * * * *

 The Internet was made for humans to communicate with each other! Even though Internet calls over video and audio are totally possible nowadays, people still enjoy sending texts to each other due to their asynchronous, permanent and casual nature. To understand how important these instant messaging systems are, just check the user growth of systems like WeChat, WhatsApp, etc.

 [
 ![](https://people.torproject.org/~asn/crowdfunding_blog/stats.png)
](http://brel54.blogspot.com/2014/02/why-19billion-for-whatsapp-could-be.html)

Unfortunately, all these major mainstream messaging systems belong to huge companies whose money comes from advertising and selling the data and metadata of their users.

*The good news* here is that in the past couple of years, there has been great progress in protecting users' data by employing **end-to-end encryption** using [the Signal protocol](https://whispersystems.org/blog/whatsapp-complete/). *The bad news* is that there has still been absolutely no progress in protecting the **metadata** and location information of users by these mainstream platforms.

Case in point, since most instant messaging systems are not anonymous, they get to learn the full location history of their users through the users' IP address history. Also, all major chat systems require a social media account or a phone number, which is simply impossible for some people, and it also makes it hard to create anonymous or burner accounts for everyone. It also makes you searchable and targettable by people who happen to know your phone number.

In this blog post, we showcase a few open-source text messaging tools that provide location privacy and additional security to their users by using Tor as a default. All of them are free and open source, so feel free to experiment!

Ricochet
========

[Ricochet](https://ricochet.im/) is an anonymous instant messaging tool that hides metadata by using Tor. It's got a slick UI and works on Windows, Linux and Mac OS X.

In the Ricochet protocol, each user is a Tor onion service. By utilizing onion services, the protocol achieves strong anonymity for its users. And because of its decentralized nature, it's impossible for attackers to censor it by taking down a single server.

Ricochet is designed with UX in mind, so it's easily usable even by people who don't understand how Tor works.

 [
 ![](https://people.torproject.org/~asn/crowdfunding_blog/ricochetscreen.png)
](https://ricochet.im/)

Chatsecure
==========

If you happen to only use mobile platforms (like most of the world these days), [Chatsecure](https://chatsecure.org/) is an app that you should check out! It works for both Android and iOS, and it allows you to connect to XMPP servers to communicate over encrypted OTR chat. This means that you can also use it to connect to other XMPP-enabled messaging systems like Facebook chat and Google Talk.

It's developed by the Guardian Project, and it's a part of their software suite for private communications that includes Orbot and Orfox. Stay tuned on our blog for more information about this software family later this December!

 [
 ![](https://people.torproject.org/~asn/crowdfunding_blog/chatsecure.png)
](https://chatsecure.org/)

And now for further excitement, let's get into the more experimental sections of the secure messaging space!

Pond
====

[Pond](https://github.com/agl/pond) is an anonymous instant messaging tool with various sophisticated security properties that is capable of hiding even the metadata of its users.

The protocol is designed in such a way that even a nasty attacker who is constantly monitoring your Internet connection will have a very hard time figuring out when you actually send and receive Pond messages, even if she conducts statistical analysis of your traffic patterns. Smoke and mirrors you might say, but if you like protocols, we invite you to check out the Pond protocol specs.

Unfortunately, Pond is a side-project, and due to lack of free time, the project is not currently actively being developed, even though there is still a community of users. It only works on Linux, and it has a GUI interface.

 [
 ![](https://people.torproject.org/~asn/crowdfunding_blog/pond.png)
](https://github.com/agl/pond/)

Briar
=====

[Briar](https://briarproject.org/) is an experimental P2P messaging system that is currently in private beta. It targets mobile users and is closely integrated with Tor onion services.

The Briar protocol is fully decentralized, and all communication is end-to-end encrypted. It aims to be highly resilient against network failures, and so it can also function over Bluetooth or WiFi. Furthermore, it attempts to hide the social graph of its users by keeping the user contact list on the client side.

 [
 ![](https://people.torproject.org/~asn/crowdfunding_blog/briar.gif)
](https://briarproject.org/)

Future directions
=================

As you can see, there have been multiple efforts for private and metadata-hiding communication over the past years. Some of these projects are supposed to be used on top of already existing chat frameworks, whereas others aim to create their own ecosystems.

Of course, the research realm of secure messaging is far from complete; it's just getting started. From improving the UX to adding new security properties, this field needs further thinking all around.

For example, **secure multiparty messaging** is a very important upcoming field that studies how the protocols above that are designed for 1-to-1 communication can scale to hundreds of clients talking at the same time while maintaining their security properties.

Furthermore, as [global surveillance is growing](https://theintercept.com/2015/07/14/communicating-secret-watched/), we better understand the importance of hiding metadata from network attackers. Only now are we starting to grasp the importance of security properties like obfuscating communication patterns, hiding the users' social graph and letting users choose when to reveal their online presence.

Tor is extremely interested [in the instant messaging space](https://blog.torproject.org/blog/tor-messenger-030b1-released), and we are always on the lookout for innovative developments and interesting messaging projects. We have deep gratitude to all of the people who have helped to push the field of secure messaging forward, and we hope to enable them in the future to provide anonymous communication tools!

[Donate](https://torproject.org/donate/donate-blog5) and we will make it happen! :)

-   [asn's blog](/blog/33 "Read asn's latest blog entries.")

Comment viewing options
-----------------------

Flat list - collapsedFlat list - expandedThreaded list - collapsedThreaded list - expanded

Date - newest firstDate - oldest first

10 comments per page30 comments per page50 comments per page70 comments per page90 comments per page150 comments per page200 comments per page250 comments per page300 comments per page

Select your preferred way to display the comments and click "Save settings" to activate your changes.

On December 12th, 2016 Anonymous said:

how do we help make end-to-end encrypted group msg happen ?

-   [reply](/comment/reply/1262/224836)

On December 13th, 2016 Anonymous said:

Briar does have end-to-end encrypted group chat: https://code.briarproject.org/akwizgran/briar/issues/127

Video: https://twitter.com/BriarApp/status/799340502235697152

-   [reply](/comment/reply/1262/224931)

On December 12th, 2016 Anonymous said:

Don't forget Conversations. One of the best XMPP clients at the moment. It implements all the important mobile extensions, it has Signal crypto with the OMEMO protocol, thus beating OTR, and it has Tor support (orbot required as additional app) built in. Especially OMEMO, Carbons and MAM allow a smooth, but still encrypted experience with multiple devices.

-   [reply](/comment/reply/1262/224842)

On December 12th, 2016 asn said:

You are right, perhaps it's worth mentioning! I haven't used it myself so I didn't know about the integrated Tor support :O

-   [reply](/comment/reply/1262/224902)

On December 13th, 2016 Anonymous said:

open source ? or payware

-   [reply](/comment/reply/1262/224953)

On December 14th, 2016 Anonymous said:

Wikipedia says its license is GPL, and version 1.15.0 is available in F-Droid on my device. Not sure why people keep saying it is payware. Please enlighten.

-   [reply](/comment/reply/1262/225108)

On December 12th, 2016 Anonymous said:

Sorry, your statement is incorrect...

"This means that you can also use [ChatSecure] to connect to other XMPP-enabled messaging systems like Facebook chat and Google Talk."

Facebook has not permitted the use of chat clients - including ChatSecure - since 2015.

Chat API (Deprecated)
 https://developers.facebook.com/docs/chat

-   [reply](/comment/reply/1262/224846)

On December 12th, 2016 asn said:

Oops, my wrong here. Thanks for correcting.

-   [reply](/comment/reply/1262/224901)

On December 13th, 2016 Anonymous said:

Also,
 \> Google dropped support for XMPP federation in May 2014, meaning that they will no longer support communicating with other XMPP servers.

https://en.m.wikipedia.org/wiki/Google\_talk

-   [reply](/comment/reply/1262/224941)

On December 12th, 2016 Anonymous said:

Thanks to all for the wonderful "Tor at Heart" series!

Already donated but plan to give more.

Some of us will need more help to use secure messaging. One of the critical missing pieces: anonymous accounts to use when communicating with journalists (e.g. Calyx, Riseup) and persuading more journalists to make themselves available using proper authentication in Calyx chat rooms (for example).

There is an on-going story possibly involving FBI malware attacks and/or NSL attacks at Riseup, which is troubling. Last word was that Riseup is seeking advice from its lawyer, and it seems that their warrant canary has vanished. I have some concern that sysadmins may be operating under duress (from USG because Riseup servers are in the USA), because as a story at The Intercept noted, their responses to internal and external queries have been strangely worded.

In the past, a critical source of Tor Project funding has been BBG, the USG funded "soft propaganda" arm which funds Radio Free Asia and other news organizations which attempt to counter certain lines in the state-run press in countries such as CN, RU, sometimes with genuine news, sometimes (some say) with slanted news, so pretty much like CN state-run news counterparts aimed at US businesspersons.

Many Tor users (and, it is said, some employees) have long urged Tor Project to seek to diversify funding to enable the Project to tell USG to take a hike if it threatens to defund Tor Project if the Project does not put in a backdoor or do other and possibly even more inimical things USIC (or the US military or other arms of USG) demands. I applaud Shari's efforts to diversify Tor funding to try to lessen the danger of such unwelcome developments.

Now both Salon and Politico are reporting that Congress (probably without realizing it) passed a law (as part of the NDAA) which guts the Board of Governors of BBG, placing BBG under control of a single Presidential appointee. This has raised fears that the new US administration will turn BBG into a full-on state-run propaganda arm offering outright fake news for foreign and domestic consumption (BBG is said to starting up English language TV stations in the US homeland, aimed at US persons). This raises the question of whether the new administration could attempt to turn Tor Project itself into a Trump propaganda arm.

-   [reply](/comment/reply/1262/224848)

On December 13th, 2016 Anonymous said:

\> Last word was that Riseup is seeking advice from its lawyer, and it seems that their warrant canary has vanished.

For what a link is worth:

https://theintercept.com/2016/11/29/something-happened-to-activist-email-provider-riseup-but-it-hasnt-been-compromised/

-   [reply](/comment/reply/1262/224964)

On December 12th, 2016 Anonymous said:

P.S. My previous submission isn't intended for publication. It's just a heads-up.

Thanks to the TorProject for everything it does. For years, the Tor browser has been the only browser I use for everyday web surfing. (Just not with my primary email or my bank, which are not Tor-friendly.)

-   [reply](/comment/reply/1262/224852)

On December 13th, 2016 Anonymous said:

Regarding: "P.S. My previous submission isn't intended for publication. It's just a heads-up."

I don't know what that means or to what comment it refers, but it does not refer to the comment which appears just above, the one (which I wrote) which begins:

\> Thanks to all for the wonderful "Tor at Heart" series!
 \>
 \> Already donated but plan to give more.

-   [reply](/comment/reply/1262/224961)

On December 12th, 2016 Anonymous said:

Hello, THIS IS NOT A COMMENT BUT A QUESTION - I cannot find the answer in your FAQ's. Today THOR was very accidently and not at all intended installed on my Win 10 system with Firefox browser. My first thougt was: 'this is malware' and I removed, with some difficulties the TOR-program. Afterwards I noticed that ALL MY ;DOC & ;JPEG FILES were RENAMED in a numerous code (in stead of a common name) and that they all got the extension .osiris. I think you EASILY CAN UNDERSTAND THIS IS NOT funny for me.

So, it would be a real joy to me if I can read your SOLUTION AND HOW TOT GET MY FILES BACK WITH THEIR NORMAL names and extensions on my computer.
 What do I have to do to RECTIFY THIS VERY ANNOYING situation; there is no one of my documents I can use; I have no acess to them!!!!

Hoping to hear from you very soon! rita.decaluwe@hotmail.com

-   [reply](/comment/reply/1262/224853)

On December 12th, 2016 arma said:

It sounds like you have been infected with ransomware. :(

This ransomware has nothing to do with Tor.

I hope that
 http://tor.stackexchange.com/questions/9922/i-got-infected-by-ransomware-and-it-tells-me-to-download-tor-whats-going-on
 will be helpful to you here.

-   [reply](/comment/reply/1262/224897)

On December 13th, 2016 Anonymous said:

Hi Roger, I remember in 'State of the Onion', you said that many people are first hearing about Tor when the get infected with ransomware, and they falsely assume that the Tor Project is somehow associated with the attackers, making it hard to defend the idea of Hidden Services. I think that was in late 2014 or early 2015; it's really sad to see that's still going on today.

-   [reply](/comment/reply/1262/224945)

On December 13th, 2016 Anonymous said:

Plus one.

I'd add that unfortunately we must also consider the possibility that at least some irate complaints about alleged infections with ransomware might actually be false reports made as part of some state-sponsored (or not) "effects campaign" targeting the Tor network.

Every citizen in every nation must recognize that at the dawn of the 21st century, we are all targets of the most sophisticated and ambitious intelligence services which have ever existed, and that the spooks frequently attempt psyops as well as more technical attacks.

Needless to add, we cannot let this unfortunate situation deter us from using Tor, engaging in activism, or from expressing our views, however objectionable our own (or other) governments may find these views.

-   [reply](/comment/reply/1262/224962)

On December 12th, 2016 Anonymous said:

how do i update Ricochet hassle free ?

-   [reply](/comment/reply/1262/224885)

On December 13th, 2016 Anonymous said:

I'm missing TorMessenger in the list of messaging apps and I can recommend CoyIM for anonymous Jabber with Tor.

Be careful with feature-rich Jabber clients like conversation. In my experience most Jabber clients which support Jingle file transfer or voice and audio chats have privacy leaks ans should not be used with Tor if anonymity is important (e.g. Gajim or Pidgin for linux desktop pc)

-   [reply](/comment/reply/1262/224920)

On December 13th, 2016 Anonymous said:

I think Conversations is Tor-aware (integrated with Orbot, but I might be thinking of another chat app) so one would think it would handle Jingle properly (or at least block it). Also, there's always Orwall, which can block non-Tor traffic and prevent an app from learning the device's public IP in the first place.

-   [reply](/comment/reply/1262/224946)

On December 13th, 2016 Anonymous said:

I also would like to have seen Tor Messenger in this blog post. Maybe it will get it's own post before the end of the month.

-   [reply](/comment/reply/1262/224971)

On December 13th, 2016 arma said:

Yes! It's on the schedule I think -- I saw Arlo working on a draft.

-   [reply](/comment/reply/1262/224972)

On December 13th, 2016 Anonymous said:

we Ricochet in Tails some time soon thanks you

-   [reply](/comment/reply/1262/224952)

On December 13th, 2016 Anonymous said:

will Briar be ios also?

-   [reply](/comment/reply/1262/224954)

On December 13th, 2016 Anonymous said:

pond does one install and run "pond" in ubuntu ?
 thanks

-   [reply](/comment/reply/1262/224955)

On December 13th, 2016 Anonymous said:

Conversations is payware, you need to buy it; Chatsecure for android is discontinued: "We are not actively developing this app anymore, but will continue to fix any critical bugs" it already has problems on android 7; that leaves only Zom. So is Zom any good?

-   [reply](/comment/reply/1262/224978)

On December 14th, 2016 Anonymous said:

That's a bummer. I used Conversations when it was free, and ChatSecure when it was actively developed. Both were pretty nice. Are you sure Conversations is payware? Wikipedia says its license is GPL, which usually makes software free as in beer.

I guess Beem is the last Free (in both senses) Android XMPP client. I think it supports OTR but is nowhere close to supporting Jingle and is not Tor-aware (although you could connect to a .onion server with it).

It's a real shame that so many XMPP clients are being discontinued or were already underdeveloped, and new (non-interoperable) messaging apps are popping up all the time.

"Let's write an app that has a federated network architecture very similar to XMPP, except it won't be compatible with XMPP clients and won't federate with XMPP servers, just so we can segment the user base instead of writing an XEP to get our little algorithm into the standard everyone is already using. We'll call it 'Matrix'." Is what the logic appears to amount to.

-   [reply](/comment/reply/1262/225105)

On December 13th, 2016 Anonymous said:

Any documentation on installing Pond around?

-   [reply](/comment/reply/1262/224990)

On December 13th, 2016 asn said:

The developer has shut down the Pond website because they feel like the project is inactive, and no one has forked it yet.

The instructions used to be around https://pond.imperialviolet.org/
 perhaps you can get to them using archive.org .

-   [reply](/comment/reply/1262/224992)

On December 13th, 2016 Anonymous said:

https://web.archive.org/web/20150812153410/https://pond.imperialviolet.org/

-   [reply](/comment/reply/1262/224994)

On December 13th, 2016 Anonymous said:

i love ricochet but i am unable to use the new version :1.4 ( it does not run).

-   [reply](/comment/reply/1262/224999)

On December 14th, 2016 Anonymous said:

We prefer Sig-int mail or Tor mail is much better that using by high profile user \^\_\^

The android/iOS/Window/macOSX still can per-install scanning software to scan the process ID / usage /port open at those secure communication software Ricochet / Chatsecure /Pond / Briar to tag as suspicious user in watchdog\_2

-   [reply](/comment/reply/1262/225010)

On December 14th, 2016 Anonymous said:

Do you really think it's a good idea to promote a program that either dormant or deprecated? If there are no (security) updates for Pond people shouldn't use it anymore -- just think about a Firefox fork that receives no updates, you wouldn't recommend that, would you?

-   [reply](/comment/reply/1262/225287)

Post new comment
----------------

Comment: \*

-   Lines and paragraphs break automatically.
-   Allowed HTML tags: \<em\> \<strong\> \<cite\> \<code\> \<ul\> \<ol\> \<li\> \<b\> \<i\> \<strike\> \<p\> \<br\>

[More information about formatting options](/filter/tips)

[![Syndicate content](/misc/feed.png "Syndicate content")](/crss) [![Syndicate content](/misc/feed.png "Syndicate content")](/crss/node/1262)

Upcoming events
---------------

-   [Many Tor people to Hamburg for 33C3](/events/many-tor-people-hamburg-33c3 "Many Tor people to Hamburg for 33C3")(11 days on Dec 26)
-   [Several Tor people attending Real World Crypto in NYC](/events/several-tor-people-attending-real-world-crypto-nyc "Several Tor people attending Real World Crypto in NYC")(20 days on Jan 4)
-   [Roger to Arlington for NSF SATC PI meeting](/events/roger-arlington-nsf-satc-pi-meeting "Roger to Arlington for NSF SATC PI meeting")(25 days on Jan 9)
-   [Matt and others to Valencia for Internet Freedom Festival](/events/matt-and-others-valencia-internet-freedom-festival "Matt and others to Valencia for Internet Freedom Festival")(81 days on Mar 6)
-   [Many Tor people to Minneapolis for PETS](/events/many-tor-people-minneapolis-pets "Many Tor people to Minneapolis for PETS")(214 days on Jul 17)

[![Add to iCalendar](/sites/all/modules/event-modified/images/ical16x16.gif)](https://blog.torproject.org/event/ical "Add this calendar to your iCalendar")

[full calendar](/event "More events.")

Recent blog posts
-----------------

-   [Tor at the Heart: Tor Messenger](/blog/tor-heart-tor-messenger)
-   [Tor Browser 6.5a6-hardened is released](/blog/tor-browser-65a6-hardened-released)
-   [Tor Browser 6.5a6 is released](/blog/tor-browser-65a6-released)
-   [Tor Browser 6.0.8 released](/blog/tor-browser-608-released)
-   [Tor at the Heart: Riseup.net](/blog/tor-heart-riseupnet)
-   [Tor 0.2.9.7-rc is released: almost stable!](/blog/tor-0297-rc-released-almost-stable)
-   [Tor at the Heart: Onion Messaging](/blog/tor-heart-onion-messaging)
-   [Tor at the Heart: Bridges and Pluggable Transports](/blog/tor-heart-bridges-and-pluggable-transports)
-   [Tor at the Heart: Tails](/blog/tor-heart-tails)
-   [Tor at the Heart: The OONI project](/blog/tor-heart-ooni-project)

[more](/blog "Read the latest blog entries.")

Blog Tag Cloud
--------------

[security fixes](/category/tags/security-fixes) [progress report](/category/tags/progress-report) [tor browser](/category/tags/tor-browser) [tor weekly news](/category/tags/tor-weekly-news) [alpha release](/category/tags/alpha-release) [tails](/category/tags/tails) [research](/category/tags/research) [tor browser bundle](/category/tags/tor-browser-bundle) [tbb](/category/tags/tbb) [anonymous operating system](/category/tags/anonymous-operating-system) [tor](/category/tags/tor) [bug fixes](/category/tags/bug-fixes)

[more tags](/tagadelic/chunk/2)

Drupal Design and Maintenance by [New Eon Media](http://neweonmedia.com "Drupal Design and Maintenance by New Eon Media")

Drupal Development by [Chapter Three](http://chapterthree.com "Drupal Development by Chapter Three")

