---
title: OHLC Charts in R | Examples | Plotly
name: OHLC Charts
permalink: r/ohlc-charts/
description: How to create OHLC charts in R.
layout: base
thumbnail: thumbnail/ohlc.jpg
language: r
page_type: example_index
has_thumbnail: true
display_as: financial
order: 1
output:
  html_document:
    keep_md: true
---



### New to Plotly?

Plotly's R library is free and open source!<br>
[Get started](https://plot.ly/r/getting-started/) by downloading the client and [reading the primer](https://plot.ly/r/getting-started/).<br>
You can set up Plotly to work in [online](https://plot.ly/r/getting-started/#hosting-graphs-in-your-online-plotly-account) or [offline](https://plot.ly/r/offline/) mode.<br>
We also have a quick-reference [cheatsheet](https://images.plot.ly/plotly-documentation/images/r_cheat_sheet.pdf) (new!) to help you get started!

### Version Check

Version 4 of Plotly's R package is now [available](https://plot.ly/r/getting-started/#installation)!<br>
Check out [this post](http://moderndata.plot.ly/upgrading-to-plotly-4-0-and-above/) for more information on breaking changes and new features available in this version.

```r
library(plotly)
packageVersion('plotly')
```

```
## [1] '4.5.6.9000'
```

### Basic OHLC Chart


```r
library(plotly)
library(quantmod)

getSymbols("AAPL",src='yahoo')

df <- data.frame(Date=index(AAPL),coredata(AAPL))
df <- tail(df, 30) 

p <- df %>%
  plot_ly(x = ~Date, type="ohlc", 
          open = ~AAPL.Open, close = ~AAPL.Close, 
          high = ~AAPL.High, low = ~AAPL.Low) %>%
  layout(title = "Basic OHLC Chart")

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = plotly_POST(p, filename="finance/ohlc-basic")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/4299.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

#Reference

See [https://plot.ly/r/reference/#ohlc](https://plot.ly/r/reference/#ohlc) for more information and chart attribute options!