# NgspiceSky130-Day5 — CMOS Power Supply and Device Variation Robustness Evaluation

## Static Behavior Evaluation — CMOS Inverter Robustness under Power Supply Variation

### L1 Smart SPICE Simulations for Power Supply Variations
When assessing the robustness of a CMOS inverter, **power supply scaling** is an important factor. As gate length is reduced, operating power decreases. Ideally, CMOS characteristics remain consistent under supply scaling.  

To validate this, two cases were simulated:

![case1](https://github.com/user-attachments/assets/03dcd0b9-4dd3-4762-83b2-9cbb882e7bc3)
![case2](https://github.com/user-attachments/assets/e403056b-c4bb-4b18-a67c-baf5b02842ab)
![case3](https://github.com/user-attachments/assets/f357c6d2-fa02-43bc-bf51-184494cf8858)
![schematic](https://github.com/user-attachments/assets/25f4e021-6818-4e30-85d9-cf300b35bd03)

The voltage transfer characteristics (VTC) were plotted for **Vdd = 2.5V, 2.0V, 1.5V, 1.0V, and 0.5V**:

![vtc](https://github.com/user-attachments/assets/87cf496c-6386-4374-9e92-1a6ef71959c1)

### L2 Advantages and Disadvantages of Low Supply Voltage
The simulated VTCs were analyzed to determine the benefits and trade-offs of reduced supply voltage. The **gain factor** (ΔVout / ΔVin) was used to compare behavior across Vdd values.

![gain-plots-1](https://github.com/user-attachments/assets/dd11da87-d570-4fe1-9439-bd449e39af6a)
![gain-plots-2](https://github.com/user-attachments/assets/102b9c1b-82ce-4d72-bc7e-fb502591c636)

Simulations show energy consumption decreases with lower Vdd:

![energy-1](https://github.com/user-attachments/assets/f9a05a5f-40c0-4bad-be1f-3cd16f1445f4)
![energy-2](https://github.com/user-attachments/assets/b96be82f-5993-4fd1-9cc2-c0756dc212df)

**Advantages of low supply voltage**
- Lower dynamic energy per switching event.
- Reduced overall power consumption in many operating regimes.

**Disadvantages**
- Slower charging/discharging of load capacitances — increases rise and fall delays and degrades performance at low Vdd.

### L3 Sky130 Supply Variation Lab
Supply was swept from **1.8V** downward in **0.2V** steps (six iterations) and the gain was computed for each step:

![supply-sweep](37.png)
![sweep-setup](39.png)
![sweep-result](40.png)

Example result:
- **Vdd = 1.8V → |Gain| = 7.6229**

## Static Behavior Evaluation — CMOS Inverter Robustness under Device Variation

### L1 Sources of Variation — Etching Process
Etching can introduce variations in gate length (L) and width (W). In layout views, the polysilicon-diffusion overlap area and edges reveal where variations are most likely. Device dimensions may vary more at edges than at the center, causing changes in drain current across devices and across an inverter chain.

![layout1](https://github.com/user-attachments/assets/f4496266-b2a9-4e21-bb84-54e6519478e4)
![chain1](https://github.com/user-attachments/assets/a326d12c-e0b7-4daa-bf13-311ccaa8e476)
![chain2](https://github.com/user-attachments/assets/8683fe6c-a634-4720-98d4-8ef619ab52b1)
![edge-variation](https://github.com/user-attachments/assets/998d8d7c-941f-4643-a768-13896c578018)
![Id-variation](https://github.com/user-attachments/assets/b1c7130a-de89-4cf1-ab2e-064702878082)

### L2 Sources of Variation — Oxide Thickness
Variations in gate oxide thickness (tox) change the gate capacitance (Cox = εox / tox) and therefore affect drain current. Cross-sectional views illustrate differences between ideal and actual tox values.

![xsec1](https://github.com/user-attachments/assets/25b705ca-1d73-4127-a9bc-a69e2af0c8c2)
![xsec2](https://github.com/user-attachments/assets/df455509-4718-4074-9eda-bb314e6462c0)
![tox-variation](https://github.com/user-attachments/assets/a802cce3-df91-4e80-9b34-d2f931de9f8d)
![cox-equation](https://github.com/user-attachments/assets/d06ee6da-3467-41cb-8a0e-280b15faae56)

### L3 Smart SPICE Simulation for Device Variations
SPICE simulations examined extreme device cases: **strong PMOS / weak NMOS** (larger PMOS width — lower resistance) and **strong NMOS / weak PMOS** (larger NMOS width). VTC shifts and noise margins were observed for these conditions.

![sim-1](https://github.com/user-attachments/assets/398d01a6-ffc4-4a10-86a8-3907d3214b69)
![sim-2](https://github.com/user-attachments/assets/41b1f2f6-c4ba-4c71-a8e6-d1fc8e3b4844)
![sim-3](https://github.com/user-attachments/assets/9314e15f-c027-47ba-b34e-f35d886e5aff)
![sim-4](https://github.com/user-attachments/assets/280f196e-1bde-417a-9955-7a0f2029ee39)
![sim-5](https://github.com/user-attachments/assets/33e8fc0e-5220-4dc4-8da9-4c8dd5406e02)

### L4 Conclusions
From the simulated data:

- The switching threshold \(V_m\) shifts **right** when PMOS is strong and **left** when NMOS is strong.
  
![Vm-shift](https://github.com/user-attachments/assets/aec473f9-00f5-4028-b122-fa2922affcb3)

- Noise margins do not vary significantly in these extreme cases, indicating the inverter remains robust across the tested device variations.

![noise-margins](https://github.com/user-attachments/assets/38851b7b-ec82-4400-93d8-c3c651d51ae9)
![summary](https://github.com/user-attachments/assets/edd63a58-b8bb-462e-84e5-b8c977d4a4d2)

### L5 Sky130 Device Variation Lab
SPICE setups show PMOS width significantly larger than NMOS (strong PMOS / weak NMOS), causing the VM to be right-shifted:

![device-lab-1](41.png)
![device-lab-2](42.png)
![device-lab-3](43.png)
![device-lab-4](44.png)
