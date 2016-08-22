---
layout: post
title:  "Safari VS Chrome."
date:   2016-08-23 9:00:00 +0100
---

Apple [claims](http://www.apple.com/safari/) that Safari is "Faster than Chrome and Firefox." I've decided to perform my own test to see is this true. My test uses newer browser versions than Apple.[^1]

## Apple results.

<img src="{{site.url}}/images/apple-safari-test" alt="Chart. JetStream. Safari is 1.15x faster than Firefox and 1.07x faster than Chrome. Speedometer, Safari more than twice as fast as Firefox and 1.8x faster than Chrome. JSBench, Safari is 6 times faster than Firefox and Chrome altogether." width="50%"/>

## My results.

<img src="{{site.url}}/images/chart-speedometer" alt="Speedometer chart. Safari 166, Chrome 157, Safari Preview 175, Chrome Canary 162. Higher is better." width="50%"/>

<img src="{{site.url}}/images/chart-jetstream" alt="JetStream chart. Safari 91, Chrome 83, Safari Preview 102, Chrome Canary 94, iOS Safari 83 Higher is better." width="50%"/>

## Conclusions.

I can confirm, Safari is faster. I've tested the latest stable and preview versions. I've also tested iOS Safari which surprised me.

I was able to get 46 scores from mobile Safari on the Speedometer and 83 scores on the JetStream which is **the same as Chrome on Mac.** Amazing.  
As you probably know, Google Chrome on iOS uses Safari engine, so there's no reason to test it.

Safari is an excellent browser and it is undervalued, ignored because of huge Chrome popularity. I blame a lot of developers for using Chrome as their primary development browser, I know that Chrome forgives many errors and can swallow bad code. This leads to the issues in other browsers, people notice and tend to blame the browser. 

Safari team prioritise performance and efficiency, while Google has bigger amount of HTML 5 features. Not all of this features are good for users. Yes, they make development easier but they also introduce security risks and make websites more complex.

Read [this interesting article](https://blog.runspired.com/2016/03/25/the-chrome-distortion-chrome-alters-our-expectations-in-highly-negative-ways/) about how Chrome negatively affects web development.

Also during the test I accidentally closed Chrome, when I opened it again it displayed not my last page but the page I had before. I tried to do the same in Safari and everything was as I left. This means Safari has better state preservation.

## Specs.

I've used 2 JavaScript benchmarks on [browserbench.org](http://browserbench.org).

I've tested 5 browsers: Safari 9.1.2, Safari Technology Preview Release 11 (Safari 9.1.2, WebKit 11603.1.2), Google Chrome 52.0.2743.116 (64-bit), Google Chrome 54.0.2832.0 (64-bit) and finally iOS 9.3.4 Safari.

Test was performed on August 18, 2016 on my Mid 2014 Retina MacBook Pro 13` with 10.11.6, 2.6 GHz Intel Core i5, 8 GB RAM and on my iPad Air 2.
You can download <a href="{{site.url}}/downloads/browser-test-screenshots.zip" target="_blank">screenshots.</a>

[^1]:Apple tested Safari 9.0 and Chrome 44.