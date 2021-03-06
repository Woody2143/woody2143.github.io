---
layout: post
title: Github Page Notes
date: 2015-12-03T15:22:31.000Z
categories: github
---

Still trying to sort out using jekyll to manage this page.

Updated 2016-02-18.

# Initial Notes:
- Some of the same markdown that can be used in README.md in my repos doesn't render the same on these pages
- Need to add a hook to prebuild before commiting to catch build errors
- May point 2143.net at this page since it currently isn't doing anything but hosting my email
- Took the time to add my linkedIn and Google Plus contact info in the footer
  - Never messed with svg icons like that before. Had to copy them from [http://codepen.io/adamaoc/pen/hoKBq?editors=110](http://codepen.io/adamaoc/pen/hoKBq?editors=110)
  - Also had to mess with sass for the first time to get the column width adjusted in the footer.

- I'm not totally sold on the site title yet, but we'll see.

# Update 2015-12-07
- Found this page that gives some good ideas for adding things to a Github page.
  - [http://jmcglone.com/guides/github-pages/](http://jmcglone.com/guides/github-pages/)

# Update 2016-02-18
- Github posted on Feb 1st some changes being made in support of Jekyll 3.0
  - [https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0](https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0)
  - It will only support [kramdown](http://kramdown.gettalong.org/) markdown engine
  - It will only support [Rouge](https://github.com/jneen/rouge) syntax highlighting
    - no more \{ % highlight % \} tags
  - Other things here that I really don't care about...
  - Changes take place May 1st, 2016
