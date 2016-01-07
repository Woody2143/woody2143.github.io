---
layout: post
title: 'New Year, New Post'
date: '2016-01-06 21:22'
tags:
  - angularjs
  - javascript
  - testing
  - github
  - reading
  - electronics
  - audible
categories:
  - programming
---

So the holidays went by pretty fast and I kept busy enough without having to try to write blog posts. It's a habit I have to work on...

I wanted to note down a few things I've read or am meaning to read over the past month. Much of it is reference links as I work on testing an AngularJS app.

# Testing AngularJS:
- A good intro; wish I would have had it earlier
  - [Not testing your Angular code? Here's how to start](https://daveceddia.com/testing-angular-part-1-karma-setup/)
  - Video here: [https://vimeo.com/150441324](https://vimeo.com/150441324)
  - In the comments someone mentions ngDescribe. It cuts down on all the boilerplate needed to write tests in angular.
    - [Github Repo](https://github.com/kensho/ng-describe)
    - [How-To Use](https://glebbahmutov.com/blog/1-2-3-tested/)

- My real goal here would have been to have more information with each of these links, like, what I got out of them.
- Some sites I've used recently while working on writing tests for an angularjs app
  - [AngularJS Docs on testing](https://docs.angularjs.org/guide/unit-testing)
  - Found a nice site talking about testing, with a video, that went a bit more in to the different types of test, what to test and when.
    - What's not to like about a site called "Year of Moo"
    - [http://www.yearofmoo.com/2013/09/advanced-testing-and-debugging-in-angularjs.html](http://www.yearofmoo.com/2013/09/advanced-testing-and-debugging-in-angularjs.html)
  - Used this to help me get on my feet initially
    - [Introduction to Unit Test: Services](http://angular-tips.com/blog/2014/06/introduction-to-unit-test-services/)
  - Another overview of AngularJS Testing. I liked some of the way this was done and adopted some of the practices
    - [Unit Testing AngularJS Applications](http://bencentra.com/code/2015/11/16/unit-testing-angularjs.html?utm_campaign=NG-Newsletter&utm_medium=email&utm_source=NG-Newsletter_124)
  - Yet another overview I skimmed through...
    - [Unit testing Best Practices in AngularJS](http://andyshora.com/unit-testing-best-practices-angularjs.html)
  - Some material on using ngMock
    - [ngMock Fundamentals for AngularJS Unit Testing - Understanding Module](http://www.bradoncode.com/blog/2015/05/24/ngmock-fundamentals-angularjs-unit-testing/)
  - So it seems that if you locally install npm modules there is a bin path you should have setup so you can run commands from those modules. This gave me a bit of a headache till I found the below.
    - [How to use package installed locally in node_modules?](http://stackoverflow.com/questions/9679932/how-to-use-package-installed-locally-in-node-modules)
  - One of the many references I used while figuring out how to test http calls
    - [Using ngMock to simulate $http calls in service unit tests](http://stackoverflow.com/questions/15927919/using-ngmock-to-simulate-http-calls-in-service-unit-tests)
  - I have way too many modals that need tested...
    - [AngularJS UI Bootstrap mocking $modal in unit test](http://stackoverflow.com/questions/21214868/angularjs-ui-bootstrap-mocking-modal-in-unit-test)
  - Getting more idea of testing AngularJS Services
    - I think this gave me some clarification that I could do multiple beforeEach calls. I forget.
    - [Simple unit test for Angular service](http://stackoverflow.com/questions/27247427/simple-unit-test-for-angular-service)
  - Of course I'd eventually get around to pulling up the Jasmine site itself
    - [Jasmine Introduction](http://jasmine.github.io/2.4/introduction.html)
  - I was getting an error for awhile in my tests and found a related SO question
    - I was using a spy while doing an http.get or post call, I think
    - [Unknown provider: $routeParamsProvider](http://stackoverflow.com/questions/29947687/unknown-provider-routeparamsprovider)
    - [Unknown provider in angular unit test](http://stackoverflow.com/questions/26627468/unknown-provider-in-angular-unit-testing)
    - [http://jsfiddle.net/fdietz/2Ny8x/](http://jsfiddle.net/fdietz/2Ny8x/)
  - Learned to use the 'debugger' keyword
    - [How do you debug Jasmine tests with Resharper?](http://stackoverflow.com/questions/16222098/how-do-you-debug-jasmine-tests-with-resharper)

# Material Design
- Google has a design specification called 'Material Design'.
  - A package for Angular was put out that makes it easy to code your web page to that specification.
  - I've not had a chance to dive in too much; but it looks like a replacement for Bootstrap.
  - There is a nice writeup that talks aboue Material Design and Angular Materials here: [http://onehungrymind.com/reasons-to-love-angular-material/](http://onehungrymind.com/reasons-to-love-angular-material/)

# Things about Reading
- The Pomodoro Technique
  - I have this as an ebook and started in to it but recently found it on Audible and started to give it a listen while driving in to work.
  - The idea is that you break up your tasks in to ~25 minute chunks. The person who came up with it literally used a kitchen timer, set it, and focused on a task for that period of time and once done, took a break. Then sat back down and worked for another chunk of time.
  - That's the overly simplified mostly not correct version of what this book talks about. It has some interesting ideas and some data to back up those ideas.
  - A side note about listening, I heard it suggested that on books like this (ie not entertaining) play it back at ~1.5x speed. I have to say; that suggestion seems to be working for me as I usually find listening to those types of books very boring. More testing is required

- I was reading an article about Reading More and picked up one reading suggestion.
  - [5 principles that will help you read more - Business Insider](http://www.businessinsider.com/5-principles-that-will-help-you-read-more-2016-1)
  - There seemed to be some good suggestions in there. I'll have to try to make notes as I read to see how/if it really enhances things for me.
  - How does one do this with ebooks, just not quite the same...
  - Which lead me to pick a book or two from Amazon
    - 'How to Read A Book'
      - Picked up the soft copy as well as the audio version.
      - Also picked up 'How to Speak How to Listen' as suggested by Amazon.

- How to be a Programmer
  - Came across this essay that had been converted to markdown and put on github
  - [https://github.com/braydie/HowToBeAProgrammer](https://github.com/braydie/HowToBeAProgrammer)
  - Basically saving this to read over later.
  - The comments on reddit were a bit back and forth on the usefulness/validity of this info

- [Community and Career Reads in 2015](http://communituity.com/community-and-career-reads-in-2015/)
  - Just saw this link courtasy of Jono Bacon on FB
  - Looks like there is some potential reading material there, just haven't looked through all the way.

# Videos
- Suggested this playlist to a friend who is trying to get in to the world of VoIP
  - [Telephone Systems](https://www.youtube.com/playlist?list=PL08C86258934DD006)

- I like this guys training videos. I at least watch the intro one for AngularJS
  - [Level Up Tutorials](https://www.youtube.com/channel/UCyU5wkjgQYGRB0hIHMwm2Sg)

- At some point I'll come back to watch this as I tinker with electronics
  - [Engineering Tutorial: How To Use A Multimeter](http://www.shaungehring.com/software-blog//engineering-tutorial-how-to-use-a-multimeter)
