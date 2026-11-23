---
title: "3D 打印机"
date: 2020-01-01
description: "万物始于‘1’"
slug: 3d-printer
categories:
  - 3D Printer
tags:
  - Mechanical Engineering
  - Tools
series:
  - Notes
image: 1.jpg
---

我做了一台十字轴传动的 3D 打印机，用来制作设备外壳和一些结构件。

![](2.jpg)

一开始，我用的是常见的步进电机驱动 DRV8825。这是一种方波驱动，噪声很大。

![](3.jpg)

于是我根据学到的知识，做了一块基于 SPWM 信号驱动的步进电机驱动板。后来我又加了磁编码器，把 SPWM 改成 SVPWM，并加入电流环闭环控制。最终的振动控制很好，运行也很安静。

![](4.jpg)

![](5.jpg)

相关设备已经在我的 GitHub 上开源。
