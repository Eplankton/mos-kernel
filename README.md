# MOS-Kernel 🥗

### Introduction 🦉
```
 A_A       _
o'' )_____//    [MOS-Kernel]
 `_/  MOS  )    Simple Preemptive RTOS Kernel on Cortex-M
 (_(_/--(_/     MOS <=> Mini-RTOS
```

### Repository 📦
[Gitee](https://gitee.com/Eplankton/mos-kernel) | [GitHub](https://github.com/Eplankton/mos-kernel) 

### Architecture 🏀
<img src="mos-arch.svg">

```
mos
├── config.h             System Configuration
├── arch                 Arch-related
│   └── cpu.hpp          asm for context_switch
│
├── kernel               Kernel(Arch-independent)
│   ├── macro.hpp        Kernel Constant Macros
│   ├── type.hpp         Basic Types
│   ├── concepts.hpp     Type Constraints(Optional)
│   ├── data_type.hpp    Basic Data Structures
│   ├── alloc.hpp        Static/Dynamic Allocator
│   ├── global.hpp       Kernel Globals
│   ├── printf.c         Thread-safe printf
│   ├── task.hpp         Task control
│   ├── sync.hpp         Sync primitives
│   ├── scheduler.hpp    Scheduler and Policy
│   ├── ipc.hpp          Inter-Process Communication
│   └── utils.hpp        Utils
│
├── kernel.hpp           Import Kernel Modules
└── shell.hpp            Simple Shell
```