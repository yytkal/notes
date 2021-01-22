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
^1610919554070

### hyperthreading
#card
allow CPU to hold state of two different threads and switch back & forth on nanosecond time scale.
Does not offer true parallelism, but reduce thread switching to order of nanosecond
^1610919554077

### GPU
#card
A GPU is a processor with thousands of tiny cores, good for small computations done in parallel. e.g. graphics, encryption, network traffic.
Not very good at serial tasks.
Hard to program.
^1610919554083

## memory
#card
hierarchy of layers
register, cache (L1/L2), main memory, rom, flash
^1610919554091

### register
#card
controlled in software
internal to CPU
same material as CPU
as fast as CPU
capacity: 32 * 32 bits on 32-bit CPU, 64 * 64 bits on 64-bit CPU
^1610919554099

### cache memory
#card
controlled by hardware
inside or very close to CPU.
main memory divided into cache lines, 64 bytes each.
cache hit take 2 clock cycles.
some machine have multiple cache layers
^1610919554107

#### L1 cache
#card
always inside CPU
feeds decided instructions into CPU
most chips have second L1 cache for data words
typically 16KB each
no delay for access
^1610919554114

#### L2 cache
#card
several MB of recent memory words
one to two clock cycles
^1610919554123

### main memory

### ROM
programmed in factory
read only
fast and inexpensive

### flash memory
#card
much slower than RAM, faster than disk
wear out after too many uses
^1610919554129

### CMOS
#card
volatile
hold current date/time
hold configuration params, e.g. boot info
powered by small battery
^1610919554135

### disk
#card
move 1 cylinder take 1ms
move to random cylinder takes 5-10ms
sequential read 50-160 MB/sec
- track::circle
^1610919554143
- cylinder::all tracks for a given arm position
^1610919554150
- sector::each track divided into sectors, 512 bytes per sector
^1610919554157
^1610919554163

### SSD
#card
stores in flash memory
^1610919554170

### virtual memory
#card
remap memory address between main memory and program address
use main memory as cache
mapping is done by MMU, part of CPU.
^1610919554179

## I/O device
#card
controller
device
driver gets a command from OS, translate and write into device registers.
^1610919554186

### access
busy waiting::issue syscall, polling device until ready
^1610919554195
interrupt::controller issue interrupt to signal completion
^1610919554204

### controller
#card
controls device
takes command from OS
present a simple interface
contain small embedded computers to do the job
^1610919554210

#### I/O port space
#card
small number of registers to communicate between driver and controller
1. device registers mapped into system address space, accessed with common memory operations
2. special I/O port space, each register have a port address, special IN/OUT instructions used to access registers.
^1610919554217

### device
#card
have simple standard interface
e.g. SATA: serial advanced technology attachment
^1610919554223

### device driver
#card
software talks to controller
most runs in kernel mode, part of OS:
1. relink kernel with new driver and reboot system, e.g. older UNIX
2. make entry in OS file and reboot. OS search driver and load. e.g. windows
3. install on the fly without reboot. e.g. USBs
^1610919554229
