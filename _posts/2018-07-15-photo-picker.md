---
layout: post
title:  "iOS Developers Lie with Photo Permissions Dialog."
date:   2018-07-15T18:33+0000
---

![Telegram requires access to photo library to change profile picture][1]

If you try to change your profile picture on Telegram, it'll demand access
to your entire photo library. Telegram doesn't need it. System image picker
doesn't need user permission! But many developers intentionally lie to us, 
so we would think we have to give a permission. 
In fact permission is only needed to add new image to the library, 
or for custom picker UI or if you want upload all of your pictures.

Since very beginning iOS allows user to select 
any photo with sandboxed image  picker. The app sees the only photo you picked, 
and you can browse through your library in private and familiar way, 
without leaving the app. However even apps which use system image picker
ask photos permission. Is it laziness or ignorance?

Did it happened to you? You wanted to changed profile picture, or selling something
and attaching a photo. You can do this easy on the web but if you
use iPhone or iPad app, you have to give full access to your media.
With this access app can easily upload all your photos, GPS coordinates history,
or even analyse all your photos with machine learning. I'm worried about 
potential privacy disaster which can come at any moment now.

Not only it's unnecessary extra step, but also often users need to navigate 
through custom buggy UI. 

I've build simple [proof of concept][2] to demonstrate that native 
`UIImagePicker` can work without your permission, your photos won't be accessible
to the app.

I've tested it on device because I can't believe that so 
many developers ask photos permission not in the right moment. Yes, you can ask
me if I try to save a photo but you can't do it when you trying to show 
`UIImagePicker`.

Go through all your apps in Settings > Privacy and disable everything you can.
Often you can still get things done by pasting an image, 
but sometimes the only private way is using Safari.

[1]: {{site.url}}/images/access.jpg
[2]: https://github.com/borisyurkevich/PhotoPicker