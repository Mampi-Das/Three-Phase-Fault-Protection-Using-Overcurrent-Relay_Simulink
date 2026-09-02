# ⚡ Three-Phase Fault Detection and Protection Using Overcurrent Relay

<p align="center">
  <img src="Model/ThreePhaseFault.png" alt="Three Phase Fault Protection Model" width="900">
</p>

<p align="center">
  <b>MATLAB/Simulink Based Three-Phase Power System Fault Analysis and Overcurrent Protection</b>
</p>

---

## 📌 Project Overview

This project presents a **MATLAB/Simulink-based simulation of a three-phase electrical power system with an overcurrent protection scheme**.

The model is developed to study the behavior of a three-phase power system under different fault conditions and to demonstrate the basic operation of an **overcurrent relay** for fault detection and protection.

Three different short-circuit fault conditions are simulated and analyzed:

- ⚡ **LG – Line-to-Ground Fault**
- ⚡ **LLG – Double Line-to-Ground Fault**
- ⚡ **LLL – Three-Phase Fault**

The three-phase currents are measured, converted into RMS values, and compared with a predefined relay pickup threshold. When an overcurrent condition is detected, the relay logic generates a trip signal for circuit-breaker operation.

The resulting **current and voltage waveforms** are observed using Simulink scopes to analyze the effect of each fault on the power system.

---

# 🎯 Objectives

The main objectives of this project are:

- To model a three-phase electrical power system using MATLAB/Simulink.
- To simulate different types of power-system faults.
- To study the effect of faults on three-phase currents.
- To analyze voltage disturbances during fault conditions.
- To implement an RMS-based overcurrent relay.
- To compare measured RMS current with a predefined pickup current.
- To generate a trip signal during an overcurrent condition.
- To demonstrate fault isolation using a circuit breaker.
- To understand the fundamental concepts of power-system protection.
- To gain practical experience with MATLAB/Simulink for electrical engineering applications.

---

# 🏗️ System Architecture

The simulated power system consists of a three-phase source, transformer, circuit breaker, measurement blocks, three-phase load, fault block, and overcurrent relay.

## Main Power Circuit

    Three-Phase Source
            │
            ▼
    Three-Phase Transformer
            │
            ▼
       Circuit Breaker
            │
            ▼
       Three-Phase Load
            │
            ▼
       Three-Phase Fault

## Protection System

    Three-Phase Currents
          │  │  │
          ▼  ▼  ▼
         Ia Ib Ic
          │  │  │
          ▼  ▼  ▼
        RMS RMS RMS
          │  │  │
          ▼  ▼  ▼
     Current Comparators
          │  │  │
          └──┼──┘
             ▼
         Trip Logic
             │
             ▼
      Circuit Breaker
             │
             ▼
       Fault Isolation

---

# 🖥️ Complete Simulink Model

The complete Simulink model includes:

- Three-phase source
- Three-phase transformer
- Circuit breaker
- Three-phase parallel load
- Three-phase fault block
- Current measurement
- Voltage measurement
- RMS measurement
- Overcurrent relay subsystem
- Comparator blocks
- SR flip-flop
- Logic gates
- Trip signal
- Scope for waveform analysis

<p align="center">
  <img src="Model/ThreePhaseFault.png" alt="Complete Three Phase Fault Simulink Model" width="1000">
</p>

---

# 🛡️ Overcurrent Relay

An **overcurrent relay** is a protection device that detects when the current flowing through a power-system section exceeds a predefined value.

In this project, the three phase currents are monitored:

    Ia
    Ib
    Ic

Each current is processed using an RMS measurement block.

The measured RMS current is then compared with the relay pickup threshold.

The basic operating condition is:

    I_RMS > I_Pickup

If the measured RMS current exceeds the pickup value, an overcurrent condition is detected.

---

# 🔧 Relay Subsystem

<p align="center">
  <img src="Relay/OverCurrentRelay.png" alt="Overcurrent Relay Subsystem" width="900">
</p>

The overcurrent relay subsystem consists of:

- RMS measurement blocks
- Relational/comparator operators
- Constant pickup-current setting
- SR flip-flop
- Logic gates
- Trip output

## Basic Relay Operation

    Phase Current
          │
          ▼
         RMS
          │
          ▼
    ┌─────────────┐
    │ Comparator  │
    │ I > Pickup  │
    └──────┬──────┘
           │
           ▼
       Trip Logic
           │
           ▼
    Circuit Breaker

The relay monitors the current continuously and produces a protection signal when an abnormal current condition is detected.

---

# 📐 Why RMS Current Is Used

AC current continuously changes with time.

The **RMS (Root Mean Square)** value represents the effective magnitude of an AC current.

In this project, the RMS value of each phase current is used for comparison with the relay pickup setting.

    Normal Condition:

    I_RMS < I_Pickup
            ↓
        Relay OFF


    Fault Condition:

    I_RMS > I_Pickup
            ↓
       Relay Operates

---

# ⚙️ System Parameters

The major parameters used in the Simulink model are shown below.

| Component | Parameter | Value |
|---|---|---:|
| Three-Phase Source | Short-Circuit Level at Base Voltage | 20 kVA* |
| Transformer | Nominal Power | 10 MVA |
| Transformer | Frequency | 50 Hz |
| Transformer Winding 1 | Voltage | 11 kV |
| Transformer Winding 1 | Resistance | 0.002 pu |
| Transformer Winding 1 | Leakage Inductance | 0.08 pu |
| Transformer Winding 2 | Voltage | 400 V |
| Transformer Winding 2 | Resistance | 0.002 pu |
| Transformer Winding 2 | Leakage Inductance | 0.08 pu |
| Transformer | Magnetization Resistance | 500 pu |
| Circuit Breaker | On-State Resistance | 0.01 Ω |
| Circuit Breaker | Snubber Resistance | 1 MΩ |
| Load | Active Power | 5 MW |
| Load | Inductive Reactive Power | 20 kVAR |
| Load | Capacitive Reactive Power | 0 |
| Overcurrent Relay | Pickup Threshold | 20 kA* |

> **Note:** Values marked with `*` represent the values currently configured in the Simulink model. Their interpretation depends on the units configured in the corresponding Simulink blocks.

---

# ⚡ Fault Types Simulated

Three major fault conditions are analyzed in this project.

---

# 1️⃣ LG Fault – Line-to-Ground Fault

An **LG fault** occurs when one phase comes into contact with ground.

Example:

    Phase A ───────────┐
                       │
                       ▼
                     Ground

## Effect of LG Fault

During an LG fault:

- The faulted phase current increases.
- The current waveform becomes disturbed.
- The voltage waveform experiences a disturbance.
- The three-phase system becomes unbalanced.
- The overcurrent relay monitors the abnormal current.
- A trip signal can be generated if the current exceeds the pickup threshold.

## 📊 LG Fault Current

<p align="center">
  <img src="Results/LG_Fault_Current.png" alt="LG Fault Current Waveform" width="850">
</p>

## 📉 LG Fault Voltage

<p align="center">
  <img src="Results/LG_Fault_Voltage.png" alt="LG Fault Voltage Waveform" width="850">
</p>

---

# 2️⃣ LLG Fault – Double Line-to-Ground Fault

An **LLG fault** occurs when two phases are connected to ground.

Example:

    Phase A ───────────┐
                       │
    Phase B ───────────┤
                       │
                       ▼
                     Ground

## Effect of LLG Fault

During an LLG fault:

- Two phases are directly involved in the fault.
- Fault current increases significantly.
- The affected phase currents become disturbed.
- The voltage system becomes unbalanced.
- The overcurrent relay monitors the abnormal current condition.
- A trip command can be generated when the protection threshold is exceeded.

## 📊 LLG Fault Current

<p align="center">
  <img src="Results/LLG_Fault_Current.png" alt="LLG Fault Current Waveform" width="850">
</p>

## 📉 LLG Fault Voltage

<p align="center">
  <img src="Results/LLG_Fault_Voltage.png" alt="LLG Fault Voltage Waveform" width="850">
</p>

---

# 3️⃣ LLL Fault – Three-Phase Fault

An **LLL fault** occurs when all three phases are involved in a short circuit.

    Phase A ───────┐
    Phase B ───────┼──── Fault
    Phase C ───────┘

When the fault conditions are identical for all three phases, the fault is considered a **symmetrical three-phase fault**.

## Effect of LLL Fault

During an LLL fault:

- All three phase currents increase significantly.
- Large short-circuit currents can flow.
- The three-phase voltage experiences a severe disturbance.
- The system experiences a symmetrical fault when the fault conditions are identical.
- The overcurrent relay monitors the resulting high current.

## 📊 LLL Fault Current

<p align="center">
  <img src="Results/LLL_Fault_Current.png" alt="LLL Fault Current Waveform" width="850">
</p>

## 📉 LLL Fault Voltage

<p align="center">
  <img src="Results/LLL_Fault_Voltage.png" alt="LLL Fault Voltage Waveform" width="850">
</p>

---

# 📊 Fault Comparison

| Fault Type | Phases Involved | System Condition | Current Behavior | Voltage Behavior |
|---|---|---|---|---|
| LG | One phase + Ground | Unbalanced | High/disturbed current in faulted phase | Voltage disturbance |
| LLG | Two phases + Ground | Unbalanced | High current in affected phases | Significant disturbance |
| LLL | Three phases | Symmetrical if identical | High current in all phases | Severe disturbance |

---

# 📈 Why Does Fault Current Increase?

A short circuit creates a low-impedance path for current.

According to Ohm's law:

\[
I = \frac{V}{Z}
\]

where:

- `I` = current
- `V` = voltage
- `Z` = impedance

During a fault, the effective impedance of the fault path becomes very small.

Therefore:

    Fault Impedance
           ↓
       Decreases
           ↓
     Fault Current
           ↑
       Increases

This is why the current during a fault can become much higher than the normal load current.

---

# 📉 Why Does Voltage Decrease During a Fault?

A fault causes a large current to flow through the impedance of the source, transformer and other elements of the power system.

The approximate voltage drop can be represented as:

\[
V_{drop} = I_{fault}Z_{system}
\]

Therefore:

    Fault Current ↑
           ↓
    Voltage Drop ↑
           ↓
    Faulted Voltage ↓

As a result, the voltage waveform becomes disturbed during fault conditions.

---

# 🧮 Normal Load Current Calculation

For a three-phase load, the approximate line current can be calculated using:

\[
I = \frac{P}{\sqrt{3}V\cos\phi}
\]

For:

    P = 5 MW
    V = 400 V

and approximately unity power factor:

\[
I =
\frac{5\times10^6}
{\sqrt{3}\times400}
\]

\[
I \approx 7217 A
\]

Therefore, the approximate normal load current is:

### **7.2 kA**

This value provides a useful reference when analyzing the simulated current waveforms and relay pickup setting.

---

# 🔄 Protection Sequence

The overall protection process can be represented as:

    Normal Operation
           │
           ▼
    Measure Phase Currents
           │
           ▼
      RMS Measurement
           │
           ▼
     Compare With Pickup
           │
      ┌────┴────┐
      │         │
      ▼         ▼
    Below     Above
    Pickup    Pickup
      │         │
      ▼         ▼
   Relay OFF  Fault Detected
                  │
                  ▼
              Trip Logic
                  │
                  ▼
           Circuit Breaker
                  │
                  ▼
            Fault Isolation

---

# 🧪 Simulation Procedure

## Step 1 – Open the Model

Open the Simulink model:

    ThreePhaseFault.slx

## Step 2 – Run Normal Operation

Run the simulation without applying a fault.

Observe:

- Three-phase current
- Three-phase voltage
- Load behavior
- Relay output

The relay should remain inactive if the normal RMS current is below the pickup threshold.

## Step 3 – Apply LG Fault

Configure the three-phase fault block for a line-to-ground fault.

Observe:

- Phase currents
- Voltage waveforms
- RMS current
- Relay output
- Trip signal
- Circuit-breaker response

## Step 4 – Apply LLG Fault

Configure the fault block for a double-line-to-ground fault.

Observe:

- Current increase
- Voltage disturbance
- Phase unbalance
- Relay response
- Breaker response

## Step 5 – Apply LLL Fault

Configure the fault block for a three-phase fault.

Observe:

- Current increase in all phases
- Voltage disturbance
- Relay response
- Circuit-breaker operation

## Step 6 – Verify Protection

The protection path should be checked as follows:

    Fault Current
          ↓
    RMS Measurement
          ↓
       Comparator
          ↓
    Overcurrent Detection
          ↓
       Trip Logic
          ↓
    Circuit Breaker
          ↓
     Fault Isolation

---

# 🔍 Relay Pickup Verification

The current relay pickup setting in the model is:

    20e3

If the RMS current signal is measured in amperes, this corresponds to:

    20,000 A = 20 kA

The important condition for correct operation is:

    Normal RMS Current < Pickup Current

and during a fault:

    Fault RMS Current > Pickup Current

Therefore, the relay setting should be verified against the actual RMS current produced by the simulation.

The protection path should also be checked:

    Overcurrent
         ↓
    Relay Detection
         ↓
     Trip Signal
         ↓
    Breaker Operation
         ↓
    Current Reduction / Fault Isolation

---

# 📊 Results and Analysis

The project analyzes the voltage and current waveforms obtained from the three different fault conditions.

## LG Fault

The LG fault produces an unbalanced disturbance, with the faulted phase experiencing a significant change in current and voltage.

## LLG Fault

The LLG fault produces a more severe disturbance involving two phases and ground. The affected phase currents increase and the voltage system becomes unbalanced.

## LLL Fault

The LLL fault involves all three phases and can produce a very large fault current. If all fault conditions are identical, the three-phase currents remain symmetrical while their magnitudes increase significantly.

---

# 🧠 Key Concepts Demonstrated

This project demonstrates practical understanding of:

- Three-phase power systems
- Power-system faults
- Short-circuit analysis
- Line-to-ground faults
- Double-line-to-ground faults
- Three-phase faults
- Symmetrical faults
- RMS measurement
- Overcurrent protection
- Relay pickup current
- Comparator operation
- SR flip-flop
- Logic gates
- Circuit-breaker operation
- Transformer modeling
- Voltage measurement
- Current measurement
- Fault detection
- Fault analysis
- MATLAB/Simulink modeling

---

# 🔌 Overcurrent Relay vs Circuit Breaker

A relay and a circuit breaker perform different functions.

## Overcurrent Relay

The relay:

- Monitors the current.
- Detects abnormal current conditions.
- Compares current with the pickup setting.
- Generates a trip command.

## Circuit Breaker

The circuit breaker:

- Receives the trip command.
- Opens the electrical circuit.
- Interrupts current flow.
- Isolates the faulty section.

Therefore:

    Relay
    = Detects the fault
    + Sends trip command


    Circuit Breaker
    = Opens the circuit
    + Interrupts fault current

---

# 📚 Learning Outcomes

Through this project, I gained practical experience in:

1. Modeling a three-phase power system.
2. Modeling transformers and loads in Simulink.
3. Simulating different short-circuit faults.
4. Measuring three-phase voltage and current.
5. Understanding RMS measurement.
6. Implementing basic overcurrent relay logic.
7. Using comparator blocks for fault detection.
8. Understanding SR flip-flop based latching.
9. Understanding relay trip signals.
10. Understanding circuit-breaker operation.
11. Analyzing voltage and current waveforms.
12. Understanding fundamental power-system protection concepts.

---

# 🛠️ Software and Tools

### Software

- MATLAB
- Simulink
- Simscape Electrical / Specialized Power Systems

### MATLAB Version

    MATLAB R2022b

> The exact toolbox requirements may depend on the Simulink blocks used in the model.

---

# 📁 Repository Structure

    Three-Phase-Fault-Protection-Simulink/
    │
    ├── README.md
    │
    ├── Simulink/
    │   └── ThreePhaseFault.slx
    │
    ├── Model/
    │   └── ThreePhaseFault.png
    │
    ├── Relay/
    │   └── OverCurrentRelay.png
    │
    ├── Results/
    │   ├── LG_Fault_Current.png
    │   ├── LG_Fault_Voltage.png
    │   ├── LLG_Fault_Current.png
    │   ├── LLG_Fault_Voltage.png
    │   ├── LLL_Fault_Current.png
    │   └── LLL_Fault_Voltage.png
    │
    └── Scripts/
        └── [MATLAB scripts, if applicable]

---

# 📷 Project Images

## Complete Simulink Model

<p align="center">
  <img src="Model/ThreePhaseFault.png" alt="Three Phase Fault Simulink Model" width="1000">
</p>

---

## Overcurrent Relay Subsystem

<p align="center">
  <img src="Relay/OverCurrentRelay.png" alt="Overcurrent Relay Subsystem" width="900">
</p>

---

# 📊 Simulation Results

## LG Fault

### Current

<p align="center">
  <img src="Results/LG_Fault_Current.png" alt="LG Fault Current" width="850">
</p>

### Voltage

<p align="center">
  <img src="Results/LG_Fault_Voltage.png" alt="LG Fault Voltage" width="850">
</p>

---

## LLG Fault

### Current

<p align="center">
  <img src="Results/LLG_Fault_Current.png" alt="LLG Fault Current" width="850">
</p>

### Voltage

<p align="center">
  <img src="Results/LLG_Fault_Voltage.png" alt="LLG Fault Voltage" width="850">
</p>

---

## LLL Fault

### Current

<p align="center">
  <img src="Results/LLL_Fault_Current.png" alt="LLL Fault Current" width="850">
</p>

### Voltage

<p align="center">
  <img src="Results/LLL_Fault_Voltage.png" alt="LLL Fault Voltage" width="850">
</p>

---

# 🚀 Future Improvements

The project can be further improved by implementing advanced protection techniques such as:

- IDMT overcurrent relay
- Earth-fault protection
- Differential protection
- Distance protection
- Overvoltage protection
- Undervoltage protection
- Relay coordination
- Multiple protection zones
- Automatic fault classification
- Fault-location estimation
- Real-time implementation
- Microcontroller-based protection
- DSP-based protection
- Hardware-in-the-loop testing

---

# ⚠️ Disclaimer

This project is developed for **academic and simulation purposes**.

It demonstrates the basic principles of three-phase fault analysis and overcurrent protection using MATLAB/Simulink.

It should not be considered a complete industrial protection system. Practical power-system protection requires detailed studies involving CT/PT characteristics, relay coordination, protection zones, breaker ratings, system parameters, time-current characteristics, applicable standards, and field testing.

---

# 👩‍💻 Author

## Mampi Das

**B.Tech – Electrical Engineering**  
**National Institute of Technology Agartala**

---

# ⭐ Acknowledgement

This project was developed as part of an academic study of:

**Three-Phase Power-System Fault Analysis and Overcurrent Protection using MATLAB/Simulink**

The project provided practical exposure to electrical power-system modeling, fault analysis, waveform interpretation, relay logic, and basic protection schemes.

---

# 📌 Keywords

    MATLAB
    Simulink
    Simscape Electrical
    Three Phase Power System
    Three Phase Fault
    LG Fault
    LLG Fault
    LLL Fault
    Overcurrent Relay
    Power System Protection
    Fault Detection
    Fault Analysis
    Circuit Breaker
    RMS Current
    Transformer
    Electrical Engineering
    Short Circuit
    Power System Fault
    Relay Protection

---

# ⭐ If You Find This Project Useful

If this project is useful for learning about power-system faults and protection, feel free to ⭐ **star this repository**.

---

<p align="center">
  <b>⚡ Three-Phase Fault Detection & Protection using MATLAB/Simulink ⚡</b>
</p>
