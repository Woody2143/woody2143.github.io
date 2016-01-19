---
published: true
layout: post
title: Fedora 22 DNF Group Error
date: "2016-01-18 22:00"
tags: 
  - linux
  - fedora
  - dnf
  - group
  - troubleshooting
categories: 
  - desktop
---


So I ran in to a fun error on a new-ish Fedora 22 install the other week...

After a recent office move (~4 months ago) I installed Fedora 22 on my work machine. It was running the latest Gnome, and I gave it a shot for awhile, but I just can't get behind that new interface. So after the holiday I sat down to install Mate as I was already using that on my laptop and liked it just fine. That is when I ran in to trouble.

I went to use the group install command but got the following error:
```
$ dnf groups
Last metadata expiration check performed 2:11:39 ago on Tue Jan 19 06:51:53 2016.
Traceback (most recent call last):
  File "/usr/bin/dnf", line 58, in <module>
    main.user_main(sys.argv[1:], exit_code=True)
  File "/usr/lib/python2.7/site-packages/dnf/cli/main.py", line 174, in user_main
    errcode = main(args)
  File "/usr/lib/python2.7/site-packages/dnf/cli/main.py", line 60, in main
    return _main(base, args)
  File "/usr/lib/python2.7/site-packages/dnf/cli/main.py", line 112, in _main
    cli.run()
  File "/usr/lib/python2.7/site-packages/dnf/cli/cli.py", line 1095, in run
    return self.command.run(self.base.extcmds)
  File "/usr/lib/python2.7/site-packages/dnf/cli/commands/group.py", line 373, in run
    self._grp_setup()
  File "/usr/lib/python2.7/site-packages/dnf/cli/commands/group.py", line 137, in _grp_setup
    comps = self.base.read_comps()
  File "/usr/lib/python2.7/site-packages/dnf/base.py", line 418, in read_comps
    self._group_persistor = self._activate_group_persistor()
  File "/usr/lib/python2.7/site-packages/dnf/base.py", line 384, in _activate_group_persistor
    return dnf.persistor.GroupPersistor(self.conf.persistdir, self._comps)
  File "/usr/lib/python2.7/site-packages/dnf/persistor.py", line 262, in __init__
    self._load()
  File "/usr/lib/python2.7/site-packages/dnf/persistor.py", line 322, in _load
    self.db = ClonableDict.wrap_dict(json.loads(content))
  File "/usr/lib64/python2.7/json/__init__.py", line 338, in loads
    return _default_decoder.decode(s)
  File "/usr/lib64/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib64/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded
```

I proceeded to scrach my head and google the error **ValueError: No JSON object could be decoded** along with various combinations of **fedora**, **dnf**, **groups**, etc...

Sadly that is just a generic python/json error and nothing useful was coming up. I went about several other searches in different ways with no luck. So I started to investigate out the various scripts called out in the traceback above. Finally I got to **/usr/lib/python2.7/site-packages/dnf/persistor.py** and found the following json file mentioned **groups.json**. 
```
    def __init__(self, persistdir, comps=None):
        self._commit = False
        self._comps = comps
        self._dbfile = os.path.join(persistdir, 'groups.json')
        self.db = None
        self._original = None
        self._load()
        self._ensure_sanity()
```
I then searched for that file on my laptop and found it under **/var/lib/dnf**. Comparing the files on the desktop and laptop I found that the desktop one was empty while the laptop had several things listed. So I copied the contents of the file over and reran the groups command
```
$ dnf groups
Last metadata expiration check performed 2:20:57 ago on Tue Jan 19 06:51:53 2016.
Installed Groups: 2
Available Groups: 33
```
Wahoo!

So after that I was able to get Mate installed and running fine. Desktop bliss...

Hopefully this gets indexed and helps someone else out down the line...
