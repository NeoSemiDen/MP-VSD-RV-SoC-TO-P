# 🔹 Day 3 – Skill 3: Sequential Logic Optimizations

---

## Lessons

## L1-L3 – Lab07: Sequential Logic Optimisations

In these lab, we will see some optimisations made by synthesis tool `Yosys` in Sequential Circuits.
- We will go through few examples.
- How there design looks like and what they are mapped as.
- We will take 3 views - `design`, `simulation` and `graphical_yosys`


### Examples:

**Number 1** - dff_const1.v

````Verilog
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
````
- Here, we have a dff, upon reset application `reset = 1`, next value taken by q is 0, and when `reset = 0`, next value taken by q is 1.
- This behaviour is like q is `not` of reset, but with edge sensitivity.
- This should synthesis as dff but, with `not reset` behaviour.

Let's see what our synthesis tool do on this design.
- Being present in verilog_files folder as in previous labs, we will execute these commands.

````bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog dff_const1.v 
synth -top dff_const1 
dfflibmap ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
````

<p align="center">
  <img src="../W1_images/dff_const1_wave.png" alt="dff_const1_wave.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 1: Simulation of above design - dff_const1.v </em>
</p>

---

<p align="center">
  <img src="../W1_images/dff_const1_yosys.png" alt="dff_const1_yosys.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 2: Yosys view of Optimisation of dff_const1.v </em>
</p>

---

**Number 2** - dff_const2.v

````Verilog
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end

endmodule
````

- Here, we have a mux, when `a = 0`, `y = b` and when `a = 1`, `y = 1`.
- This behaviour can be expressed as `y = a or ((not a) and b)`
- This is nothing but `OR` of a and b.

Let's see what our synthesis tool do on this design. 

<p align="center">
  <img src="../W1_images/dff_const2_wave.png" alt="dff_const2_wave.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 3: Simulation of above design - dff_const2.v </em>
</p>

<p align="center">
  <img src="../W1_images/dff_const2_yosys.png" alt="dff_const2_yosys.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 4: Yosys view of Optimisation of dff_const2.v </em>
</p>


----

**Number 3** - dff_const3.v

````Verilog
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
````

- Here, we have a mux, when `a = 0`, `y = 0` and
- When `a = 1`, we look into c.
  - If `c = 1`, then `y = b` else `y = 0`
- This behaviour can be expressed as `y = a and ( c and b)`
- This is nothing but `AND` of a, b, and c.

Let's see what our synthesis tool do on this design. 

<p align="center">
  <img src="../W1_images/dff_const3_wave.png" alt="dff_const3_wave.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 5: Simulation of above design - dff_const3.v </em>
</p>

<p align="center">
  <img src="../W1_images/dff_const3_yosys.png" alt="dff_const3_yosys.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 6: Yosys view of Optimisation of dff_const3.v </em>
</p>


----

**Number 4** - dff_const4.v

````Verilog
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
````

- Here, we have a mux, when `a = 0`, `y = not c` and
- When `a = 1`, we look into b.
  - If `b = 1`, then `y = a and c` else `y = c`
- This simplifies as `XNOR Gate` only - `y = a xnor c`.
- Let's see what our synthesis tool do on this design. 

<p align="center">
  <img src="../W1_images/dff_const4_wave.png" alt="dff_const4_wave.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 7: Simulation of above design - dff_const4.v </em>
</p>

<p align="center">
  <img src="../W1_images/dff_const4_yosys.png" alt="dff_const4_yosys.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 8: Yosys view of Optimisation of dff_const4.v </em>
</p>


----

**Number 5** - dff_const5.v

````Verilog
module dff_const5(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b0;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
````

- Here, we have a design with multiple module.
- We can notice that we have used 2 modules here, but when we flatten the design, we observe that `n1 = a` and n2 and n3 are never used.
- So the output expression is `y = c or (a and b)`
- These are the commands we run in the yosys to get view of its optimisation.
  
<p align="center">
  <img src="../W1_images/dff_const5_wave.png" alt="dff_const5_wave.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 9: Simulation of above design - dff_const5.v </em>
</p>

<p align="center">
  <img src="../W1_images/dff_const5_yosys.png" alt="dff_const5_yosys.png" width="600" style="border:2px solid black;"/>
  <br/>
  <em>Figure 10: Yosys view of Optimisation of dff_const5.v </em>
</p>


----
