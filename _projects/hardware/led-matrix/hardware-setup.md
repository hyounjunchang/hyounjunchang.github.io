---
layout: article
title: "16x16 WS2812B LED Matrix — Hardware Setup"
description: "PCB design and wiring for a Raspberry Pi-driven 16x16 WS2812B LED matrix."
topic: hardware
topic_title: Hardware
subtopic: led-matrix
subtopic_title: WS2812B LED Matrix
date: 2026-03-01
tags: [Raspberry Pi, WS2812B, SPI, hardware]
---

## Overview

A 16x16 grid of WS2812B addressable RGB LEDs driven by a Raspberry Pi over SPI using DMA via the `rpi-ws281x` library.

## Hardware Details

- **LEDs**: WS2812B (256 total)
- **Layout**: Serpentine/zigzag routing on PCB — odd rows run right-to-left
- **Interface**: SPI with DMA for timing-accurate signal generation
- **Power**: External 5V supply; logic level shifted from 3.3V Pi GPIO

## Serpentine Remapping

Because the PCB routes rows in alternating directions, pixel index remapping is required:

```c
int remap(int x, int y) {
    if (y % 2 == 0)
        return y * WIDTH + x;
    else
        return y * WIDTH + (WIDTH - 1 - x);
}
```