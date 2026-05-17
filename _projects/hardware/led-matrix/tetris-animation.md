---
layout: article
title: "Tetris-Style Falling Color Animation"
description: "Implementing a falling color animation on the WS2812B LED matrix in C."
topic: hardware
topic_title: Hardware
subtopic: led-matrix
subtopic_title: WS2812B LED Matrix
date: 2026-03-15
tags: [Raspberry Pi, animation, C, WS2812B]
---

## Overview

A Tetris-inspired animation where columns of color fall from the top of the 16x16 LED matrix, stack at the bottom, and repeat with new colors.

## Implementation

Each column tracks a falling head position. On each frame:
1. Advance the head down by one row
2. Light the head pixel with the column's color
3. When the head hits the bottom or a stacked pixel, lock it and start a new head

```c
void update_column(int col) {
    if (head[col] < stack_height[col]) {
        set_pixel(col, head[col], column_color[col]);
        head[col]++;
    } else {
        stack_height[col]++;
        head[col] = 0;
        column_color[col] = random_color();
    }
}
```

## Build System

The project uses a modern Makefile with incremental builds and automatic header dependency tracking via `-MMD -MP` gcc flags.