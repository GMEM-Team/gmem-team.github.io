---
# Title, summary, and page position.
linktitle: 接口说明
summary: Learn how to use Wowchemy's docs layout for publishing online courses, software documentation, and tutorials.
weight: 3
icon: book
icon_pack: fas

# Page metadata.
title: 接口说明
date: '2023-12-14T00:00:00+01:00'
type: book # Do not modify.
---

GMEM通过特定的flag申请对等互访的虚拟内存，并对外提供了一些内存优化语义，通过这部分内存语义可以达到性能优化的效果。
libgmem是GMEM用户接口的抽象层，主要功能是是对上述内存语义进行封装，简化用户的使用。