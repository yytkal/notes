---
cards-deck: tech::assembly
---

# io_in/out
#card
in: read from device to cpu
out: write from cpu to device
^1610437447901

# cli/sti
#card
clear interrupt flag
set interrupt flag
^1610437447908

# DB
#card
define byte, 文件寫入1byte
^1610437447917

# RESB
#card
reserve byte (create new variable/array)
^1610437447925

# ORG
#card
程序裝載內存地址
^1610437447931

# AX
#card
accumulator register
^1610437447938

# CX
#card
counter
^1610437447946

# DX
#card
data
^1610437447956

# BX
#card
base index, general purpose
^1610437447964

# SP
#card
stack pointer
^1610437447974

# BP
#card
base, 基址寄存器
^1610437447982

# SI
#card
source index
^1610437447989

# DI
#card
destination index
^1610437447997

# AL; AH
#card
AL: 0-7 bit
AH: 8-15 bit
^1610437448004

# ES
#card
extra segment
^1610437448012

# CS
#card
code segment
^1610437448020

# SS
#card
stack segment
^1610437448028

# DS
#card
data segment
^1610437448037

# \[SI\]
#card
MOV AL, \[SI\]: assign mem\[SI\] to AL
^1610437448045

# BYTE\[\]
#card
MOV BYTE[678], 123: Store 123 at mem[678] in one byte
^1610437448053

# word
#card
2 bytes
^1610437448060

# dword
#card
4 bytes
^1610437448067

# INT
#card
soft interrupt
^1610437448073

# HLT
#card
stop cpu, idle
^1610437448080

# \[ES:BX\]
#card
mem\[ES x 16 + BX\]
^1610437448089

# \[1234\]
#card
equals \[DS:1234\] where DS is the default seg register
^1610437448096

# EQU
#card
define const
^1610437448105

# flipflop, latch
#card
single bit register
^1610437448114

# register
#card
serial or parallel combination of flipflops
^1610437448123

# von neumann model
#card
cpu::datapath + control FSM
memory::array of words
input/output: disk, keyboard, mouse, etc
^1610437448130

# RISC
#card
reduced instruction set computer, reduced means most instructions only access registers (no direct memory access besides load,store)
^1610437448137

# load-store architecture
#card
load into register -> compute -> store to memory^1610437448145
