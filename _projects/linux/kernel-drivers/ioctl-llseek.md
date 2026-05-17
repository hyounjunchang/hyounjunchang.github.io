---
layout: article
title: "ioctl & llseek Integration"
description: "Implementing AESDCHAR_IOCSEEKTO ioctl and custom llseek in a kernel driver."
topic: linux
topic_title: Linux
subtopic: kernel-drivers
subtopic_title: Kernel Drivers
date: 2026-01-15
tags: [kernel, ioctl, llseek, C]
---

## Overview

This article covers adding `ioctl` and `llseek` support to the `aesdchar` driver, enabling userspace programs to seek directly to specific circular buffer entries.

## AESDCHAR_IOCSEEKTO

The custom ioctl command accepts a struct with:
- `write_cmd` — index of the target circular buffer entry
- `write_cmd_offset` — byte offset within that entry

The kernel handler translates these into an absolute file offset, accounting for evicted bytes.

## llseek

Custom `llseek` handles:
- `SEEK_SET` — absolute position from start of all written data
- `SEEK_CUR` — relative to current position
- `SEEK_END` — relative to end of all buffered data

Key insight: kernel module state persists across userspace process restarts — `rmmod`/`insmod` is required to fully reset driver state during development.