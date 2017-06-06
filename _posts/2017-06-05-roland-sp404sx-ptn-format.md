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

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at ROLAND/SP-404SX/PTN. Here are a few example pattern files:

60 30 01 00 7f 40 00 60   

- 60 = Number of Ticks till next note
- 30 = Pad Code
- 01 = Bank Switch
- 00 = ???
- 7f = Velocity
- 40 = ???
- 0060 = Length of Sample (double byte)