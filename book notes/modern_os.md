---
cards-deck: tech::modern_os
---

# overview

## processor

### general registers
#card
program counter
stack register
stack
frame
PSW
^1610912464846

#### program counter
#card
containing memory address of next instruction to be fetched
^1610912464810

#### stack register
#card
point to top of current stack in memory
^1610912464819

#### stack
#card
contains one frame per procedure that has been entered but not exited
^1610912464825

#### frame
#card
contains input parameters, local variables and temporary variables not in register
^1610912464832

#### PSW
#card
Program Status Word, contains condition code bits, set by comparison instructions, CPU priority, (kernel/user) mode, etc. Important in syscall and IO.
^1610912464839

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
^1610919554163

#### track
#card
circle
^1610919554143

#### cylinder
#card
all tracks for a given arm position
^1610919554150

#### sector
#card
each track divided into sectors, 512 bytes per sector
^1610919554157

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
DMA::direct memory access, use special DMA chip, talk to mem and controller itself. After done, signal interrupt.
^1611302949406

#### interrupt
#card
1. CPU -> disk controller
2. disk control -> interrupt controller chip
3. if interrupt controller is ready, assert a pin on CPU chip.
4. when CPU is ready, push PSW and PC to stack, switch to kernel mode and handle interrupt.

##### interrupt vector
#card
memory section containing interrupt handler for a device
^1611302949413

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

## buses

### PCIe
#card
- main bus in system
- transfer rate: tens of gigabits per sec
- dedicated point-to-point connections
- serial bus architecture
- data send in a message, similar to network packet
^1611302949424

### shared bus architecture
#card
multiple devices use same wire to transfer data.
^1611302949433

### parallel bus architecture
#card
send each word of data over multiple wires, e.g. PCI bus
^1611302949444

### DMI
#card
direct media interface
^1611302949454

### USB
#card
universal serial bus
invented for slow I/O devices
centralized bus, root device polls all I/O devices every 1msec
USB 2.0:480Mbps; USB 3.0: 5Gbps
^1611302949460

### SCSI
#card
small computer system interface, high performance bus for fast disks, scanners.
640MB/sec
^1611302949467

### Plug&Play
#card
dynamically assign interrupt request level and addresses for I/O card.
^1611302949474

## Boot

### BIOS
#card
Basic Input OutputSystem, contain low-level I/O software, held in flash RAM.
1. Check RAM, keyboard and other basic devices
2. Scan PCIe buses.
3. Determine boot device stored in CMOS memory.
4. Load and run first sector from boot device, includes partition table and boot loader.
5. Boot loader loads OS.
6. OS configures and loads device driver.
^1611302949482

## Real-Time Operating Systems
- hard real-time: action absolutely must occur at a certain time
- soft real-time: missing an occasional deadline is not desirable but acceptable. e.g. multimedia system

## Terms

### Processes
A program in execution

#### address space
#card
list of memory locations from 0 to maximum
contains: program, data, stack

#### process table
#card
struct containing all information about process, other than its own address space. e.g. open files, registers, alarms and related processes.

#### core image
#card
a suspended process consists of its address space.

#### alarm signal
#card
software analog of hardware interrupts. Cause process to temporarily suspend and run signal-handling procedure.

#### working directory
#card
each process has a current working directory.

### File

#### special file
#card
make I/O devices look like files, under /dev/ dir

##### block special files
#card
model devices consisting a collection of randomly addressable blocks. e.g. disks

##### character special files
#card
model devices accept or output character stream. e.g. printer, modems

#### pipe
#card
pseudofile used to connect two processes
process cannot tell difference between a pipe and a normal file without special syscall.

### Syscalls
#card
push parameter onto stack (reverse order)
call library procedure
put syscall code in register
call TRAP (switch from user to kernel)
kernel dispatch to syscall handler based on code

#### execve
#card
replace process core image with command to execute

#### memory segment
#card
text segment: program code, low address
data segment: variables, grow upward, above text segment (heap?)
stack segment: grow downward, from high address to low

#### link
#card
create a new directory entry with i-number of an existing file.
If either one removed with unlink, the file still exists.

#### i-node
#card
Each unix file has a unique i-number. Directory is simply a file containing (i-node, filename) pairs

### OS Structure

#### Monolithic
#card
Entire OS runs as a single binary in kernel mode.
OS is a collection of procedures and free to call each other.
Efficient, but lower reliability.
- main program
- service procedures (handle syscall)
- utility procedures (helper function)

#### Layered System
#card
e.g. MULTICS. multiple rings, inner ring is more privileged. Enforced with hardware support.

#### Microkernels
#card
Split OS into small, well-defined modules, minimize kernel component.
Offers high reliability.
Put mechanism in kernel but not policy, e.g. kernel runs high priority processes, but priority scheduling run in user mode.  

#### Exokernels
#card
partition resources directly, jail?

### Compiler
#card
c preprocessor: reads .c imports .h and translate macro, create object file
linker: combine object file, library function into binary

# Processes

thread creation is 10-100x faster than process creation

Notes:116
Head:134
