---
layout: subtopic
title: "Embedded Linux with Buildroot & QEMU"
slug: buildroot-embedded-linux
topic: cu-boulder-embedded
topic_title: "CU Boulder: Embedded Systems Engineering Projects"
description: "Building a complete AArch64 embedded Linux system with Buildroot, deployed and tested in QEMU."
pdf: /assets/pdfs/buildroot-report.pdf
tags: [Buildroot, QEMU, AArch64, Linux, CI/CD]
---

This project builds a reproducible embedded Linux image using Buildroot for an AArch64 QEMU target. It includes out-of-tree kernel module packaging, rootfs overlay configuration, init scripts for automatic driver loading, and a GitHub Actions CI pipeline for automated builds.