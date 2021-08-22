### 计划安排
#### 学习书籍为官方三级考试Linux教程
| 日期  |   章节  |   页码   |  程度  | 笔记 |
| ---  |   ---   |   ---   |  ---  | --- |
| 0724 | 1.1、1.2 | 3～16    | *一般* | [第1章](#计算机体系结构与操作系统)|
| 0725 | 1.3～1.5 | 17～49   | *一般* |     |
| 0726 | 2～      | 50～61   | *一般* | [第2章](#Linux系统概述)   |
| 0727 | 3.1、3.2 | 62～80   | *一般* | [第3章](#Linux系统使用基础)   |
| 0728 | 3.3～3.5 | 80～93   | *一般* |     |
| 0729 | 4.1、4.2 | 94～105  | **重要** |     |
| 0730 | 4.3、4.4 | 105～137 | **重要** |     |

#### 计算机体系结构与操作系统
1. ”计算机科学的奠基人“、”人工智能之父“ 英国数学家图灵（1912-1954）图灵奖
2. ”现代计算机之父“、”博弈论之父“ 美籍匈牙利 冯诺伊曼（1903-1957）
3. 冯诺伊曼结构计算机由 ***控制器、运算器、存储器、输入设备、输出设备*** 五部分组成（控制器和运算器构成现在CPU）
4. 计算机的主要研究方向为 ***系统研究*** 即设计实现计算机，包含计算机的理论研究和计算机系统设计实现（硬件、软件），***应用研究*** 即使用计算机解决实际问题
5. 计算机体系（系统）结构是与计算机系统组织和实现相关的基本理论、工作原理、设计方法和技术的总称
6. ***摩尔定律***，每过 ***18个月***，芯片上可以集成的集体管数量将翻一倍
7. 计算机结构层次：     
    0层：数字逻辑层，主要是实现计算机的硬件的逻辑电路和连接线路     
    1层：微体系结构层，通过控制器和存储器的微指令集设计计算机系统架构   
    2层：传统机器层，通过机器语言设计计算机体系结构     
    3层：操作系统层，使用操作系统的管理命令管理和调度计算机系统中的软硬件资源       
    4层：汇编语言层，连接高级语言和机器语言，编译器（编译程序）将高级语言翻译成汇编语言、汇编器（汇编程序）将汇编语言翻译成机器语言     
    5层：高级语言层，普通程序员使用如c，java，python带语言完成程序      
    6层：应用程序层，面向普通使用者的       
8. 指令集是一个计算机系统支持的所有机器指令的集合，软硬件层面的分界
9. 计算机系统工作的基本过程：程序员编写的软件经编译器翻译成可执行程序，即一个机器的指令序列，然后由底层硬件一条条读取指令执行，该过程即代表，软件的最终体现为指令集中的各种指令。
10. 指令集是计算机设计中重要的一环，指令集对上限定类软件的基本功能，对下制定了硬件实现的功能目标
11. 基本指令格式：***操作码+操作数（地址）***；依据操作数量的不同可以分为 ***零地址指令、一地址指令、二地址指令、三地址指令、多地址指令***；如加法指令需要操作码和三个操作数【加法操作码+加数操作数(地址)+加数操作数(地址)+结果保存操作数(地址)】
12. 按指令的寻址空间来分，寻址方式：***立即数寻址、寄存器寻址、主存寻址、堆栈寻址***
13. 指令的操作码以及操作数在计算机中用二进制表示，为了方便记忆使用助记符（如加法是ADD、减法是SUB，传送是MOV等），汇编语言通常采用采用助记符。       
    例子，将寄存器AX等值设为0010H，寄存器BX等值设为0020H，然后将AX和BX内容相加，结果保存在AX中。   
    ```     
    MOV AX,0010H    
    MOV BX,0020H    
    ADD AX,BX   
    ```
14. ***指令集体系结构***（ISA，Instruction Set Architecture）分为 ***CISC***（复杂指令系统计算机 Complex Instruction Set Computer）、***RISC***（精简指令系统 Reduced Instruction Set Computer）
15. 常用等ISA为：***X86、ARM、MIPS***
16. 在CPU和主存之间有高速缓冲存储器（Cache），Cache和主存储器的地址映射方式有三种：
    * ***全相联映射***
    * ***直接映射***
    * ***组相联映射**
17. 在采用全相联映射和组相联映射的系统中，当Cache满的时候需要使用**替换策略**，常用的替换策略有 ***随机法（RAND）、先进先出法（FIFO）、最近最少使用法（LRU）***
18. Cache与主存之间的数据一致性，通过两种常用的Cache写操作方式来保证：***写直达、写回***
19. 缓存一致性协议 最经典的是 ***MESI（Modified Exclusive Shared or Invalid）***，MESI协议Cache Line状态：***修改、独占、共享、失效***
20. 传统的单核CPU由控制器和运算器这两个主要部件组成。
21. 多核处理器（CMP，Chip Multi-Processor）:
    * ***同构多核：计算内核相同、地位对等***
    * ***异构多核：计算内核不同、地位不对等***
    * 各核心之间数据的共享和同步，基于总线共享的Cache结构（每个内核共享二级或三级Cache，结构简单，通信速度高，可扩展性差）、基于片上的互联结构（每个核心有自己的Cache，核心之间通过消息通信，可扩展性好，硬件结构复杂软件改动大）
22. CPU指令执行的过程：***取指令(IF)➡️指令译码(ID)➡️执行指令(EX)➡️访问数据(MEM)➡️结果写回(WB)***，以上五个阶段形成一个指令周期（CPU取出并执行一条指令所需的全部时间称为指令周期）
23. CPU周期（机器周期），一个CPU周期包含若干个时钟周期，时钟周期定义为CPU时钟频率的倒数，是计算机中最基本、最小的时间单位
24. 操作系统从用户角度看，为用户提供的服务：程序开发、程序运行、I/O设备访问、文件访问、系统资源的访问、错误检测和响应、日志服务
25. 操作系统从系统角度看，计算机就是一组软硬件资源的集合，操作系统负责管理这些资源，资源按作用分：处理器，存储器、I/O设备、文件（程序和数据）
26. 现代操作系统一般具有 ***并发、共享、虚拟、异步（随机、不确定性）这四个基本特征***，还有安全和可扩展性
    * ***并发***：两个或多个事件在同一时间间隔内发生
    * ***共享***：
27. ***并行***：两个或多个事件在同一时刻发生
28. 从资源管理的角度，操作系统五大基本功能：***处理器管理、存储管理、设备管理、文件管理、作业管理***
29. ***进程***：计算机中的程序在某数据集合上帝一次运行活动，是系统进行资源分配和调度的基本单位；***并发环境中程序的执行过程***
30. ***PCB（Process Control Block）进程控制块是进程存在的唯一标准***
31. 进程和程序的区别：
    * 进程是个动态概念，程序是个静态概念
    * 进程有并发特征，程序没有
    * 进程有生命周期，只在计算机运行期间才有可能存在；程序可以在外存长期保存
    * 进程和程序之间并不总是一一对应的，一个程序执行在不同数据集上就成为不同进程
    * 进程与程序的组成不同，进程实体的组成包括程序数据和进程控制块PCB
32. ***线程***：线程包含在进程中，一条线程就是进程中一个单一顺序的控制流，在一个进程中可以并发多个线程。线程<进程
33. 进程的状态：***运行态、就绪态、等待态、（新建态、终止态）***
34. 5种进程状态转换：***新建➡️就绪、就绪➡️运行、运行➡️就绪、运行➡️等待、等待➡️就绪、运行➡️终止***
35. 文件的物理结构：顺序结构、链接结构、索引结构
36. 文件存储空间管理方法：空闲表法、空闲链表法（成组链接法）、位示图法
37. 文件目录管理，文件控制块（File Control Block，FCB），单级目录、二级目录、**多级目录（树形目录结构）**，在树形目录结构中，从根到任何文件都有唯一路径；现代操作系统基本上都是树形目录结构
38. 文件共享：
    * 基于索引节点的共享方式-硬链接：引入索引节点，把文件的物理地址及其他文件属性等信息放到索引节点中，文件目录项中只包含文件名和指向索引节点的指针；在索引节点中应有一个链接计数器（count字段）用于表示链接到本索引节点的目录数量（当count=2时说明有两个目录链接到文件上，或者说有两个用户共享此文件）
    * 利用符号链实现的共享方式-软链接：创建一个Link类型的文件（符号链），内容只保存被共享文件的路径名，当访问符号链时，操作系统会根据符号链的内容将访问操作转到被共享的文件
#### Linux系统概述
1. 1964年 MULTICS分时操作系统（贝尔实验室、麻省理工、美国通用电气）
2. 1969年 Ken Thompson、Dennis Ritchie 开发了UNIX系统和C语言
3. 用于教学的功能有限的类UNIX系统——MINIX Andrew Tanenbaum 
4. 1991年10月5日 Linux系统（0.0.2版本，目前最新5.5.7） Linus Torvalds(linux之父)
5. 1984  GNU计划和自由软件基金会  里查德.斯托曼
6. 1994年3月 Linux 1.0 发布
7. 1996年6月 Linux 2.0 发布
8. Linux操作系统版本分为内核版本和发行版本
9. 内核-设备驱动、文件系统、进程管理、网络通信等

#### Linux系统使用基础
1. 常用的桌面 KDE、GNOME、MATE、Cinnamon、Unity
2. 可以在低配置运行的桌面 Fluxbox、Xfce、JWM、Fvwm、fvwm95
3. 一般的命令格式：命令 [选项] [参数]
4. w/who命令查看已登录的用户信息，w还可以看到其他用户的执行任务的情况 
    w [-h 不显示输出信息标题；-l 用详细格式输出；-s 用简洁格式输出] [用户名]
    who [-a 列出所有信息，相当于所有选项；-b 列出系统最近的启动时间； -l 列出所有可登录的终端信息； -m 仅列出当前终端信息；-q 列出在本地系统上的用户数和用户数的清单；-r 显示当前系统运行级别；-s 仅显示名称、线路和时间字段，是who命令默认选项；-u 显示当前每个用户的用户名、登录终端、登录时间、、线路活动和进程标识] [file 默认是从/var/run/utmp文件获取登录用户信息，也可以通过指定文件来获取]
5. echo命令可以将命令行中的参数显示到标准输出（屏幕）上，-e 选项支持反斜线控制和字符转换；-n 选项内容不会换行显示
6. date命令可以显示和修改时间 -s 选项设置时间 `data -s "01:01:01 2021-08-20"`
7. passwd是密码配置命令 ``passwd [选项] [用户名]`；普通用户只能修改自己的秘密，root用户可以修改自己和普通用户的密码
8. Linux下的软件包分为 ***源码包*** 和 ***二进制包***
9. 源码包通常使用Tarball工具压缩，格式为*.tar.gz，Tarball是Linux系统的一款打包工具，可以对源码包进行打包压缩
10. 二进制包说编译之后的包，有RPM和DPKG两大包管理系统
11. RPM安装包的命令格式为`rpm -ivh [包全名]`；可以多个包安装，用空格分开`rpm -ivh a.rpm b.rpm c.rpm`
12. RPM升级包`rpm -Uvh [包全名]` U大写表示该软件如果没有安装则直接安装，若已安装则升级到最新版本；`rpm -Fvh [包全名]` F大写标识如该软件没安装则不会安装
13. RPM卸载`rpm -e [包全名]`
14. RPM查询`rpm -q [包全名]` q代表query；查询所有已安装的软件包`rpm -qa` qa代表 query all；可以使用查找符`rpm -q |grep httped`; 查询软件包相关信息`rpm -qi [包全名]` i 代表 information信息；查询未安装软件包的信息`rpm -qip [包全名]` p表示package 未安装的软件包
15. 使用RPM安装软件包必须考虑与其他RPM包的依赖关系，`rpm -qR [包全名]`可以用来查询已安装软件包所依赖的其他包；`rpm -qRp [包全名]`可以查看未安装软件吧的依赖关系