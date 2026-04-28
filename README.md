🔷 RV32I RISC-V Processor: Complete RTL-to-GDSII Flow

📌 Project Overview

This project demonstrates a complete VLSI design flow (RTL → GDSII) for a custom 32-bit RV32I RISC-V Processor. The design implements the base integer instruction set architecture (RV32I ISA) and was taken through the full ASIC design methodology.

The primary goal was to gain practical exposure to semiconductor industry workflows, understanding Power, Performance, and Area (PPA) trade-offs using industry-standard EDA tools.

📂 Repository Structure

riscv_project/
├── rtl/                 # RTL source code of processor modules
├── tb/                  # Testbenches for simulation
├── verification/        # cocotb tests, assertions, regressions
├── synthesis/           # Cadence Genus scripts/reports
├── sta/                 # Tempus timing reports
├── physical_design/     # Innovus scripts and GDSII outputs
├── docs/                # Architecture diagrams / reports
├── waves/               # Simulation waveform files
├── reports/             # Final summaries / metrics
└── scripts/             # TCL / shell automation scripts


🏗️ Part 1: RTL Design & Implementation

The processor follows a structured datapath and control path methodology.

1. Specifications

ISA: RISC-V RV32I (Base Integer)

Architecture: 32-bit single-cycle (Modular for future pipelining)

Register File: 32 registers (x0 to x31)

Interfaces: Separate Instruction and Data Memory interfaces

2. Implemented Instructions

Arithmetic: ADD, SUB, ADDI, SLT, SLTI

Logical: AND, OR, XOR, ANDI, ORI, XORI

Shift: SLL, SRL, SRA, SLLI, SRLI, SRAI

Memory: LW, SW

Control Flow: BEQ, BNE, BLT, BGE, JAL, JALR

3. RTL Modules

Module

Function

pc.v

Program Counter

decoder.v

Instruction Decode Unit

regfile.v

32-entry Register File

alu.v

Arithmetic Logic Unit

imm_gen.v

Immediate Value Generator

branch_unit.v

Branch Decision Logic

cpu_top.v

Top-level SoC Integration

🧪 Part 2: Functional Verification

A self-checking verification environment was built to ensure $100\%$ ISA compliance.

Methodology: Directed Tests & Random Regressions.

Reference Model: Behavior compared against the Spike ISA Simulator.

Tools: Verilator, Icarus Verilog, cocotb (Python-based).

Key Assertions:

Register x0 must always remain zero.

PC must remain word-aligned ($4$-byte).

No memory writes allowed during active-low Reset.

⚡ Part 3: Synthesis & Sign-off

Logic Synthesis: Performed using Cadence Genus to map RTL to standard cells.

Formal Verification: Used Cadence Conformal (LEC) to verify RTL vs. Gate-level netlist equivalence.

Static Timing Analysis (STA): Performed using Cadence Tempus to ensure zero Setup/Hold violations.

🎨 Part 4: Physical Design (Backend)

The backend flow was executed in Cadence Innovus to generate the final GDSII layout.

Floorplanning: Core utilization planning, IO pin placement, and Power Grid (PG) creation.

Placement: Timing-driven placement of standard cells.

CTS (Clock Tree Synthesis): Balancing clock skew and minimizing insertion delay.

Routing: Global and detailed routing with DRC/LVS closure.

GDSII Generation: Exporting the final manufacturable database.

📊 PPA Metrics & Learnings

Area: Optimized core utilization for minimal die size.

Power: Analyzed leakage vs. dynamic power consumption.

Timing: Closed timing at target frequency.

Key Learning: Hands-on experience with the complete RTL-to-GDSII flow.

🛠️ Tools & Technologies

RTL/Verif: Verilog, cocotb, Spike, GTKWave

EDA Suite: Cadence Genus, Innovus, Tempus, Conformal

Scripting: TCL, Python, Bash

🚀 How to Run

Linting

verilator --lint-only rtl/*.v


Simulation

iverilog -o sim rtl/*.v tb/*.v
vvp sim


View Waveforms

gtkwave dump.vcd


👨‍💻 Author

Rajnesh Kumar M.Tech in VLSI Design LinkedIn | Portfolio

Note: This project was developed as part of a VLSI Design project to master the ASIC design flow.
