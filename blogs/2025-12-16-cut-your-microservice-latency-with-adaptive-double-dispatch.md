---
title: "Cut your microservice latency with adaptive double dispatch"
url: "https://medium.com/teads-engineering/cut-your-microservice-latency-with-adaptive-double-dispatch-64911b1b707f?source=rss----3aab18f692b6---4"
date: "2025-12-16"
author: "Guy Kobrinsky"
feed_url: "https://medium.com/feed/teads-engineering"
---
Serving millions of requests per minute with a microservices environment is not an easy task. Every request is routed to many applications, and may potentially stall or fail at any step in the flow. Needless to say, not every one of the hundreds of microservices was written by the strongest coder — which means that context switches, gc spikes or just inefficient code could creep up on you at any moment We always try to find ways to reduce latency, but before getting to that, let’s understand how our system behaves How does your service latency graph look like?
