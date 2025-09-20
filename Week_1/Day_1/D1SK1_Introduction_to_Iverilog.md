# 🔹 Day 1 – Skill 1: Introduction to Icarus Verilog (iverilog)

This skill introduces the **open-source Verilog simulator Icarus Verilog (iverilog)** and explains how to write and run a simple **Verilog testbench**.

---

## Lessons

### L1 – Introduction to iverilog Design Testbench
**Objective:**  
- Learn how to write a basic Verilog module and testbench.  
- Understand simulation workflow using iverilog.

**Key Concepts:**  
- Verilog module structure (`module`, `endmodule`)  
- Testbench components: stimulus generation, clock, and reset signals  
- Compilation and simulation using `iverilog`  
- Viewing results with GTKWave (`.vcd` files)  

**Example Code:**
```verilog
// Simple AND gate module
module and_gate(
    input a,
    input b,
    output y
);
    assign y = a & b;
endmodule

// Testbench
module tb_and_gate;
    reg a, b;
    wire y;

    // Instantiate DUT
    and_gate dut(.a(a), .b(b), .y(y));

    initial begin
        // Test vectors
        a = 0; b = 0; #10;
        a = 0; b = 1; #10;
        a = 1; b = 0; #10;
        a = 1; b = 1; #10;
        $finish;
    end
endmodule
