# MOS-Kernel 🥗

### Introduction 🦉
```
 A_A       _
o'' )_____//    [MOS-Kernel]
 `_/  MOS  )    Simple Preemptive RTOS Kernel on Cortex-M
 (_(_/--(_/     MOS <=> Mini-RTOS
```

### Repository 📦
[GitHub](https://github.com/Eplankton/mos-kernel) | [Gitee](https://gitee.com/Eplankton/mos-kernel)

### Structure 🏀
```
mos
├── config.h             System Configuration
├── arch                 Arch-related code
│   └── cpu.hpp          ASM of ContextSwitch
│
├── kernel               Kernel(arch-independent)
│   ├── macro.hpp        Configured Macros
│   ├── type.hpp         Basic Types
│   ├── concepts.hpp     C++20 Concepts
│   ├── data_type.hpp    Kernel Data Structures
│   ├── alloc.hpp        Static/Dynamic Allocator
│   ├── global.hpp       Kernel Globals
│   ├── printf.c         printf implementation
│   ├── task.hpp         Task create, yield, terminate, block...
│   ├── sync.hpp         Sync primitives
│   ├── scheduler.hpp    Scheduler and Policy
│   └── util.hpp         Utils
│
├── kernel.hpp           Import Kernel Modules
└── shell.hpp            Simple Shell
```