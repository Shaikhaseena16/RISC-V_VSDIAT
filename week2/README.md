# VSDBabySoC

**Author:** Shaik Haseena


---

## 🧠 Project Overview
## 🧠 Understanding System on Chip (SoC)

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

