# 🔹 Day 3 – Skill 1: Introduction to Optimizations

---

## Lessons

## L1 – Introduction to optimisations (Part 1)

### Combinational Logic Optimisation

- Squeezing the logic to get the most optimised design
  - Area and Power Savings
- Constant Propagation
  - Direct Optimisation
- Boolean Logic Optimisation
  - K-map
  - Quine McKluskey
 
### Constant Propagation: Example

`Y = NOT ((A AND B) OR C)`

If `A = 0` then

`Y = NOT (( 0 ) OR C)`

`Y = NOT C`

- It is optimised when A never chnages and is always 0.

- From 2 gates, it turned out to be a single inverter.

### Boolean Logic Optimisation

- Another example : `y = a ? (b ? c:(c?a:0)) : (!c)`
- This says, if `a = 0` then `y = not c`
- If `a = 1` then go ahead and evaluate for b.
  - If `b = 1` then `y = c`.
  - If `b = 0` then go ahead and evaluate for c.
    - If `c = 0` then `y = 0`
    - If `c = 1` then `y = a`.

- In general, this will be seen as 3 multiplexers.
- But when simplified/optimised, the expresseion will come out to be ` y = a xnor b`.

---

## L2 – Introduction to optimisations (Part 2)

### Sequential Logic Optimisations
- Basic
  - Sequential Constant propagation
- Advanced
  - State optimisation
  - Retiming
  - Sequential Logic Cloning (FLoorplan Aware Synthesis)
 
### 4. Sequential Constant Propagation

- **Definition:** An optimisation in sequential circuits where registers or logic driven by constant values are simplified or removed.  
- **Key Idea:** If a register’s output is always constant (due to constant input or active reset), it can be optimised away.

---

#### 📝 Examples

1. **DFF with constant input (0) → AND gate**
   - If the DFF input is always `0`, then its output will always be `0`.  
   - The AND gate fed by this DFF will also always output `0`.  
   - Result: The DFF is redundant and can be replaced with a constant `0`.

---

2. **DFF with changing input but reset always ON**
   - Even if the input changes, the always-active reset keeps the DFF output at `0`.  
   - The AND gate output will always be `0`.  
   - Result: The DFF and subsequent logic can be replaced with constant `0`.

---

3. **DFF with constant input but set signal available**
   - Suppose the input is constant `0`.  
   - However, if a **set signal** exists, it can force the DFF output high temporarily.  
   - This means the DFF output is not truly constant.  
   - Result: Optimisation **cannot** be performed because the set signal can alter the output.

---

#### ⚖️ Takeaway
Sequential constant propagation is more complex than combinational constant propagation.  
It requires checking not just constant inputs but also the effect of **reset** and **set** signals before safely removing registers.

---

## L3 – Introduction to optimisations (Part 3)

### 🔧 Advanced Optimisation Techniques

#### State Optimisation
- **Definition:** Reducing the number of states in a finite state machine (FSM) without changing its behavior.  
- **Why:** Fewer states → fewer flip-flops → reduced area and sometimes power.  
- **How:**
  - State minimization (merging equivalent states).  
  - State encoding (binary, one-hot, Gray, etc.).  
- **Trade-off:** Smaller state count may increase transition logic complexity.  
- **Example:**  
  - Original FSM has states: `IDLE`, `READ`, `WRITE`, `WAIT`, `WAIT_ACK`  
  - After merging equivalent states `WAIT` and `WAIT_ACK` → fewer flip-flops required.  
  - Hardware area reduces, logic simpler.

---

#### Retiming
- **Definition:** Moving flip-flops across combinational logic without changing functionality.  
- **Why:** Balances delay between pipeline stages → higher clock frequency.  
- **How:**
  - Relocate registers to shorten critical paths.  
  - Often automated during synthesis.  
- **Trade-off:** Latency (pipeline depth) may change, but I/O behavior stays consistent.  
- **Example:**  
  - Consider a 3-stage combinational logic pipeline: `A -> B -> C`.  
  - Critical path: A → B → C → slow clock.  
  - Retiming: Move registers between B and C → shorter critical path → higher clock frequency.
  
---

#### Sequential Logic Cloning
- **Definition:** Duplicating registers that drive multiple high-fanout paths.  
- **Why:** Reduces fanout load → improves timing closure.  
- **How:**
  - Create multiple identical registers closer to their destination logic.  
- **Trade-off:** Area overhead (extra registers) but better performance.  
- **Example:**  
  - A single register feeds 10 AND gates across the design → long routing delay.  
  - Clone the register closer to 5 of the AND gates each → reduced fanout per register → timing improved.  

---

These advanced Optimisation Techniques won't be demonstrated in the labs.

---
