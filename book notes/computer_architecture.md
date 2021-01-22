
---
cards-deck: tech::architecture
---

Chapter 1 Page 100


# Responsiveness and predictability
#card
key characteristics for media applications.
real-time performance requirement::a segment of the application has an absolute maximum execution time.

# Soft real time
#card
The average time for a particular task is constrained as well as the number of instances when some maximum time is exceeded. It is possible to occasionally miss the time constraint on an event, as long as not too many are missed.

# WSC
#card
warehouse-scale computers, clusters: WSC use redundant inexpensive component as building blocks, relying on a software layer to catch and isolate many failures that will happen with computing at this scale.

# Application Parallelism
DLP::Data-level, Data items can be operated at the same time.
TLP::Task-level, Task of work can operate independently and largely in parallel.

# Hardware Parallelism
Instruction-level Parallelism::Exploits DLP with compiler help using ideas of pipelining and at medium level using speculative execution[^1].
Vector Architecture and Graphics Processing Unit::Exploits DLP by applying single instruction to a collection of data in parallel.
Thread-level Parallelism::Exploits either DLP or TLP in tightly coupled hardware model that allows for interaction among parallel threads.
Request-level Parallelism::Exploits parallelism among largely decoupled tasks specified by programmers or operating systems.

# Hardware Implementations
SISD::single instruction stream, single data stream, Uniprocessor, standard sequential computer, but can still use instruction-level parallelism.
SIMD::Same instruction executed by multiple processors using different data stream. DLP
MISD::No commercial multi processor has been built
MIMD::TLM. More flexible than SIMD, more generally applicable, but more expansive. MIMD can also exploit DLP, but overhead is generally higher than SIMD.

# ISA Instruction-level Architecture
#card
programmer visible instruction set. Boundary between software and hardware.

## Class
Nearly all ISAs today are general-purpose register architecture, where operands are either registers or memory locations. All recent ISAs are load-store ISA.
register-memory::80x86
load-store::ARM, MIPS, can only access memory with load, store
Memory-memory, not existing today

## Instruction Size
computers with fewer alternatives simplify the compiler’s task since there are fewer decisions for the compiler to make
Computers with a wide variety of flexible instruction formats reduce the number of bits required to encode the program
The number of registers also affects the instruction size since you need log2 (number of registers) for each register specifier in an instruction


## Memory Addressing
#card
Virtually all servers and desktops use byte addressing to access memory operands. Some required objects must be aligned. An access to an object of size s byte at byte address A is aligned if A mod s = 0. Access are generally faster if aligned.

## Addressing modes
#card
Addressing modes specify the address of a memory object, e.g. register, immediate (constants) and displacement.

## Types and size of operands
#card
8/16/32/64 bit. 80x86 also support 80-bit extended double precision.

### Operations
#card
Categories: data transfer; arithmetic logical, control, floating point.
flow instructions: conditional branches, unconditional jumps, procedure calls and returns. PC-relative addressing.
ISA encoding: Fixed length, variable length. All ARM, MIPS are 32 bits long. 80x86 is variable length. Program compiled for 80x86 is usually smaller than compiled for MIPS.

# Microarchitecture, organization
high-level aspects of computer design, e.g. memory system, memory interconnect and design of internal processor. (different implementation of same ISA)

# Hardware
refers to the specifics of a computer, including the detailed logic design and packaging technology of a computer. Often a line of computers contains computers of identical ISA, nearly identical organization but differ in detailed hardware implementation.

# Tech trends
Integrated circuit logic::Transistor density increases by about 35% per year. Increases in die size 10%-20% per year. A growth rate in transistor count on a chip 40%-55% per year.
Semiconductor DRAM::(dynamic random-access memory): Capacity per DRAM chip has increased by 25% to 40% per year. Foundation of main memory.
Semiconductor Flash::(electrically erasable programmable read-only memory): Nonvolatile semiconductor memory, standard storage device in PMDs. Capacity per chip increased by 50% to 60% per year. 15 to 20 times cheaper per bit than DRAM. SSD?
Magnetic disk::15-25x cheaper per bit than Flash.
Network::depends on performance of switches and transmission system.
Performance Trends::Bandwidth over Latency: Performance is the primary differentiator for microprocessors and networks. Rule of thumb, bandwidth grows by at least the square of improvement in latency.

# Scaling of Transistor performance and wires
Feature Size::Integrated circuit processes are characterized by feature size, which is minimum size of a transistor or a wire in either x or y dimension.

Density of transistors increases quadratically with a linear decrease in feature size. To a first approximation, transistor performance improves linearly with decreasing feature size.

Although transistors improve in performance with decreased feature size, wires do not, becoming a major design limitation for large integrated circuits.

Trends in power and energy::Power is the biggest challenge facing computer design. Power must be distributed around the chip. power is dissipated as heat and must be removed.

# Energy and Power within Microprocessor
Energy ~ Capacitive Load * Voltage^2
Energy Pulse ~ ½ * Capacitive Load * Voltage ^2
Power ~ ½ * Capacitive Load * Voltage ^2 * Frequency
For a fixed task, slower clock rate reduce power not energy.
Clock frequency growth to slow down if we can’t reduce voltage or increase power per chip.
Distributing the power, removing the heat and preventing hot spots have become increasingly difficult challenges.
Power is now the major constraint.

# Techniques to improve energy efficiency
#card
1. Do nothing well. Microprocessors today turn off clock of inactive modules to save energy.
2. Dynamic Voltage-Frequency Scaling DVFS. Modern microprocessors typically offer a few clock frequencies and voltages in which to operate that use lower power.
3. Design for typical case.Relying on “emergency slowdown” to avoid overheating.
4. Overclocking. Intel started offering Turbo mode, where chip decided that it is safe to run at a higher clock rate for a short time possibly on a few cores until temperature starts to rise.
5. Race-to-half. Use a faster, less energy efficient processor to allow the rest of the system to go into sleep mode.

# Module Reliability
#card
a measure of the continuous service accomplishment (or, equivalently, of the time to failure) from a reference initial instant.  
The primary way to cope with failure is redundancy, either in time (repeat the operation to see if it still is erroneous) or in resources (have other components to take over from the one that failed)


the mean time to failure (MTTF)::is a reliability measure
FIT (for failures in time)::The reciprocal of MTTF is a rate of failures, generally reported as failures per billion hours of operation
Service interruption::measured as mean time to repair (MTTR)
Mean time between failures (MTBF)::is simply the sum of MTTF + MTTR
Module availability::is a measure of the service accomplishment with respect to the alternation between the two states of accomplishment and interruption. Availability::MTTF / MTBF


# Wall-clock time
#card
response time, elapsed time, latency to complete a task

# CPU time
#card
the time the processor is computing, not including the time waiting for I/O or running other program

# Benchmark
The best choice of benchmarks to measure performance is real applications
# common pitfalls
#card
Kernels::which are small, key pieces of real applications
Toy programs::which are 100-line programs from beginning programming assignments, such as quicksort
Synthetic benchmarks::which are fake programs invented to try to match the profile and behavior of real applications, such as Dhrystone
(Compiler) Flags::One way to improve the performance of a benchmark has been with benchmark specific flags; these flags often caused transformations that would be illegal on many programs or would slow down performance on others
Source code modification::In addition to the question of compiler flags, another question is whether source code modifications are allowed.
benchmark suites::collections of benchmark applications are a popular measure of performance of processors with a variety of applications

# SPEC
#card
Standard Performance Evaluation Corporation, One of the most successful attempts to create standardized benchmark application suites

SPEC benchmarks are real programs modified to be portable and to minimize the effect of I/O on performance.

## The integer benchmarks
#card
vary from part of a C compiler to a chess program to a quantum computer simulation.

## The floatingpoint benchmarks
#card
include structured grid codes for finite element modeling, particle method codes for molecular dynamics, and sparse linear algebra codes for fluid dynamics.

## SPECrate
#card
a measure of request-level parallelism, a simple throughput benchmark where the processing rate of a multiprocessor can be measured by running multiple copies (usually as many as there are processors) of each SPEC CPU benchmark and converting the CPU time into a rate.

## SPECSFS
#card
a file server benchmark. a benchmark for measuring NFS (Network File System) performance using a script of file server requests; it tests the performance of the I/O system (both disk and network I/O) as well as the processor. is a throughput-oriented benchmark but with important response time requirements.

## SPECWeb
#card
Web server benchmark.  simulates multiple clients requesting both static and dynamic pages from a server, as well as clients posting data to the server

## SPECjbb
#card
measures server performance for Web applications written in Java.

## SPECvirt_sc2010
#card
evaluates end-to-end performance of virtualized datacenter servers, including hardware, the virtual machine layer, and the virtualized guest operating system.

# Transaction-processing (TP) benchmarks
#card
measure the ability of a system to handle transactions that consist of database accesses and updates.

## Transaction Processing Council (TPC)
#card
to try to create realistic and fair benchmarks for TP
TPC-C::simulates a complex query environment. All the TPC benchmarks measure performance in transactions per second. In addition, they include a response time requirement, so that throughput performance is measured only when the response time limit is met.
TPC-H::models ad hoc decision support—the queries are unrelated and knowledge of past queries cannot be used to optimize future queries.
TPC-E::is a new On-Line Transaction Processing (OLTP) workload that simulates a brokerage firm’s customer accounts.
TPC Energy::which adds energy metrics to all the existing TPC benchmarks.


The guiding principle of reporting performance measurements should be **reproducibility**—list everything another experimenter would need to duplicate the results.

**summarize the performance** results of the suite
*   Average: compare the arithmetic means of the execution times of the programs in the suite.
*   Weighted Average: add a weighting factor to each benchmark and use the weighted arithmetic mean as the single number to summarize performance.
*   SPECratio: normalize execution times to a reference computer by dividing the time on the reference computer by the time on the computer being rated, yielding a ratio proportional to performance. Because a SPECRatio is a ratio rather than an absolute execution time, the mean must be computed using the geometric mean.
*   GeoMean: the motivations to use the geometric mean are substantial, especially when we use performance ratios to make comparisons.  

# Principles of Computer Design
Take Advantage of Parallelism::is one of the most important methods for improving performance.
Principle of Locality::Programs tend to reuse data and instructions they have used recently. A widely held rule of thumb is that a program spends 90% of its execution time in only 10% of the code.
Temporal locality::states that recently accessed items are likely to be accessed in the near future.
Spatial locality::says that items whose addresses are near one another tend to be referenced close together in time.
Focus on the Common Case::In making a design trade-off, favor the frequent case over the infrequent case.  the frequent case is often simpler and can be done faster than the infrequent case.

# The Processor Performance Equation
Essentially all computers are constructed using a clock running at a constant rate.
Processor performance is dependent upon three characteristics: clock cycle (or rate), clock cycles per instruction, and instruction count
Ticks, cycles::these discrete time events. Computer designers refer to the time of a clock period by its duration (e.g., 1 ns) or by its rate (e.g., 1 GHz).
CPU time::CPU time = CPU clock cycles for a program * Clock cycle time = CPU clock cycles for a program / Clock Rate
IC::instruction path length or instruction count (IC)
CPI::clock cycles per instruction (CPI)
IPC::instructions per clock (IPC)
CPI::CPU clock cycles for a program / Instruction count


## Pitfalls

### Multiprocessors are a silver bullet.
performance is now a programmer’s burden, increasing performance with each generation of technology—is now up to programmers.

### Falling prey to Amdahl’s heartbreaking law
Only when the overall speedup is disappointing do we recall that we should have measured first before we spent so much effort enhancing it!

### A single point of failure

### Hardware enhancements that increase performance improve energy efficiency or are at worst energy neutral.

### Benchmarks remain valid indefinitely
A big factor influencing the usefulness of a benchmark is its ability to resist “benchmark engineering” or “benchmarketing.”

## Peak performance tracks observed performance
The only universally true definition of peak performance is “the performance level a computer is guaranteed not to exceed

## Fault detection can lower availability
In processors that try to aggressively exploit instruction-level parallelism, not all the operations are needed for correct execution of the program.


Appendix A - P.523

# Desktop computing
#card
performance of programs with int and fp data types, with little regard for program size.

# Server computing
#card
primarily for databases, file server, web applications and some time-sharing applications for many users. Fp performance is far less important than int.

# Personal mobile devices and embedded applications
#card
value cost and energy. Code size is important due to less memory and energy. Some classes of instructions (e.g. fp) may be optional to reduce chip costs.


# Speculative execution
#card
an optimization technique where a computer system performs some task that may not be needed. Work is done before it is known whether it is actually needed, so as to prevent a delay that would have to be incurred by doing the work after it is known that it is needed.
