---
layout: post
title: "Auto Layout Scroll View with footer."
date: 2017-11-01T12:01+0000
---

![iOS simulator screenshot with blue content area and yellow footer][image-1]

The goal of this Auto Layout exercise is to build scroll view with dynamic content height and footer. There's 2 challenges here.

1. Sticking footer to the bottom even when there's very little content.
2. Allowing scroll view to scroll even though content height is unknown.

First, read ["iOS: How To Make AutoLayout Work On A ScrollView" from Natasha][1] as it's very practical and saved me many hours.

The fastest and easiest way to get started is Storyboard and Interface Builder.  [Download sample project from GitHub.][2]

1. Add Scroll View to your root view and add pin it with 4 constraints. Your root view should have only 1 child which is the scroll view. 
2. Create new "container" view and add it to the scroll view. Scroll view can have only one child view. This was mentioned by Natasha and I always follow this rule since, I lost many hours when I didn’t know about this.
3. Add constraint for container view width to be equal with root view width.
4. Add footer view and pin it to the bottom.
5. Scroll view can't function when content height is unknown. Add height constraint outlet. In this example for my content I have single label, I don't set container view height because it will change depending on label height. I pinned label to its superview. Make sure your Storyboard file doesn't have error messages and layout conflicts resolved.

![Interface Builder with footer sticking to the top][image-2]

At this point you should get something like this in your Interface Builder. We still have some work to do. Open view controller and add following code.

{% highlight swift %}
labelHeightConstraint.constant = view.bounds.height - footerView.bounds.height
{% endhighlight %}

So far I have no content and we had to increase label heigh so footer sticks to the bottom as design required. If I set text for the label it will truncate which I don't want. I had to disable this constraint and allow scrolling.

{% highlight swift %}
labelHeightConstraint.isActive = false
{% endhighlight %}

![2 screens with text taking all the space.][image-3]


## iPhone X

I though I'm done but when I run the code I realised it's very broken on new iPhone X. Here's code snippet that helped me.

{% highlight swift %}
override func viewDidAppear(_ animated: Bool) {
	super.viewDidAppear(animated)
	
	labelHeightConstraint.constant = (view.frame.height - view.safeAreaInsets.top) - footerView.bounds.height
}
{% endhighlight %}

The key is `viewDidAppear` because safe area insets equal to zero in `viewDidLoad.` I also had to disable landscape layout. 

I noticed that iPhone X screen is very tall so all my text was visible and footer was in the middle of the screen, I had to activate constraint again. Only disable height constraint when you have many pages of content, iPhone X can fit surprising amount of information.

![iPhone X screenshot][image-4]

[1]:	https://www.natashatherobot.com/ios-autolayout-scrollview/
[2]:    https://github.com/borisyurkevich/Scroll-View-with-Footer

[image-1]:	{{ site.url }}/images/scroll-view.png
[image-2]:  {{ site.url }}/images/height-constraint.png
[image-3]:  {{ site.url }}/images/scrollable-content.png
[image-4]:  {{ site.url }}/images/iPhone-X-layout.png
