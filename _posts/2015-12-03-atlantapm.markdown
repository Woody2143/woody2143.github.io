---
layout: post
title: Atlanta.pm - December 2015
date: '2015-12-03 21:00'
tags:
  - perl
  - javascript
  - testing
  - github
  - jekyll
categories:
  - atlanta.pm
---

Just some incomplete notes from the December Atlanta Perl Mongers meeting. If anyone has any additions for this post they are welcome to submit a pull request to my [blog repo](https://github.com/Woody2143/woody2143.github.io).

# General
- Roofers and Contractors suck for various reasons
- Central Git hosting solutions
  - Gitlab - [https://about.gitlab.com/features/](https://about.gitlab.com/features/)
  - Bitbucket
  - Confluance [https://www.atlassian.com/purchase/product/confluence](https://www.atlassian.com/purchase/product/confluence)

- Commitmas 2015 [https://github.com/commitmas/30-days-of-commitmas-2015](https://github.com/commitmas/30-days-of-commitmas-2015)

# I ramble on for a Bit
- [Github pages](http://pages.github.com)
  - Went over setting it up and options available
  - Forgot to cover creating a Github Page for a specific repo/project.
    - [Creating Project Pages](https://help.github.com/articles/creating-project-pages-manually/)
    - This is neat in my opinion; create an orphan branch and populate it with html and whatnot and it will just appear as `http://username.github.io/repository`.

- [Jekyll](http://jekyllrb.com/) - Blogging engine for coders
  - [Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)
  - Jekyll is pretty good on it's own, even if you don't want to use Github Pages.
  - Steven asked if any other libraries are used in Jekyll.
    - No, it's very lightweight
    - Steven went on to talk about Flexbox being interesting
      - [A Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
      - And [CSS Tricks](https://css-tricks.com) is a great resource.

- There was some discussion about browsers and various feature support and the universal hatred of IE
  - Went over the testing I've been doing in javascript
    - A short overview of the output of karma and what it does
    - Showed some of the unit tests written in Jasmine
    - Showed the code coverage output of karma

      ![Karma Coverage](/assets/karma_coverage_screenshot_2015-12-03_21-45-38.png)

    - Some discussion around testing in general and last months talk and some of the positive affects that had.

  - Some talk about the small book, [Javascript: The Good Parts](http://shop.oreilly.com/product/9780596517748.do)

    ![The Good Parts](/assets/js_tgp.gif)

  - In expressing my frustration in javascript and testing some disparaging general remarks were made about various languages
  - This fit the conversation at the time:

    ![Consulting](/assets/consultingdemotivator_grande.jpeg)

# Scott asks a question about Perl training
- Util suggested looking at [http://learnxinyminutes.com/](http://learnxinyminutes.com/)
- There ended up being some talk around Perl 5, [Moose](https://metacpan.org/pod/Moose) and Perl 6

# Util Talks
- Used [Hunt the Wumpus](http://rosettacode.org/wiki/Hunt_The_Wumpus) code to go over a few features of Perl 6
  - Steven had a question about constants in Perl 6, this went on for a bit.
  - I have to admit; I didn't capture as much of this as I should have.
  - Functional Programming: Variables don't and Constants aren't.
  - `prompt` function
  - `repeat {} until $condition` is fairly neat
  - Util said some wrong stuff. Corrections were made. Apologies were offered. We grew closer as a group.
  - Pick and Roll

# Misc
- MDW has a noisy phone.
