---
title: 8086CPU实模式内存映射表
date: 2022-03-16 12:51:30
categories:
  - 操作系统
tags:
  - memery
  - system
---

8086 实模式内存映射表

<!--more-->

# <center>实模式内存地址表</center>

| 起始  | 结束  | 大小             | 用途                                                                   |
| :---- | :---- | :--------------- | :--------------------------------------------------------------------- |
| FFFF0 | FFFFF | 16B              | BIOS 入口地址,此 16 字节内容为 jmp f000: e05b                          |
| F0000 | FFFEF | 16B-64KB         | 系统 BIOS 范围为 F0000-FFFFF,共 640k,减去 16B 所以此处终止地址为 FFFEF |
| C8000 | EFFFF | 160KB            | 映射硬件适配器的 ROM 或者内存映射式 IO                                 |
| C0000 | C7FFF | 32KB             | 显示适配器 BIOS                                                        |
| B8000 | BFFFF | 32KB             | 用于文本模式显示适配器                                                 |
| B0000 | B7FFF | 32KB             | 用于黑白显示适配器                                                     |
| A0000 | AFFFF | 64KB             | 用于彩色显示适配器                                                     |
| 9FC00 | 9FFFF | 1KB              | EBDA(Extend BIOS Data Area),扩展 BIOS 数据区                           |
| 7E00  | 9FBFF | 622080B,约 608KB | 可用区域                                                               |
| 7C00  | 7DFF  | 512B             | MBR 被 BIOS 加载与此处，共 512 字节                                    |
| 500   | 7BFF  | 30464B，约 30KB  | 可用区域                                                               |
| 400   | 4FF   | 256B             | BIOS 数据区域                                                          |
| 0     | 3FF   | 1K               | Interrupt Vector Table,中断向量表                                      |
