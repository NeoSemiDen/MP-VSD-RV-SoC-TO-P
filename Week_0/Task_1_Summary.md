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
![SoC Design Flow](./W0_images/O4_and_Applications.png)  
![O4 & Applications](./W0_images/SoC_Design_Flow.png)  

---

## ✅ Applications
Once taped out & verified, the SoC is deployed in:  
- Smart wearables (iWatch)  
- Arduino boards  
- TV panels  
- AC / consumer electronics  

---
