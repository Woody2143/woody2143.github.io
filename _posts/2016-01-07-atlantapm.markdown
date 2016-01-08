---
layout: post
title: "Atlanta.pm - January 2016"
date: "2016-01-07 19:23"
tags: 
  - perl
categories: 
  - atlanta.pm
published: true
---




Notes from the January Atlanta Perl Mongers meeting.

# Pre-Pre-meeting Discussion.
- Companies dealing in blood, suck.
- Karma HotSpot
  - Scott was talking about this pay-as-you-go hotspot, may be worth a look.
  - [Karma](https://yourkarma.com/how-it-works)

- New Postgres release (9.5)
  - Fun new feature; Up-Sert
    - Inserts or Updates
    - mySQL has had it for awhile: [Insert on duplicate](https://dev.mysql.com/doc/refman/5.7/en/insert-on-duplicate.html)

- [Dreamhost](https://www.dreamhost.com/) has some pretty good pricing right now.

# Pre-meeting discussion
- [cut out discussion of politics]
- Scott admitted doing something stupid.
  - relating to programming in perl 5 vs perl 6

- The tax on people who can't do math is up to $675mil
- [Simply Noise](https://simplynoise.com/)
  - For when you want to cut down background noise or just be a smartass at a meeting.

- I needed to send a link to Scott and asked him for his preferred method, he pointed out Slack
  - [Slack](https://slack.com)

- Yubikey - hardware 2-factor authentication
  - Was showing mine to the group.
  - [Yubikey](https://www.yubico.com/products/yubikey-hardware/)

# Stephen's talk - Keeping internet wolves at bay
- I ruined his punchline slide.
- Free SSL Certs @ [Let's Encrypt](https://letsencrypt.org/)
  - short life span on certs; gets renewed through client on server

- "How likely is it someone is going to get my cookies"
  - Ask this guy
  - ![Cookie Monster](/assets/Cookie_monster.jpg)

- Some discussion around how some slides are more blank than others
- [Pi Hole](http://pi-hole.net/) is a great name
- [HTTPS Everywhere](https://www.eff.org/https-everywhere) is a handy plugin
- Stephen needs to use github.io instead of ~~geocities~~ Google Pages...
  - [stephen.cristol.googlepages.com](https://stephen.cristol.googlepages.com)
  - It seems that everyone loves GeoCities

- The media may or may not lie.

# Post talk discussion
- Last year was 'Christmas'! - Stephen
  - Last year was 2015 - Util
  - Basically asking what happened with the Christmas release.
  - I taught everyone that [Lego Advent calendars are a thing](http://www.target.com/p/lego-city-advent-calendar-60099/-/A-21505862)
  - [Perl 5 Advent Calendar](http://www.perladvent.org/2015/)
  - Util sums up what was put out this holiday
    - Good post on the [Perl 6 Advent Calendar](https://perl6advent.wordpress.com/) site

- Util got [Thing Explainer](http://amzn.com/0544668251) for Christmas.
  - Good, fun read.

- The [The Mathematics Calendar 2016](http://amzn.com/1884550754) is on Amazon.
- [True Caller](https://www.truecaller.com/) handy when you get phone calls in the middle of your own presentation.

# Util talks about a thing.
- Out of general interest Util looked at [AP CS Course](https://secure-media.collegeboard.org/digitalServices/pdf/ap/ap-computer-science-a-course-description.pdf)
  - Language used in the course: Java
  - He copied down the code using the One True Brace System
  - Took code example from PDF (page 29) and rewrote in to Perl 6
    - I mainly copied the code down to see how the code block looked on the page.
    - I can't type fast enough to show all the code he had done.

```Perl6
my Int @numbers;
# Precondition: numbers contains int values in no particular order.
sub mystery ( Int $num --> Int ) {
  for @numbers.keys.reverse -> $k {
    return $k if @numbers[k] < $num;
  }
  return -1;
}
```
- Util will post his code online at some point

- Scott asked how you can find all the Perl6 keywords; ex .value .key etc
  - Read [the docs](docs.perl6.org)
  - and/or run

  ```
  p6g -e 'my $a = 42; .say for sort $a.^methods>>.name'
  ```
  
# Around the dinner table
- [Magnetic Notebook](http://imgur.com/gallery/psjYb)
- Util was initially mistaken for a woman by the server. :)
  - In her defence he has long hair, and she saw him from behind initially
- Further discussion of Stephens talk
  - who runs their own DNS servers
    - I've used [Dyn Internet Guide](http://dyn.com/labs/dyn-internet-guide/) from time to time.
- During his talk Util had mentioned he was unable to copy the code from the PDF he was referencing.
  - Scott said that [PDFPen Pro](https://smilesoftware.com/pdfpenpro) is a tool he's used before to work around that type of problem
    - Mac only
    - $$
- Some talk about how he manages browswers with many (many) open tabs
  - Util wrote a script to dump page titles and urls to a text file
  - Stephen suggested a the 'Session Manager' plugin
    - Chrome [link](https://chrome.google.com/webstore/detail/session-manager/bbcnbpafconjjigibnhbfmmgdbbkcjfi?hl=en)
    - Firefox [link](https://addons.mozilla.org/en-US/firefox/addon/session-manager/)
  - I am trying to write up posts with the links and what I got out of them; but that's a fairly lofty goal.
  - I also save off information to [Evernote](https://evernote.com/)
- Fesability of putting ChromeOS on an older laptop
  - Scott said it should work fine; may want to put in an SSD though
  - [Quick Start Guide](https://www.chromium.org/chromium-os/quick-start-guide)
- [Penrose Tiling](https://en.wikipedia.org/wiki/Penrose_tiling)
- [Gold Dust Woman by Karen Elson](http://shz.am/t62691974) was remarked on as it played in the restraunt
- I asked if anyone had read [The Player of Games](http://amzn.com/0316005401) or read anything from the [Culture](http://www.amazon.com/Iain-M.-Banks/e/B000APXAVG/) series.
  - I heard read about it online, both Zuckerberg and Musk endorsed it as a must-read.
  - I finished it over the holiday
  - Util is a third of the way in
  - Enjoyed it; surprised it was from 1988
  - I would like to read more about why Zuckerberg/Musk endorsed it