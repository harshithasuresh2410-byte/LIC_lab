## MOSFET and Common Source Amplifier: Fundamental Theory

## 1. Introduction to MOSFETs : 
The MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) is a voltage-controlled device used for switching and amplification.
Unlike a Bipolar Junction Transistor (BJT) which is current-controlled, the MOSFET uses an electric field at the Gate to control the flow of current between the Source and Drain.

## 2. Classification of MOSFETs : 

MOSFETs are classified by the type of channel formed between the Source and Drain : 

**NMOS (n-channel MOSFET):**

<img width="474" height="477" alt="Screenshot 2026-02-26 042704" src="https://github.com/user-attachments/assets/f239ec41-eec7-45dd-a4d2-14cba70261e9" />

* _Majority Carriers_ : __Electrons__ (negative charge).

* _Substrate_ : __p-type__

* _Control_ : Turns ON when $V_{GS}$ is positive and exceeds the threshold ($V_{GS} > V_{th}$).

* _Efficiency_ : Generally faster due to higher electron mobility.

**PMOS (p-channel MOSFET)**

<img width="449" height="484" alt="Screenshot 2026-02-26 042828" src="https://github.com/user-attachments/assets/97b8dda1-7b68-4df6-8ee1-7f4d64d96a12" />

* _Majority Carriers_: __Holes__ (positive charge).

* _Substrate_: __n-type__.

* _Control_: Turns ON when $V_{GS}$ is negative ($V_{GS} < V_{th}$).

* _Usage_: Used in this specific experiment for the Common Source configuration.

## 3. NMOS: Regions of Operation

The NMOS enters different regions based on the relationship between $V_{GS}$, $V_{DS}$, and $V_{th}$:

__(i) Cut-off Region:__

* Condition: $V_{GS} < V_{th}$

* Behavior: No channel exists.
The transistor is "OFF."

__(ii) Triode (Linear) Region__:

* Condition: $V_{GS} > V_{th}$ AND $V_{DS} < (V_{GS} - V_{th})$

* Behavior: The channel is continuous.
The transistor acts like a voltage-controlled resistor.

__(iii) Saturation (Active) Region:__

* Condition: $V_{GS} > V_{th}$ AND $V_{DS} \geq (V_{GS} - V_{th})$

* Behavior: The channel "pinches off" at the drain.

* Current ($I_D$) becomes independent of $V_{DS}$.
This is the region required for Amplification.

## 4. PMOS: Regions of Operation

Because PMOS uses holes, the conditions are often written using absolute values ($|V|$) to avoid confusion with negative signs:

__(i) Cut-off Region:__

* Condition: $|V_{GS}| < |V_{th}|$
      
* Behavior: No hole flow.
Transistor is "OFF".
      
__(ii) Triode (Linear) Region:__
       
* Condition: $|V_{GS}| > |V_{th}|$ AND $|V_{DS}| < (|V_{GS}| - |V_{th}|)$

* Behavior: Transistor is fully "ON" with low resistance.

__(iii) Saturation (Active) Region:__

* Condition: $|V_{GS}| > |V_{th}|$ AND $|V_{DS}| \geq (|V_{GS}| - |V_{th}|)$

* Behavior: Current is stable.
  This is where we bias the PMOS for the Common Source Amplifier.

 ## 5. The Common Source (CS) Amplifier

<img width="184" height="179" alt="image" src="https://github.com/user-attachments/assets/ee110eee-af0b-452f-ba6b-15b517c3f485" />

The CS Amplifier is the most basic single-stage amplifier topology.
     
* **Configuration**: The Source terminal is common to both the input and output (connected to $V_{DD}$ for PMOS).

* **Input/Output:** Signal enters the Gate and is taken from the Drain.

* **Phase Shift:** A key characteristic is the 180° phase inversion.
As input voltage increases, the $V_{GS}$ of the PMOS effectively decreases,reducing the current and causing the output voltage to move in the opposite direction of the input.

## 6. Project Context: Why We Perform This Experiment

Performing this experiment in a 180nm process is vital for the following reasons:

(i) __Theory vs. Simulation:__
To verify that the hand-calculated load resistance ($R_d = 4.5k\Omega$) correctly biases the circuit at the desired operating point ($200\mu A$ current).

(ii)__Power Constraints:__
To learn design discipline by meeting a strict 1mW power budget ($0.36mW$ achieved).

(iii) __Short-Channel Effects:__
At 180nm, secondary effects like Channel Length Modulation ($r_o$) become visible,
showing why practical gain ($10.4dB$) differs slightly from theoretical gain ($10.9dB$).

(iv) __Engineering Workflow:__
To master the full design cycle:
Hand Calculations → LTspice Simulation → Performance Verification.

   
