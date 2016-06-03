---
layout: post
title: "Atlanta.pm - June 2016"
date: '2016-06-02 19:33'
tags:
  - perl
categories:
  - atlanta.pm
published: true
---

Here are the notes from the June meeting of the Atlanta Perl Mongers. I make no claims as to completion or accuracy. Updates welcome.

# Pre-Meeting
- I was talking about a CRUD-ish website I've had to fix.
- Scott is here!
- The police can use your fingerprints to unlock your phone without a warrant.
- pathogen - vim package manager

# DB Change Tracking
Basically the classic problem of how to track changes to a database.
- I went over my 'home grown' solution
  - 'ChangeLog' table in database
    - as SQL files are run their filenames are added to the 'ChangeLog' table.
    - SQL files have one or more command
    - script checks to see if file has already been run or not
  - MDW does something similar but they use date/times for in their filenames
  - The group helped me make some improvements to my script.
  - I'll put up the files to github at some point.

- Scott and Eye mentioned: activerecord / rake
  - Go from version to version of the database
  - [DBIx::ActiveRecord](http://search.cpan.org/~tsaito/DBIx-ActiveRecord-0.01/lib/DBIx/ActiveRecord.pm)

- MDW mentioned [squitch](http://sqitch.org/) - a Perl solution

# Git Discussion
- [git workflow](http://nvie.com/posts/a-successful-git-branching-model/) a guide for branching

# Ansible/Puppet Discussion
- I totally missed what was said here. Sorry

# Apache / Nginx
- Some have dumped Apache for Nginx due to speed issues
- [Nginx](https://www.nginx.com/resources/wiki/) doesn't handle CGI; but great as a proxy

# Round Table - Cool Perl Tricks
- Eye
  - Have a module, 'use testing;' that when used causes any following modules 'used' to be pulled from the DEV path.
  - uses the users-id to determine which path to look for modules; can be overwritten

- MDW
  - [RapidApp](https://metacpan.org/pod/RapidApp)
    - A way to quickly get a CRUD site up

- Yehuda
  - When you do a single capture in Perl (regex); instead of $1 or \1 if you can use the below $vars
  - $& is the match ($1)
  - $\" gives you everything after the match
  - $\` gives you before the match
  - if you do this once in code every regex will support it
  - Seen in 'Perl One Liners'

- Scott
  - Is unabale to contribute.

- Eye
  - If you use environment variable PERL5OPT is sets commandline switches for every perl command run
  - [PerlRun](http://perldoc.perl.org/perlrun.html)

- Woody
  - Along the lines of RapidApp; just not exitPerl specific
  - Bitnami [Dreamfactory](https://bitnami.com/stack/dreamfactory)
    - Can interface to database and produce a RESTful interface right away
    - Has free/nonfree parts
    - I've played around with it some; seems neat

- MS forcing Windows 10 upgrade sucks.

- Eye
  - [JSFiddle](https://jsfiddle.net) is handy

- Scott
  - Anyone using [Gitlab](https://about.gitlab.com/)?
  - Github like but can be self-hosted.


# Dinner Chat
- MDW sold at least one laptop for Lenovo; I'm considering one as well.
  - [Lenovo Thinkpad Yoga 11e](http://amzn.com/B01B16MXLU) $310
  - Get the [memory upgrade](http://amzn.com/B006YG8X9Y) too, $23.
- Talked about the virtues of Postgresql
  - It has native replication as of last Christmas
- Talked about git; multiple master repos/mirrors.
  - I need to look up info on git mirror push...
- There was some continued discussion around systems like Puppet.
