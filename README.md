**Name : Harshitha S**

**USN  : 4NI24EC051**

__Course: BEC456B - Linear Integrated Circuits.__

__Technnology node : tsmc 180nm.__

 #                                           High-Performance PMOS Common Source Amplifier Design.


## 1. Introduction : 

This project involves the design and evaluation of a Common Source (CS) Amplifier using a PMOS transistor. 
By utilizing the 180nm CMOS process, the design achieves a specific quiescent point and gain while strictly adhering to a 1mW power budget. 
This repository documents the transition from theoretical calculations to practical LTspice verification.

## 2. Design Parameters & Mathematical Derivations:

Using the provided constraints, the circuit was designed with the following values:

_Supply Voltage_ ($V_{DD}$): __1.8V__

_Drain Current_ ($I_D$): __200µA__

_Power Dissipation_ ($P$): __0.36mW__ (Verified - Well below the 1mW limit)

_Load Resistance_ ($R_d$): __4.5kohm__

_Transistor Dimensions_:  
__$W = 5.18144\mu m$__,
__$L = 180nm$__

## 3. Simulation Methodology & Results:

  __1. Circuit Schematic :__
  
  The design uses a PMOS (M1) in a common source configuration with a resistive load $R_d$.

  __2. DC Operating Point Analysis :__

  Verified through simulation that the transistor is in the Saturation Region: 

  _Output Voltage_ : __0.900022 V__
 
  _Drain Current_  : __200.0005 µA__

__3. Transient & AC Analysis__

Phase Relationship: A 180 degree phase shift was observed, confirming CS operation.

_Practical Gain_   : __10.4263 dB__

_Theoretical Gain_ : __10.95404 dB__

__4. Conclusion__

The design successfully meets all requirements and power constraints. 
   
The minor 4.8% deviation in gain is attributed to the channel length modulation effect of the 180nm PMOS mode
   
