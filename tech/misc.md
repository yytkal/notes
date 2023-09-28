---
cards-deck: tech::misc
---

# 硬件訪問
#card
內存映射 （顯卡）
接口訪問， 讀寫接口寄存器

# strace
#card
trace system calls and signals

# UDB
#card
understand, design, build

# lsof
#card
list file descriptor

# hdparm/ioctl
#card
set device parameter

# c-state/p-state
#card
c: control sleep level when cpu idle, 0 wake- 6 powered off
p: control desired performance from a core: 0 highest (turbo if possible), 1 max baseline, 15 lowest

# chroot
#card
change root dir for current process and children

# cpu/chip/microprocessor
#card
actual integrated circuit IC

# socket
#card
physical connector on motherboard accept a single chip

# processor
#card
either a logical execution unit (core) or a chip

# core
#card
logical execution unit containing L1 cache and functional unit

# balloning
#card
reclaim guest memory page

# HAL
#card
hardware abstraction layer, layer between hardware and software and hides difference between hardware

# hyper-threading
#card
intel's architecture allowing single processor running multiple threads simulataneously

# iscsi
#card
protocal allowing scsi commands transmitted over tcp/ip

# large page
#card
allow TLB to index 2MB, 4MB pages in addition to 4KB page

# TLB
#card
translation lookaside buffer, a CPU cache to hold page table entries

# LUN
#card
logical unit number, a number identifying a single logical unit, representing a single disk or a partition on an array

# MMU
#card
memory management unit, act as interface between CPU and memory, part of CPU

# NAS
#card
network attached storage

# NFS
#card
network file system protocol

# NIC
#card
network interface card

# NPT
#card
nested page table. perform virtualization of MMU in hardware. EPT in Intel

# Paravirtualization
#card
modify guest kernel to communicate to hypervisor in order to perform priviledged CPU and memory operation

# PCIe
#card
computer bus specification

# Thrashing
#card
situation when virtual or physical memory is not large enough, resulting frequent IO to paging file, located on hard disk

# virtual machine monitor
#card
software, firmware or hardware creates and runs virtual machine

# VPS
#card
virtual private server, type of os virtualization, partition hardware into small parts, negligible overhead, direct syscalls, no emulation, but cannot run different kernel

# virtualization
## type
#card
operating systen
hardware

## hardware virtualization
#card
full
partial
paravirtualization

### full virtualization
#card
- almost complete simulation of actual hardware
- guest unmodified
- inefficient due to trapping syscalls

#### hardware assisted
#card
improve virtualization efficiency
support of virtualization in hardware

### partial virtualization
#card
- some hardware simulated
- guest program need some modification

### paravirtualization
#card
- hardware not simulated
- guest is modified
- guest is aware of hypervisor, more efficient

# hypervisor

## type
#card
type-1
type-2

### type-1 hypervisor
#card
native, baremetal.
hardware -> hypervisor -> guest

### type-2 hypervisor
#card
hosted
hardware -> OS -> hypervisor -> guest

# virtualization vs emulation
#card
emulation can emulate different architecture, e.g. GBA, andoid emulator

# desktop virtualization
#card
VDI, virtual desktop infrastructure
HVD, hosted virtual desktop, e.g. cloudtop?

# nested virtualization
#card
running hypervisor inside the other, benefit (requires?) hardware support

# kernel samepage merging
#card
share memory page having identical contents across VMs on same host

# process virtual machine
#card
