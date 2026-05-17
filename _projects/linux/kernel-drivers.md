---
layout: subtopic
title: Kernel Drivers
slug: kernel-drivers
topic: linux
topic_title: Linux
description: "Building Linux character device drivers, ioctl interfaces, and kernel modules."
---

This section covers the development of out-of-tree Linux kernel modules, focusing on the `aesdchar` character device driver. Topics include circular buffer management in kernel space, implementing `read`, `write`, `llseek`, and `ioctl` system calls, and integrating the driver with a userspace socket server.