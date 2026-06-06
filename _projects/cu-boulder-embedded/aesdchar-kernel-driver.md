---
layout: subtopic
title: "aesdchar Kernel Driver & Socket Server"
slug: aesdchar-kernel-driver
topic: cu-boulder-embedded
topic_title: "CU Boulder: Embedded Systems Engineering Projects"
description: "An out-of-tree Linux kernel character device driver backed by a circular buffer, integrated with a TCP socket server."
pdf: /assets/pdfs/aesdchar-report.pdf
tags: [Linux, kernel, C, driver, sockets, ECEN5713]
---

This project develops `aesdchar`, a Linux kernel module implementing a character device backed by a 10-slot circular buffer. The driver supports `read`, `write`, `llseek`, and a custom `ioctl` command (`AESDCHAR_IOCSEEKTO`). It is integrated with `aesdsocket`, a daemon-style TCP server that pipes network data into the device.