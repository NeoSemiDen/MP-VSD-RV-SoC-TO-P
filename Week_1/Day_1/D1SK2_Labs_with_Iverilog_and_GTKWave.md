# 🔹 Day 1 – Skill 2: Labs using Icarus Verilog and GTKWave

---

## Lessons

## L1 – Lab1: Introduction to Lab

- File setup and cloning required git repos to begin with.

````bash
mkdir VLSI
cd VLSI
git clone https://github.com/kunalg123/vsdflow.git
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
````

<p align="center">
  <img src="./W1_images/VLSI_dir.png" alt="Snapshot of VLSI Directory" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 1: VLSI directory with cloned repos</em>
</p>

---

## L2 – Lab2: Introduction to Icarus Verilog & GTKWave (Part 1)

- We will start this lab with simulating a basic design of a mux present in the directory cloned.
- We will start with being present in VLSI directory created in Lab 1.

**Step 1: Enter the Folder of Verilog Files**

````bash
cd sky130RTLDesignAndSynthesisWorkshop
cd verilog_files
````

**Step 2: Usingn Iverilog build the vcd file for good mux**

````bash
iverilog good_mux.v tb_good_mux.v
./a.out
````
- This will create `tb_good_mux.vcd` file.

**Step 3: Observe the functionality using waveforms**
- For this we need to use gtkwave

````bash
gtkwave tb_good_mux.vcd
````

<p align="center">
  <img src="../W1_images/good_mux_waveform.png" alt="O4 and Applications" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 2: Good Mux Waveform in GTKWavew</em>
</p>

---

## L3 – Lab2: Introduction to Icarus Verilog & GTKWave (Part 2)



---
