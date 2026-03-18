# 4bit-Ripple-Carry-Adder-Verilog
4-bit Ripple Carry Adder in Verilog with testbench and waveform output


This project implements a **4-bit Ripple Carry Adder (RCA)** using Verilog HDL.
The design is built using **Full Adders**, where the carry output of each stage is passed to the next stage (ripple effect).

---

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
