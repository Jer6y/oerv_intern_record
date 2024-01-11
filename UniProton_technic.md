# UniProton Kernel 软件架构以及移植指南		- Jer6y

## 前言

- **UniProton** 作为 openEuler 的一款**嵌入式实时内核**，既支持了单核MCU，也支持了**多核强力的CPU** 【这个是许多RTOS不支持的，比如UCOSIII 以及 TencentOSTiny】，UniProton也为开发者提供了相当多的API接口，原生的**UAPI**，以及**LIBC接口**，和后续可能会实现的**POSIX接口**，以及特殊的**KAL层接口**，提供了许多组件库，如**NET协议栈组件库**，**SHELL组件库**，当然在配置上也是十分灵活，支持用户通过预编译宏裁剪模块等。很有幸能够尝试对UniProton Kernel 进行RISCV的移植 。谈及Kernel ， 就不得不谈到架构，硬件问题，因为Kernel 会实时和这些东西打交道，因此移植一个Kernel 需要牵涉到的模块也繁多。此次的移植过程中，笔者希望自己能够掌握UniProton Kernel 的**软件架构**，学习项目在如此强耦合的情况下如何去**解耦**，让UniProton 成为一个移植性十分可观的Kernel ，同时此次也会以**UML图**的形式对各个模块进行剖析，**对模块间的关系进行剖析**。
- 如果您对我的工作**感兴趣**，可以**随时联系我**，我的githubid : **Jer6y**
- 如果您想要参与**与我一同工作**，也欢迎加我的微信： **Jer6y**

### 软件框架模块图

- 下面通过对**各个独立模块**进行解析，**再合并**的形式进行**软件框架**解析
- **红色部分** **- 移植需要完成的部分**    **橙色部分 -   强调部分**

### 异常模块UML图

![](pic/Exception_module.png)

- 该模块牵涉到的所有文件

  - ```shell
    src/include/prt_exc.h
    ```

  - ```shell
    src/core/kernel/kexc/prt_kexc.c
    ```

  - ```shell
    src/core/kernel/include/prt_kexc_external.h
    ```

  - ```shell
    src/arch/include/prt_exc_external.h
    ```

  - ```shell
    src/arch/cpu/.../common/prt_exc.c            -> 自己移植实现
    ```

  - ```shell
    src/uapi/hw/../ xxx.h 	              -> 自己移植实现
    ```

    

    