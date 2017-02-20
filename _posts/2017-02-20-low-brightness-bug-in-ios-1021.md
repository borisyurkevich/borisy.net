---
layout: post
title:  "Low Brightness Bug in iOS 10.2.1"
date:  2017-02-20T23:06:23+0000
---

<p style style="color:black;"><b>If you having Low Brightness issue, turning Zoom on and off in Settings > General > Accessibility can help you.</b><p/>

With iOS 10.2.1 update Apple engineers fixed [lots of security problems.](https://support.apple.com/en-us/HT207482) I was impressed with the list of fixes and the fact that Apple credited some people and organisations which helped to discover the problems.

I went to Twitter to find out how update is doing, as I sometimes do, and found one complaint from Tim Carr about brightness issues on his iPhone 6. First I was sceptical because I read release  notes prior and I couldn't make a connection between patching core iOS security and breaking brightness.

<blockquote class="twitter-tweet" data-lang="en-gb"><p lang="en" dir="ltr">Do not update to iOS 10.2.1. It breaks your screen brightness.</p>&mdash; Tim Carr (@TimothyDRCarr) <a href="https://twitter.com/TimothyDRCarr/status/823649398999678976">23 January 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script> 

Turns out there's real bug which locks maximum iPhone 6 and 6s[^2] brightness at certain battery levels. Tim Carr is registered blind and having maximum screen brightness at all time is very important for him and many other users with visual disabilities.  Quick search brought this [iMore forum thread](http://forums.imore.com/ask-rene/382928-dim-iphone-screen-after-updating-ios-10-2-1-a.html) which proves that's it's not isolated problem.

<img src="{{site.url}}/images/brightness-bug.jpg" alt="Two iPhone 6 phones. Left is without latest update. Right is with latest update. Left screen is much brighter." width="337"/>
*Two iPhone 6 phones. Left is without latest update. Right is with latest update. Both set to full brightness. Image from Tim Carr's tweet.*

We tried to troubleshoot it and came to a conclusion that's issue was in iOS not his iPhone. I hoped that Apple Support could help and encouraged Tim to talk to them. That's didn't help at all. Tim tried to reach them in many ways — through Twitter and phone calls and couldn't get any solution. In his desperation he even tweeted to Tim Cook:[^1]

<blockquote class="twitter-tweet" data-lang="en-gb"><p lang="en" dir="ltr"><a href="https://twitter.com/tim_cook">@tim_cook</a> I&#39;m registered blind. Now I cannot use my phone as soon as the battery hits 70% because the screen is so dim. I&#39;ve logged a call..</p>&mdash; Tim Carr (@TimothyDRCarr) <a href="https://twitter.com/TimothyDRCarr/status/825116715361112064">27 January 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

and got this poor response:

<blockquote class="twitter-tweet" data-lang="en-gb"><p lang="en" dir="ltr"><a href="https://twitter.com/TimothyDRCarr">@TimothyDRCarr</a> You came to the right spot. We&#39;ll check it out and see what&#39;s going on here. To start, send us a DM using this link: <a href="https://t.co/GDrqU22YpT">https://t.co/GDrqU22YpT</a></p>&mdash; Apple Support (@AppleSupport) <a href="https://twitter.com/AppleSupport/status/825136164969521152">28 January 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

It would be much better if Apple could admit their fault and inform their support team. I bet some iPhone 6 owners talking to Apple Support right now and getting standard responses to restore their devices. Apple Support at this moment has no idea about the problem and taking every enquiry through the standard path when it could be just a single reply: *Thank you, we working on a fix, I'm meanwhile please try to turn Zoom on and off.*

Instead they making it worse:

<blockquote class="twitter-tweet" data-lang="en-gb"><p lang="en" dir="ltr"><a href="https://twitter.com/AppleSupport">@AppleSupport</a> as a note, a restore doesn&#39;t solve everything. Plus asking a visually impaired or blind person to restore their phone</p>&mdash; Tim Carr (@TimothyDRCarr) <a href="https://twitter.com/TimothyDRCarr/status/825136886284967941">28 January 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-lang="en-gb"><p lang="en" dir="ltr"><a href="https://twitter.com/AppleSupport">@AppleSupport</a> you&#39;ve closed two of my posts down too. There were disabled users in them watching for any update. Now they can&#39;t.</p>&mdash; Tim Carr (@TimothyDRCarr) <a href="https://twitter.com/TimothyDRCarr/status/825136607649005569">28 January 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

As Tim found out, there's a workaround. I mentioned it on the top. I also submitted [a radar #30612785.][3] Let's hope it's going to be fixed.

[^1]: Note Apple Support monitors tweets to Tim Cook.
[^2]: I couldn't reproduce issue on my 6s which means not all devices affected.
[2]: https://openradar.appspot.com/30612785