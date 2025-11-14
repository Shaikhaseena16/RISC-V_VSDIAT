
# 🛠 GLS of BabySoC — Post-Synthesis Simulation

## 🔹 Purpose of GLS

Gate-Level Simulation (GLS) verifies the functionality of a design **after synthesis**. Unlike RTL or behavioral simulation, GLS works on the **synthesized netlist**, which includes actual gates and interconnections used in the final design.

**Key Points:**

1. **Timing Verification**
   - Uses **SDF files** to check timing accuracy.
   - Ensures the SoC meets real-world timing requirements.

2. **Design Validation**
   - Confirms logical correctness after synthesis.
   - Detects potential issues like glitches or metastability.

3. **Simulation Tools**
   - **Icarus Verilog (`iverilog`)** for compilation.
   - **GTKWave** for waveform analysis.

4. **Importance for BabySoC**
   - Verifies modules like RISC-V core, PLL, DAC interact correctly.
   - Confirms timing compliance across all synthesized logic.

---

## 🔹 Step-by-Step Post-Synthesis Flow

### Step 1: Load Top-Level Design and Supporting Modules
```bash
yosys
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/yosys.png)

Inside the Yosys shell, run:
```yosys
read_verilog haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/module/vsdbabysoc.v
read_verilog -I haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/rvmyth.v
read_verilog -I haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/clk_gate.v

```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/read_desgin%20-1.png)

![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/read_design%20-2.png)


---

### **Step 2: Load the Liberty Files for Synthesis**
Inside the same Yosys shell, run:
```yosys
read_liberty -lib haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -lib haseena@haseena/DesktopVSDBabySoCC/VSDBabySoC/src/lib/avsddac.lib
read_liberty -lib haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/read_library.png)

---

### **Step 3: Run Synthesis Targeting `vsdbabysoc`**
```yosys
synth -top vsdbabysoc
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/synth_clk.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/synth_rvmyth.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/synth_babysoc.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/synth_hierarcy.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/syth_check.png)

---

### **Step 4: Map D Flip-Flops to Standard Cells**
```yosys
dfflibmap -liberty haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/diff.png)

---

### **Step 5: Perform Optimization and Technology Mapping**
```yosys
opt
abc -liberty haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib -script +strash;scorr;ifraig;retime;{D};strash;dch,-f;map,-M,1,{D}
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/opt.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/abc.png)

---

### **Step 6: Perform Final Clean-Up and Renaming**
```yosys
flatten
setundef -zero
clean -purge
rename -enumerate
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/flatten.png)

---

### **Step 7: Check Statistics**
```yosys
stat
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/stat_1.png)
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/stat_2.png)

---

### **Step 8: Write the Synthesized Netlist**
```yosys
write_verilog -noattr haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v
```
![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/write_verilog.png)

---

## POST_SYNTHESIS SIMULATION AND WAVEFORMS
---

### **Step 1: Compile the Testbench**
Run the following `iverilog` command to compile the testbench:
```bash
iverilog -o haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM -DFUNCTIONAL -DUNIT_DELAY=#1 -I haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/include -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module haseena@haseena/Desktop/VSDBabySoCC/VSDBabySoC/src/module/testbench.v
```
---
### **Step 2: Navigate to the Post-Synthesis Simulation Output Directory**
```bash
cd output/post_synth_sim/
```
---
### **Step 3: Run the Simulation**

```bash
./post_synth_sim.out
```
---
### **Step 4: View the Waveforms in GTKWave**

```bash
gtkwave post_synth_sim.vcd
```
---

![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/post_synth.png)

![screenshot](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/Week%203/Task%201/waveform.png)
