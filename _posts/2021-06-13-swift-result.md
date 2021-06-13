---
layout: post
title: "Swift Result"
date: 2021-06-13T12:54:40+0100
---

Swift Result is great but sometimes optional error does the job.

While working on [Caffeine++][1] 2.0, I have replaced most of my completion handlers with [`Result`][2]. I'm a fan of this language feature so I started to apply it everywhere. I have noticed that `Result` introducing an extra weight, and I like my code to be light. In many situations, like, getting HealthKit authorisation status, your result doesn't have a value to return, which is why you can use `Void`, this means you need to pass ugly `()` for success:

```swift
// Function declaration
func authorizeHealthKit(completion: @escaping (Result<Void, Error>) -> Void) {
    // Request authorisation and call completion block
    completion(.success(()))
}

// Usage example
healthManager.authorizeHealthKit { result in
    switch result {
    case .success:
        // Handle success
    case .failure(let error):
        // Handle error
    }
}
```

```swift
// Function declaration
func authorizeHealthKit(completion: @escaping (Error?) -> Void) {
    // Request authorisation and call completion block
    completion(nil)
}

// Usage example
healthManager.authorizeHealthKit { optionalError in
    if let error = optionalError {
        // Handle error
    } else {
        // Handle success
    }
}
```

In this case, I prefer `Error?`, but you decide what works for you.

[1]: https://cocoaswitch.com/caffeine++
[2]: https://developer.apple.com/documentation/swift/result
