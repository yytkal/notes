---
cards-deck: tech::misc
---

# 硬件訪問
#card 
內存映射 （顯卡）
接口訪問， 讀寫接口寄存器
^1610437507801

# strace
#card 
trace system calls and signals
^1610505089599

# UDB
#card 
understand, design, build
^1610505089607

# lsof
#card 
list file descriptor
^1610505089616

# hdparm/ioctl
#card 
set device parameter
^1610505089627

# c-state/p-state
#card 
c: control sleep level when cpu idle, 0 wake- 6 powered off
p: control desired performance from a core: 0 highest (turbo if possible), 1 max baseline, 15 lowest
^1610505089635

# chroot
#card 
change root dir for current process and children
^1610505089647

# cpu/chip/microprocessor
#card 
actual integrated circuit IC
^1610505089655

# socket
#card 
physical connector on motherboard accept a single chip
^1610505089662

# processor
#card 
either a logical execution unit (core) or a chip
^1610505089669

# core
#card 
logical execution unit containing L1 cache and functional unit
^1610505089677

# balloning
#card 
reclaim guest memory page
^1610505089684

# HAL
#card 
hardware abstraction layer, layer between hardware and software and hides difference between hardware
^1610505089692

# hyper-threading
#card 
intel's architecture allowing single processor running multiple threads simulataneously
^1610505089700

# iscsi
#card 
protocal allowing scsi commands transmitted over tcp/ip
^1610505089709

# large page
#card 
allow TLB to index 2MB, 4MB pages in addition to 4KB page
^1610505089716

# TLB
#card 
translation lookaside buffer, a CPU cache to hold page table entries
^1610505089724

# LUN
#card 
logical unit number, a number identifying a single logical unit, representing a single disk or a partition on an array
^1610505089735

# MMU
#card 
memory management unit, act as interface between CPU and memory, part of CPU
^1610505089745

# NAS
#card 
network attached storage
^1610505089752

# NFS
#card 
network file system protocol
^1610505089760

# NIC
#card 
network interface card
^1610505089767

# NPT
#card 
nested page table. perform virtualization of MMU in hardware. EPT in Intel
^1610505089775

# Paravirtualization
#card 
modify guest kernel to communicate to hypervisor in order to perform priviledged CPU and memory operation
^1610505089785

# PCIe
#card 
computer bus specification
^1610505089793

# Thrashing
#card 
situation when virtual or physical memory is not large enough, resulting frequent IO to paging file, located on hard disk
^1610505089801

# virtual machine monitor
#card 
software, firmware or hardware creates and runs virtual machine
^1610505089809

# VPS
#card
virtual private server, type of os virtualization, partition hardware into small parts, negligible overhead, direct syscalls, no emulation, but cannot run different kernel
^1610505089819

# virtualization
## type
#card
operating systen
hardware
^1610505089830

## hardware virtualization
#card
full
partial
paravirtualization
^1610505089838

### full virtualization
#card 
- almost complete simulation of actual hardware
- guest unmodified
- inefficient due to trapping syscalls
^1610505089845

#### hardware assisted
#card 
improve virtualization efficiency
support of virtualization in hardware
^1610505089854

### partial virtualization
#card 
- some hardware simulated
- guest program need some modification
^1610505089862

### paravirtualization
#card 
- hardware not simulated
- guest is modified
- guest is aware of hypervisor, more efficient
^1610505089871

# hypervisor

## type
#card
type-1
type-2
^1610505089878

### type-1 hypervisor
#card 
native, baremetal. 
hardware -> hypervisor -> guest
^1610505089886

### type-2 hypervisor
#card 
hosted
hardware -> OS -> hypervisor -> guest
^1610505089893

# virtualization vs emulation
#card 
emulation can emulate different architecture, e.g. GBA, andoid emulator
^1610505089901

# desktop virtualization
#card 
VDI, virtual desktop infrastructure
HVD, hosted virtual desktop, e.g. cloudtop?
^1610505089908

# nested virtualization
#card 
running hypervisor inside the other, benefit (requires?) hardware support
^1610505089915

# kernel samepage merging
#card 
share memory page having identical contents across VMs on same host
^1610505089924

# process virtual machine
#card
JVM?^1610505089931
