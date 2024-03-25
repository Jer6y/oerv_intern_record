# Proot  Riscv

## 前情提要

- 一天，Jer6y 闲来无事，翻阅 OERV 的Porting Pool 的时候发现了此项目， 在仔细了解后，发现很对 Jer6y的胃口， 于是便有了此记录
- proot 项目内容可自行github搜索， 本文档用于记录移植的过程和感悟，技术向的解析在这里 , [link](./proot_riscv_technical.md)
- 【简要解说】为什么比较对 Jer6y 的胃口 ?
  - 基于 systemcall 的一个项目， posix 下的， 依赖的 so 库是一个内存分配库 talloc 和制作归档的库， 正好，这段时间Jer6y 正在学习一些 syscall 相关的内容，想找项目练手
  - 在简要阅读了相关内容后，觉得这个很值得学习，觉得很有意思的一个项目，同时又能广泛学到各个 syscall 的内容 【这里是因为ptrace 监管各个 syscall 入口，然后修改子进程的入口参数，来做一个fake 的文件空间, 感觉很有意思的一个东西】

## 过程记录

#### 2024-03-25

- 今日完成进度
  - 整理完成 mem, reg 等通用的库 ，【将ptrace  peek, poke data peek,poke register 重新封装新API的库】
- 预计明日进度
  - 整理event相关的处理 