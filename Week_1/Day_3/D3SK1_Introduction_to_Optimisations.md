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
 
### Sequential Constant propagation

Explanation Coming up.

---

## L3 – Introduction to optimisations (Part 3)

### Advanced Optimisations Technique

#### State Optimisation
#### Retiming
#### Sequential Logic Cloning


---
