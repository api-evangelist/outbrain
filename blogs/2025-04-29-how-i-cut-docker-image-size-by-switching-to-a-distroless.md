---
title: "How I Cut Docker Image Size by Switching to a Distroless Base Image"
url: "https://medium.com/teads-engineering/how-i-cut-docker-image-size-by-switching-to-a-distroless-base-image-4ccf260aad50?source=rss----3aab18f692b6---4"
date: "2025-04-29"
author: "Dorian Grasset"
feed_url: "https://medium.com/feed/teads-engineering"
---
Thumbnail made by Lucas Introduction One of the main challenges of updating multiple Node.js projects, sometimes upgrading from version 14 to 22, was adapting Dockerfiles to ensure optimal compatibility while minimizing image size. This optimization was essential for improving security, reducing vulnerabilities, and speeding up build and deployment times. This article aims to improve this process by adapting the Dockerfiles to reduce the image size, and enhance build and deployment efficiency.
