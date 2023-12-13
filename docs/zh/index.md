## 简介

### 业界背景
后摩尔时代正不断涌现GPU、TPU、FPGA等领域专用加速器。它们与CPU类似，需要将数据放在本地的DRAM（例如LPDDR或HBM）中以提高计算速度，这就要求每个加速器有一套内存管理系统去管理他们的内存；例如，NVIDIA GPU的UVM驱动中含有约七万行内存管理代码，这已经和Linux内核中的内存管理代码（八万行）处于同一量级。

随着各类新型加速器的不断涌现，加速器厂商们不可避免地需要开发复杂的内存管理系统；遗憾的是，尽管各类加速器内存管理系统的高层设计逻辑与Linux内核并无本质差异，但它们却不能复用Linux内核中更趋成熟的内存管理代码。

### GMEM简介
GMEM革新了Linux内核中的内存管理架构，通过引入一层逻辑页表，即vm_object，将内存管理的高层逻辑与CPU硬件进一步解耦，从而抽象出能让各类加速器复用的High-Level内存管理逻辑。

加速器驱动仅需使用GMEM抽象出的High-Level API，并注册由GMEM规范好的、与加速器硬件微架构相关的MMU函数，即可将本地内存管理托管至GMEM，无需额外开发内存管理逻辑。例如，在华为自研的昇腾加速器中，使用GMEM可以免去三万行的内存管理代码。

所有通过GMEM API获取内存管理能力的加速器，均可向用户提供统一地址空间的编程框架：用户可以直接使用OS原生的mmap接口，或使用由GMEM用户态库提供的malloc函数分配统一虚拟内存；CPU和加速器均可直接使用统一虚拟内存进行编程。任意时刻，对于同一统一虚拟地址，CPU和进程中挂载的任意加速器所读写的数据均保持一致。

以上所述的一致内存视角由GMEM使能。

考虑到实际应用往往需要将领域加速器的专用计算能力，与CPU的通用计算能力相结合，GMEM允许加速器通过GMEM API将加速器挂载到用户进程中；进一步地，GMEM利用逻辑页表的信息，使用加速器注册好的MMU函数和CPU微架构的页表函数，维护了不同处理器、不同微架构间多份页表的一致性。加速器只需要注册底层函数，不再需要实现任何统一地址空间协同的高层逻辑。

除了统一地址空间编程框架之外，GMEM还提供了加速器内存的自动超售功能。在加速器内存不足时，GMEM可自动将较冷的内存换出到CPU的DRAM上。这意味着，用户无需任何适配，便可将一个内存消耗远超加速器HBM容量的应用运行在加速器上，从而在应用透明的情况下，大大拓展了应用处理问题的规模。


## 架构

GMEM架构如下：
![GMEM架构图](/assets/index/image-20230917-gmem-arch.jpg)


## 功能描述

- 在内核中提供GMEM High-Level API，允许加速器驱动通过注册GMEM规范所定义的MMU函数直接获取内存管理功能

- 为接入GMEM内存管理的加速器提供统一虚拟内存编程框架、透明的加速器内存超售功能

- 在SYSCALL中新增分配统一虚拟内存的mmap标志，新增协助用户指引内核优化异构内存管理的hmadvise接口

- 提供分配统一虚拟内存的malloc库，libgmem

> [GMEM用户接口说明](https://gitee.com/openeuler/libgmem/blob/master/README_CN.md#%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
######
> 注：提供基于GMEM优化的华为昇腾AI加速器驱动实例，以及演示程序，包括矩阵乘、大模型等应用样例。


## 应用场景

### 功能场景

#### 异构统一内存编程

在异构加速器编程时，使用GMEM接口可以分配CPU-加速器的统一虚拟内存，显著降低编程复杂度，提升异构编程性能

#### 加速器内存自动超售

使用GMEM接口分配的内存不受加速器的物理内存容量限制，应用可以透明地超售内存（当前上限为CPU的DRAM容量）

### 业务实例

#### 大模型训推场景

GMEM实现异构内存透明扩容技术，使能HBM内存自动超分，实现高性能、低门槛训推；GMEM提供的OS原生的极简异构内存管理在超大模型训练中，性能相比NVIDIA-UVM提升60%

#### 高并发服务场景

提供低内存碎片的动态HBM分配机制，解除按峰值HBM开销预留内存的限制，提高单位时间内的服务并发量。


## 社区

[Github]()

[openEuler](https://gitee.com/openeuler/docs/tree/master/docs/zh/docs/GMEM)

**Repo:**

- [Kernel](https://gitee.com/openeuler/kernel/blob/openEuler-23.09/mm/gmem.c)

- [Driver](https://gitee.com/openeuler/kernel/tree/openEuler-23.09/drivers/remote_pager)

- [Lib of GMEM](https://gitee.com/openeuler/libgmem)


## 联系我们
SIG Email(Sig-Computing): <dev@openeuler.org>

