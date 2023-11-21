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
| mos/.
|     | arch/. 
|     |      | cpu.hpp          Arch-related code
|     | 
|     | kernel/.                Arch-independent code
|              | global.hpp     Kernel global
|              | task.hpp       Task create, yield, terminate, block...
|              | scheduler.hpp  Scheduler
|              | sync.hpp       Synchronization primitive
|
| config.h                      System Configuration
```