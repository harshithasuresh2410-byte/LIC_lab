MOSFET and Common Source Amplifier: Fundamental Theory

1. Introduction to MOSFETs : 
The MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) is a voltage-controlled device used for switching and amplification.
Unlike a Bipolar Junction Transistor (BJT) which is current-controlled, the MOSFET uses an electric field at the Gate to control the flow of current between the Source and Drain.

2. Classification of MOSFETs : 

    MOSFETs are classified by the type of channel formed between the Source and Drain : 

   NMOS (n-channel MOSFET):

    Majority Carriers : Electrons (negative charge).

    Substrate : p-type.

    Control : Turns ON when $V_{GS}$ is positive and exceeds the threshold ($V_{GS} > V_{th}$).

    Efficiency : Generally faster due to higher electron mobility.

   PMOS (p-channel MOSFET)

    Majority Carriers: Holes (positive charge).

    Substrate: n-type.

    Control: Turns ON when $V_{GS}$ is negative ($V_{GS} < V_{th}$).

   Usage: Used in this specific experiment for the Common Source configuration.

3. NMOS: Regions of Operation

    The NMOS enters different regions based on the relationship between $V_{GS}$, $V_{DS}$, and $V_{th}$:

     (i) Cut-off Region:

          * Condition: $V_{GS} < V_{th}$

          Behavior: No channel exists.
          The transistor is "OFF."

     (ii) Triode (Linear) Region: * Condition: $V_{GS} > V_{th}$ AND $V_{DS} < (V_{GS} - V_{th})$

           Behavior: The channel is continuous.
           The transistor acts like a voltage-controlled resistor.

     (iii) Saturation (Active) Region:

            * Condition: $V_{GS} > V_{th}$ AND $V_{DS} \geq (V_{GS} - V_{th})$

            Behavior: The channel "pinches off" at the drain.

            Current ($I_D$) becomes independent of $V_{DS}$.
            This is the region required for Amplification.

   4. PMOS: Regions of Operation

       Because PMOS uses holes, the conditions are often written using absolute values ($|V|$) to avoid confusion with negative signs:

        (i) Cut-off Region:

             * Condition: $|V_{GS}| < |V_{th}|$
      
             Behavior: No hole flow.
             Transistor is "OFF".
      
        (ii) Triode (Linear) Region:
       
              * Condition: $|V_{GS}| > |V_{th}|$ AND $|V_{DS}| < (|V_{GS}| - |V_{th}|)$

              Behavior: Transistor is fully "ON" with low resistance.

        (iii) Saturation (Active) Region:

               * Condition: $|V_{GS}| > |V_{th}|$ AND $|V_{DS}| \geq (|V_{GS}| - |V_{th}|)$

                Behavior: Current is stable.
                This is where we bias the PMOS for the Common Source Amplifier.

   5. The Common Source (CS) Amplifier

      The CS Amplifier is the most basic single-stage amplifier topology.
     
       Configuration: The Source terminal is common to both the input and output (connected to $V_{DD}$ for PMOS).

       Input/Output: Signal enters the Gate and is taken from the Drain.

       Phase Shift: A key characteristic is the 180° phase inversion.
       As input voltage increases, the $V_{GS}$ of the PMOS effectively decreases,
       reducing the current and causing the output voltage to move in the opposite direction of the input.

   6. Project Context: Why We Perform This Experiment

      Performing this experiment in a 180nm process is vital for the following reasons:

      (i) Theory vs. Simulation:
          To verify that the hand-calculated load resistance ($R_d = 4.5k\Omega$) correctly biases the circuit at the desired operating point ($200\mu A$ current).

      (ii) Power Constraints:
           To learn design discipline by meeting a strict 1mW power budget ($0.36mW$ achieved).

      (iii) Short-Channel Effects:
            At 180nm, secondary effects like Channel Length Modulation ($r_o$) become visible,
            showing why practical gain ($10.4dB$) differs slightly from theoretical gain ($10.9dB$).
       (iv) Engineering Workflow:
            To master the full design cycle:
            Hand Calculations → LTspice Simulation → Performance Verification.

   
