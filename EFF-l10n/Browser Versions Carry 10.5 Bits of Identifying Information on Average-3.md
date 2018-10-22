
Browser Versions Carry 10.5 Bits of Identifying Information on Average
======================================================================


*This is part 3 of a series of posts on user tracking on the modern web. You can also read [part 1](https://www.eff.org/deeplinks/2009/09/new-cookie-technologies-harder-see-and-remove-wide) and [part 2](https://www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks)*.

Whenever you visit a web page, your browser sends a "User Agent" header to the website saying precisely which operating system and web browser you are using. This information could help distinguish Internet users from one another because these versions differ, often considerably, from person to person. We recently ran an experiment to see to what extent this information could be used to track people (for instance, if someone deletes their browser cookies, would the User Agent, alone or in combination with some other detail, be unique enough to let a site recognize them and re-create their old cookie?).

Our experiment to date has shown that the browser [User Agent](http://en.wikipedia.org/wiki/User_agent) string usually carries 5-15 bits of identifying information (about 10.5 bits on average). That means that on average, only one person in about 1,500 (2<sup>10.5</sup>) will have the same User Agent as you. On its own, that isn't enough to recreate cookies and track people perfectly, but in combination with another detail like geolocation to a particular ZIP code or having an uncommon browser plugin installed, the User Agent string becomes a real privacy problem.

### User Agents: An Example of Browser Characteristics Doubling As Tracking Tools

When we analyze the privacy of web users, we usually focus on user accounts, cookies, and IP addresses, because those are the usual means by which a request to a web server can be associated with other requests and/or linked back to an individual human being, computer, or local network.

Typical advice for improving your privacy as you surf the web might include blocking or deleting cookies (and [supercookies](https://www.eff.org/deeplinks/2009/09/new-cookie-technologies-harder-see-and-remove-wide)), and using proxy servers or tools like [Tor](https://www.torproject.org/) to hide your IP address.

It's not intuitively obvious that a User Agent poses a similar risk to a unique tracking cookie. After all, cookies were designed, in part, to help web sites distinguish and recognize individual browsers, and User Agents weren't. And there could be millions of people out there who use the same browser and operating system that you do. But let's examine the matter more closely. A typical User Agent string looks something like this:

    Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)

In fact, that was the most common user agent string among browsers visiting the EFF website during the test period: Firefox 3.5.3 running on Windows XP. Notice that the operating system and browser versions are extremely specific and that the User Agent also includes the user's preferred language. There are a lot of things that can vary inside that string, and those variations can be used to distinguish and track people as they browse the Web.

### Our Results to date on User Agent Identifiability

We ran an experiment to measure precisely how identifying the User Agent strings would have been among a 36-hour anonymized sample of requests to the EFF website. The following table shows different classes of browser, with the number of bits for best and average case User Agents within that class:

### Identifying information in various classes of browsers

| Browser class           | Avg. identifying information | Minimum identifying information | (Least identifying user agent)                                                                                                                  |
|-------------------------|------------------------------|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Modern Windows Desktops | 10.3-11.3 bits               | 4.6 - 5.0 bits                  | Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)                                   |
| Internet Explorer       | 13.2-13.5 bits               | 6.3 - 7.2 bits                  | Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)                                                                                         |
| Firefox                 | 8.6 - 9.4 bits               | 4.6 - 5.0 bits                  | Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)                                   |
| Chrome                  | 7.5-8.5 bits                 | 5.7 - 6.2 bits                  | Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/532.0 (KHTML, like Gecko) Chrome/3.0.195.27 Safari/532.0                            |
| Linux                   | 11.8-13.15 bits              | 6.6-7.9 bits                    | Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/9.04 (jaunty) Firefox/3.0.14                                       |
| Ubuntu                  | 9.6 - 11.7 bits              | 6.6 - 7.8 bits                  | Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/9.04 (jaunty) Firefox/3.0.14                                       |
| Debian                  | 13.5-15.3 bits               | 10.50 - 11.7 bits               | Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009091010 Iceweasel/3.0.6 (Debian-3.0.6-3)                                          |
| Macintosh               | 8.8-9.3 bits                 | 5.8-5.8 bits                    | Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3                                                 |
| iPhone                  | 10.8 - 11.3 bits             | 8.7 - 9.3 bits                  | Mozilla/5.0 (iPhone; U; CPU iPhone OS 3\_1 like Mac OS X; en-us) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7C144 Safari/528.16  |
| Blackberry              | 14.7 - 15.5 bits             | 12.0 - 12.7 bits                | BlackBerry9530/4.7.0.148 Profile/MIDP-2.0 Configuration/CLDC-1.1 VendorID/105                                                                   |
| Android                 | 14.4 - 14.4 bits             | 12.2-12.4 bits                  | Mozilla/5.0 (Linux; U; Android 1.6; en-us; T-Mobile G1 Build/DRC83) AppleWebKit/528.5+ (KHTML, like Gecko) Version/3.1.2 Mobile Safari/525.20.1 |

There are several remarkable facts about this dataset. Overall, it's amazing how identifying User Agent strings are. 10.5 bits is about one-third of the total information required to identify an Internet user.

It's also surprising that platforms like Firefox and Ubuntu, which have lower market penetration, are on average comparable or even less identifying than Windows and Microsoft Internet Explorer, which have very large userbases and should therefore have larger crowds to hide in. Part of this may be that visitors to the EFF website are over-representative of the former groups, but it's also clear that a large part of this is that Internet Explorer has a very high level of variation in its User Agent strings, with typical examples looking something like this:

Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.5.30729; .NET CLR 3.0.30618)

All of the different library and component versions there essentially function as partial tracking tokens.

We've launched a project called [Panopticlick](https://panopticlick.eff.org/) to collect a new dataset that extends this analysis from User Agents to the full browser plugin and configuration space. You can use Panopticlick to receive a [uniqueness measurement](https://panopticlick.eff.org/) for your own browser, and help EFF's privacy research efforts at the same time!

### Methodology

During September 2009, we took a 36 hour sample of anonymized requests to the eff.org web server by hashing the IP address of each request with a random salt, and throwing away the salt. We then calculated the amount of identifying information conveyed by each browser. Identifying information is measured in "[bits of entropy](https://www.eff.org/deeplinks/2010/01/primer-information-theory-and-privacy)", and says how large a crowd the information would reveal you within. Browsers usually convey between 5 and 15 bits of identifying information, about 10.5 bits on average. 10 bits of identifying information would allow you to be picked out of a crowd of 2<sup>10</sup>, or 1024 people. 10.5 bits of information identifies can identify people from crowds of just under 1,448.

Because we did not use cookies or any other mechanism to distinguish between repeat and new visitors, each measurement of bits of identifying information lies between an upper and lower bound.<a href="#footnote1_wmojrq5" id="footnoteref1_wmojrq5" class="see-footnote" title="One bound is based on a count in which each hashed IP address is counted for only one request; the other bound is based on treating each hit as a unique browser.  In almost all cases, the true amount of identifying information pertaining to the browser should lie between these two values.">1</a>

-   

    <a href="#footnoteref1_wmojrq5" class="footnote-label">1.</a> One bound is based on a count in which each hashed IP address is counted for only one request; the other bound is based on treating each hit as a unique browser. In almost all cases, the true amount of identifying information pertaining to the *browser* should lie between these two values.

Related Issues
--------------

[Privacy](/issues/privacy)

**Share It** <a href="https://twitter.com/intent/tweet?text=Browser%20Versions%20Carry%2010.5%20Bits%20of%20Identifying%20Information%20on%20Average&amp;url=https%3A//www.eff.org/deeplinks/2010/01/tracking-by-user-agent&amp;via=eff&amp;related=eff" class="share-twitter" title="Share on Twitter"><span>Share on Twitter</span><em></em></a> <a href="https://www.facebook.com/share.php?u=https%3A//www.eff.org/deeplinks/2010/01/tracking-by-user-agent&amp;title=Browser%20Versions%20Carry%2010.5%20Bits%20of%20Identifying%20Information%20on%20Average" class="share-facebook" title="Share on Facebook"><span>Share on Facebook</span><em></em></a> <a href="https://plus.google.com/share?url=https%3A//www.eff.org/deeplinks/2010/01/tracking-by-user-agent" class="share-google" title="Share on Google+"><span>Share on Google+</span><em></em></a> <a href="https://www.eff.org/deeplinks/2010/01/tracking-by-user-agent" class="share-clipboard disabled" title="Copy to clipboard"><span>Copy link</span><em></em></a>

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

[Back to top](#main-content)


