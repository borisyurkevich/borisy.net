---
layout: post
title:  "How Electron Made GitHub Desktop Worse."
date:  2018-01-22T22:20+0000
---

Not long ago GitHub released new version of their Mac app. Big update which is actually rewrite. New version uses Electron. We know Electron from Slack. I decided to compare 2 versions to demonstrate difference between native and not native.  
![Website presents new version of GitHub Desktop][image-1]

The fact that new version is presented as "The new native" offenses me. GitHub Desktop at farthest point from native it ever was.

Let's look at App size.  
![2 app sizes][image-2]

Old app is 63.7 MB and new is 168 MB. Not surprised as web app need to include all dependencies and custom frameworks. Native apps can use powerful system frameworks which is already included into OS once.

Let's open application. First thing I noticed, minimum window size for Electron app is much larger. Look how many white space is wasted. Old native app could be resizes to much smaller size which makes it's superior for those who keep many windows on screen and value space.
 
![Native version of GitHub Desktop][image-6]
![Electron version of GitHub Desktop][image-7]

Now let’s focus on the title bar. Electron app missing title. Not only title shows what item selected but is also possible to click on it and navigate file hierarchy. Right Click on the drop down menu and select item, this opens Finder. 
![Title Bar options][image-8]

New app has black top and white content area. That’s not a good look, usually Mac apps have main color scheme, dark apps dark everywhere, iMovie is perfect example, and apps like Finder and Safari have light background.

On the screenshots you can see how basic “Add Local Repository” interface differs. Pay attention on the buttons styles, old GitHub apps has familiar buttons looks which is the same as any other Mac app, while new Electron app has its own style. Not only it looks out of place, this also adds additional cognitive load. The same is true for apps font, old app uses excellent system font. At least Cancel button is on the left.

Last let’s click on the File menu. Menu bar is important on Mac. Everything that’s app does can be accesses from menu bar, it allows user to study what app can do, it also displays shortcut commands.  
![Menu comparison][image-4]

Now here, I have to say, new GitHub Desktop does not a bad job, some web apps don’t have menu commands at all. However particularly in the File menu I noticed that old app had more options. One of most important changes is ability to open multiple windows. This core function is lacking from Electron version.

Another subtle benefit using native app is lack of need to click twice when window not active. Any web site or web app can recognize click only in active mode. Normal Mac apps can receive click events even when window not active. For example, you can click on the + button in top right corner of GitHub Desktop even when window is not active. Any web application will require 2 clicks in this situation.  

### Conclusion.  
Web apps never going to feel native. You can call it "React native" but it will not make code more native. You can call it "Electron" but it will not make app size smaller and efficient. 

[Native GitHub Desktop app is no longer available but you can download my copy.][1] I still use it to this day and I will continue until it works.

[image-1]:	{{ site.url }}/images/github-electron-web.png
[image-2]:	{{ site.url }}/images/app-size.png
[image-4]:	{{ site.url }}/images/menu-comparison.png
[image-6]:	{{ site.url }}/images/new-electron.png
[image-7]:	{{ site.url }}/images/new-github.png
[image-8]:	{{ site.url }}/images/title-bar.png

[1]: {{ site.url }}/downloads/GitHub-Desktop.zip
