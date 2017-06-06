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
<center>
<img src="https://i.imgur.com/hr6Cx6I.jpg" alt="SP-404SX" style="width: 300px;"/>
</center>

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at ROLAND/SP-404SX/PTN. Here is an  example pattern file:

1. 60 5e 00 00 7f 40 00 3c
2. 60 5d 00 00 7f 40 00 3c
3. 60 5b 00 00 7f 40 00 3c
4. 60 5c 00 00 7f 40 00 3c
5. 00 8C 00 00 00 00 00 00 
6. 00 01 00 00 00 00 00 00

The last 2 lines of each pattern file are an end encoding in which the 3rd and 4th byte of the last line represent the length of the pattern in bars, in this case 1. Each bar in the SP-404SX is divided into 384 _ticks_. The following is a breakdown of the first line.

<center>
1. 60 5e 00 00 7f 40 00 3c   
</center>


- 60 = **Next Note**
- 5e = **Pad Code**
- 00 = **Bank Switch** (00 or 01)
- 00 = ???
- 7f = **Velocity** (1-127)
- 40 = ???
- 003c = **Length**

### Next Note
Specifies the number of _ticks_ untill the next note in the pattern should be triggered. For notes played simultaneously all but one have a Next Note value of 0, which makes sense play the next sample 0 ticks after this sample.
### Pad Code

### Bank Switch
### Velocity
### Length

   