---
cards-deck: tech::architecture
---

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
- AMAT = HitTime + MissRatio * MissPenalty
- TAG (hash), valid, dirty, data
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
