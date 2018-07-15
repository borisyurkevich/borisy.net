---
layout: post
title:  "Why iOS Developers Ask for Photo Library Access."
date:   2018-07-15T18:33+0000
---

![Telegram requires access to photo library to change profile picture][1]

Did it happened to you? You wanted to changed profile picture, or selling something
and attaching a photo. You can do this easy on the web but if you
use iPhone or iPad app, you have to give full access to your media.
With this access app can easily upload all your photos, GPS coordinates history,
or even analyse all your photos with machine learning.


Not only it's unnecessary extra step, but also often users need to navigate 
through custom buggy UI. 
Since very beginning iOS allows user to select any photo with sandboxed image 
picker. The app sees the only photo you picked, and you can browse
through your library in private and familiar way, without leaving the app.

I've build simple [proof of concept][2] to demonstrate how easy is to use native 
`UIImagePicker`. I've tested it on device because I can't believe that so 
many developers don't use it. I'm worried about potential privacy disaster 
which can come at any moment now.

Go through all your apps in Settings > Privacy and disable everything you can.
Often you can still get things done by pasting an image, 
but sometimes the only private way is using Safari.

[1]: {{site.url}}/images/access.jpg
[2]: https://github.com/borisyurkevich/PhotoPicker