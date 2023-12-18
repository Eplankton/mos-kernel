# MOS-Kernel 🥗

### 介绍 🦉
```
 A_A       _
o'' )_____//    [MOS-Kernel]
 `_/  MOS  )    Cortex-M上的简单RTOS内核，支持抢占式多任务处理
 (_(_/--(_/     MOS <=> Mini-RTOS
```

### 仓库 📦
[Gitee](https://gitee.com/Eplankton/mos-kernel) | [GitHub](https://github.com/Eplankton/mos-kernel) 

### 项目结构 🏀
```
mos
├── config.h             配置系统，设定资源、宏
├── arch                 架构相关代码
│   └── cpu.hpp          上下文切换的汇编实现
│
├── kernel               内核(硬件无关)
│   ├── macro.hpp        系统配置宏
│   ├── type.hpp         基础类型
│   ├── concepts.hpp     C++20 Concepts
│   ├── data_type.hpp    内核数据结构
│   ├── alloc.hpp        静态/动态内存分配
│   ├── global.hpp       内核全局变量
│   ├── printf.c         输出系列函数实现
│   ├── task.hpp         任务创建、阻塞、挂起、终止...
│   ├── sync.hpp         同步原语
│   ├── scheduler.hpp    调度器
│   └── util.hpp         其他工具
│
├── kernel.hpp           内核模块导入
└── shell.hpp            简单的Shell
```