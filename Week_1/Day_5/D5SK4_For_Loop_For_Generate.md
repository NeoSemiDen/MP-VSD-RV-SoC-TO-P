# 🔹 Day 5 – Skill 4: For Loop and For Generate

---

## Lessons

## L1 – For Loop and For Generate (Part 1)

### LOOPING CONSTRUCTS

#### FOR LOOP 
- Evaluating expressions, not for generating expression.
- Used inside always block.

#### GENERATE FOR LOOP
- Used to generate hardware, instantiating hardware.
- Used outside always, shouldn't be used inside always.

**FOR STATEMENT Example: Mux**

- To write a 2:1 Mux, we have 2 case statement.
````Verilog
always@(*) begin
  case(sel)
      1'b0: y = i0;
      1'b1: y = i1;
end
````

- To write a 4:1 Mux, we have 4 case statement.
````Verilog
always@(*) begin
  case(sel)
      2'b00: y = i0;
      2'b01: y = i1;
      2'b01: y = i2;
      2'b11: y = i3;
end
````

- Now if, we have 32:1 Mux, we need 32 statements inside case statements.
- This is too much to write.

**What can we do? Use FOR LOOP**
````Verilog
integer i;
always @(*) begin
  for (i = 0; i < 32; i = i + 1) begin
    if( i == sel)
      y = inp[i];
  end
end
````

- builds 32:1 Mux with such small code, and with just one alteration, we can even build 256:1 MUX.

---

## L2 – For Loop and For Generate (Part 2)

#### DEMUX Construction
- 1x8 Demux
````Verilog
always@(*) begin
  op_bus[7:0] = 8'b0;
  for (i = 0; i < 8; i = i + 1) begin
    if(i == sel)
      op_bus[i] = input;
  end
end
````
- Very wide MUX/DEMUX -> FOR statement is very handy.

### FOR GENERATE STATEMENT

````Verilog
and u_and1 (.a(), .b(), .y());
and u_and2 (.a(), .b(), .y());
.
.
and u_and8 (.a(), .b(), .y());
````
- We can have large number of such repeating gates.
- Here, we can use `for-generate` => for replicating the HW (outside always block)

````Verilog
genvar i;
generate
    for( i = 0; i < 8; i = i + 1) begin
      and u_and (.a(in1[i]), .b(in2[i]), .y(y[i]));
    end
endgenerate
````

---

## L3 – For Loop and For Generate (Part 3)

Let's talk about a complex design - **RIPPLE CARRY ADDER**
---
- Let's say we have 4-bit Ripple Carry Adder.
- Here, we have 4 Full Adder instantiated
- Rather than instantiating the Full Adder 4 times, we can just use `for-generate` to build the RCA as the same HW is used multiple times.

Summary:
| **FOR** | **FOR GENERATE** |
| --- | --- |
| Inside Always | Outside Always |
| Multiple Evaluations | HW Replication |
