## TASK - 1
# VSDBabySoC

---

## 🧠 System on Chip (SoC)

A **System on a Chip (SoC)** is like a **complete computer packed into a single chip**. Instead of using separate components for processing, memory, graphics, and communication, an SoC **integrates everything into one compact unit**, making it ideal for space- and power-constrained devices like **smartphones, smartwatches, and IoT gadgets**.

---

### 🔍 Key Components of an SoC

| Component | Role |
|-----------|------|
| **CPU (Central Processing Unit)** | Acts as the *brain* of the system, handling instructions and computations |
| **Memory (RAM & ROM/Flash)** | RAM stores temporary data while ROM stores permanent firmware or system code |
| **I/O Interfaces** | Enable communication with external devices like sensors, displays, USB, or audio |
| **GPU (Graphics Processing Unit)** | Handles image and video rendering for visual output |
| **DSP (Digital Signal Processor)** | Optimized for processing audio, video, and communication signals |
| **Power Management Unit** | Regulates power usage for efficiency and longer battery life |
| **Special Modules (Wi-Fi, Bluetooth, Security, etc.)** | Added based on application needs |

---
## Types of SoCs

### 1. Microcontroller-based SoC
- Built around a microcontroller.  
- Low power usage and high efficiency.  
- Ideal for simple control tasks in **home appliances, cars, and IoT devices**.  

### 2. Microprocessor-based SoC
- Built around a microprocessor.  
- Provides higher processing power and supports operating systems.  
- Common in **smartphones and tablets** for handling multiple tasks and complex applications.  

### 3. Application-Specific SoC
- Custom-designed for specific high-performance tasks.  
- Optimized for **speed and efficiency**.  
- Used in **graphics cards, AI hardware, networking, and multimedia systems**.  

### ✅ Why SoCs Are So Popular

- **💡 Space Efficient** — Reduces the need for multiple components  
- **🔋 Power Efficient** — Consumes less energy due to shorter internal interconnects  
- **⚡ High Performance** — Faster communication between modules  
- **💰 Cost Effective** — Manufacturing one chip is cheaper than integrating many parts  
- **🛡️ Reliable** — Fewer components mean fewer points of failure

---


**VSDBabySoC** is a compact, open-source System on Chip (SoC) built around the **RVMYTH RISC-V core**. It combines digital processing and analog interfacing, featuring:

- A **Phase-Locked Loop (PLL)** for stable and synchronized clock generation  
- A **10-bit Digital-to-Analog Converter (DAC)** to convert the digital outputs into analog signals  
- Capability to output audio/video signals to analog devices (e.g. TVs, mobile phones)  
- Implementation in **Sky130 process technology** for educational and prototyping use  

This SoC is designed to serve as a **hands-on learning platform** for exploring mixed-signal SoC design, bridging theory and real-world interfacing.

---

## 🏗️ Architecture & Components

### Core Blocks

| Module | Purpose |
|---|---|
| **RVMYTH CPU (RISC-V Core)** | Executes instructions, generates data (e.g., via register `r17`) |
| **PLL (Phase-Locked Loop)** | Produces a stable, synchronized clock for the system |
| **10-bit DAC** | Converts digital data into analog waveforms |
| **Clock & Reset Logic** | Ensures orderly initialization and timing alignment |
| **Analog Output Interface** | Exports the converted analog signal (e.g., saved as `OUT`) |

### Operation Flow (Simplified)

1. **Clock Start** ⏱: The PLL locks onto a reference input and generates a clean system clock.  
2. **Data Generation**: RVMYTH cycles through data (for example, with register `r17`) as it runs instruction sequences.  
3. **Digital-to-Analog Conversion**: The DAC receives digital values and produces analog voltages.  
4. **Output Delivery**: The analog signal is output or stored (e.g. `OUT` file) and can be fed into external analog equipment for audio/video output.

---

# Role of Functional Modeling in VSDBabySoC Design Flow

Before moving to **RTL (Register Transfer Level)** and **physical design**, functional modeling plays a critical role in the development of **VSDBabySoC**.  

## Why Functional Modeling?
- **Early Validation:** Ensures the SoC concept and architecture work as intended before detailed RTL coding.  
- **Design Exploration:** Allows testing of multiple design ideas (e.g., clocking, data flow, DAC behavior) quickly.  
- **Bug Detection:** Identifies logical or architectural flaws early, saving time and cost in later design stages.  
- **Reference Model:** Acts as a “golden” model against which RTL implementations can be verified.  

## Application in VSDBabySoC
1. **System Behavior:** Models the interaction between RVMYTH, PLL, and DAC to validate overall data flow.  
2. **Clock Synchronization:** Simulates PLL behavior to check stable clock generation for processor and DAC.  
3. **Data Processing:** Verifies that the RVMYTH’s r17 register cycles values correctly for continuous data streams.  
4. **Analog Output:** Emulates the DAC’s digital-to-analog conversion to ensure correct multimedia output (saved in **OUT**).  

## Benefits Before RTL & Physical Design
- Reduces risk of costly design rework.  
- Provides confidence that RTL implementation will meet system-level goals.  
- Shortens design cycle by catching errors early.  
- Guides physical design by validating functionality before focusing on layout, timing, and power.  
---
# Why BabySoC is a Simplified Model for Learning SoC Concepts

**BabySoC** is designed as a small and easy-to-understand System on Chip, making it perfect for beginners to learn how SoCs work.  

## Reasons BabySoC is Simplified
- **Small Size:** Uses only a few key components (RVMYTH processor, PLL, DAC).  
- **Clear Functionality:** Each block has a simple, well-defined role (process data, generate clock, convert signals).  
- **Easy Flow:** Shows the basic sequence of SoC operation — input → process → output.  
- **Hands-On Learning:** Lets learners see how digital data becomes real-world signals (like sound or video).  
- **Step-by-Step Approach:** Provides a foundation before moving to complex SoCs with many IPs and large designs.  

## Learning Benefits
- Understand core SoC concepts without being overwhelmed.  
- Practice the complete design flow: **functional modeling → RTL → physical design.**  
- Build confidence to explore larger, real-world SoC projects.  
---
## 🎯 Use Cases & Learning Value

- **Signal Output & Multimedia Demo**: Interface with analog hardware (TVs, speakers) for visual or audio projects  
- **Mixed-Signal Education**: Understand how digital logic and analog circuits coexist in a single chip  
- **SoC Prototyping in Sky130**: Enables simulation and potential real silicon implementation  
- **RISC-V Instruction Practice**: Write simple programs to drive analog behavior  

---

## 🔭 Future Extensions (Ideas)

- **Analog-to-Digital Converter (ADC)**: For reading sensors or external analog inputs  
- **On-chip Memory (RAM/ROM)**: To store programs and data  
- **Peripheral Interfaces**: UART, GPIO, I²C, or SPI for external communication  
- **Audio / Video Protocols**: PWM, I2S, or composite video output  

---

---

## 📌 One Sentence Summary

> **In simple terms, SoC technology enables modern devices to be *smaller, faster, and smarter* by combining multiple electronic functions into a single chip.**

> **VSDBabySoC is a learner-centric RISC-V SoC that not only computes digitally, but also outputs in analog form, enabling you to experiment with real-world audio/video signals.**

---

## TASK - 2

# 🧪 VSD BabySoC – RTL Simulation & Waveform Analysis

This project simulates the **VSD BabySoC** design using Verilog, Icarus Verilog, and GTKWave. It includes a testbench, simulation instructions, and waveform analysis to verify the functionality of the RTL design.

---

## 📁 Project Structure

```
VSDBabySoC/
├── LICENSE
├── Makefile
├── README.md              # This file
├── src/
│   └── module/
│       ├── vsdbabysoc.v           # RTL Design (DUT)
│       ├── tb_vsdbabysoc.v        # Testbench
│       ├── vsdbabysoc_tb.vvp      # Compiled simulation output
|       ├── rvmyth.v               # rvmyth verilog file(sub module)
|       ├── avsddac.v              # avsddac verilog file(sub module)
|       ├── avsdpll.v              # avsdpll verilog file(sub module)
│       ├── vsdbabysoc_wave.vcd    # Waveform output
│       └── testbench.v            # (Alternate or unused testbench)
```

---

## 🔧 Tools Required

- [Icarus Verilog](http://iverilog.icarus.com/) – Verilog simulator  
- [GTKWave](http://gtkwave.sourceforge.net/) – Waveform viewer  
- Ubuntu or any Linux-based terminal

### 🛠️ Installation on Ubuntu

```bash
sudo apt update
sudo apt install iverilog gtkwave
```

---

## 🚀 How to Run the Simulation

### 1️⃣ Navigate to Project Directory

```bash
cd src/module
```

### 2️⃣ Compile the Verilog Files

```bash
iverilog -o vsdbabysoc_tb.vvp vsdbabysoc.v tb_vsdbabysoc.v
```

- Compiles RTL and testbench into `vsdbabysoc_tb.vvp`

![screenshot 02-10](relative/path/to/image.png)


### 3️⃣ Run the Simulation

```bash
vvp vsdbabysoc_tb.vvp
```

- Generates a waveform file: `vsdbabysoc_wave.vcd`

### 4️⃣ View the Waveform

```bash
gtkwave vsdbabysoc_wave.vcd
```

- Open GTKWave and inspect the signals like `CLK`, `reset`, `OUT`, etc.

---

## 📈 Signals Observed in GTKWave

| Signal Name     | Description                    |
|------------------|-------------------------------|
| `CLK`           | Clock signal                   |
| `reset`         | System reset                   |
| `ENB_CP`        | Enable Charge Pump             |
| `ENB_VCO`       | Enable VCO                     |
| `OUT`           | Main output of the module      |
| `VCO_IN`        | VCO input                      |
| `REF`           | Reference input                |
| `VREFH`, `VREFL`| High and Low reference voltages|
| `RV_TO_DAC[]`   | Bus connected to DAC           |

---

## 📝 Output Example

When simulation runs correctly:

```bash
VCD info: dumpfile vsdbabysoc_wave.vcd opened for output.
```

In GTKWave, you will see signal waveforms from 0 to 1020 ns. Zoom, pan, and mark signal transitions to inspect logic behavior.

---

## 📷 Screenshots (Optional)

You can include the following screenshots in your GitHub repo or README:

- Terminal showing compilation & simulation
- GTKWave with signal waveform
- Zoomed-in timing for critical signals

---

## ✅ Results

- ✅ Successful compilation of Verilog code
- ✅ Simulation generated a valid `.vcd` waveform
- ✅ Signal transitions behave as expected
- ✅ Design verified using GTKWave

---

## 📌 Notes

- Ignore this GTK warning if it appears:
  ```
  Gtk-Message: Failed to load module "canberra-gtk-module"
  ```
  It does not affect simulation or waveform analysis.

- If you make any changes to your Verilog files, rerun all steps (compile, simulate, and view).

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👨‍💻 Author

- **Your Name**
- [GitHub Profile](https://github.com/yourusername)

---

## 🙌 Acknowledgments

- [Icarus Verilog](http://iverilog.icarus.com/)
- [GTKWave](http://gtkwave.sourceforge.net/)
- [VSDOpen](https://vsdiat.com/) – for open-source SoC design enablement
