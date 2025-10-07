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

