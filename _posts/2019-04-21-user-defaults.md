---
layout: post
title:  "UserDefaults In Practice"
date:  2019-04-21T10:28+0000
external-url: http://dscoder.com/defaults.html
---

My favourite `UserDefaults`[^2] use-case is preserving User Interface states, one of the essential items on the list of every *good* Mac and iOS application.

`UserDefaults` is one of the most powerful examples of why I love writing programs for Apple hardware. It is easy to get started, performant, and got even simpler[^3] over time. Just two three lines of code and you wrote something to permanent storage. Which you can read at any time, so efficient, adding your caching code would even hurt performance[^1].

David Smith wrote [an excellent guide][3] to `UserDefaults` for [DS Coder.][1] I have learned something new from the article:

> Having an alternate code path for "no value set" is also generally unnecessary, as you can provide a default value instead.

Thank you, David, for this excellent guide.

[^1]: `UserDefaults` optimised for reading.
[^2]: Omitting `NS` prefix, it doesn't exist in Swift.
[^3]: There's no need to call [`synchronize()`][2] method anymore.

[1]: http://dscoder.com
[2]: https://developer.apple.com/documentation/foundation/userdefaults/1414005-synchronize
[3]: http://dscoder.com/defaults.html