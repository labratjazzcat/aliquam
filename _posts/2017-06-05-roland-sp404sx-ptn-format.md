---
layout: post
title: Roland SP-404SX Pattern Format
category: spedit
comments: false
description: Roland SP404SX binary pattern format
tags:
  - spedit
published: true
---

## The Roland SP-404SX Pattern Format
![]({{site.baseurl}}/https://i.imgur.com/hr6Cx6I.jpg)

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at (path/to/pattern).

| 60 | 30 | 01 | 00 | 7f | 00 | 0060 |
|:---|:---|:---|:---|:---|:--:|-----:|
| a  | b  | c  | d  | e  | f  | g    | 

- a = Number of Ticks till next note
- b = Pad Code
- c = Bank Switch
- d = ???
- e = Velocity
- f = ???
- g = Length of Sample