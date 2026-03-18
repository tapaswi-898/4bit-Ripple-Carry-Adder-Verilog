# 4bit-Ripple-Carry-Adder-Verilog
4-bit Ripple Carry Adder in Verilog with testbench and waveform output


This project implements a **4-bit Ripple Carry Adder (RCA)** using Verilog HDL.
The design is built using **Full Adders**, where the carry output of each stage is passed to the next stage (ripple effect).

## HERE IS MY VERILOG CODE.....
## 1) module
`timescale 1ns / 1ps

module ripple_carry_adder_4bit(
    input [3:0] A,
    input [3:0] B,
    input Cin,
    output [3:0] Sum,
    output Cout
    );

wire c1, c2, c3;

// Instantiate Full Adders
full_adder FA0 (A[0], B[0], Cin,  Sum[0], c1);
full_adder FA1 (A[1], B[1], c1,   Sum[1], c2);
full_adder FA2 (A[2], B[2], c2,   Sum[2], c3);
full_adder FA3 (A[3], B[3], c3,   Sum[3], Cout);

endmodule

## 2) testbench
`timescale 1ns / 1ps

module ripple_carry_adder_tb;

reg [3:0] A;
reg [3:0] B;
reg Cin;

wire [3:0] Sum;
wire Cout;

// Instantiate DUT (Device Under Test)
ripple_carry_adder_4bit uut (
    .A(A),
    .B(B),
    .Cin(Cin),
    .Sum(Sum),
    .Cout(Cout)
);

initial begin
    // Monitor output
    $monitor("Time=%0t | A=%b B=%b Cin=%b | Sum=%b Cout=%b",
              $time, A, B, Cin, Sum, Cout);

    // Test cases
    A = 4'b0000; B = 4'b0000; Cin = 0; #10;
    A = 4'b0011; B = 4'b0101; Cin = 0; #10;
    A = 4'b1111; B = 4'b0001; Cin = 0; #10;
    A = 4'b1010; B = 4'b0101; Cin = 1; #10;
    A = 4'b1111; B = 4'b1111; Cin = 1; #10;

    $finish;
end

endmodule
# # waveform
<img width="1602" height="581" alt="image" src="https://github.com/user-attachments/assets/b784047b-92b3-4025-a30d-39713945896b" />




##  Features

* 4-bit binary addition
* Modular design using Full Adders
* Includes a testbench for simulation
* Simple and beginner-friendly Verilog implementation

---

##  Working Principle

A Ripple Carry Adder works by connecting multiple Full Adders in series.

* Each Full Adder adds:

  * Two input bits (`A`, `B`)
  * One carry input (`Cin`)
* It produces:

  * Sum (`Sum`)
  * Carry output (`Cout`)

The carry output from one stage becomes the carry input for the next stage.

---

##  Project Structure

```
├── full_adder.v                # Basic full adder module
├── ripple_carry_adder_4bit.v  # 4-bit RCA using 4 full adders
├── ripple_carry_adder_tb.v    # Testbench for simulation
```

---

##  Simulation Steps (Vivado)

1. Create a new RTL project in Vivado
2. Add all `.v` files
3. Set `ripple_carry_adder_tb` as top module
4. Run **Behavioral Simulation**
5. Observe waveforms for:

   * Inputs: `A`, `B`, `Cin`
   * Outputs: `Sum`, `Cout`

---

## Example

| A    | B    | Cin | Sum  | Cout |
| ---- | ---- | --- | ---- | ---- |
| 0011 | 0101 | 0   | 1000 | 0    |
| 1111 | 0001 | 0   | 0000 | 1    |

---

# Limitation

* The carry propagates through each stage sequentially
* This results in **higher delay** for larger bit sizes

---

## Future Improvements

* Implement **Carry Look-Ahead Adder (CLA)** for faster operation
* Extend to 8-bit or 16-bit adder
* FPGA implementation with output display

Tapaswini Panda
Electrical_engineering

This project is open-source and free to use for learning purposes.
