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

Just some incomplete notes from the December [Atlanta Perl Mongers](http://atlanta.pm.org) meeting. If anyone has any additions for this post they are welcome to submit a pull request to my [blog repo](http://github.com/Woody2143/woody2143.github.io).

# General pre-meeting discussion
- Roofers and Contractors suck for various reasons
- Central Git hosting solutions
  - Gitlab - [http://about.gitlab.com/features/](http://about.gitlab.com/features/)
  - Bitbucket
  - Confluance [http://www.atlassian.com/purchase/product/confluence](http://www.atlassian.com/purchase/product/confluence)

- Commitmas 2015 [http://github.com/commitmas/30-days-of-commitmas-2015](http://github.com/commitmas/30-days-of-commitmas-2015)

# My Pseudo talk: Github Pages & Jekyll (The Coders Blog software)
- [Github pages](http://pages.github.com)
  - Went over setting it up and options available
  - Forgot to cover creating a Github Page for a specific repo/project.
    - [Creating Project Pages](http://help.github.com/articles/creating-project-pages-manually/)
    - This is neat in my opinion; create an orphan branch and populate it with html and whatnot and it will just appear as `http://username.github.io/repository`.

- [Jekyll](http://jekyllrb.com/) - Blogging engine for coders
  - [Using Jekyll with Pages](http://help.github.com/articles/using-jekyll-with-pages/)
  - I meant to include the below link in my talk. It shows the Repository metadata you can access via your Github page within Jekyll
    - [Repository metadata on GitHub Pages](http://help.github.com/articles/repository-metadata-on-github-pages/)

  - Jekyll is pretty good on it's own, even if you don't want to use Github Pages.
  - [Stephen](http://stephen.cristol.googlepages.com/) asked if any other libraries are used in Jekyll.
    - No, it's very lightweight
    - [Stephen](http://stephen.cristol.googlepages.com/) went on to talk about Flexbox being interesting
      - [A Guide to Flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
      - And [CSS Tricks](http://css-tricks.com) is a great resource.

- There was some discussion about browsers and various feature support and the universal hatred of IE
  - Went over the testing I've been doing in javascript
    - A short overview of the output of karma and what it does
    - Showed some of the unit tests written in Jasmine
    - Showed the code coverage output of karma

      ![Karma Coverage](/assets/karma_coverage_screenshot_2015-12-03_21-45-38.png)

    - Some discussion around testing in general and last months talk and some of the positive effects that had.

  - Some talk about the small book, [Javascript: The Good Parts](http://shop.oreilly.com/product/9780596517748.do)

    ![The Good Parts](/assets/js_tgp.gif)

  - In expressing my frustration in javascript and testing some disparaging general remarks were made about various languages
  - This fit the conversation at the time:

    ![Consulting](/assets/consultingdemotivator_grande.jpeg)

# Scott asks a question about Perl training
- [Util](http://perlmonks.org/?node=Util) suggested looking at [http://learnxinyminutes.com/](http://learnxinyminutes.com/)
  - [Perl 6 Intro](http://perl6intro.com) is another resource (Scott liked that one better)

- There ended up being some talk around Perl 5, [Moose](http://metacpan.org/pod/Moose) and Perl 6

# [Util](http://perlmonks.org/?node=Util) Talks
- Used [Hunt the Wumpus](http://rosettacode.org/wiki/Hunt_The_Wumpus) code to go over a few features of Perl 6
  - [Stephen](http://stephen.cristol.googlepages.com/) had a question about constants in Perl 6, this went on for a bit.
  - I have to admit; I didn't capture as much of this as I should have.
  - Functional Programming: Variables don't and Constants aren't.
  - `prompt` function
  - `repeat {} until $condition` is fairly neat
  - [Util](http://perlmonks.org/?node=Util) said some wrong stuff. Corrections were made. Apologies were offered. We grew closer as a group.
  - Pick and Roll are not only functions, but they are fun to say.

# Misc
- MDW has a noisy phone.

# Post Meeting Meal
- A lengthy debate over display size and aspect ratio
- A shorter debate over MacBook memory upgrade-ability
- [Perl 6 Docs](http://docs.perl6.org) was another resource [Util](http://perlmonks.org/?node=Util) suggested checking out.
  - Greater content there in terms of Perl 5/Perl 6 code.

- Some discussion about the Christmas release of Perl 6
- Talked some about the [Atom](http://atom.io) editor and it's benefits
  - extensible, CLI install of plugins, etc

- If you don't teach your child fun military acronyms, who will? (Scott... Scott will teach them.)
  - ex.
    - WHISKEY TANGO FOXTROT
    - FUBAR
    - SNAFU
    - ASS HOT
    - TANGO UNIFORM

- [Stephen](http://stephen.cristol.googlepages.com/) asked Scott his opinion of [FreeNAS](http://www.freenas.org) vs [OpenFiler](http://www.openfiler.com)
  - Scott prefers FreeNAS as he's not a fan of the system OpenFiler is based on
    - And he has had better personal experiences with FreeNAS

- I suggested giving [Bootstrap](http://getbootstrap.com) a look, good framework for site layouts (least from a non-designer perspective)
- There was also some talk of the differences between [jQuery](http://jquery.com) and [AngularJS](http://angularjs.org)
- Elliot really did NOT like what he got for dinner, tasted good, but not worth the cost vs meat content.
- Cable cards are a lot easier to get now a-days than they used to be...
- It's beginning to feel a lot like winter.
