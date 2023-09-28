---
cards-deck: tech::assembly
---

# io_in/out
#card
in: read from device to cpu
out: write from cpu to device

# cli/sti
#card
clear interrupt flag
set interrupt flag

# DB
#card
define byte, 文件寫入1byte

# RESB
#card
reserve byte (create new variable/array)

# ORG
#card
程序裝載內存地址

# AX
#card
accumulator

# CX
#card
counter

# DX
#card
data

# BX
#card
base

# SP
#card
stack pointer. Points to first unused location. SS:SP refer to current position.

# BP
#card
base pointer, reference parameter variables in subroutine. e.g. Input parameter can be accessed via Reg[BP]-4/-8/..., local variables is Reg[BP] +0/+4/..

# SI
#card
source index for string operations

# DI
#card
destination index for string operations

# AL; AH
#card
AL: 0-7 bit
AH: 8-15 bit

# ES
#card
extra segment

# CS
#card
code segment, contains all instructions to be executed

# SS
#card
stack segment, contains data and return address of procedures or subroutines.

# DS
#card
data segment, store starting address of data segment

# \[SI\]
#card
MOV AL, \[SI\]: assign mem\[SI\] to AL

# BYTE\[\]
#card
MOV BYTE[678], 123: Store 123 at mem[678] in one byte

# word
#card
2 bytes

# dword
#card
4 bytes

# INT
#card
soft interrupt

# HLT
#card
stop cpu, idle

# \[ES:BX\]
#card
mem\[ES x 16 + BX\]

# \[1234\]
#card
equals \[DS:1234\] where DS is the default seg register

# EQU
#card
define const

# flipflop, latch
#card
single bit register

# register
#card
serial or parallel combination of flipflops

# von neumann model
#card
cpu::datapath + control FSM
memory::array of words
input/output: disk, keyboard, mouse, etc

# RISC
#card
reduced instruction set computer, reduced means most instructions only access registers (no direct memory access besides load,store)

# load-store architecture
#card
