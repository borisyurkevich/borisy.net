---
layout: post
title:  "Apps Should Work Offline, with Visible Status Bar."
date:  2017-09-16T18:28:54+0000
---

We have not expensive data plan, and I disable mobile data for most of my apps. I have a problem with “Internet Wall” appearing in even one of the best apps like Carrot Weather ([iOS][1] or [Mac][2]) or Super Mario Run [(iOS). ][3]Just today I opened Carrot Weather while on vacation to have white screen of nothing telling me there’s connection problem. 

![Apple Wather on left and Carrot on the right. Apple app has visible status bar and shows all data even though both apps don't have immidiate internet acces.][image-1]

And not only I can’t check the weather but I can’t see time, battery level and most important, connection status. I guess developer decided their custom made artistic interface is more important than Status Bar. 

I use Carrot Weather for their great Apple Watch app. On iPhone I prefer Weather but I launch Carrot from time to time. Recently Carrot Weather had big 2.0 update with new UI. I am sure developer very proud of all extra features and personality added into Carrot Weather but I don’t care. I even turned off all “fun” features. And this is why I continue to use Weather, it shows me the weather in any conditions, especially when I am trying to manage my data plan usage. It also shows me Status Bar at any screen.

Recently we shipped goEvo [(iOS),][4] app with daily planner for meals and exercises, and function to log emotional state and even have 2 way conversations with virtual coach. I am proud that all of its features work without internet connection. 

Every non-web software developer should understand that application they develop should not require immediate internet connection. It’s not hard to do, and it’s good for performance and energy efficiency. Otherwise what’s point of making native app? If Carrot Weather can’t do data persistence, they should’ve focus their development building web application instead.

[1]:	https://itunes.apple.com/gb/app/carrot-weather/id961390574?mt=8&uo=4&at=1010l4GJ
[2]:	https://itunes.apple.com/gb/app/carrot-weather-talking-forecast-robot/id993487541?mt=12&uo=4&at=1010l4GJ
[3]:	https://itunes.apple.com/gb/app/super-mario-run/id1145275343?mt=8&uo=4&at=1010l4GJ
[4]:	https://itunes.apple.com/gb/app/goevo/id1204199991?mt=8&uo=4&at=1010l4GJ

[image-1]:	{{site.url}}/images/weather-vs-carrot.jpg "Apple Weather and Carrot Weather while offline"