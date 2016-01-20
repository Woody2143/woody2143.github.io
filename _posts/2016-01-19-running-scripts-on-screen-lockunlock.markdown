---
layout: post
title: "Running scripts on screen lock/unlock"
date: "2016-01-19 18:47"
tags:
  - linux
  - fedora
  - mate
  - automation
categories:
  - desktop
---

So I am working on automating a few things I do daily on my desktop. I have my Yubikey setup for login, which is nice. But I also wanted to run some scripts to enable/disable zoneminder when I lock/unlock my system.

My Google-Foo is either failing me or there just isn't much call to run scripts when a screen is locked/unlocked. After looking awhile I did find one [Stack Overflow question](http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock) that appears to have what I need.

So the bash script is below. Just need to change the 'echo SCREEN_LOCKED' with whatever scripts I want to run.

{% highlight sh %}
dbus-monitor --session "type='signal',interface='org.mate.ScreenSaver'" |
  while read x; do
    case "$x" in
      *"boolean true"*) echo SCREEN_LOCKED;;
      *"boolean false"*) echo SCREEN_UNLOCKED;;  
    esac
  done
{% endhighlight %}

Looks straight forward enough. I went ahead and just ran the 'dbus-monitor' command just to see what the output looks like, and it does seem to match up fine.

{% highlight sh %}
$ dbus-monitor --session "type='signal',interface='org.mate.ScreenSaver'"
signal sender=org.freedesktop.DBus -> dest=:1.127 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.127"

signal sender=:1.66 -> dest=(null destination) serial=14 path=/org/mate/ScreenSaver; interface=org.mate.ScreenSaver; member=ActiveChanged
   boolean true
signal sender=:1.66 -> dest=(null destination) serial=15 path=/org/mate/ScreenSaver; interface=org.mate.ScreenSaver; member=ActiveChanged
   boolean false
{% endhighlight %}

I also found this [StackOverflow question](http://unix.stackexchange.com/questions/212347/how-to-monitor-the-screen-lock-unlock-in-the-ubuntu-14-04) that has some python code included; basically based on the previous SO question/code.

{% highlight python %}
#!/usr/bin/env python
import gobject
import dbus
from dbus.mainloop.glib import DBusGMainLoop

def filter_cb(bus, message):
if message.get_member() != "EventEmitted":
    return
args = message.get_args_list()
if args[0] == "desktop-lock":
    print("Lock Screen")
elif args[0] == "desktop-unlock":
    print("Unlock Screen")

DBusGMainLoop(set_as_default=True)
bus = dbus.SessionBus()
bus.add_match_string("type='signal',interface='org.mate.ScreenSaver'")
bus.add_message_filter(filter_cb)
mainloop = gobject.MainLoop()
mainloop.run()
{% endhighlight %}

Course my first instinct is to rewrite it in to Perl. And there appears to be a module for it already, [Net::DBus](http://search.cpan.org/~danberr/Net-DBus-0.33.1/lib/Net/DBus.pm)

Looking around at that I found a module that does what I want already, [Event::ScreenSaver](https://metacpan.org/pod/Event::ScreenSaver)

[Code](http://cpansearch.perl.org/src/IVANWILLS/Event-ScreenSaver-v0.0.6/lib/Event/ScreenSaver/Unix.pm) that caught my eye initially. Uses  [Net::DBus::Reactor](http://search.cpan.org/~danberr/Net-DBus-0.33.5/lib/Net/DBus/Reactor.pm).

[Event::ScreenSaver](https://metacpan.org/pod/Event::ScreenSaver) comes with a nice example program 'player-pause' that pauses/unpauses music when the screen is locked/unlocked.

Otherwise my script is pretty straight forward, this is just a test run to see it work.

{% highlight perl %}
#!/usr/bin/env perl

use strict;
use warnings;
use utf8;
use Event::ScreenSaver;

my $ss = Event::ScreenSaver->new(
    start => sub {print "ScreenSaver started!\n" },
    stop  => sub {print "ScreenSaver stopped!\n" },
)->run;
{% endhighlight %}

Cause of course nothing goes to plan right away.

{% highlight sh %}
$ ./bin/dbus-monitor-screensaver.pl
org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files
{% endhighlight %}

Ok, so the Perl module needs an update. Lucky for me it's on GitHub [https://github.com/ivanwills/Event-ScreenSaver](https://github.com/ivanwills/Event-ScreenSaver).

I've gone ahead and forked it, [https://github.com/Woody2143/Event-ScreenSaver](https://github.com/Woody2143/Event-ScreenSaver). I'll get around to a pull request sometime.

So the original code in file "lib/site_perl/5.22.0/Event/ScreenSaver/Unix.pm" is this:
{% highlight perl %}
    my $screensaver = $bus->get_service("org.gnome.ScreenSaver");

    my $screensaver_object = $screensaver->get_object("/org/gnome/ScreenSaver", "org.gnome.ScreenSaver");
{% endhighlight %}

And I changed it to this:
{% highlight perl %}
    my $screensaver = $bus->get_service("org.mate.ScreenSaver");

    my $screensaver_object = $screensaver->get_object("/org/mate/ScreenSaver", "org.mate.ScreenSaver");
{% endhighlight %}

I gave my simple script a test run and locked the screen. It worked, but the script immediately exited.
{% highlight sh %}
~$ bin/dbus-monitor-screensaver.pl
ScreenSaver started!
~$
{% endhighlight %}

I'll have to dig in to why that happened....
