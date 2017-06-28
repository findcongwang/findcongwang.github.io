---
layout: post_simple
title:  "StockML Dev Notes #2 - Learning The Ropes"
date:   2017-06-28
published: true
comments: true
author: Cong Wang

type: "Article"

tags:
- Stock
- Trading

---

A technical trader uses charts and indicators to interpret market movements, assuming that the price of the underlying security "prices-in" news items. Thus it was natural to learn the ropes and get familiar with the tools I'll be using for trading.

I found this really nice resource called [Chart School](http://stockcharts.com/school/doku.php?id=chart_school), courtesy of StockChart.com. Decided to just jump in and read all of the overview, indicators, and overlays articles, getting a board picture without going too deeply.

In my reading exercises, I found many systems of trading and interpretations of the same technical indicators. Mostly importantly, the article on [Multicollinearity](http://stockcharts.com/school/doku.php?id=chart_school:trading_strategies:multicollinearity) which advises on how to build your own trading system using indicators.

**ADX, PPO, BB, CMF, STO ...**

The multicollinearity article discuss about three dimensions in which indicators fall under.
* Momentum
* Trend
* Volume

So one should be careful about using the same information multiple times as support toward a market analysis. For example, when Full Stochastics (STO) and Relative Strength Index (RSI) both suggest that a stock is oversold. Similarly, Percentage Price Oscillator (PPO) and Moving Average Convergence Divergence (MACD) show the same information but normalized differently.

**Putting a few indicators together**

After some reading I put together a charting setup that helps me analyze securities. Featuring:
* STO, Full Stochastics (14, 3, 3)
* MA, Simple Moving Averages (14, 50)
* BB, Bollinger Bands (20, 2)
* VBP, Volume By Price
* PPO, Percentage Price Oscillator (12, 26, 9)
* ADX, Average Directional Index (14)
* CMF, Chaikin Money Flow (20)
* PVO, Percentage Volume Oscillator (12, 26, 9)

<img src="/img/blog/stockml-dev-notes-hcg_daily.png" width="80%"/>

The initial thoughts behind putting using these indicators are:

* Using BB and MAs to get a sense of the security (trend)
* Using VBP to help identify support and resistance zones
* Using PVO to help support price movements (volume)
* Using STO and CMF to assess buying and selling pressures
* Using ADX and PPO to help support reversal signals
