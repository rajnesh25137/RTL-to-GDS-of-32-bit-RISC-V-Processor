# RTL-to-GDS-of-32-bit-RISC-V-Processor
# 🔷 RV32I RISC-V Processor | Complete RTL to GDSII Flow (VLSI Project)

## 📌 Overview
This project demonstrates a **complete VLSI design flow (RTL → GDSII)** for a custom **32-bit RV32I RISC-V Processor** implementing the base integer instruction set architecture (**RV32I ISA**).

The processor was designed from scratch starting from **microarchitecture planning**, followed by **RTL implementation**, **functional verification**, **logic synthesis**, **formal verification**, **static timing analysis**, and **physical design** using industry-standard EDA tools.

The project is divided into two major parts:

- **Part 1:** RTL Design, Functional Verification, Synthesis, STA, Formal Verification  
- **Part 2:** Physical Design (Floorplanning → Placement → CTS → Routing → GDSII)

The primary goal of this project is to gain practical exposure to complete **ASIC design methodology**, understand **Power, Performance, Area (PPA)** trade-offs, and build a strong processor-based semiconductor project.

---

## 📂 Repository Structure
riscv_project/
│── rtl/                  # RTL source code of processor modules
│── tb/                   # Testbenches for simulation
│── verification/         # cocotb tests, assertions, regressions
│── synthesis/            # Cadence Genus scripts/reports
│── sta/                  # Tempus timing reports
│── physical_design/      # Innovus scripts and outputs
│── docs/                 # Architecture diagrams / reports
│── waves/                # Simulation waveform files
│── reports/              # Final summaries / metrics
│── scripts/              # TCL / shell automation scripts

🔹 PART 1: RTL DESIGN & PROCESSOR IMPLEMENTATION
1️⃣ Design Specification

A custom 32-bit RISC-V RV32I Processor capable of executing integer arithmetic, logic, memory, and branch instructions.

Inputs
clk : system clock
rst : active reset
instruction_in : instruction memory input
data_in : data memory read input
Outputs
pc_out : current program counter
alu_result : ALU computation output
data_out : data memory write output
writeback_data : data written to register file
2️⃣ Key Features
32-bit datapath architecture
RV32I instruction support
Register file with 32 registers
Modular RTL hierarchy
Separate ALU and Control Unit
Immediate generation logic
Branch / jump support
Memory read/write interface
Scalable architecture for future pipeline upgrade
3️⃣ Instruction Set Implemented
Arithmetic Instructions
ADD
SUB
ADDI
SLT
SLTI
Logical Instructions
AND
OR
XOR
ANDI
ORI
XORI
Shift Instructions
SLL
SRL
SRA
SLLI
SRLI
SRAI
Memory Instructions
LW
SW
Control Flow Instructions
BEQ
BNE
BLT
BGE
JAL
JALR
4️⃣ RTL Modules Designed
pc.v → Program Counter
imem.v → Instruction Memory
decoder.v → Instruction Decode Unit
control_unit.v → Main Control Logic
regfile.v → Register File
alu.v → Arithmetic Logic Unit
imm_gen.v → Immediate Generator
dmem.v → Data Memory
branch_unit.v → Branch Decision Logic
cpu_top.v → Top Integration Module
5️⃣ RTL Architecture

The processor follows a structured datapath/control path methodology.

Data Path Includes:
PC update path
Register read path
ALU compute path
Memory access path
Writeback path
Control Path Includes:
Opcode decode
ALU control signals
Branch enable
Memory enable
Register write enable
🔹 PART 2: FUNCTIONAL VERIFICATION
🎯 Objective

To verify functional correctness of the processor across all instruction classes and corner cases.

1️⃣ Verification Methodology
Directed testbenches
Self-checking verification environment
Assertions
Automated regressions
Waveform debugging
Golden reference comparison
2️⃣ Verification Tools Used
Verilator
Icarus Verilog
GTKWave
Python
cocotb
Spike ISA Simulator
3️⃣ Directed Tests Performed
Arithmetic Tests
ADD correctness
SUB correctness
Signed comparison tests
Logic Tests
AND / OR / XOR verification
Immediate logic operations
Memory Tests
Load word verification
Store word verification
Address alignment checks
Branch Tests
Branch taken
Branch not taken
Jump target validation
Register File Tests
Read-after-write check
x0 constant zero verification
4️⃣ Assertions Implemented
x0 register always zero
Program counter remains aligned
No invalid memory write during reset
Proper control signal activation
Valid branch update sequencing
5️⃣ Golden Reference Validation

Processor behavior compared with Spike RISC-V ISA Simulator.

Compared Parameters
Register values
Program Counter flow
Instruction execution results
Memory transactions
6️⃣ Regression Flow

Multiple tests executed automatically using Python/cocotb.

Outputs
PASS / FAIL summary
Execution logs
Error traces
Functional confidence improvement
🔹 PART 3: SYNTHESIS FLOW
Tool Used
Cadence Genus
Inputs
RTL Verilog files
Timing constraints (.sdc)
Standard cell libraries (.lib)
Synthesis Goals
Area optimization
Timing closure
Balanced PPA targets
Clean netlist generation
Outputs Generated
Gate-level netlist
Area report
Power report
Timing report
Constraint summary
Learnings
Constraint-driven synthesis
Combinational logic optimization
Sequential cell mapping
Area vs timing trade-offs
🔹 PART 4: FORMAL VERIFICATION
Tool Used
Cadence Conformal
Objective

Verify equivalence between:

RTL Design  =  Synthesized Gate Netlist

Ensures no functional mismatch introduced during synthesis.

Benefits
Logical correctness confidence
Netlist signoff readiness
Industry-standard verification methodology
🔹 PART 5: STATIC TIMING ANALYSIS (STA)
Tool Used
Cadence Tempus
Timing Checks Performed
Setup analysis
Hold analysis
Critical path extraction
Slack measurement
Clock path timing checks
Learnings
Timing closure methodology
Setup/Hold understanding
Delay path optimization
Constraint debugging
🔹 PART 6: PHYSICAL DESIGN (RTL → GDSII)
Tool Used
Cadence Innovus
Objective

Implement backend flow and generate final manufacturable layout database.

1️⃣ Floorplanning
Core area definition
Utilization planning
Macro placement planning
IO pin planning
Power ring generation
Observations
Lower utilization improves routability
Higher utilization reduces die area
2️⃣ Placement
Standard cell placement
Wirelength optimization
Congestion reduction
Timing-driven placement
Effects
Improved path delay
Better density balance
3️⃣ Clock Tree Synthesis (CTS)
Clock buffer insertion
Clock skew balancing
Hold fixing buffers
Effects
Reduced skew
Better hold timing
Stable clock distribution
4️⃣ Routing
Global routing
Detailed routing
Via optimization
DRC cleanup
Effects
Final connectivity completion
Timing improvement after route
5️⃣ Final Outputs
Routed design database
DEF / GDSII files
Timing reports
Power reports
Utilization summary
🔹 PART 7: PPA ANALYSIS
Power
Leakage Power
Internal Power
Switching Power
Performance
Critical path delay
Setup/Hold closure
Frequency potential
Area
Standard cell area
Core utilization
Density optimization
🛠️ Tools & Technologies
RTL / Verification
Verilog HDL
SystemVerilog
Verilator
Icarus Verilog
GTKWave
Python
cocotb
Spike ISA Simulator
ASIC Design Flow
Cadence Genus
Cadence Conformal
Cadence Tempus
Cadence Innovus
FPGA Validation
Vivado
Scripting
TCL
Bash
📊 Key Learnings
Complete Processor RTL to GDSII Flow
Processor microarchitecture implementation
Functional verification methodology
Assertions and regression testing
Synthesis and optimization techniques
Formal verification flow
Static timing closure
Floorplanning, Placement, CTS, Routing
Power, Performance, Area trade-offs
Real-world ASIC design methodology
🚀 How to Run
RTL Lint
verilator --lint-only rtl/*.v
RTL Simulation
iverilog -o sim rtl/*.v tb/*.v
vvp sim
Waveform Debug
gtkwave dump.vcd
👨‍💻 Author

Rajnesh Kumar
M.Tech VLSI
