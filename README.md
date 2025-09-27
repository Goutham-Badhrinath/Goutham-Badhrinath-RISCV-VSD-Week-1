# Day 1 - Introduction to Verilog RTL Design and Synthesis

---

## 1. Introduction to iVerilog

I was introduced to **open-source simulators**, specifically **iVerilog**, which is used for verifying RTL designs.

### Key Learnings

* Purpose of a simulator and how it verifies RTL designs.
* Concepts of **design** and **testbench (TB)**.
* How simulators evaluate inputs and produce outputs.
* Role of **primary inputs and outputs** in a design.
* Basic **iVerilog simulation flow**.

### Simulator

* A simulator checks if the RTL design behaves as intended.
* iVerilog monitors **input signals** and only recalculates outputs when inputs change.
* Designs can have multiple primary inputs/outputs, but testbenches do not.

### Design vs Testbench

* **Design:** RTL code written to meet specifications.
* **Testbench:** Provides inputs and observes outputs to verify the design.

### Simulator Workflow

* Event-driven: inputs are observed, and outputs are updated only when inputs change.

---

## 2. Labs using iVerilog & GTKwave

I worked on **practical labs** to simulate and verify RTL designs using iVerilog and GTKwave.

### Key Learnings

* Organized workspace by creating **VSD/VLSI** folders.
* Cloned the **Sky130 RTL repository** from GitHub and explored its files.
* Used **iVerilog** to compile and simulate design modules with testbenches.
* Generated **VCD files** and visualized outputs using **GTKwave**.
* Explored modules and testbenches in **gvim**.

### Simulation Workflow

1. Compile and simulate design and testbench with iVerilog.
2. Run the generated executable to dump a **VCD file**.
3. Open the VCD file in GTKwave to view the waveforms.

### Notes

General simulation commands:

```bash
iverilog <module_name.v> <testbench_name.v>
./a.out
gtkwave <testbench_name.vcd>
```

---

## 3. Introduction to Yosys & Logic Synthesis

I learned about **logic synthesis** and how to use **Yosys** to convert RTL designs into gate-level netlists.

### Key Learnings

* A **synthesizer** converts RTL to a gate-level netlist.
* The same testbench can be reused since primary inputs/outputs stay the same.
* `.lib` files contain standard cells (slow, medium, fast).
* Setup and hold times define constraints for data capture.
* Different cell flavors affect speed, power, and hold constraints.

### Setup and Hold Time

* **Setup time:** Data must be stable before the clock edge.
* **Hold time:** Data must remain stable after the clock edge.

### Fast vs Slow Cells

* **Fast cells:** Low delay, higher area/power, used to increase circuit speed.
* **Slow cells:** Higher delay, lower area/power, used to prevent hold-time violations.

---

## 4. Labs using Yosys & Sky130 PDK

I performed hands-on labs to synthesize and realize a MUX design using Yosys and the Sky130 PDK.

### Key Learnings

* Load a standard cell library in Yosys with `read_liberty`.
* Import RTL design using `read_verilog`.
* Run synthesis using `synth`.
* Perform technology mapping with `abc`.
* Visualize logic with `show`.
* Write the synthesized netlist using `write_verilog`.
* Inspect the generated netlist in **gvim**.

### Lab Workflow

1. **Read library:** `read_liberty -lib <path_to_library_file>`
2. **Read RTL:** `read_verilog good_mux.v`
3. **Synthesize:** `synth -top good_mux`
4. **Map to gates:** `abc -liberty <path_to_library_file>`
5. **Visualize logic:** `show`
6. **Write netlist:** `write_verilog -noattr good_mux_netlist.v`
7. **Inspect netlist:** `gvim good_mux_netlist.v`

---
