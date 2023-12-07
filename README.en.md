# MOS-Kernel

#### Introduction
```
 A_A       _
o'' )_____//    Mini Preemptive RTOS Kernel on Cortex-M
 `_/  MOS  )    MOS <=> Mini-RTOS
 (_(_/--(_/
```

#### Structure
```
src
├── config.h                    System Configuration
├── main.cpp                    Entry point
│
├── drivers                     Hardware Drivers(SPL/HAL/...)
│   ├── device                  Other hardware(LED, LCD, etc.)
│   └── stm32f4xx               STM32F4xx on-chip periphs
│
└── mos
    ├── arch                    Arch-related code
    │   └── cpu.hpp
    │
    └── kernel                  Arch-independent code
        ├── global.hpp          Kernel global
        ├── scheduler.hpp       Scheduler
        ├── sync.hpp            Sync primitive
        └── task.hpp            Task create, yield, terminate, block...
```