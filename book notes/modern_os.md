---
cards-deck: tech::modern_os
---

# overview

## processor

### general registers
#card
- program counter::containing memory address of next instruction to be fetched
^1610912464810
- stack register::point to top of current stack in memory
^1610912464819
- stack::contains one frame per procedure that has been entered but not exited
^1610912464825
- frame::contains input parameters, local variables and temporary variables not in register
^1610912464832
- PSW::Program Status Word, contains condition code bits, set by comparison instructions, CPU priority, (kernel/user) mode, etc. Important in syscall and IO.
^1610912464839
^1610912464846

### superscalar CPU
#card
multiple fetch/decoder unit -> holding buffer -> multiple execute unit
^1610912464852

### user mode/kernel mode
#card
all instructions involving I/O and memory protection are disallowed in user mode
user program make system call to trap into kernel mode with TRAP instruction

### hyperthreading
#card
allow CPU to hold state of two different threads and switch back & forth on nanosecond time scale.
Does not offer true parallelism, but reduce thread switching to order of nanosecond

### GPU
#card
A GPU is a processor with thousands of tiny cores, good for small computations done in parallel. e.g. graphics, encryption, network traffic.
Not very good at serial tasks.
Hard to program.

## memory
#card
hierarchy of layers
register, cache (L1/L2), main memory, rom, flash

### register
#card
controlled in software
internal to CPU
same material as CPU
as fast as CPU
capacity: 32 * 32 bits on 32-bit CPU, 64 * 64 bits on 64-bit CPU

### cache memory
#card
controlled by hardware
inside or very close to CPU.
main memory divided into cache lines, 64 bytes each.
cache hit take 2 clock cycles.
some machine have multiple cache layers

#### L1 cache
#card
always inside CPU
feeds decided instructions into CPU
most chips have second L1 cache for data words
typically 16KB each
no delay for access

#### L2 cache
#card
several MB of recent memory words
one to two clock cycles

### main memory

### ROM
programmed in factory
read only
fast and inexpensive

### flash memory
#card
much slower than RAM, faster than disk
wear out after too many uses

### CMOS
#card
volatile
hold current date/time
hold configuration params, e.g. boot info
powered by small battery

### disk
#card
move 1 cylinder take 1ms
move to random cylinder takes 5-10ms
sequential read 50-160 MB/sec
- track::circle
- cylinder::all tracks for a given arm position
- sector::each track divided into sectors, 512 bytes per sector

### SSD
#card
stores in flash memory

### virtual memory
#card
remap memory address between main memory and program address
use main memory as cache
mapping is done by MMU, part of CPU.

## I/O device
#card
controller
device
driver gets a command from OS, translate and write into device registers.

### access
busy waiting::issue syscall, polling device until ready
interrupt::controller issue interrupt to signal completion
DMA::direct memory access, use special DMA chip, talk to mem and controller itself. After done, signal interrupt.

#### interrupt
#card
1. CPU -> disk controller
2. disk control -> interrupt controller chip
3. if interrupt controller is ready, assert a pin on CPU chip.
4. when CPU is ready, push PSW and PC to stack, switch to kernel mode and handle interrupt.

##### interrupt vector
#card
memory section containing interrupt handler for a device


### controller
#card
controls device
takes command from OS
present a simple interface
contain small embedded computers to do the job

#### I/O port space
#card
small number of registers to communicate between driver and controller
1. device registers mapped into system address space, accessed with common memory operations
2. special I/O port space, each register have a port address, special IN/OUT instructions used to access registers.

### device
#card
have simple standard interface
e.g. SATA: serial advanced technology attachment

### device driver
#card
software talks to controller
most runs in kernel mode, part of OS:
1. relink kernel with new driver and reboot system, e.g. older UNIX
2. make entry in OS file and reboot. OS search driver and load. e.g. windows
3. install on the fly without reboot. e.g. USBs


## buses

### PCIe
#card
- main bus in system
- transfer rate: tens of gigabits per sec
- dedicated point-to-point connections
- serial bus architecture
- data send in a message, similar to network packet

### shared bus architecture
#card
multiple devices use same wire to transfer data.

### parallel bus architecture
#card
send each word of data over multiple wires, e.g. PCI bus

### DMI
#card
direct media interface

### USB
#card
universal serial bus
invented for slow I/O devices
p33
