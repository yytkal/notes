---
cards-deck: tech::architecture
---

# 5-stage pipeline
IF: Instruction Fetch stage. Maintains PC, fetch instructions.
RF:  Register File stage: Read source operands from register file.
ALU: ALU stage.
MEM: Memory stage. If LD op, use ALU results as address and pass memory data.
WB: Write-back stage. Write results back to register file.

# Pipeline Hazard
Pipelining tries to overlap the executation of multiple instructions, but depends on earlier instruction.
- Data value -> data hazard
- program counter -> control hazard (branches, jumps, exceptions)