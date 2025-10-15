# NgspiceSky130-Day4 — CMOS Noise Margin Robustness Evaluation

## Static Behavior Evaluation — CMOS Inverter Robustness to Noise Margin

### L1 Introduction to Noise Margin
This section explores the CMOS inverter’s robustness with respect to **noise margin** and its evaluation using simulations.  
**Noise Margin** quantifies how much unwanted electrical noise a logic circuit can withstand on its input without causing an incorrect output.

In an ideal inverter, for inputs 0 and 1, outputs are 1 and 0 respectively, with an infinite switching slope:

![ideal-inverter](https://github.com/user-attachments/assets/2465a4e2-199d-4698-aa7d-58f0b42f0c6f)

In practice, the slope becomes finite due to parasitic resistances and capacitances that introduce delay:

![practical-slope](https://github.com/user-attachments/assets/f8f2f3f3-dc21-45eb-90b7-c9f2fdb8ef94)

For input values between **0 and VIL (input low voltage)**, the output remains at **VOH (output high)**.  
When the input lies between **VIH (input high voltage)** and **Vdd**, the output drops to **VOL (output low)**.

![inverter-vohvih](https://github.com/user-attachments/assets/8e3c22bf-b012-4a75-a08d-910511ed2980)

### L2 Noise Margin Voltage Parameters
Under non-ideal conditions, the inverter transfer curve is more gradual.  
When **0 < Vin < VIL**, the output stays within **VOH < Vout < Vdd**, and when **VOL < Vin < Vdd**, the output lies within **0 < Vout < VOL**.  
It follows that **VOL < VOH < Vdd**, and **0 < VOL < VIL**.  

The slope around the transition is roughly -1, as an increase in Vin results in a decrease in Vout.

![nonideal-vtc](https://github.com/user-attachments/assets/d848d4c0-de9b-4b6b-8c6a-f3006bae557c)

### L3 Noise Margin Equation and Summary
To compute the noise margins, both input and output voltages are plotted on the same axis:

![vtc-overlay](https://github.com/user-attachments/assets/c25a3266-d8f3-4e16-8afa-298756b3a59d)

From the plot:
- **Noise Margin High (NMH)** = VOH − VIH  
- **Noise Margin Low (NML)** = VIL − VOL  

Voltages that fall within these noise margins are considered logically valid (‘0’ or ‘1’).  
Values outside this range are undefined and may fluctuate between logic levels.

![noise-graph1](https://github.com/user-attachments/assets/80791538-0e36-46a8-9bf1-043e740dd778)
![noise-graph2](https://github.com/user-attachments/assets/6443e129-644a-4d0d-a4c4-0439ba4165de)

### L4 Noise Margin Variation with PMOS Width
Next, the dependence of noise margin on **PMOS width** is analyzed to demonstrate CMOS inverter robustness.  
The slope points where **dVout/dVin = -1** are identified and extended to locate VIL, VIH, VOL, and VOH.

![pmos-variation-1](https://github.com/user-attachments/assets/5ab8cb26-4ab7-4e77-9a04-be82cfcdac12)

A larger noise margin indicates a stronger and more noise-tolerant inverter.

![pmos-variation-2](https://github.com/user-attachments/assets/98daed0b-5528-4d72-8a99-06806511d1b8)
![pmos-variation-3](https://github.com/user-attachments/assets/89b5f850-df64-4e6e-abcb-366cc3755d13)
![pmos-variation-4](https://github.com/user-attachments/assets/13199ec4-704c-4812-aba2-38257330e40b)

For **(W/L)p = 4(W/L)n** and **(W/L)p = 5(W/L)n**, the noise margins remain the same, indicating that beyond a certain PMOS width, further increase does not improve noise immunity.

![pmos-table](https://github.com/user-attachments/assets/fca7bcac-471c-4114-8c64-4b97cba1f5b0)

This verifies the robustness of the CMOS inverter and helps distinguish the operational regions used in **digital** versus **analog** design.

![digital-vs-analog-1](https://github.com/user-attachments/assets/3e9a0cf6-a232-4ff2-ad4c-214b03803af3)
![digital-vs-analog-2](https://github.com/user-attachments/assets/56c5c94d-b59f-456c-ba92-b22fab03b6d9)

### L5 Sky130 Noise Margin Lab
The Sky130 SPICE simulations were performed to measure noise margins experimentally.

![lab-setup](32.png)

PMOS/NMOS ratio was set to **(W/L)p:(W/L)n = 2.77**, and **Vin** was swept from **0 to 1.8 V** with a step of **0.01 V**.

![lab1](33.png)
![lab2](34.png)
![lab3](35.png)
![lab4](36.png)

The points where the slope equals **-1** give **VIL, VIH** (x-axis) and **VOL, VOH** (y-axis).

**Calculated results:**
- **Noise Margin High (NMH)** = VOH − VIH = 1.70952 − 0.98778 = **0.72 V**  
- **Noise Margin Low (NML)** = VIL − VOL = 0.7733 − 0.09523 = **0.678 V**
