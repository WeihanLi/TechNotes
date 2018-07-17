# 操作系统概览

## 概念

计算机系统由硬件和软件两部分组成。操作系统（OS，Operating System）是配置在计算机硬件上的第一层软件，是对硬件系统的首次补充。

## 操作系统的目标

1. 有效性

    - 提高系统资源利用率
    - 提高系统的吞吐量

1. 方便性

    - 使得计算机更容易被使用

1. 可扩充性

    - 方便增加新的功能和模块

1. 开放性

    - 提供统一的开放环境
    - 遵循世界标准规范

## 操作系统的作用

1. 作为用户与计算机硬件系统之间的接口，使用用户更方便使用
1. 作为计算机系统资源的管理者，对资源进行协调提高系统各种资源的利用率
1. 实现对计算机资源的抽象

## 操作系统的基本特性

1. 并发性

    - 并行：两个或多个事件在同一时刻发生
    - 并发：两个或多个事件在同一时间间隔内发生
    - 进程：操作系统引入进程的目的就是为了使得多个程序能并发执行，系统必须为每个程序建立进程。
    - 线程：20世纪80年代中期提出的比进程更小的单位，进一步提高系统的并发行

1. 共享性

    - 共享：系统中的资源可供内存中多个并发执行的进程（线程）共同使用，也称之为资源共享或资源复用
    - 互斥共享：系统中某些资源一段时间内只允许一个进程进行访问，一个进程访问结束并释放掉该资源后才允许其他资源访问。这种资源被称之为临界资源或独占资源。
    - 同时访问：允许多个进程（线程）“同时”进行访问（这里的同时往往是指宏观上的同时）

1. 虚拟技术

    - 时分复用技术
      - 虚拟处理机技术
      - 虚拟设备技术

    - 空分复用技术
      - 虚拟磁盘技术
      - 虚拟存储器技术

1. 异步性

    - 进程的异步性：进程是以人们不可预知的速度向前推进

## 操作系统的主要功能

- 处理机管理功能
  - 进程控制
  - 进程同步
  - 进程通信
  - 调度

- 存储器管理功能
  - 内存分配
  - 内存保护
  - 地址映射
  - 内存扩充

- 设备管理功能
  - 缓冲管理
  - 设备分配
  - 设备处理

- 文件管理功能
  - 文件存储空间管理
  - 目录管理
  - 文件的读写管理和保护

- 操作系统与用户之间的接口
  - 用户接口
  - 程序接口

## 总结

总而言之，言而总之，操作系统是为了让我们的计算机更高效的为我们工作。