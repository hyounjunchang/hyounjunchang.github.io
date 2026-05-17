---
layout: article
title: "aesdchar: Character Device Driver"
description: "Building a circular-buffer character device driver as a Linux kernel module."
topic: linux
topic_title: Linux
subtopic: kernel-drivers
subtopic_title: Kernel Drivers
date: 2026-01-01
tags: [kernel, C, driver, ECEN5713]
---

## Overview

`aesdchar` is an out-of-tree Linux kernel module implementing a character device (`/dev/aesdchar`) backed by a 10-slot circular buffer. Each `write()` appends a command entry; each `read()` returns data from the current file position.

## Key Implementation Details

### Circular Buffer

- 10 fixed slots; oldest entry is evicted when full
- Tracks `total_bytes_evicted` for correct `llseek` offset accounting

### System Call Implementations

- **`write`**: Appends data until a newline, then commits the entry
- **`read`**: Returns bytes from the current file position across entry boundaries
- **`llseek`**: Supports `SEEK_SET`, `SEEK_CUR`, `SEEK_END` with eviction-aware offsets
- **`ioctl`** (`AESDCHAR_IOCSEEKTO`): Seeks to a specific entry index + byte offset

## Bugs Fixed

- Deadlock from calling `down()` twice on the same mutex
- Off-by-one in eviction count tracking
- File position not snapping correctly after eviction

## Source

[GitHub Repository](https://github.com/hyounjunchang)