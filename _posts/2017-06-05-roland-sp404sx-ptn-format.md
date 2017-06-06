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

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at ROLAND/SP-404SX/PTN/. This is an example pattern file:

1. 60 5E 00 00 7F 40 00 3C
2. 60 5D 00 00 7F 40 00 3C
3. 60 5B 00 00 7F 40 00 3C
4. 60 5C 00 00 7F 40 00 3C
5. 00 8C 00 00 00 00 00 00 
6. 00 01 00 00 00 00 00 00

The last 2 lines of each pattern file are an end encoding in which the 3rd and 4th byte of the last line represent the length of the pattern in bars, in this case 1. Each bar in the SP-404SX is divided into 384 _ticks_. The following is an of n analysis he first line of the pattern file, . 

<center>
1. 60 5E 00 00 7F 40 00 3C   
</center>


- 60 = **Next Sample**
- 5E = **Pad Code**
- 00 = **Bank Switch** (00 or 01)
- 00 = ???
- 7F = **Velocity** (1-127)
- 40 = ???
- 003C = **Length**

### Next Sample
Specifies the number of _ticks_ untill the next sample in the pattern should be triggered. For samples played simultaneously all but one have a Next Sample value of 0, play the next sample 0 ticks after the current sample.
### Pad Code
Specifies the bank offset and pad number according to the following formula: bank_offset*12 + pad_number(1-12) + 46.
### Bank Switch 
Specifies whether the bank offset refers to the top row(A/B/C/D/E), 00 or the bottom row(F/G/H/I/J), 01.
### Velocity
Specifies the velocity or amplitude of the sample in the range 1 - 127. While the SP-404SX does not  record velocity nor have velocity sensitive pads the pattern function can playback samples with respect to the velocity specified here.
### Length
Specifies the number of _ticks_ until the sample should be turned off.
