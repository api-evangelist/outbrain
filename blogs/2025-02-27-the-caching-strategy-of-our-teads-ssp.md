---
title: "The caching strategy of our Teads SSP"
url: "https://medium.com/teads-engineering/the-caching-strategy-of-our-teads-ssp-b0e152e951d0?source=rss----3aab18f692b6---4"
date: "2025-02-27"
author: "Tristan Sallé"
feed_url: "https://medium.com/feed/teads-engineering"
---
And how we made it scale the past 10 years Our team at Teads manages what is called a Supply side platform or SSP. This service receives traffic from the browser and handles auctions by sending bid requests to our internal Demand side platform (DSP) or externals DSPs then wait for them to return bid responses and finally select the winner of the auction to return the right ad to the user. Today our SSP handles several hundreds of thousands requests per second worldwide, distributed over hundreds of individual instances, while maintaining a latency below 150 milliseconds on our p99 .
