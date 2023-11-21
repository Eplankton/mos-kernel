# MOS-STM32

#### 介绍
```
 A_A       _
o'' )_____//
 `_/  MOS  )    STM32F4, Cortex-M上的简单RTOS
 (_(_/--(_/	 	MOS <=> Mini-RTOS

- Board: Nucleo-144 F429ZI
- MCU:   STM32F429ZIT6 (256KB SRAM, 2MB FLASH)
```

#### 项目结构
```
| mos/.
|     | drivers/                硬件设备驱动抽象层(SPL/HAL/...)
|     |
|     | arch/.
|     |      | cpu.hpp          架构相关代码
|     |
|     | kernel/.                内核-硬件无关代码
|              | global.hpp     内核全局变量
|              | task.hpp       任务创建、阻塞、挂起、终止
|              | scheduler.hpp  调度器、上下文切换
|              | sync.hpp       同步原语
| 
| main.cpp                      入口函数
| config.h                      配置系统，设定资源、宏
```

#### 使用例
```C++
// MOS Kernel & Shell
#include "mos/kernel/kernel.hpp"
#include "mos/shell.hpp"

// STM32F4xx HAL
#include "drivers/stm32f4xx/hal.hpp"

// Devices
#include "drivers/device/led.hpp"

namespace MOS::UserGlobal
{
    using namespace HAL::STM32F4xx;
	using namespace Driver;
    
    // Serial in and out
    auto& uart = STM32F4xx::convert(USART3);

    // LED red, green, blue
    Driver::LED_t leds[] = {...};
}

namespace MOS::Bsp
{
    using namespace Driver;
    using namespace UserGlobal;

    void LED_Config()
    {
        ...
        for (auto& led: leds) {
            led.init();
        }
    }

    void USART_Config()
    {
        ...
        uart.init(9600-8-1-N);
    }

    void config()
    {
        ...
        LED_Config();
        USART_Config();
        ...
    }
}

namespace MOS::App // User tasks
{
    using UserGlobal::leds;

    void Task0(void* argv)
    {
        while (true) {
            leds[0].toggle();
            Task::delay(500);
        }
    }
}

int main(void)
{
    using namespace MOS;

    Bsp::config(); // Init Hardware
    Task::create(App::Task0, nullptr, 1, "T0"); // Create user task
    Scheduler::launch(); // Begin Scheduling, never return

    while (true) {
        // ...
    }
}
```

#### 烧录启动
```
 A_A       _
o'' )_____//  Version  @ x.x.x
 `_/  MOS  )  Platform @ xxx, xxx
 (_(_/--(_/   Build    @ xx:xx:xx

Tid  Name   Priority   Status    PageUsage
-------------------------------------------
#0   idle     15       READY          10%
#1   T0       0        RUNNING         9%
-------------------------------------------
```

#### 版本
```
初始版本(0.0.1)，完成基本的调度器设计，计划完成以下部分：
1. 定时器，时间片轮转调度
2. 进程间通信 IPC，管道、消息队列
3. 进程同步 Sync，信号量、互斥锁
4. 移植简单的Shell
5. 可变页面大小，内存分配器
6. SPI 驱动开发，移植LVGL图形库
7. 移植到其他开发板，如ESP32-C3（RISC-V架构）
```
```
版本(0.0.2)，完成以下部分：
1. Sync::{Semaphore_t, Lock_t}
2. Policy::{PreemptivePriority}，允许相同优先级的任务以时间片轮转方式进行调度
3. Task::terminate() 在任务退出时隐式调用
4. Shell::{Command, CmdCall, launch}，简单的命令交互
5. LCD ST7735S SPI 驱动
6. os_ticks 和 Task::delay()，阻塞延时
7. 重组项目结构 {kernel, arch, driver}

计划：
1. 带有优先级继承机制的互斥锁 Mutex_t
2. 进程间通信 IPC，管道、消息队列等
3. 简单的动态内存分配器
4. 移植 GUILite/LVGL
```