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
Process::an instance of executing program including the current values of program counter, registers and variables

daemons::background processes

fork::syscall, creates an exact clone of calling process

execve::syscall, allow child process to change memory image and start new program

copy-on-write::parent and child process have distinct address space and do not share writable memory

process group::In Unix, a process and all its children and further descendants together form a process group.

## state
blocked: input ready=>ready
ready: scheduler picks the process => running
running: process wait for resource => blocked; scheduler picked another process => ready

## process table
#card
one entry per process, contains process state, program counter, stack pointer, memory localtion, open files, accounting and scheduling.

## interrupt vector
Location of interrupt service procedure associated with each I/O class.
Interrupt controller chip pushes current process's information onto stack, then jump to location of interrupt service procedure. When finshed, scheduler is called to see who to run next

## degree of multiprogramming
#card
CPU utilization = 1 - p^n (p: fraction of time waiting for IO, n: number of processes)

## threads
 thread creation is 10-100x faster than process creation

per-process resource::threads in same process share resources. e.g. address space, global variables, open files, child processes, signal handling
per-thread resource::each thread has its own stack, register, program counter, state

thread_yield::allows thread to voluntarily give up the CPU to let another thread run. Important as there is no clock interrupt to enforce multiprogramming as there is with processes.

pthread::POSIX Threads

### implementation
#### user-space
* Thread implemented in user space as a library. 
* Kernel manages single threaded processes. 
* Each process need its own private thread table. 
+ Efficiency: Thread scheduler also in user space, no trap; no context switch; no memory flush.
+ Each process has its own customized scheduling algorithm.
- Page faults cause entire process being blocked.
- Fairness: Kernel is unaware of threads (no clock interrupts within process). Unless threads yield, thread scheduler cannot do anything.
- Blocking system calls blocks all threads in the process. Alternatives:
   * reimplement syscalls as unblockign
   * wrapper/jacket: wrapping syscalls so that blocking syscalls are made only when safe

#### kernel
* kernel owns thread table
* More overhead compared to user space implementation, alternative:
   * recycling with thread pool, when thread is destroyed, marked as not runnable, but kernal data structure is unaffected. Reactivated when new thread created. 

#### hybrid
* Flexibility: Use kernel-level threads and multiplex user-level threads onto some of them.

#### upcall
* roughly analogous to a signal in UNIX, allowing kernel activate run-time system.
- violates structure inherent in layered system. (lower level system should not call procedures in upper level)

#### popup thread
* used in distributed systems, when new message arrival, system creates new thread
+ no registers, stacks to be restored (brand-new threads)

## interprocess communication: IPC
Communications between processes
1. Shared data structures, e.g. semaphores can be stored in kernel and accessed with syscall
2.  Modern OS (Unix, Windows) offer a way for processes to share some portion of address space with other process

### mutual exclusion
#### disabling interrupt
* process disables interrupt (including clock interrupts) after entering critical region and reenable afterwards
+ useful technic in kernel, but not user processes
- bad to grant user process power to turn off interrupts
- not working on multiprocessor, since interrupts is turned off on only one cpu

#### Lock memory bus (hardware support)
busy wait::loop and test a variable until some value appears, should avoid unless expect wait time is short
spin lock::a busy wait lock

TSL::Test and set lock
XCHG::Exchange contents of two locations atomically, e.g. register and memory word

priority inversion problem::high priority process busy waiting on low priority process, while low priority process not able to run.

#### Sleep and Wakeup
sleep::syscall, causes caller to block
wakeup::syscall, the process to be awakened

##### semaphores
#card
* Value 0 means no wakeups were saved, or some positive value if one or more wakeups were pending
* Instead of sleep/wakeup, down and up.
* Check value, changing it and possibly goto sleep done as actomic action

binary semaphores::semaphores that are initialized to 1 and used by two or more processes to ensure only one of them enter its critical region. (a basic lock?)
mutex semaphore::used for mutual exclusion (same as binary semaphore?)
synchronizzation::guarantee that certain event sequences do or do not occur.

###### mutex
#card 
* a simplified semaphore for managing mutual exclusion to some shared resource
* a shared variable that can be either locaked or unlocked. 0 is unlocked, other value is locked
* attempt to acquire a locked mutex put the thread to blocked state
* Simple to implement in user space with TSL or XCHG
+ no busy waiting
+ fast as completely implemented in user space

###### Futexes: fast user space mutex
#card
* Implemented in linux
* Basica locking, but avoids dropping in kernel unless really has to
* Has two parts, kernel service and user lib:
	* Kernel service provides wait queue allowing processes to wait on lock, requires expicit unblock from kernel
	* Need syscall to put on wait queue
	* When no contention, futex works completely in user space by using a user space lock variable

###### condition variables
#card
* allow threads to block due to some condition not being met, pthread_cond_wait/signal
* always used with mutex. e.g. one thread lock mutex and wait on conditional variable


Notes: 137 - 173


# Questions
1. threads share address space but has its own stack. How does it actually look? Do you allocate the stack when you create new threads, otherwise how to prevent from overlapping?

2. [Answered?] how does kernel enforce multiprogramming?
By using clock interrupts?

3. How does interrupt vector actually work?
In p95, the information pushed onto the stack by the interrupt is removed and stack pointer is set to point to a temporary stack used by the process handler. Why clean the stack?3. How does interrupt vector actually work?
In p95, the information pushed onto the stack by the interrupt is removed and stack pointer is set to point to a temporary stack used by the process handler. Why clean the stack?3. How does interrupt vector actually work?
In p95, the information pushed onto the stack by the interrupt is removed and stack pointer is set to point to a temporary stack used by the process handler. Why clean the stack?