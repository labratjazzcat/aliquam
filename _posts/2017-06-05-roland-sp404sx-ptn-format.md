---
layout: post
title: Roland SP-404SX Pattern Format
category: sp-edit
comments: false
description: Roland SP-404SX binary pattern format
tags:
  - sp-edit
published: true
---

## The Roland SP-404SX Pattern Format

<img src="https://i.imgur.com/hr6Cx6I.jpg" alt="SP-404SX" style="width: 200px;"/>

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at ROLAND/SP-404SX/PTN. Here is an  example pattern file:

1. 60 5e 00 00 7f 40 00 3c
2. 60 5d 00 00 7f 40 00 3c
3. 60 5b 00 00 7f 40 00 3c
4. 60 5c 00 00 7f 40 00 3c
5. 00 8C 00 00 00 00 00 00 
6. 00 01 00 00 00 00 00 00

The last 2 lines each pattern file are an end encoding in which the 3rd and 4th byte of the last line represent the length of the pattern in bars. The following is a breakdown of the first line.

60 5e 00 00 7f 40 00 3c   

- 60 = Number of Ticks till next note
- 5e = Pad Code
- 00 = Bank Switch
- 00 = ???
- 7f = Velocity
- 40 = ???
- 003c = Length of Sample (double byte)


