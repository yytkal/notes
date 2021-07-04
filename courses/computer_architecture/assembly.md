---
cards-deck: tech::architecture
---

# high-level FSM
#card
each state are more than simple logic levels
^1610929295894

# byte addresses
#card
memory addresses are byte addressed.
e.g. instructions are 32-bit words, consecutive instruction addresses differ by 4.
^1610929295903

# 32/64bit architecture
#card
32/64 bit registers and 32/64 bit datapath
^1610929295910

# type of instructions
#card
ALU, Load & Store, Branch
^1610929295919


# assembler
#card
reads text file of asm program and produce 32-bit words to be loaded into memory
^1610929295926

# UASM
microassembler

# little-endian
#card
least-significant bytes stored at lowest memory address

# .symbol
#card
the next byte address to be filled in main memory
can read, write or leave empty space
e.g:
.=0x100 // set memory address to 0x100
k=. // put memory location into k
.=.+16 // skip 16 bytes

# .aligh 4
#card
ensure instruction start on word boundary (address = 0 mod 4)

# pseudo instructions
#card
provide a larger instruction set, although underneath using implemented via small instruction set.

# compiler
analysis(front)::generate intermediate representation: lexical analysis -> syntax analysis -> semantics analysis -> generate IR
synthesis(backend)::optimize and translate to code for target ISA: optimize IR -> Generate ASM

# linkage pointer
#card
call the register holding the return address

# activation record/stack frame
#card
block of storage for each active procedure call


# stack discipline
#card
use stack at any time, but leave it as you found it

# stack
## convention
reverse order::arguments are pushed to stack in reverse order. First argument is last to be pushed to stack.
callee saves::callee guarantees that all register values will be preserved across the procedure call.

# CPU design tradeoffs
* max performance
MIPS::million instructions per second
"iron law" of performance::time/program = instructions/program * cycles/instructions * time/cycle; perf = 1/time
* min cost
* best price perf

# register file
#card
array of processor registers in CPU

# control signal
## register file
WA::write address
WE::write enable
WD::write data
## ALU
ALUFN::ALU function
## Memory
MWR/MWE::memory write enable, write WD into selected memory location by end of the cycle
MOE::memory output enable

# Memory Tech
Register::a few KB/20ps (processor datapath)
SRAM(cache)::10KB-10MB/1-10ns/~$1000/GB
DRAM::~10GB/80ns/~$10/GB

# DRAM vs SRAM
- More compact due to circuitry
- Initial row access is slow, but subsequent is close to SRAM

# Flash
- Density similar to DRAM
- NOR flash read 10s of nanosec
- NAND flash read 10s of microsec

Compiler decides register & ram
Circuity manages cache & DRAM

# Cache
- TAG (hash), valid, data
- block size: size of data field. usually 64 bytes
- SRAM
- Directed Mapped Cache
  - hash function: mod
  - Potentially have conflict misses. (multiple addresses mapped to same cache line)
- Fully Associated Cache
  - hash function: memory address
  - no conflict misses, but expensive
- N-Way Set-Associative Cache
  - N direct-mapped caches in parallel
