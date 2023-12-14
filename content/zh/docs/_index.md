---
title: GMEM
type: book # Do not modify.
toc: false
---

GMEM将特定于CPU的实现从Linux内存系统中分离出来，这样设备驱动程序就可以注册与硬件相关的函数，让操作系统在一个统一的虚拟地址空间中管理加速器的本地内存。


