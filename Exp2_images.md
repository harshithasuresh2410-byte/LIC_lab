## Experiment 2: Detailed Analysis of CS Amplifier Topologies

##  Project Objective
To design and analyze three Common Source (CS) amplifier configurations using **tsmc 180nm** technology. We aim to maintain a power budget of $P \le 1mW$ and a drain current $I_D \approx 200\mu A$.

---

## 1. Configuration A: CS Amplifier with Source Resistance ($R_S$)

### 1.1 Circuit Schematic

<img width="1068" height="828" alt="ckt1" src="https://github.com/user-attachments/assets/6ba315ce-bd95-40a4-b2ac-7c89cee4eed0" />


### 1.2 Theoretical Calculations
* **Transconductance ($g_m$):** $g_m = \sqrt{2\mu_n C_{ox} \frac{W}{L} I_D}$
* **Voltage Gain ($A_v$):** $$A_v = \frac{-g_{m1} \cdot R_D}{1 + g_{m1} \cdot R_S}$$
* **Input/Output Swing:** Limited by $V_{ov}$ and $I_D \cdot R_S$.

### 1.3 Simulation Results
* **DC Analysis:** * $V_{GS} \approx 0.7V$, $V_{DS} \approx 0.9V$. 
    * Result: $M_1$ is in Saturation ($V_{DS} > V_{GS} - V_{th}$).
    <img width="942" height="780" alt="DC ckt1" src="https://github.com/user-attachments/assets/ef8de1b5-6390-4282-bd10-40c29466f550" />

* **Transient Analysis:** * Input: $20mV_{p-p}$ | Output: $224.4mV_{p-p}$
    * **Gain:** $11.22 V/V$
    <img width="1919" height="800" alt="transient ckt1" src="https://github.com/user-attachments/assets/f05944ac-3d1d-4c2d-b37e-a2cb30a65f97" />

* **AC Analysis:** * **3dB Bandwidth:** $203.52 MHz$
    * **UGB:** $2.28 GHz$
    <img width="1919" height="793" alt="AC Analysis ckt1" src="https://github.com/user-attachments/assets/8fe216c0-89cd-43ab-9ad5-b14ff2953fe2" />

---

## 2. Configuration B: CS Amplifier with Active Load (PMOS)

### 2.1 Circuit Schematic

<img width="1195" height="829" alt="ckt2" src="https://github.com/user-attachments/assets/88739370-cd66-422e-920e-3de073e63e40" />


### 2.2 Theoretical Calculations
* **Output Resistance ($R_{out}$):** $R_{out} = r_{o1} \parallel r_{o2}$
* **Voltage Gain ($A_v$):**
$$A_v = -g_{m1} (r_{o1} \parallel r_{o2})$$

### 2.3 Simulation Results
* **DC Analysis:** Used to fix $V_{bias}$ for the PMOS to maintain $200\mu A$ current.
    <img width="965" height="779" alt="DC op pnt ckt2" src="https://github.com/user-attachments/assets/d130ff49-0598-4c8a-ab37-319eb25d077f" />

* **Transient Analysis:** Maximum swing observed due to active load characteristics.
    * **Gain:** $14.67 V/V$
    <img width="1915" height="806" alt="transient analysis ckt2" src="https://github.com/user-attachments/assets/0ccaca6d-5a65-4ca5-8a01-f4619592153d" />

* **AC Analysis:** * **3dB Bandwidth:** $422.31 MHz$
    <img width="1916" height="808" alt="AC Analysis ckt2" src="https://github.com/user-attachments/assets/b275a383-1744-4225-b64e-2889b1f5427d" />

---

## 3. Configuration C: CS Amplifier with Diode-Connected Load

### 3.1 Circuit Schematic

<img width="1272" height="824" alt="ckt3 exp2" src="https://github.com/user-attachments/assets/9b2b8987-535d-4f6b-9c33-1e766cd12fa9" />


### 3.2 Theoretical Calculations
* **Load Resistance:** $R_L = \frac{1}{g_{m3}}$
* **Voltage Gain ($A_v$):**
$$A_v \approx -\frac{g_{m1}}{g_{m3}} = -\sqrt{\frac{(W/L)_1}{(W/L)_3}}$$

### 3.3 Simulation Results
* **DC Analysis:** <img width="953" height="785" alt="ckt3 DC" src="https://github.com/user-attachments/assets/160fa4be-6aac-461f-85d7-a20b2f89a76d" />

* **Transient Analysis:** Stable but lower gain due to low impedance load ($1/g_m$).
    * **Gain:** $4.13 V/V$
    <img width="1916" height="834" alt="transient analysis ckt3" src="https://github.com/user-attachments/assets/a5073c75-d8c5-41a2-8c64-15259836331a" />

* **AC Analysis:** * **3dB Bandwidth:** $140.92 MHz$
    <img width="1914" height="835" alt="ckt3 AC" src="https://github.com/user-attachments/assets/c6576bb3-8dba-42a1-a0af-099f3954c782" />


---

## 📈 Final Performance Comparison

| Configuration | Gain ($A_v$) | 3dB BW | UGB ||
| :--- | :---: | :---: | :---: | :---: |
| **Source Degeneration** | 11.22 | 203.52 MHz | 2.28 GHz |
| **Active Load** | **14.67** | **422.31 MHz** | **6.19 GHz** |
| **Diode-Connected** | 4.13 | 140.92 MHz | 582.45 MHz |

---

## 💡 Conclusion
From the analysis, **Configuration B (Active Load)** is the most efficient for high-performance integrated circuits, providing the highest gain and bandwidth. **Configuration A** offers a balanced approach with improved linearity, while **Configuration C** is suitable for process-insensitive gain requirements.
