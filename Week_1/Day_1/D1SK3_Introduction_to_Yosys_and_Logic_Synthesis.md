
# 🔹 Day 1 – Skill 3: Introduction to Yosys and Logic Synthesis

---

## Lessons

## L1 – Introduction to Yosys

### Synthesizer
- Tool used for coverting the RTL to netlist
- **Yosys** is the synthesizer used in this Session.

### Yosys Setup
- Yosys takes Design and .lib as inputs and gives netlist as output.

<p align="center">
  <img src="../W1_images/yosys_setup.png" alt="yosys_setup" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 1: Yosys Setup with relevent commands</em>
</p>

- For reading the design - `read_verilog`
- For reading the .lib - `read_liberty`
- For writing  out the netlist - `write_verilog`

---

### Verify the Synthesis
- We need to verify the systhesis too, to check if we get the similar behaviour.
- We use the same set setup as before, and this time, instead of design we have Netlist as input.

<p align="center">
  <img src="../W1_images/synthesis_verification.png" alt="yosys_setup" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 2: Synthesized Netlist Verification Setup</em>
</p>

## L2 – Introduction to Logic Synthesis (Part 1)
### RTL Design
- Behavioral representation of the required specification

**IS THIS WHAT WE NEED?**
- No, we need Digital Logic Circuit.

**HOW?**

### Synthesis

## L3 – Introduction to Logic Synthesis (Part 2)
