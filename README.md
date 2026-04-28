# 🔷 RV32I RISC-V Processor | Complete RTL to GDSII Flow (VLSI Project)

## 📌 Overview

This project demonstrates a **complete VLSI design flow (RTL → GDSII)** for a custom **32-bit RV32I RISC-V Processor** implementing the base integer instruction set architecture.

The processor was designed from scratch starting from **RTL coding**, followed by **functional verification**, **logic synthesis**, **formal verification**, **static timing analysis**, and **physical design** using industry-standard EDA tools.

The project is divided into two major parts:

- **Part 1:** RTL Design, Functional Verification, Synthesis, STA, Formal Verification  
- **Part 2:** Physical Design (Floorplanning → Placement → CTS → Routing → GDSII)

The main goal of this project is to understand complete ASIC design methodology and optimize **Power, Performance, and Area (PPA)**.

---

## 📂 Repository Structure

riscv_project/
├── rtl/
├── tb/
├── verification/
├── synthesis/
├── sta/
├── physical_design/
├── docs/
├── waves/
├── reports/
└── scripts/
# 🔹 PART 1: RTL DESIGN & PROCESSOR IMPLEMENTATION

## 1️⃣ Design Specification

A custom **32-bit RISC-V RV32I Processor** capable of executing integer arithmetic, logic, memory, and branch instructions.

### Inputs

- `clk` : system clock  
- `rst` : active reset  
- `instruction_in` : instruction memory input  
- `data_in` : data memory read input  

### Outputs

- `pc_out` : current program counter  
- `alu_result` : ALU computation output  
- `data_out` : data memory write output  
- `writeback_data` : data written to register file  

---

## 2️⃣ Key Features

- 32-bit datapath architecture  
- RV32I instruction support  
- Register file with 32 registers  
- Modular RTL hierarchy  
- Separate ALU and Control Unit  
- Immediate generation logic  
- Branch / jump support  
- Memory read/write interface  
- Scalable architecture for future pipeline upgrade  

---

## 3️⃣ Instruction Set Implemented

### Arithmetic Instructions

- ADD  
- SUB  
- ADDI  
- SLT  
- SLTI  

### Logical Instructions

- AND  
- OR  
- XOR  
- ANDI  
- ORI  
- XORI  

### Shift Instructions

- SLL  
- SRL  
- SRA  
- SLLI  
- SRLI  
- SRAI  

### Memory Instructions

- LW  
- SW  

### Control Flow Instructions

- BEQ  
- BNE  
- BLT  
- BGE  
- JAL  
- JALR  

---

## 4️⃣ RTL Modules Designed

- `pc.v` → Program Counter  
- `imem.v` → Instruction Memory  
- `decoder.v` → Instruction Decode Unit  
- `control_unit.v` → Main Control Logic  
- `regfile.v` → Register File  
- `alu.v` → Arithmetic Logic Unit  
- `imm_gen.v` → Immediate Generator  
- `dmem.v` → Data Memory  
- `branch_unit.v` → Branch Decision Logic  
- `cpu_top.v` → Top Integration Module  

---

## 5️⃣ RTL Architecture

The processor follows a structured datapath/control path methodology.

### Data Path Includes

- PC update path  
- Register read path  
- ALU compute path  
- Memory access path  
- Writeback path  

### Control Path Includes

- Opcode decode  
- ALU control signals  
- Branch enable  
- Memory enable  
- Register write enable  
