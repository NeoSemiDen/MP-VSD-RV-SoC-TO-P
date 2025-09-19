# Week 0 – Task 1  
**Digital VLSI SoC Design & Planning (RISC-V Tapeout Program – India)**  

---

## 📌 SoC Design Flow (O1 → O4)

### 🔹 O1 – Chip Modelling
- Define specs using **C model**  
- Verify functionality with **C testbench**  

---

### 🔹 O2 – RTL Architecture
- Hardware description in **RTL (Verilog)**  
- Functional verification: **C model ≡ RTL model** (same testbench)  

---

### 🔹 O3 – Synthesis & SoC Integration
- **Processor** → Gate-level netlist  
- **Peripherals/IPs** → Synthesized macros & analog IPs  
- Integrated via **GPIOs**  
- Validation: RTL design ↔ Gate-level design  

---

### 🔹 O4 – RTL → GDSII
- **PnR Flow** → Floorplanning, Placement, CTS, Routing  
- Macros & analog IPs hardened (**Hard Macros**)  
- Processor can be **soft logic** or **hard macro**  
- Output: **GDSII** → checked with **DRC/LVS** before tapeout  
- Final validation: **O1 = O2 = O3 = O4**  

---

## 📷 Flow Diagrams

<p align="center">
  <img src="./W0_images/SoC_Design_Flow.png" alt="SoC Design Flow" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 1: SoC Design Flow (O1 → O4)</em>
</p>

<p align="center">
  <img src="./W0_images/O4_and_Applications.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 2: O4 Stage and Real-world Applications</em>
</p>


---

## ✅ Applications
Once taped out & verified, the SoC is deployed in:  
- Smart wearables (iWatch)  
- Arduino boards  
- TV panels  
- AC / consumer electronics  

---
