<div align="center">

# 🚀 RV32I Single-Cycle Processor Core

[![RISC-V](https://img.shields.io/badge/RISC--V-RV32I-blue.svg)](https://riscv.org/)
[![Language](https://img.shields.io/badge/Language-SystemVerilog-brightgreen.svg)]()
[![PDK](https://img.shields.io/badge/PDK-SkyWater%20130nm-orange.svg)]()

*A 32-bit single-cycle RISC-V CPU core designed from scratch, optimized for digital IC design flows.*

</div>

## 📖 Overview

This project implements a single-cycle processor architecture based on the **RISC-V (RV32I)** Base Integer Instruction Set. It serves as a comprehensive educational and practical reference for RTL modeling, functional verification, and logic synthesis within a modern digital design flow.

### ✨ Key Features
* **Architecture:** 32-bit Single-Cycle Datapath.
* **ISA Support:** Standard RV32I Base Integer Instruction Set.
* **Modularity:** Cleanly separated functional units (ALU, Register File, Control Unit, ImmGen, etc.).
* **ASIC Ready:** Synthesizable SystemVerilog code, targeting the open-source SkyWater 130nm PDK.

---

## 🏗️ Hardware Architecture & Datapath

The core follows a classic single-cycle datapath layout. It seamlessly integrates essential components including the Program Counter (PC), Instruction Memory (IMEM), Register File, Arithmetic Logic Unit (ALU), Data Memory (DMEM), and the Main Control Unit to decode instructions and manage data routing.

<div align="center">
  <img width="850" alt="RISC-V Datapath" src="https://github.com/user-attachments/assets/de6d36b7-e479-4b10-8c32-dd630c18e295" />
  <p><i>Figure 1: Single-Cycle RV32I Datapath Architecture</i></p>
</div>

---

## 🧩 Instruction Formats

The decoding logic is designed to execute the base 32-bit instruction formats rigorously defined by the standard RISC-V ISA specification.

<div align="center">
  <img width="800" alt="RISC-V Instruction Formats" src="https://github.com/user-attachments/assets/fff457b9-adf3-4bec-a929-c51a0afdf2b2" />
  <p><i>Figure 2: Supported 32-bit RISC-V Instruction Formats (R, I, S, B, U, J)</i></p>
</div>

---

## 🧠 Control & Decoding Logic Implementation

The processor relies on a robust control logic system to decode opcodes, orchestrate ALU operations, and extract immediate values efficiently.

### 1. Main Control Unit
Acts as the central brain of the processor. It parses the 7-bit `opcode` from the fetched instruction to assert the correct multiplexer selection signals and memory access flags (`MemRead`, `MemWrite`, `RegWrite`, etc.).

<div align="center">
  <img width="800" alt="Control Unit Implementation" src="https://github.com/user-attachments/assets/1ab7f60c-0b78-4ecf-b385-a590567066d4" />
  <p><i>Figure 3: Main Control Unit RTL Logic</i></p>
</div>

### 2. ALU Control Module
Works in tandem with the Main Control Unit. It takes the broad `ALUOp` signal and refines it using the `funct3` and `funct7` fields from the instruction to dictate the precise arithmetic or logical operation the ALU must perform (e.g., distinguishing between ADD and SUB in R-type instructions).

<div align="center">
  <img width="800" alt="ALU Control Implementation" src="https://github.com/user-attachments/assets/761b4f21-86e5-41d7-9a42-bd0320025a33" />
  <p><i>Figure 4: ALU Control RTL Logic</i></p>
</div>

### 3. Immediate Generator (ImmGen)
Responsible for extracting and formatting immediate values from the 32-bit instruction. Depending on the instruction format (I, S, B, U, J), it slices the relevant bits, rearranges them, and performs sign-extension to generate a proper 32-bit operand for the ALU or branch target calculations.

<div align="center">
  <img width="800" alt="ImmGen Implementation" src="https://github.com/user-attachments/assets/fcb81c3e-b014-49fe-8828-6bfa12cbac6c" />
  <p><i>Figure 5: Immediate Generator (ImmGen) Logic</i></p>
</div>

---


<div align="center">
  <i>If you find this project helpful, please consider giving it a ⭐️!</i>
</div>
