# Pipeline MIPS32 Processor in Verilog
A 5-Stage Pipelined Implementation of the MIPS32 Architecture*

# Overview
This project implements a fully functional 5-stage pipelined MIPS32 processor in Verilog, designed for FPGA synthesis and academic exploration. The processor supports a subset of the MIPS instruction set, including arithmetic, memory access, and control-flow operations, while handling pipeline hazards through intelligent stalling and forwarding mechanisms.

# Key Features
# 1. Pipeline Architecture
5-Stage Design: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), Memory Access (MEM), and Write Back (WB).

Dual-Clock Synchronization: Uses clk1 and clk2 for phase-aligned stage transitions, mimicking real-world pipelining constraints.

Supported Instructions:

Arithmetic/Logical: ADD, SUB, AND, OR, SLT, MUL (R-type)

Immediate Operations: ADDI, SUBI, SLTI (I-type)

Memory Access: LW (load), SW (store)

Control Flow: BEQZ, BNEQZ (conditional branches)

# 2. Hazard Handling
Load-Use Hazard Detection: Automatically inserts pipeline stalls (bubbles) when a dependent instruction follows a LW.

Branch Prediction: Static "not taken" approach with flush-and-refetch on misprediction (handled via TAKEN_BRANCH flag).

Register File Bypassing: Avoids write-after-read (WAR) hazards by forwarding results directly from EX/MEM/WB stages.

# 3. Memory & Register File
32x32 Register Bank: Zero register ($0) hardwired to 0, with edge-case handling for writes.

1024x32 Data Memory: Byte-addressable memory for LW/SW operations, with alignment checks.

Instruction Memory: Pre-loaded with test programs (simulated as a read-only array).

# 4. Testing & Scalability
Modular Design: Separates pipeline stages into distinct procedural blocks (always @(posedge clk)) for easy debugging.

