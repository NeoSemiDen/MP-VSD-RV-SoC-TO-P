# Week 0 – Task 2  
**System Check & Basic Tool Installation (RISC-V Tapeout Program – India)**  

---

## 🖥️ System Check  
System requirements for the program environment:  

- **OS**: Ubuntu 20.04+  
- **RAM**: 6 GB  
- **Storage**: 50 GB  
- **CPU**: 4 vCPUs  

📷 *System Check Snapshot*  
<p align="center">
  <img src="./W0_images/system_check.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 1: System Check Snapshot</em>
</p>


---

## ⚙️ Tool Checks  

### 🔹 Yosys – Logic Synthesis  
Used for **RTL synthesis** in the digital design flow.  

````bash
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make
$ sudo make install
````
📷 *Yosys Tool Snapshot*   
<p align="center">
  <img src="./W0_images/yosys_tool_check.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 2: Yosys Tool Check Snapshot</em>
</p>

### 🔹 Icarus Verilog (iverilog) - Simulation
Used for **Verilog simulation and testing.**

````bash
$ sudo apt-get update
$ sudo apt-get install iverilog 
````
📷 *Iverilog Tool Snapshot*   
<p align="center">
  <img src="./W0_images/iverilog_tool_check.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 3: Iverilog Tool Check Snapshot</em>
</p>

### 🔹 GTKWave – Waveform Viewer
Used to **visualize simulation waveforms.**

````bash
$ sudo apt-get update
$ sudo apt install gtkwave 
````
📷 *GTKWave Tool Snapshot*  
<p align="center">
  <img src="./W0_images/gtkwave_tool_check.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 4: GTKWave Tool Check Snapshot</em>
</p>



