---
layout: post_simple
title:  "StockML Dev Notes #3 - Building the MVP"
date:   2017-10-06
published: true
comments: true
author: Cong Wang

type: "Article"

tags:
- Stock
- Trading

---

The skeleton of StockML exists now! After much procrastination, the actual effort it took to build a minimally viable version for myself turned out to much less than I thought. So many more ideas came out as a result of building the MVP, and I only wish that I had done it sooner, can't wait to make my first trade reading off this app.

**Goal of the MVP**

The original motive for the MVP was simple, I use StockChart.com and love it, but I needed my pet peeves.
* wanted to see all my indicators on one screen without scrolling, and it didn't use the width of my screen
  * almost bought a portrait monitor to deal with this
* wanted to quickly or simultaneously glance at the weekly and daily charts, had to open two windows and they don't sync
* wanted to navigate between stocks that I was interested in easier
* wanted a playground to present indicators that optimized the way I view them

**Stripping out all the fluff**

Looking back, I believe a lot of the excuses I used to procrastinate was wanting the app to be more full-featured. This was literally against the very concept of a MVP and I knew it well, but it's just so convenient to fall for that. Eventually I came around to it and stopped worrying about the "fluff," partly driven by my own disappointment at making no progress. A big piece of fluff was:

* user concept that allowed login and different people to use the app which ...
  * required Questrade access tokens and watch lists to be persisted with user instances which ...
    * required authentication to know which profile to send to frontend which ...
      * required the app to be more complicated to deal with sessions and web tokens

Essentially a lot of things you'd expect on literally **any** app, which is the point. It doesn't define what the app does at all. Another was having a well designed API to interface with my frontend app.

> Really, seriously, you should give *zero* fucks about what your API looks like in a MVP. Make it up as you go.

Oh I also skipped databases altogether to persist results, motto was to compute everything on the fly and learn what make sense to persist as I go. The few things I had to persist I used ... files. Yes I know that's ugly.

**Questrade and TA-Lib**

Ended up picking Python for the backend, mainly because TA-lib has a really neat Python wrapper, and I learned the lesson about trying to reinvent the wheel last time around. Questrade because that's the platform I trade on myself, which I did pick out initially because they had a nice API.

The access token refresh and expiry (along with specified server a token is allocated to access) was a pain in the ass, but was somewhat expected for a finance product API to prevent abuse and keep performance high. I wrote a cool snippet that auto-freshed and retried any queries in my app if the access token expired, was pretty proud.

Results, ta-da!

<img src="/img/blog/stockml-dev-notes-stockml_oct_06.png" width="80%"/>

**Thoughts and next steps**

At this stage I think I've made some progress to tick off some boxes I wanted in my goals, plenty of improvements to be done. A few main ones include:

* deploy this on AWS behind some trivial Nginx authentication to let others try
* the candle pattern recognition picks up way too many hits, need to make it more usable. Thinking about combining that into one custom indicator for myself. Again by treating myself as the user, looking at how I end up digesting this information
