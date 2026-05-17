---
layout: article
title: "AArch64 Embedded Linux with Buildroot & QEMU"
description: "Setting up a full embedded Linux environment targeting AArch64 in QEMU."
topic: linux
topic_title: Linux
subtopic: buildroot-qemu
subtopic_title: Buildroot & QEMU
date: 2026-02-01
tags: [Buildroot, QEMU, AArch64, embedded]
---

## Overview

This project sets up a complete embedded Linux system using Buildroot, cross-compiled for AArch64 and booted in QEMU. The goal is a reproducible environment for developing and testing out-of-tree kernel modules.

## Key Steps

1. Configure Buildroot for `qemu_aarch64_virt_defconfig`
2. Add out-of-tree kernel module via a custom Buildroot package
3. Use `modules_install` with `INSTALL_MOD_PATH` to place `.ko` in the standard module tree
4. Write an init script (S-file) with execute permissions to `modprobe` the driver on boot
5. Create `/dev/aesdchar` via `mknod` if udev is not available

## Issues Encountered

- `BUILD_CMDS` macro invocation errors in the `.mk` file
- Stale duplicate build directories causing cached failures
- Missing execute bit on init scripts
- `modprobe` failing due to missing `modules.dep` — fixed by running `depmod`