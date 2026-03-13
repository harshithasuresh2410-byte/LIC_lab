# Experiment 2: Design and Characterization of Common Source (CS) Amplifier Topologies

## 1. Problem Statement
**Design Task:** Design a Common Source (CS) Amplifier with various load configurations using **tsmc 180nm** technology node in **LTSPICE**.  
**Constraints:** * **Power Dissipation ($P$):** $\le 1\text{mW}$
* **Supply Voltage ($V_{DD}$):** $1.8\text{V}$
* **Load Capacitance ($C_L$):** $10\text{pF}$
* **Channel Length ($L_n$):** $180\text{nm}$
* **Goal:** Compare performance and justify the interpretations through DC, Transient, and AC analysis.

---

## 2. Aim
To design and analyze three distinct Common Source (CS) amplifier configurations—Source Degenerated, Active Load, and Diode-Connected Load—ensuring all designs operate within the specified power budget and maintain transistors in the saturation region.

---

## 3. Components Required
* **Simulation Software:** LTSPICE.
* **Technology Library:** tsmc 180nm CMOS library.
* **Active Devices:** NMOS ($M_1, M_3$), PMOS ($M_2$).
* **Passive Devices:** Resistor ($R_S$), Capacitor ($C_L$).
* **Sources:** DC Voltage Sources ($V_{DD}, V_{bias}$), Signal Source ($V_{in}$).

---

## 4. Theoretical Design & Calculations

### 4.1 Power and Current Budgeting
Given the maximum power $P \le 1\text{mW}$ and $V_{DD} = 1.8\text{V}$:
* $I_D \le \frac{1\text{mW}}{1.8\text{V}} = 555.6\mu\text{A}$.
* **Design Target:** We fix **$I_D = 200\mu\text{A}$** to ensure power compliance and thermal stability.

### 4.2 Operating Point and Sizing ($W/L$)
For amplification, the MOSFET must remain in the **Saturation Region**: $V_{DS} \ge V_{ov}$.
* **Saturation Condition Check:** $\frac{V_{DD}}{2} \ge V_{ov} \rightarrow 0.9\text{V} \ge 0.25\text{V}$ (Satisfied).
* **Bias Parameters:** Overdrive voltage $V_{ov} = 0.25\text{V}$, Threshold voltage $V_{th} = 0.36\text{V}$.
* **Gate Bias ($V_{GS}$):** $V_{GS} = V_{ov} + V_{th} = 0.61\text{V}$.

**NMOS Sizing ($M_1$):**
Using $I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{ov})^2$:
* Calculated Width: **$W_n = 4.995\mu\text{m}$** (for $L = 180\text{nm}$).

**PMOS Sizing ($M_2$):**
Using $V_{SG} = |V_{thp}| + V_{ov} = 0.39\text{V} + 0.25\text{V} = 0.64\text{V}$:
* Gate Voltage $V_G = V_{DD} - V_{SG} = 1.16\text{V}$.
* Calculated Width: **$W_p = 11.823\mu\text{m}$**.

### 4.3 Source Resistor ($R_S$) for Degeneration
To provide local negative feedback:
* Let voltage drop $I_D \cdot R_S = 0.2\text{V}$.
* **Resistance:** $R_S = \frac{0.2\text{V}}{200\mu\text{A}} = 1\text{k}\Omega$.
* **New Bias:** $V_{B1} = V_{GS1} + I_D R_S = 0.81\text{V}$.

---

## 5. Circuit Topologies and Simulation Results

### Configuration 1: CS with Source Degeneration ($R_S$)
Utilizes a source resistor to improve linearity and stabilize gain at the cost of magnitude.

* **DC Analysis:** $I_D = 199.1\mu\text{A}$.
* **Transient Analysis:** $V_{in(p-p)} = 19.632\text{mV}$, $V_{out(p-p)} = 223.64\text{mV}$.
* **Voltage Gain ($A_v$):** $11.222\text{ V/V}$ ($21\text{dB}$).
* **AC Analysis:** Bandwidth = $203.52\text{MHz}$.
* **Simulation Waveform:** <img width="1919" height="800" alt="transient ckt1" src="https://github.com/user-attachments/assets/2c7da381-73df-456f-b6dd-4bc83a162a1e" />


### Configuration 2: CS with Active Load (PMOS)
Replaces the resistor with a high-impedance PMOS current source to maximize gain.

* **DC Analysis:** $I_D = 199.3\mu\text{A}$.
* **Transient Analysis:** $V_{in(p-p)} = 19.328\text{mV}$, $V_{out(p-p)} = 279.486\text{mV}$.
* **Voltage Gain ($A_v$):** $14.676\text{ V/V}$ ($23.332\text{dB}$).
* **AC Analysis:** Bandwidth = $422.31\text{MHz}$.
* **Simulation Waveform:** <img width="1916" height="808" alt="AC Analysis ckt2" src="https://github.com/user-attachments/assets/d9da6825-dd8e-412d-a473-d10261eda497" />


### Configuration 3: CS with Diode-Connected Load
Uses a MOSFET load with its gate shorted to its drain, creating a small-signal resistance of $1/g_m$.

* **DC Analysis:** $I_D = 200.007\mu\text{A}$.
* **Transient Analysis:** $V_{in(p-p)} = 19.458\text{mV}$, $V_{out(p-p)} = 79.486\text{mV}$.
* **Voltage Gain ($A_v$):** $4.133\text{ V/V}$ ($12.327\text{dB}$).
* **AC Analysis:** Bandwidth = $140.924\text{MHz}$.
* **Simulation Waveform:** <img width="953" height="785" alt="ckt3 DC" src="https://github.com/user-attachments/assets/205df3da-b262-4be9-9b85-800902ed92e4" />


---

## 6. Performance Comparison & Validation

| Metric | Source Degeneration | Active Load (PMOS) | Diode-Connected |
| :--- | :---: | :---: | :---: |
| **Voltage Gain ($A_v$)** | $11.22$ | **$14.67$** | $4.13$ |
| **3dB Bandwidth** | $203.5\text{ MHz}$ | **$422.3\text{ MHz}$** | $140.9\text{ MHz}$ |
| **GBP** | $2.28\text{ GHz}$ | **$6.19\text{ GHz}$** | $582\text{ MHz}$ |
| **Power Consumed** | $0.358\text{ mW}$ | $0.359\text{ mW}$ | $0.358\text{ mW}$ |

---

## 7. Interpretation & Validation

### 7.1 Validation of Results
1. **Gain Comparison:** The **Active Load** configuration yielded the highest gain ($14.67\text{ V/V}$) as theoretically expected, due to the high output resistance $r_{o1} \parallel r_{o2}$.
2. **Bandwidth:** Configuration 2 (Active Load) achieved the highest bandwidth ($422\text{ MHz}$), proving superior for high-frequency signal processing.
3. **Stability:** The **Diode-Connected** load shows the lowest gain but provides higher stability against process variations since the gain depends on geometric ratios ($g_{m1}/g_{m3}$).

### 7.2 Final Inference
* The **Active Load CS Amplifier** is ideal for applications requiring high gain and speed within integrated circuits.
* **Source Degeneration** is preferred for precision applications where linearity and input swing are more critical than absolute gain.
* All configurations successfully met the power constraint of $\le 1\text{mW}$, with an average consumption of $\approx 0.358\text{mW}$.

---
