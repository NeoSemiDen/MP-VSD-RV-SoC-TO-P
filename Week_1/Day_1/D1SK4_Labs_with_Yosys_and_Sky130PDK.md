# 🔹 Day 1 – Skill 4: Labs using Yosys and Sky130 PDKs
---

## Lessons

## L1 – Lab3: Yosys – 1 Good MUX (Part 1)

In this lab we will synthesize the design (which we simulated before) in yosys.
- We have already installed the required tools.

We will start with being present in `~/sky130RTLDesignAndSynthesisWorkshop/verilog_files`

**Step 1: Start Yosys**

````bash
yosys
````

**Step 2: Read the input - .lib and .v**

````bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog good_mux.v
````

**Step 3: Start synthesizing and generate netlist**

````bash
synth -top good_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
````
- mentioning the top module of our design
- Technology mapping using ABC
- show to see the graphical representation of realised circuit.

---

## L2 – Lab3: Yosys – 1 Good MUX (Part 2)

- We saw the graphical represntation of the synthesized design.
- We can also see manually that the logic verifies with design intended as it is very small design, a mux to be precise.

---

## L3 – Lab3: Yosys – 1 Good MUX (Part 3)

**Step 4: Write the generated netlist**

````bash
write_verilog -noattr good_mux_netlist.v
````

- noattr switch to have atributes in written netlist.
- We can observe the netlist in any editor.
  

---






