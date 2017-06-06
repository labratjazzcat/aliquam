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

The Roland SP-404SX is a portable hardware sampler with the ability to store patterns for playback. On the SP-404SX these patterns are stored on a removable SD card at ROLAND/SP-404SX/PTN/. This is an example pattern file viewed as hex:

<div class="env-header">hex of binary</div>
{% highlight python linenos %}
  60 5E 00 00 7F 40 00 3C
  60 5D 00 00 7F 40 00 3C
  60 5B 00 00 7F 40 00 3C
  60 5C 00 00 7F 40 00 3C
  00 8C 00 00 00 00 00 00 
  00 01 00 00 00 00 00 00
{% endhighlight %}

The last 2 lines of each pattern file are an end encoding in which the 3rd and 4th bytes of the last line represent the length of the pattern in bars, in this case 1. Each bar in the SP-404SX is divided into 384 _ticks_. The following is an analysis of the first line of the pattern file, . 

<center>
1. 60 5E 00 00 7F 40 00 3C   
</center>


- 0x60 = **Next Sample**
- 0x5E = **Pad Code** 
- 0x00 = **Bank Switch** (00 or 01)
- 0x00 = appears to always be 00
- 0x7F = **Velocity** (0-7F)
- 0x40 = appears to always be 40
- 0x003C = **Length**

### Next Sample
Specifies the number of _ticks_ untill the next sample in the pattern should be triggered. For samples played simultaneously all but one have a Next Sample value of 0, play the next sample 0 ticks after the current sample. All 4 samples in the example pattern have a Next Note value of 0x60 which is the hex value that represents a quater bar. 384 / 4 = 96 or 0x60. 
### Pad Code
Specifies the bank offset and pad number according to the following formula: Pad Code = bank_offset*12 + pad_number(1-12) + 46. This is a snippet of the function that generates the bank letter and pad number from the hex code.
<div class="env-header">python</div>
{% highlight python linenos %}
real_code = int(hex_code, 16) - 46
bank = real_code $\textdiv$ 12
pad = real_code % 12
if pad == 0:
	pad = 12
	bank -= 1
{% endhighlight %}
For the first line in the example pattern the Pad Code specifies the bank offset 3, pad number 12.

### Bank Switch 
Specifies whether the bank offset refers to the top row(A/B/C/D/E), 00 or the bottom row(F/G/H/I/J), 01. For the first line in the example pattern the Bank Switch is 00 so the sample this line refers to is D12.
### Velocity
Specifies the velocity or amplitude of the sample in the range 1 - 127. While the SP-404SX does not  record velocity nor have velocity sensitive pads the pattern function can playback samples with respect to the velocity specified here.
### Length
Specifies the number of _ticks_ until the sample should be turned off.
