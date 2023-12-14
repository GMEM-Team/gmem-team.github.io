---
# Title, summary, and page position.
linktitle: 功能描述
summary: Learn how to use Wowchemy's docs layout for publishing online courses, software documentation, and tutorials.
weight: 2
icon: book
icon_pack: fas

# Page metadata.
title: 功能描述
date: '2018-09-09T00:00:00Z'
type: book # Do not modify.
---

在内核中提供GMEM High-Level API，允许加速器驱动通过注册GMEM规范所定义的MMU函数直接获取内存管理功能

为接入GMEM内存管理的加速器提供统一虚拟内存编程框架、透明的加速器内存超售功能

在SYSCALL中新增分配统一虚拟内存的mmap标志，新增协助用户指引内核优化异构内存管理的hmadvise接口

提供分配统一虚拟内存的malloc库，libgmem