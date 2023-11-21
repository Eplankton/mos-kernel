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
| mos/.
|     | arch/.
|     |      | cpu.hpp          架构相关代码
|     |
|     | kernel/.                内核-硬件无关代码
|              | global.hpp     内核全局变量
|              | task.hpp       任务创建、阻塞、挂起、终止
|              | scheduler.hpp  调度器、上下文切换
|              | sync.hpp       同步原语
|
| config.h                      配置系统，设定资源、宏
```