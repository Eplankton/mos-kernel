# MOS-Kernel

#### 介绍
```
 A_A       _
o'' )_____//    Cortex-M上的简单RTOS内核，支持抢占式多任务处理
 `_/  MOS  )    MOS <=> Mini-RTOS
 (_(_/--(_/
```

#### 项目结构
```
src
├── config.h                    配置系统，设定资源、宏
├── main.cpp                    入口函数
│
├── drivers                     硬件设备驱动抽象层(SPL/HAL/...)
│   ├── device                  其他硬件设备(LED, LCD等)
│   └── stm32f4xx               stm32f4xx系列的片上外设
│
└── mos
    ├── arch                    架构相关代码
    │   └── cpu.hpp
    │
    └── kernel                  内核，硬件无关代码
        ├── global.hpp          内核全局变量
        ├── scheduler.hpp       调度器、上下文切换
        ├── sync.hpp            同步原语
        └── task.hpp            任务创建、阻塞、挂起、终止
```