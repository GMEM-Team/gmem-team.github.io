---
widget: hero
headless: true
weight: 10
title: GMEM
hero_media: book.svg
design:
  background:
    gradient_start: '#4bb4e3'
    gradient_end: '#2b94c3'
    text_color_light: true
cta:
  url: https://gitee.com/openeuler/docs/blob/master/docs/zh/docs/GMEM/%E5%AE%89%E8%A3%85%E4%B8%8E%E9%83%A8%E7%BD%B2.md
  label: 使用GMEM
  icon_pack: fas
  icon: download
cta_alt:
  url: docs/
  label: 了解GMEM
---

GMEM将特定于CPU的实现从Linux内存系统中分离出来，这样设备驱动程序就可以注册与硬件相关的函数，让操作系统在一个统一的虚拟地址空间中管理加速器的本地内存。

