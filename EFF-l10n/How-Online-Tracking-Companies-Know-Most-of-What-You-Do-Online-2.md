
How Online Tracking Companies Know Most of What You Do Online (and What Social Networks Are Doing to Help Them)
===============================================================================================================

DEEPLINKS BLOG

Technical Analysis by [Peter Eckersley](/about/staff/peter-eckersley)

September 21, 2009

**Share It** <a href="https://twitter.com/intent/tweet?text=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29&amp;url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;via=eff&amp;related=eff" class="share-twitter" title="Share on Twitter"><span>Share on Twitter</span><em></em></a> <a href="https://www.facebook.com/share.php?u=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;title=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29" class="share-facebook" title="Share on Facebook"><span>Share on Facebook</span><em></em></a> <a href="https://plus.google.com/share?url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-google" title="Share on Google+"><span>Share on Google+</span><em></em></a> <a href="https://www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-clipboard disabled" title="Copy to clipboard"><span>Copy link</span><em></em></a>

How Online Tracking Companies Know Most of What You Do Online (and What Social Networks Are Doing to Help Them)
===============================================================================================================

**Share It** <a href="https://twitter.com/intent/tweet?text=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29&amp;url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;via=eff&amp;related=eff" class="share-twitter" title="Share on Twitter"><span>Share on Twitter</span><em></em></a> <a href="https://www.facebook.com/share.php?u=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;title=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29" class="share-facebook" title="Share on Facebook"><span>Share on Facebook</span><em></em></a> <a href="https://plus.google.com/share?url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-google" title="Share on Google+"><span>Share on Google+</span><em></em></a> <a href="https://www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-clipboard disabled" title="Copy to clipboard"><span>Copy link</span><em></em></a>

*This post is Part 2 of a series on user tracking on the web today. You can read Part 1 [here](https://www.eff.org/deeplinks/2009/09/new-cookie-technologies-harder-see-and-remove-wide) and Part 3 [here](https://www.eff.org/deeplinks/2010/01/tracking-by-user-agent).*

3rd party advertising and tracking firms are ubiquitous on the modern web. When you visit a webpage, there's a good chance that it contains tiny images or invisible JavaScript that exists for the sole purpose of tracking and recording your browsing habits. This sort of tracking is performed by many dozens of different firms. In this post, we're going to look at how this tracking occurs, and how it is being combined with data from accounts on social networking sites to build extensive, identified profiles of your online activity.

### How 3rd parties get to see what you do on the web.

Let's start with an example of 3rd party tracking: when we went to CareerBuilder.com, which is the largest online jobs site in the United States, and searched for a job, CareerBuilder included JavaScript code from 10 (!) different tracking domains: [Rubicon Project](http://www.rubiconproject.com/), AdSonar, Advertising.com, Tacoda.net (all three are divisions of [AOL advertising](//advertising.aol.com/advertiser-solutions/sponsored-listings)), [Quantcast](http://quantserve.com/), [Pulse 360](http://pulse360.com/), [Undertone](http://www.undertone.com/), AdBureau (part of [Microsoft Advertising](http://www.atlassolutions.com/)), [Traffic Marketplace](http://www.trafficmarketplace.com/), and [DoubleClick](http://www.doubleclick.com/) (which is owned by Google). On other visits we've also seen CareerBuilder include tracking scripts and non-JavaScript [web bugs](http://en.wikipedia.org/wiki/Web_bug) from several other domains. There are pretty sound reasons to hope that when you search for a job online, that fact isn't broadcast to dozens of companies you've never heard of — but that's precisely what's happening here.

![Ten 3rd party tracking sites' content is included in CareerBuilder search results](/files/cb-ns2.jpg)
(in this screenshot, [NoScript](http://noscript.net/) is being used to identify the third parties whose code is embedded in the page)

Each of these tracking companies can track you over multiple different websites, effectively following you as you browse the web. They use either cookies, or hard-to-delete ["super cookies"](https://www.eff.org/deeplinks/2009/09/new-cookie-technologies-harder-see-and-remove-wide), or other means, to link their records of each new page they see you visit to their records of all the pages you've visited in the previous minutes, months and years. The widespread presence of 3rd party web bugs and tracking scripts on a large proportion of the sites on the Web means that these companies can build up a long term profile of most of the things we do with our web browsers.

### They can track us, but do they know who we are?

Given how much tracking firms know about our browsing history, it's worth asking whether these companies also know who we are. The answer, unfortunately, appears to be "yes", at least for those of us who use social networking sites.

[A recent research paper](http://conferences.sigcomm.org/sigcomm/2009/workshops/wosn/papers/p7.pdf) by Balachander Krishnamurthy and Craig Wills shows that social networking sites like Facebook, LinkedIn and MySpace are giving the hungry cloud of tracking companies an easy way to add your name, lists of friends, and other profile information to the records they already keep on you.

The main theme of the paper is that when you log in to a social networking site, the social network includes advertising and tracking code in such a way that the 3rd party can see which account on the social network is yours. They can then just go to your profile page, record its contents, and add them to their file. Of the 12 social networks surveyed in the paper, only one (Orkut) didn't leak any personally identifying information to 3rd parties.

There are some interesting technical details in how the social networking sites leak this data. In some cases, the leakage may be unintentional, but in others, there is clever and surreptitious anti-privacy engineering at work.

### Paths for Data Leakage from Social Networks to 3rd party Tracking Firms

The most obvious way that a 3rd party tracker might learn which account on a social networking site is yours is via the [HTTP Referrer header](http://en.wikipedia.org/wiki/HTTP_referrer). A typical URL on a social networking site includes a username or user ID number, and any 3rd party will be able to see that.<a href="#footnote1_cl3509c" id="footnoteref1_cl3509c" class="see-footnote" title="One subtlety here is that sometimes the 3rd party won&#39;t be able to tell whether a profile is yours or belongs to someone else. But there are several ways around that: they can look for URLs associated with profile editing or other activites that your friends can&#39;t do with to your profile; they can see which profile you visit first when you log in to the site, and they can see which profile you visit most often over time.">1</a>

A second and slightly more revealing method that some social networks use to leak personal information is through [URL/URI parameters](http://en.wikipedia.org/wiki/URI_scheme#Examples) for the 3rd party content. Here's an anonymized example from the paper:

    GET /track/?...&fb_sig_time=1236041837.3573&
         fb_sig_user=123456789&...
    Host: adtracker.socialmedia.com
    Referer: http://apps.facebook.com/kick_ass/...

(In this request, a Facebook app is sending the user's facebook user ID and signin time to to adtracker.socialmedia.com)

The third and most surprising method for leaking personal information is to alias 3rd party tracking servers into the host site's domain name in such a way that the 3rd party can see the host site's cookies, in violation of the [same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy). Here's an example from the paper:

    GET /st?ad_type=iframe&age=29&gender=M&e=&zip=11301&...
    Host: ad.hi5.com
    Referer: http://www.hi5.com/friend/profile/displaySameProfile.do?userid=123456789
    Cookie: LoginInfo=M_AD_MI_MS|US_0_11301; Userid=123456789;Email=jdoe@email.com;

(ad.hi5.com is actually ad.yieldmanager.com, and it's receiving different bits of personal information via referrer, URI parameters, and the hi5.com cookie which the same origin policy wouldn't have allowed it to have — so it's an example of all three leakage methods at once)

### What can I do to protect myself?

Unfortunately, there is no easy way to use modern, cookie- and JavaScript-dependent websites and social networking sites and avoid tracking at the same time. In order to be substantially protected against these tracking mechanisms, you'd need to do the following:

1.  Pick a good cookie policy for your browser, like "only keep cookies until I close my browser", or manual approval of all cookies.
2.  Disable Flash Cookies and all the other kinds of "super cookies".
3.  Use the Firefox extensions [RequestPolicy](http://www.requestpolicy.com/) and [NoScript](http://noscript.net/) to control when 3rd party sites can include content in your pages or run code in your browser, respectively. These tools are very effective, but be aware that they're hard to use: lots of sites that depend on JavaScript will need to be whitelisted before they work correctly.
4.  Use the [Targeted Advertising Cookie Opt-Out](http://taco.dubfire.net/) plugin. This will automatically opt you out of any 3rd party trackers who have an opt out somewhere that requires you to accept a cookie. Be aware that not all 3rd parties will offer opt outs, or that some of them may interpret "opt out" to mean "do not show me targeted ads", rather than "do not track my behavior online".
5.  As always, it doesn't hurt to use [Tor](https://torproject.org) via TorButton to hide your IP address and other browser characteristics when you want maximal browser privacy.

Unfortunately, many of the steps above are quite difficult to follow, and we're fearful that the vast majority of Internet users will continue to be tracked by dozens of companies — companies they've never heard of, companies they have no relationship with, companies they would never *choose* to trust with their most private thoughts and reading habits.

It isn't going to be easy to fix this mess. On the technical side, all of this tracking follows from the design of the Web as an interactive hypertext system, combined with the fact that so many websites are willing to assist advertisers in tracking their visitors. Browsers could be altered to make them harder to track, but great care and clever design will be required to achieve that without undermining the virtues of interactive hypertext in the first place. It's not clear that anyone has found the right way to do that yet.

On the legal side, it's clear that the current U.S. privacy regime isn't working: behavioral tracking companies can put whatever they want in the fine print of their privacy policies, and few of the visitors to CareerBuilder or any other website will ever realize that the trackers are there, let alone read their policies. It's time we found legal rules to ensure that people actually *know* when their privacy is part of the price they pay to visit a site.

-   

    <a href="#footnoteref1_cl3509c" class="footnote-label">1.</a> One subtlety here is that sometimes the 3rd party won't be able to tell whether a profile is yours or belongs to someone else. But there are several ways around that: they can look for URLs associated with profile editing or other activites that your friends can't do with to your profile; they can see which profile you visit first when you log in to the site, and they can see which profile you visit most often over time.

Related Issues
--------------

[Privacy](/issues/privacy)

[Online Behavioral Tracking](/issues/online-behavioral-tracking)

**Share It** <a href="https://twitter.com/intent/tweet?text=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29&amp;url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;via=eff&amp;related=eff" class="share-twitter" title="Share on Twitter"><span>Share on Twitter</span><em></em></a> <a href="https://www.facebook.com/share.php?u=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks&amp;title=How%20Online%20Tracking%20Companies%20Know%20Most%20of%20What%20You%20Do%20Online%20%28and%20What%20Social%20Networks%20Are%20Doing%20to%20Help%20Them%29" class="share-facebook" title="Share on Facebook"><span>Share on Facebook</span><em></em></a> <a href="https://plus.google.com/share?url=https%3A//www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-google" title="Share on Google+"><span>Share on Google+</span><em></em></a> <a href="https://www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks" class="share-clipboard disabled" title="Copy to clipboard"><span>Copy link</span><em></em></a>

Join EFF Lists
--------------

### Join Our Newsletter!

Email updates on news, actions, events in your area, and more.

Email Address

Postal Code (optional)

Thanks, you're awesome! Please check your email for a confirmation link.

Oops something is broken right now, please try again later.

Related Updates
---------------

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/google-spy-eye.png?itok=K1Qdm24Y" title="Google Spying" alt="Google Spying" width="250" height="250" />](/deeplinks/2018/10/privacy-badger-now-fights-more-sneaky-google-tracking)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Bennett Cyphers](/about/staff/bennett-cyphers), Alexei Miagkov, [Andrés Arrieta](/about/staff/andres-arrieta)</span> <span class="node-date"> | October 4, 2018</span>

### [Privacy Badger Now Fights More Sneaky Google Tracking](/deeplinks/2018/10/privacy-badger-now-fights-more-sneaky-google-tracking)

With its latest update, Privacy Badger now fights “link tracking” in a number of Google products. *Link tracking* allows a company to follow you whenever you click on a link to leave its website. Earlier this year, EFF rolled out a Privacy Badger update [targeting Facebook’s use of this...](https://www.eff.org/deeplinks/2018/05/privacy-badger-rolls-out-new-ways-fight-facebook-tracking)

[<img src="https://www.eff.org/files/styles/teaser/public/issues/icon-privacy-1_0.png?itok=sB3fvf2s" width="250" height="250" />](/deeplinks/2018/10/new-york-city-home-sharing-ordinance-could-create-privacy-nightmare)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Rebecca Jeschke](/about/staff/rebecca-jeschke)</span> <span class="node-date"> | October 3, 2018</span>

### [New York City Home-Sharing Ordinance Could Create Privacy Nightmare](/deeplinks/2018/10/new-york-city-home-sharing-ordinance-could-create-privacy-nightmare)

Many cities across the country are struggling with issues surrounding short-term vacation rentals and how they affect the availability and price of housing for local residents. However, New York City’s [latest ordinance](https://www.nytimes.com/2018/07/18/nyregion/new-york-city-airbnb-crackdown.html) aimed at regulating home-sharing platforms is an extraordinary governmental overreach with invasive privacy ramifications, and EFF is...

[<img src="https://www.eff.org/files/styles/teaser/public/eff-pr-og.png?itok=Sovgqi6b" width="250" height="250" />](/press/releases/briefing-thursday-effs-eva-galperin-and-lookout-discuss-demo-cybersecurity-attacks-0)

[Press Release](/updates?type=press_release) <span class="node-date"> | October 3, 2018</span>

### [Briefing Thursday: EFF’s Eva Galperin and Lookout Discuss, Demo Cybersecurity Attacks On Democracy](/press/releases/briefing-thursday-effs-eva-galperin-and-lookout-discuss-demo-cybersecurity-attacks-0)

Washington, D.C.—On Thursday, Oct. 4, at 2 pm, Electronic Frontier Foundation (EFF) Director of Cybersecurity [Eva Galperin](https://www.eff.org/about/staff/eva-galperin) will speak at a special session for congressional staffers and representatives about how malware and spyware targeted at mobile devices is being used against dissidents, activists, journalists, and others to disrupt democracy...

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/police-2.png?itok=xJIFjHGT" width="250" height="250" />](/deeplinks/2018/10/lifting-cloak-secrecy-nypd-surveillance-technology)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Nathan Sheard](/about/staff/nathan-nash-sheard-0)</span> <span class="node-date"> | October 3, 2018</span>

### [Lifting the Cloak of Secrecy From NYPD Surveillance Technology](/deeplinks/2018/10/lifting-cloak-secrecy-nypd-surveillance-technology)

For too long, the New York Police Department has secretly deployed cutting-edge spy tech, without notice to the public. Many of these snooping devices invade our privacy, deter our free speech, and disparately burden minority and immigrant communities. Fortunately, a proposed ordinance (“the POST Act”) would lift the cloak of...

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/54_banner_eff2.jpg?itok=IJrfiALE" alt="A photo of the book." width="250" height="250" />](/deeplinks/2018/10/mcsweeneys-and-eff-team-end-trust)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Dave Maass](/about/staff/dave-maass)</span> <span class="node-date"> | October 2, 2018</span>

### [McSweeney’s and EFF Team Up for “The End of Trust”](/deeplinks/2018/10/mcsweeneys-and-eff-team-end-trust)

For 20 years, McSweeney’s has been the first name (or last name, actually) in emerging short fiction. But this November, McSweeney’s will debut the first all-non-fiction issue of Timothy McSweeney’s Quarterly Concern: [“The End of Trust” (Issue 54)](https://store.mcsweeneys.net/products/mcsweeney-s-issue-54-the-end-of-trust) is a collection of essays and interviews focusing on issues related...

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/icon-free-speech-1.png?itok=GGjhfEFS" width="250" height="250" />](/deeplinks/2018/09/fake-news-and-elections-brazil-several-initiatives-no-easy-answer)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Veridiana Alimonti](/about/staff/veridiana-alimonti)</span> <span class="node-date"> | October 2, 2018</span>

### [Fake News and Elections in Brazil: Several Initiatives, No Easy Answer](/deeplinks/2018/09/fake-news-and-elections-brazil-several-initiatives-no-easy-answer)

Brazil’s federal elections are set for October 7, 2018, but the fear that “fake news” online might unfairly interfere with the electoral process has been looming over the country for far longer than this year’s campaign. In June, the President of the Superior Electoral Court declared such interference [could...](https://www.valor.com.br/politica/5611825/fux-eleicoes-podem-ser-anuladas-se-influenciadas-por-noticias-falsas)

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/icon-free-speech-1.png?itok=GGjhfEFS" width="250" height="250" />](/deeplinks/2018/09/fake-news-and-elections-brazil-several-initiatives-no-easy-answer)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Veridiana Alimonti](/about/staff/veridiana-alimonti)</span> <span class="node-date"> | October 2, 2018</span>

### [Fake News and Elections in Brazil: Several Initiatives, No Easy Answer](/deeplinks/2018/09/fake-news-and-elections-brazil-several-initiatives-no-easy-answer)

Brazil’s federal elections are set for October 7, 2018, but the fear that “fake news” online might unfairly interfere with the electoral process has been looming over the country for far longer than this year’s campaign. In June, the President of the Superior Electoral Court declared such interference [could...](https://www.valor.com.br/politica/5611825/fux-eleicoes-podem-ser-anuladas-se-influenciadas-por-noticias-falsas)

[<img src="https://www.eff.org/files/styles/teaser/public/issues/icon-security-trans.png?itok=LqXbaL24" title="Security transparent" alt="Security" width="250" height="250" />](/deeplinks/2018/10/project-verify)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Gennie Gebhart](/about/staff/gennie-gebhart), [Starchy Grant](/about/staff/david-grant)</span> <span class="node-date"> | October 1, 2018</span>

### [The Devil Is in The Details Of Project Verify’s Goal To Eliminate Passwords](/deeplinks/2018/10/project-verify)

A coalition of the four largest U.S. wireless providers calling itself the [Mobile Authentication Taskforce](http://verify.verizonacsf.acsitefactory.com/about-us) [recently announced an initiative](https://www.theverge.com/2018/9/13/17855074/project-verify-passwords-mobile-login-att-sprint-tmobile-verizon) named [Project Verify](http://verify.verizonacsf.acsitefactory.com/). This project would let users log in to apps and websites with their phone instead of a password, or serve as an alternative to [...]()

[<img src="https://www.eff.org/files/styles/teaser/public/banner_library/digital-search_2.png?itok=7CF3Y3_n" width="250" height="250" />](/deeplinks/2018/10/eff-urges-ninth-circuit-let-criminal-defense-teams-vet-forensic-software)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Stephanie Lacambra](/about/staff/stephanie-lacambra), [Kit Walsh](/about/staff/kit-walsh)</span> <span class="node-date"> | October 1, 2018</span>

### [EFF Urges Ninth Circuit to Let Criminal Defense Teams Vet Forensic Software](/deeplinks/2018/10/eff-urges-ninth-circuit-let-criminal-defense-teams-vet-forensic-software)

You shouldn’t be convicted by secret evidence in a functional democracy. So when the government uses forensic software to investigate and build its case in a criminal prosecution, it should not hide that technological evidence from the defense. In an [amicus brief](https://www.eff.org/document/brief-amicus-curiae-electronic-frontier-foundation-support-defendant-appellants-petition-0) filed today EFF urged the Ninth Circuit...

[<img src="https://www.eff.org/files/styles/teaser/public/issues/icon-privacy-1_0.png?itok=sB3fvf2s" width="250" height="250" />](/deeplinks/2018/10/new-witness-and-new-experts-bolster-our-jewel-case-we-fight-governments-latest-0)

[Deeplinks Blog](/updates?type=blog) <span class="node-author"> by [Cindy Cohn](/about/staff/cindy-cohn)</span> <span class="node-date"> | October 1, 2018</span>

### [New Witness and New Experts Bolster Our Jewel Case As We Fight Government’s Latest Attempt to Derail Lawsuit Challenging Unconstitutional NSA Spying](/deeplinks/2018/10/new-witness-and-new-experts-bolster-our-jewel-case-we-fight-governments-latest-0)

EFF has presented its full evidentiary case that the five ordinary Americans who are plaintiffs in *[Jewel v. NSA](https://www.eff.org/cases/jewel)* were among the hundreds of millions of nonsuspect Americans whose communications and communications records have been touched by the government’s [mass surveillance regimes](https://www.eff.org/nsa-spying). This [presentation](https://www.eff.org/document/plaintiffs-opposition-governments-summary-judgment-motion-and-plaintiffs-motion-proceed) includes a new...

