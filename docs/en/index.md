## Introduce

This is the golden age of accelerators. 

Memory is the core of AI infrastructure, AI/heterogeneous applications require: 

- CPU coordination

- Large memory capacity

- Fast memory allocation

- High memory utilization

However, the reality is...

- Poor programmability : CPU buffer? GPU buffer? 

- OOM (Out-of-memory) : small HBM capacity

- Slow "malloc/free" : not reinvented well

- Memory Fragmentation : failed to malloc 500MB with 10GB free HBM!

The cost of reinventing "mm systems" is extremely high. But the performorce of those "mm systems" is particularly unsatisfactory. 

And, as the code expands, the number of issues and problems also increases.

So, here comes GMEM, which would be the heart of "OS for AI".

GMEM Stop people from further reinventing the wheel, no more "malloc" and "mm systems" for accelerators drivers. 


## Features

GMEM provides those features:

- No more "malloc" impl for GPU, TPU, etc...

- No more "mm systems" for device drivers

- Enhanced programmability

- Unified virtual address space / User-guided memory advice

- Device memory oversubscription

- Better memory service

- Faster malloc/free speed

- Higher memory utilization


## Architecture

![gmem-arch](/assets/index/image-20230917-gmem-arch.jpg)

## Community

[Github]()

[openEuler]()

**Repo:**

- [Kernel](https://gitee.com/openeuler/kernel/blob/openEuler-23.09/mm/gmem.c)

- [Driver](https://gitee.com/openeuler/kernel/tree/openEuler-23.09/drivers/remote_pager)

- [Lib of GMEM](https://gitee.com/openeuler/libgmem)


## Contact Us

[SIG Email(Sig-Computing)](dev@openeuler.org)

