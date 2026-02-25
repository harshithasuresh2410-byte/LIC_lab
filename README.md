Course: BEC456B - Linear Integrated Circuits

High-Performance PMOS Common Source Amplifier Design

Technnology node : tsmc 180nm

Introduction : This project involves the design and evaluation of a Common Source (CS) Amplifier using a PMOS transistor. 
By utilizing the 180nm CMOS process, the design achieves a specific quiescent point and gain while strictly adhering to a 1mW power budget. 
This repository documents the transition from theoretical calculations to practical LTspice verification.

Design Parameters & Mathematical Derivations:

Using the provided constraints, the circuit was designed with the following values:

Supply Voltage ($V_{DD}$): 1.8V

Drain Current ($I_D$): 200µA

Power Dissipation ($P$): 0.36mW (Verified - Well below the 1mW limit)

Load Resistance ($R_d$): 4.5kohm

Transistor Dimensions: $W = 5.18144\mu m$,
$L = 180nm$

Simulation Methodology & Results:

1. Circuit Schematic : The design uses a PMOS (M1) in a common source configuration with a resistive load $R_d$.

2. DC Operating Point Analysis :

  Verified through simulation that the transistor is in the Saturation Region: 

  Output Voltage : 0.900022 V

  Drain Current  : 200.0005 µA

3. Transient & AC Analysis

   Phase Relationship: A 180 degree phase shift was observed, confirming CS operation.

   Practical Gain   : 10.4263 dB

   Theoretical Gain : 10.95404 dB

Conclusion

The design successfully meets all requirements and power constraints. 
The minor 4.8% deviation in gain is attributed to the channel length modulation effect of the 180nm PMOS mode
   
