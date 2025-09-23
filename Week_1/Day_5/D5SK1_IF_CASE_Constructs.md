# 🔹 Day 5 – Skill 1: IF CASE Constructs

---

## Lessons

## L1 – IF CASE Constructs (Part 1)

### IF - generally used for priority logic

**Syntax:**
````Verilog
if <cond1> begin
  ......
  ......
end else if <cond2> begin
  ......
  ......
end else begin
  ......
  ......
end
````
- `IF` portion have the priority over the `ELSE` condition.
- Hardware ? Muxes according to numbers of ifs and it will look like step ladder.
- If condition 1 is true, condition 2 or later of least significant for us.

**Danger/Caution with IF: Inferred Latch**
- When we don't intend a latch but this is what my logic infers as.
- This is when we have incomplete if statements.
  
````Verilog
if <cond1> begin

end
//That's it
````
- This will infer as latch because we have incomplete if statement here, which is not intended here.

## L2 – IF CASE Constructs (Part 2)

There are times when the latch behaviour is intended in a design.
**For Example: A Counter**
````Verilog
always@(posedge clock or posedge reset) begin
  if (reset)
    count <= 0;
  else if (en)
    count <= count + 1;
end
````
- Now, here we have incomplete if statement and it will infer latch. But here it is intended.


### CASE Statement

- Whatever value being assigned insde `IF` or `CASE` Statement should be `reg type`

**Syntax**
````Verilog
always@(*) begin
  case(sel)
    2'b00: begin
            .....
            .....
    end
    2'b01: begin
            .....
    end
    .
    .
    .
    .
    .

  endcase
end
````

This will also infer as mux.

**Danger with CASE**
- 1. Incomplete Case => Infers Latch
````Verilog
always@(*) begin
  case(sel)
    2'b00: begin
            .....
            .....
    end
    2'b01: begin
            .....
    end
  endcase
end
````
Solution: Code `CASE` with default to avoid unintentional inferred latches.

````Verilog
always@(*) begin
  case(sel)
    2'b00: begin
            .....
            .....
    end
    2'b01: begin
            .....
    end
    default: begin
          .....
    end
  endcase
end
````

---

## L3 – IF CASE Constructs (Part 3)

---

- 2. Partial Assignments in CASE
````Verilog
reg [1:0] sel
reg x, y;

always@(*) begin
  case(sel)
    2'b00: begin
          x = a; y = b;
    end
    2'b01: begin
          x = c;
    end
    default : begin
          x = d; y = e;
    end
  endcase
end
````

- Here when `sel = 2'b00`, `x = a` and `y = b` but when `sel = 2'b0`, we have problem.
- The problem is that only x gets a value assigned, no value gets assigned to y.
- So, still after using default we gets inferred latch.

Solution: Assign values to all outputs in all cases.

---

- 3. CASE statement checks for every case, while if stops once the condition pass

---
