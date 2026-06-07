---
layout: subtopic
title: "Board 3: Golden Arduino Board"
slug: board3_golden_arduino
topic: ecen5730-pcb
topic_title: "ECEN5730: PCB Design"
description: "Custom PCB for Arduino using ATmega328"
pdf: /assets/pdfs/ECEN5730/ECEN5730_Board3_Report.pdf
featured: true
---

A custom PCB for an Arduino board was designed (Golden Arduino), functioning on Arduino IDE. Pin headers were placed exactly the same as a traditional Arduino board for compatibility. Parts were manually assembled on manufactured PCB, and signals were measured for comparison between a commercial Arduino board and the Golden Arduino board.

There was a failure with the Reset Circuit rendering the CH340g (USB-to-TTL) unusable. This problem persisted on Board 4, and the root cause are the size of decoupling capacitors (too large), which affects the circuitry.