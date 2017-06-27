---
layout: post_simple
title:  "StockML Dev Notes #1"
date:   2017-06-10
published: true
comments: true
author: Cong Wang

type: "Article"

tags:
- Stock
- Trading

---

A little while ago I decided to take a more serious look at algorithmic trading. I had little to no trading experience or training, but I thought to myself that if I am to make it in trading, it would have to be leveraging my strength. So I dwelled myself in technical analysis immediately, only skimming theories on fundamental analysis.

Here's what happens when you understand so little of a subject that you think it's simple, you make elementary mistakes about skipping to the endgame immediately. Instead of trying to just trade algorithmically, or _just trade_, I wanted to tackle the pinnacle of algorithmic trading. To me, those were:
* HFT, leveraging algorithms to outpace other players
* ML, finding the optimal weight of technical indicators, and adapt faster than market

**Mistake: trying to tackle HFT (high-frequency trading)**

I think the true mistake here is trying to do high-frequency _trading_ without knowing how to trade yet, but in pursuing HFT I decided to start writing things in Rust. It's very seductive to do a side project in a language like Rust, and I fell for it. It had compounded impact on trying to do anything towards the project, since a lot of times I had to write the tools myself.

Seriously, what's the point to think about scaling at this stage.
* Where's the vertical slice that confirms a trade can be performed?
* Where's the data source? Getting it at < 10ms intervals, really?

**Mistake: trying to jump right in and "just apply machine learning"**

On paper is sounds good right? Get some daily data for 10-20 years, use [TA-Lib](http://ta-lib.org/function.html) to compute indicators, shove them all in [Tensorflow](https://www.tensorflow.org/) and call it a day. I can picture generating heuristics and back-testing them already, although I haven't quite figured out how back-testing is done yet.

Honestly it's still tempting today.

My mistakes were more trivial though, since I had to build TA libraries for Rust to even start. And I got to deal with all these nice things:
* Floating point storage in database
* Butterfly effect on computed indicators
* Caching what values to computer different indicators
* Separating indicators and cached values to faster fetch
* If the math were correct
* ...

Basically I got way ahead of myself. The good thing is I had to read up so much on technical indicators and the math behinds them.
