---
layout: subtopic
title: "Piano Tiles LED Game"
slug: piano-tiles-led
topic: cu-boulder-embedded
topic_title: "CU Boulder: Embedded Systems Engineering Projects"
description: "A Raspberry Pi-based Piano Tiles game using a 16x16 WS2812B LED matrix and TCP beatmap server."
pdf: /assets/pdfs/piano-tiles-led-report.pdf
tags: [Raspberry Pi, C, WS2812B, TCP, pthreads]
---

This project implements a Piano Tiles-style rhythm game on a Raspberry Pi 4, driven by a 16x16 WS2812B LED matrix. A TCP socket server streams beatmap data to the game client. Background audio playback runs via libmpg123 and libout123 on a dedicated pthread, routed to the 3.5mm audio jack through ALSA.