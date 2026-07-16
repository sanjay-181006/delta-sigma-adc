# 🚀 Delta-Sigma ADC [![DOI](https://zenodo.org/badge/1277797819.svg)](https://doi.org/10.5281/zenodo.20928318)

A MATLAB/Simulink and LTspice-based implementation of a **1-bit First-Order Delta-Sigma Analog-to-Digital Converter (ΔΣ ADC)** developed for the **IIT Ropar's Internal Hackathon**. The project demonstrates the principles of **oversampling**, **noise shaping**, and **digital decimation filtering**, while evaluating converter performance through **FFT analysis**, **Signal-to-Noise Ratio (SNR)**, and **Effective Number of Bits (ENOB)** metrics.

---

## 📖 Overview

Delta-Sigma ADCs achieve high-resolution conversion by shaping quantization noise outside the signal band and removing it through digital filtering. This project presents both:

- A **behavioral model** implemented in MATLAB/Simulink
- An **analog circuit implementation** developed in LTspice

The design is analyzed across multiple Oversampling Ratios (OSRs) to study the effects of noise shaping and decimation on converter performance.

### Key Features

- First-Order 1-Bit Delta-Sigma Modulator
- Behavioral Modeling in MATLAB/Simulink
- Analog Circuit Design in LTspice
- Oversampling Ratio (OSR) Sweep
- CIC Decimation Filtering
- FFT-Based Spectral Analysis
- SNR and ENOB Evaluation
- Quantization Noise Shaping Verification

---

## 🏗️ System Architecture

```text
Analog Input │
             ▼
       ┌──────────┐
       │Integrator│
       └────┬─────┘
            │
             ▼
       ┌──────────┐
       │1-Bit ADC │
       │Quantizer │
       └────┬─────┘
            │
             ▼
   Delta-Sigma Bitstream │
                         ▼
               CIC Decimation Filter │
                                     ▼
                           Reconstructed Output │
                                                ▼
                                         FFT / SNR / ENOB
```

---

## 📂 Repository Structure

```text
delta-sigma-adc/
│
├── DeltaSigma_ADC.slx
├── DeltaSigmaAnalogBreakdown.asc
├── Matlab.mat
└── Simulation_Code.txt
```

| File | Description |
|:---|:---|
| `DeltaSigma_ADC.slx` | Main Simulink model of the Delta-Sigma ADC |
| `DeltaSigmaAnalogBreakdown.asc` | LTspice schematic of the analog Delta-Sigma modulator |
| `Matlab.mat` | Predefined MATLAB workspace variables |
| `Simulation_Code.txt` | Source code for simulation, FFT, SNR, and ENOB analysis |

---

## ⚡ LTspice Analog Design

The repository includes an LTspice implementation of the analog Delta-Sigma modulator.

**File:**
```text
DeltaSigmaAnalogBreakdown.asc
```

The LTspice schematic provides a circuit-level representation of the analog building blocks used in the Delta-Sigma ADC, including:
- Integrator stage
- Comparator (1-bit quantizer)
- Feedback path
- Analog signal conditioning circuitry

This complements the Simulink behavioral model by providing insight into the underlying analog implementation.

---

## ⚙️ Simulation Parameters

| Parameter | Value |
|:---|:---|
| Input Frequency | 13 Hz |
| Signal Bandwidth | 1000 Hz |
| Input Amplitude | 0.66 |
| DC Offset | 0.5 |
| Quantizer Resolution | 1-bit |
| Simulation Duration | 2 s |
| Oversampling Ratios (OSR) | 64, 128, 256 |

---

## ▶️ Getting Started

To execute the simulation, ensure your MATLAB current directory is set to this folder, then use the following quick-run routine:

### 1. Load Workspace Environment Variables
Load the required foundational workspace structures directly into your memory:
```matlab
load('Matlab.mat');
```

### 2. Run the Analysis Code
Open `Simulation_Code.txt`, copy its entire contents, and paste them directly into the **MATLAB Command Window** (or an active Editor script file) to run. 

The execution routine automatically performs:
- Delta-Sigma ADC loop configuration
- Automatic Simulink model launching
- OSR dynamic sweeps
- Decimation filtering calculation
- Spectral FFT generation
- SNR and ENOB compilation matrix 
- Performance graphical visualization profiles

---

## 📊 Performance Metrics

### Signal-to-Noise Ratio (SNR)
> **SNR = 10 × log₁₀(Psignal / Pnoise)**

where:
- `Psignal` = Signal Power
- `Pnoise` = Noise Power

### Effective Number of Bits (ENOB)
> **ENOB = (SNR − 1.76) / 6.02**

These metrics are computed for each Oversampling Ratio (OSR) to evaluate converter performance.

---

## 📈 Expected Results

Increasing the Oversampling Ratio improves converter performance by reducing in-band quantization noise.

```text
OSR ↑ ├── In-Band Noise ↓ ├── SNR ↑ ├── ENOB ↑ └── FFT Noise Floor ↓
```

### Observations
✔ Lower in-band quantization noise  
✔ Improved signal fidelity  
✔ Higher SNR  
✔ Increased effective resolution  
✔ Enhanced noise-shaping performance  

---

## 🔬 Analysis Performed

### Time-Domain Analysis
- Input waveform inspection
- Integrator response
- Quantizer output
- Delta-Sigma bitstream behavior

### Frequency-Domain Analysis
- FFT spectrum generation
- Noise floor evaluation
- Signal peak identification
- Quantization noise distribution

### Performance Evaluation
- SNR vs OSR
- ENOB vs OSR
- Noise-shaping verification

---

## 🛠️ Requirements

### Software
- MATLAB R2022a or newer
- Simulink
- LTspice XVII (optional, for analog circuit simulation)

### Toolboxes
- DSP System Toolbox

---

## 🎯 Applications

Delta-Sigma ADCs are widely used in applications requiring high resolution and excellent noise performance:
- Space and satellite telemetry
- Sensor interfaces
- Biomedical instrumentation
- Precision measurement systems
- Industrial data acquisition
- Audio and instrumentation converters

---

## 📚 Concepts Demonstrated

- Delta-Sigma Modulation
- Oversampling
- Noise Shaping
- Quantization Noise Reduction
- CIC Decimation Filtering
- FFT-Based Spectral Analysis
- Signal-to-Noise Ratio (SNR)
- Effective Number of Bits (ENOB)
- Mixed-Signal System Modeling

---

## 🕹️ How to Use

Follow these exact steps to run the simulation and performance analysis on your local machine:

### 1. Set MATLAB Directory
1. Download and extract this project folder.
2. Open **MATLAB**.
3. In the **Current Folder** browser panel, navigate to and open this extracted project folder containing `DeltaSigma_ADC.slx` and `Matlab.mat`.

### 2. Load Workspace Parameters
Before running the simulation script, load the predefined dataset structures into your MATLAB workspace by running this command in the **Command Window**:
```matlab
load('Matlab.mat');
```

### 3. Execute Analysis Script
1. Open the file **`Simulation_Code.txt`** using any text editor or inside MATLAB.
2. Select all text (`Ctrl+A` or `Cmd+A`) and copy it.
3. Paste the code directly into the **MATLAB Command Window** and press **Enter**.

### 📊 Expected Automated Outputs
Once pasted, the simulation routine will execute automatically and perform:
* **System Simulating:** Launches the underlying `DeltaSigma_ADC.slx` model configurations automatically.
* **OSR Dynamic Sweep:** Simulates the mixed-signal pipeline across multiple Oversampling Ratios (64, 128, 256).
* **Decimation Filtering Calculation:** Compiles the Cascaded Integrator-Comb (CIC) filter data metrics.
* **Spectral Analysis:** Computes and plots the system frequency response profiles using Fast Fourier Transforms (FFT).
* **Metrics Visualization:** Generates system tracking plots along with comparative performance charts for **SNR vs. OSR** and **ENOB vs. OSR**.

---

## 📜 License

This repository is intended for academic, educational, and research purposes. Feel free to use and extend the work with appropriate attribution.
