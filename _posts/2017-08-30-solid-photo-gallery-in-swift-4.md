---
layout: post
title:  "SOLID Photo Gallery in Swift 4"
date:   2017-08-30T03:59+0000
---

Goal of this exercise is to improve my code design. I am hearing a lot about SOLID design principles and "uncle Bob", so I decided to understand its ideas. This exercise is my attempt to implement this ideas on practice in simple and modern Swift application. Although SOLID principles explained with C++ examples, its good Object Oriented Design principles can be applied to Swift.

As mentioned by Robert C. Martin before, this principles is only recommendations and is not a law. Sometimes it is better to violate this good design principles but only when necessary. I also have to mentions that this is only mine interpretation, I can be wrong. Please [write to me][1] if you have any feedback.

## Goal.
Applications accesses Flickr API and displays image gallery, displays meta data for each image.

To satisfy acceptance criteria we need to display collection of photos, be able to show all metadata for each photo and perform actions on each photo. I designed 3 screens and to implement them we will need following:
1. PhotosCollectionViewController
2. PhotoViewController
3. MetadataViewController

Let’s assume, later we will need to add sorting feature for the next version of application.

## Naive Design.
For getting photos from Flickr singe service class is created. This class sends data to `PhotosCollectionViewController.`

For the UI we use single Storyboard file.

## Good Model Design.
What makes design good or bad? How we can judge it? There’s 3 warnings signs in which we can evaluate design quality. This was described in [The Dependency Inversion Principle.][2]

1. Code that hard to change.
2. Every change breaks code in unexpected place.
3. Code can’t be reused.

In order to create reusable design we need to think what parts of application can be changed in the future and what kind of change we should be ready for.  We can improve naive design in many ways. Let’s focus on model design and UI design separately and start with model.

Lets say everything user can’t see is part of the model. First decision that I made is to write separate `NetworkService` protocol. Swift protocol itself can have only method definition, not implementation. I extended `NetworkService` and chose to use Apple `URLSession` to request data with status and optional error object. 

Let’s imagine this source code need to be used in another project which relies on third party Alamofire library. In this case, developer need to replace `NetworkService ` extension. If developer keeps same method definition, good news, `PhotosCollectionViewController` will not need to change. Job well done.

Another struct is required to specify request path, I called it `FlickrService.` It has endpoint path and data type parameter. I also created `FlickrDataModel` struct. In this struct I added method to parse data into Flickr model taking advantage of Swift 4 Standard Library with `JSONDecoder.` I chose to use nested Decodable Structs to mirror data model from an Flickr endpoint.

Unlike naive model, in this design I separated Flickr related logic and networking logic into separate abstractions. This enables easy code reuse, and also allows easier refactoring of one part of application without breaking other part.

`PhotosCollectionViewController` communicates with lower level networking module through higher level  `FlickrService` class which conforms to abstract `NetworkService` protocol and can perform request. I believe this is good example of The Dependency Inversion Principle. Higher level abstractions doesn’t depend on lower level implementation.

### The rest of application.
So far I spend most of my attention into `PhotosCollectionViewController.` There’s 2 other goals:

1. View controller  for displaying photo in full screen and performing some actions: sharing photo, opening original  Flickr web page.
2. Displaying metadata in full screen.

This can be done with 2 or 1 view controller. Whenever `Photo` metadata changes, this view controllers and UI would need to change as well. I chose to split metadata viewer and full screen photo view into 2 different view controllers. I created 2 Storyboard files and took advantage of Storyboard References. That’s better than using single Storyboard file, now engineers can work simultaneously. Storyboard itself allows us to separate view logic from business logic. This allows changes in UI design and layout without need to change view controller code.

I assume one can say that this design violates The Dependency Inversion Principle — changes in `Photo` object model, replacement it with another object, or adding new data source types, require changes in UI and controllers.  For this simple exercise I chose to keep UI static. We can’t be ready to every possible change and need to think carefully what areas of application can change. Because this is photo browsing app I keep core UI functionality together. I believe it is important to understand purpose of the application, in our case it is displaying photos with meta data. We should design our code to be ready for additional features and changes in implementation. In case when core purpose changes, it is better to start from scratch.

### Separating User Interface.
Okay version one is finished. I am satisfied with design. I would like to implement sort function in the future. It’s easy to do if just add UI controller and write all logic in the same view controller. But his will be naive design. What if I want to use sorting module in some other application?

The Dependency Inversion Principle states that UI should not be connected with business logic directly, UI should communicate through higher level abstractions. 

To fix this, we can create `SortOptions` struct which defines `SortType` enum and its order. It also contains text to be displayed in UI. We use `UISegmentedControl`, I consider it as low lever class which should know nothing about business logic. We extend this control with `SortControl`extension which would take `SortOptions` and would configure  `UISegmentedControl.` to display appropriate number of segments with appropriate labels. 

I included  `SortOptions` struct into `PhotosCollectionViewController` which is fine but I didn’t connect `UISegmentedControl` directly to`PhotosCollectionViewController` like it’s done in naive model. Instead, I created `SortViewController` and took advantage of Cocoa Touch Container View. This allows me to move `UISegmentedControl` into separate Storyboard file, meaning if UI changes, `PhotosCollectionViewController` will work the same, only `SortViewController` would require change. As long as our collection view conforms to `SortableCollection` protocol and communicates through `SortViewController`, design does not violates The Dependency Inversion Principle.

## Bibliography.
[SOLID (object-oriented design)][3]
[Principles Of OOD, Robert C. Martin (Uncle BOB)][4]
[Swift implementation for The Principles of OOD based on Uncle Bob articles.][5]

## Xcode project.
[Project is available in GitHub.][6]


[1]:	mailto:boris.yurkevich@gmail.com
[2]:	http://docs.google.com/a/cleancoder.com/viewer?a=v&pid=explorer&chrome=true&srcid=0BwhCYaYDn8EgMjdlMWIzNGUtZTQ0NC00ZjQ5LTkwYzQtZjRhMDRlNTQ3ZGMz&hl=en
[3]:	https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)
[4]:	http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod
[5]:	https://github.com/ochococo/OOD-Principles-In-Swift
[6]:	https://github.com/borisyurkevich/photos