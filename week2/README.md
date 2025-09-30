# VSDBabySoC

**Author:** Shaik Haseena

![RISC-V Architecture](https://github.com/Shaikhaseena16/RISC-V_VSDIAT/blob/main/week2/RISC%20V%20.png)  

---

## 🧠 Project Overview

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

> **VSDBabySoC is a learner-centric RISC-V SoC that not only computes digitally, but also outputs in analog form, enabling you to experiment with real-world audio/video signals.**

---

