# UniProton 基础公共库文档

[TOC]



## 公共库 - 类型库

- **所在文件		     : **  `src/include/uapi/prt_typedef.h`

- **库作用		        ：** 定义一系列其他库和其他模块依赖的类型

- **依赖库或依赖模块     ：** GNU-C编译器的类型头文件 `stdint.h` `stddef.h` `stdbool.h`

- **所有定义的类型【无漏缺】**

  - **类型定义**

  - | 类型       | 意义                           |
    | ---------- | ------------------------------ |
    | U8         | 无符号byte                     |
    | U16        | 无符号short                    |
    | U32        | 无符号int                      |
    | U64        | 无符号long long                |
    | S8         | 有符号byte                     |
    | S16        | 有符号short                    |
    | S32        | 有符号int                      |
    | S64        | 有符号long long                |
    | VirtAddr   | void *                         |
    | PhyAddr    | void *                         |
    | OsVoidFunc | 参数为空且返回值为空的函数指针 |

  - **宏定义**

  - | 宏定义                | 意义                                                         |
    | --------------------- | ------------------------------------------------------------ |
    | OS_SEC_ALW_INLINE     | 无 [此处未揣测出原作者的意义]                                |
    | OS_EMBED_ASM          | 内联汇编宏   使用方法(riscv):	OS_EMBED_ASM("csrr t0,mhartid"); |
    | INLINE                | 静态inline宏，宏定义的函数替代，使用这个宏声明函数为内联静态函数 |
    | ALIGN(addr,boundrary) | 地址对齐宏(向上),boundrary为2的幂                            |
    |                       | 使用方法:ALIGN(0x321432,0x1000)=0x322000  ALIGN(0x321000,0x1000)=0x321000 |
    | TRUNCATE(addr, size)  | 地址对齐宏(向下),boundrary为2的幂                            |
    |                       | 使用方法:   TRUNCATE(0x321432,0x1000)=0x321000               |
    | YES                   | 1                                                            |
    | NO                    | 0                                                            |
    | TRUE                  | (bool)1                                                      |
    | FALSE                 | (bool)0                                                      |
    | NULL                  | (void*)0                                                     |
    | OS_ERROR              | (U32)(-1)                                                    |
    | OS_INVALID            | -1                                                           |
    | OS_OK                 | 0                                                            |
    | OS_FAIL               | 1                                                            |
    | U8_INVALID            | 0xffU                                                        |
    | U12_INVALID           | 0xfffU                                                       |
    | U16_INVALID           | 0xffffU                                                      |
    | U32_INVALID           | 0xffffffffU                                                  |
    | U64_INVALID           | 0xffffffffffffffffUL                                         |
    | U32_MAX               | 0xFFFFFFFFU                                                  |
    | S32_MAX               | 0x7FFFFFFF                                                   |
    | S32_MIN               | (-S32_MAX-1)                                                 |
    | LIKELY(x)             | 判断x是否为真                                                |
    | UNLIKELY(x)           | 判断x是否为假                                                |

- **模块`UML`图及与其他模块的耦合**
  - ![](pic/UML_TYPEDEF.png)















## 公共库 - 模块库

- **所在文件		     : **  `src/include/uapi/prt_module.h`

- **库作用		        ：** 定义了UniProton的所有模块

- **依赖库或依赖模块     ：** [prt_typedef](#公共库 - 类型库) 

- **所有定义的模块【无缺漏】**

  - | 模块           | 意义                                                         |
    | -------------- | ------------------------------------------------------------ |
    | OS_MID_SYS     | 系统模块                                                     |
    | OS_MID_MEM     | 内存模块                                                     |
    | OS_MID_FSCMEM  | 内存模块 【未被使用过，可能是原作者想要在管理算法上面做不同层次的内存模块】 |
    | OS_MID_TSK     | 任务模块                                                     |
    | OS_MID_SWTMR   | .模块  【目前尚未进行到此，若后续进行制到此填充】            |
    | OS_MID_TICK    | TICK模块                                                     |
    | OS_MID_CPUP    | CPU使用率计算模块                                            |
    | OS_MID_SEM     | 信号量模块                                                   |
    | OS_MID_HWI     | 硬件中断模块                                                 |
    | OS_MID_HOOK    | 钩子函数模块                                                 |
    | OS_MID_EXC     | 异常模块                                                     |
    | OS_MID_EVENT   | 事件模块                                                     |
    | OS_MID_QUEUE   | 消息队列模块                                                 |
    | OS_MID_TIMER   | 软件定时器模块                                               |
    | OS_MID_HARDDRV | .模块  【目前尚未进行到此，若后续进行制到此填充】            |
    | OS_MID_APP     | APP模块                                                      |
    | OS_MID_SIGNAL  | 信号模块                                                     |
    | OS_MID_SHELL   | SHELL模块                                                    |

- **模块`UML`图及与其他模块的耦合**

  - ![](pic/UML_module.png)















## 公共库 - 错误码库

- **所在文件		     : **  `src/include/uapi/prt_errno.h`

- **库作用		        ：** 定义一系列制作错误码的宏，包括制作不同级别，不同模块的错误码

- **依赖库或依赖模块     ：** [prt_typedef](#公共库 - 类型库)  [prt_module](#公共库 - 模块库)

- **所有定义**

  - | 定义宏               | 意义                                                         |
    | -------------------- | ------------------------------------------------------------ |
    | ERRNO_OS_ID          | OS错误码标记位，0x00表示OS **[其他模块基本不用，不作为PORT向其他内核模块的宏]** |
    | ERRTYPE_NORMAL       | 定义错误的等级:提示级别 **[其他模块基本不用，不作为PORT向其他内核模块的宏]** |
    | ERRTYPE_WARN         | 定义错误的等级:告警级别 **[其他模块基本不用，不作为PORT向其他内核模块的宏]** |
    | ERRTYPE_ERROR        | 定义错误的等级:严重级别 **[其他模块基本不用，不作为PORT向其他内核模块的宏]** |
    | ERRTYPE_FATAL        | 定义错误的等级:致命级别 **[其他模块基本不用，不作为PORT向其他内核模块的宏]** |
    | OS_ERRNO_BUILD_FATAL | **定义OS致命错误码且PORT向其他模块的宏** ,宏需要两个参数 **一是模块号 二是错误号** |
    | (mid, errno)         | 使用方法:**定义一个内存模块的1号错误码  OS_ERRNO_BUILD_FATAL(OS_MID_MEM,0x1)** |
    | OS_ERRNO_BUILD_ERROR | **定义OS严重错误码且PORT向其他模块的宏**,宏需要两个参数 **一是模块号 二是错误号** |
    | (mid, errno)         | 使用方法:**定义一个内存模块的2号错误码  OS_ERRNO_BUILD_ERROR(OS_MID_MEM,0x1)** |

- **模块`UML`图及与其他模块的耦合**

  - ![](pic/UML_module.png)



















## 公共库 - 模块库