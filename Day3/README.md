# NgspiceSky130-Day3-CMOS switching threshold and dynamic simulations

## Voltage transfer characteristics-SPICE simulations

### L1 SPICE deck creation for CMOS inverter
We will now simulate the VTC. For that we need to **create the SPICE deck**. It is a connectivity information (Netlist). As there is information about substrate, the circuit is as shown below.Here M1 is PMOS and M2 is NMOS</br>

<img width="546" height="501" alt="image" src="https://github.com/user-attachments/assets/87648d3d-9f23-4e6a-b66a-872306e570f1" />

Next we will write down the **Component Vlaues**, keeping W/L for both NMOS and PMOS same.</br>

<img width="622" height="487" alt="image" src="https://github.com/user-attachments/assets/01bb49d8-39b6-40e1-850f-6a6a95dc5946" />

Next we will assume the **Vin and Vout values**

<img width="585" height="482" alt="image" src="https://github.com/user-attachments/assets/38af526d-c53a-4ff7-91c5-bd804fd572da" />

Next step is to **Identify the Nodes** (Node is the point where two components meet)

<img width="766" height="532" alt="image" src="https://github.com/user-attachments/assets/e7a2d759-0ff9-4c2c-939e-ac4af8840cae" />

**Name the nodes** In model file we will mention like, 2.5V input lies between Vin and 0, similarly Vdd lies between vdd and 0.

<img width="592" height="482" alt="image" src="https://github.com/user-attachments/assets/683acee0-3468-498a-9f94-c804122c5a4b" />

Now let us write the SPICE deck:

<img width="1227" height="585" alt="image" src="https://github.com/user-attachments/assets/1b54b47c-edea-4a16-ac0d-fe40405cd393" />
We know for Mosfet the syntax is DGSS(Drain gate source and substrate).

### L2 SPICE simulation for CMOS inverter
<img width="1197" height="582" alt="image" src="https://github.com/user-attachments/assets/6d58c77a-50fe-4eab-9891-287d7a98ae44" />
<img width="1192" height="553" alt="image" src="https://github.com/user-attachments/assets/a06f6d8e-c074-4aa9-9946-6056ed71f927" />
<img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/f4e7acd7-6158-432b-8003-b2c74656f9b0" />

Next comes the **Simulation Commands**</br>
Here we will be sweeping the gate input voltage from 0 to 2.5V with steps of 0.05. We need to find the VTC, for this only we will be sweeping the input voltage and measuring the output voltage.</br>
Final step is to describe the **Model files**, all the information about the technological parameteres is given inside the model files.</br>

<img width="1223" height="565" alt="image" src="https://github.com/user-attachments/assets/1bd6f151-618b-4612-82fd-6b43f7eec459" />

Now we will do the SPICE simulation for Wn=Wp=0.375u, Ln=Lp=0.25u, Wn/ln=Wp/Lp=1.5. Below is the VTC we get for the above netlist.</br>

<img width="743" height="567" alt="image" src="https://github.com/user-attachments/assets/91c4ab55-57f1-45ab-826b-b9a9631647ee" />

Next we will get the VTC for Wn= 0.375u, Wp= 0.9375u, Ln,p=0.25u; Wn/Ln=1.5, Wp/Lp=2.5  (PMOS width is 2.5 times more than NMOS)

<img width="741" height="572" alt="image" src="https://github.com/user-attachments/assets/5d83f191-3962-4e25-99b3-aa5d3f520d92" />

If we observe the previous graph is left shifted slightly. This happens because NMOS is more stronger than PMOS in previous graph.</br>

### L3 Labs Sky130 SPICE simulation for CMOS
We now get the VTC characteristics

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3e6c8b58-05e8-4c43-94a8-e1f8323a9e00" />
We are using both pfet and nfet for CMOS inverter. We can see that W/L ratio of pmos is 2.33 times greater than that of nmos. And we will be sweeping Vin from 0 to 1.8V with step isze of 0.01V and plotting the Vout.</br>

<img width="1913" height="1078" alt="image" src="https://github.com/user-attachments/assets/a9aa02e7-a3f0-4485-9b07-129fd8260d03" />
To get the plot type `ngspice` and `plot out vs in`.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2b2cd0ab-86fa-43cb-aae5-6192e7c52c10" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/e71074c8-50af-44c1-9316-790007b9394e" />

Now we need to know the Switching Threshold from this graph, it is the point when Vin=Vout.</br>
To zoom in the curve; press righ mouse button + hold it.</br>

<img width="1918" height="1076" alt="image" src="https://github.com/user-attachments/assets/f23c8b99-6ef4-49e3-860b-2e0c324f4320" />
So switching threshold for W/L=2.3 is around 0.876V</br>

<img width="280" height="30" alt="image" src="https://github.com/user-attachments/assets/816fa465-de21-4d8d-bff4-fb79ab059723" />

We will now see the transient analysis:</br>
For that we will go inside the tansient SPICE file for day3</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/fe3e84fa-8511-4f02-917e-570de93216d9" />
We can see that it is for typical corner as before and the W/L is also same. But now we taking transient pulse from 0v to 1V with shift of 0 with rise time and fall time being 0.1ns and 0.1ns respectively, pulse width of 2ns and total time period of 4ns. Let us run this.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/93a365ad-7eff-4172-921b-d0301c2978f7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/786bea0f-e506-4475-b099-575545bd0685" />

So for rise delay and fall delay, we need to consider 50% of output curve i.e. at 0.9V; out-in.</br>
<img width="305" height="67" alt="image" src="https://github.com/user-attachments/assets/9e8f888e-74a1-465c-8cb5-71ee3302b0f7" />

Therefore **Rise delay = 2.482ns-2.15ns = 0.333ns**

For fall delay, consider while falling.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/4c675f5c-cef5-4f78-8692-67398bbf94eb" />
<img width="315" height="71" alt="image" src="https://github.com/user-attachments/assets/73197af2-d7b5-4545-a2b6-aebde88f7f20" />
Therefore **Fall Delay = 4.334ns-4.050ns = 0.285ns**

## Static behaviour evaluation-CMOS inverter robustness-Switching Threshold

### L1 Switching Threshold, Vm
Let us compare the two different CMOS inverters with different W/L ratios of PMOS and NMOS, we can see that the shape of the VTC is same in both the cases only the switching threshold is different. This shows the robustnesss of CMOS inverter.</br>

<img width="1243" height="578" alt="image" src="https://github.com/user-attachments/assets/c246dc3c-6686-4d8f-b8a5-74136a9323de" />
Let us find out the Switching threshold, Vm in both the cases by drawing a 45 degree line.</br>

So, in first case Vm comes out to be somewhere around 0.9V and in second case Vm=1.2V.</br>
<img width="1168" height="417" alt="image" src="https://github.com/user-attachments/assets/7b300b9a-c5ee-4a11-ab44-6bc6027f8b63" />

This is the area where PMOS and NMOS both are in saturation region. Current flows from both the transistor, it is actually a dangerous situation.

<img width="1083" height="462" alt="image" src="https://github.com/user-attachments/assets/5b52f85c-c43e-4b4f-b38f-e51e8fe28170" />

### L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p
We will now calculate the value of Vm w.r.t the NMOS and PMOS width and length. </br>
<img width="553" height="367" alt="image" src="https://github.com/user-attachments/assets/6c11d77c-26a3-46e5-bf6c-349740e6eb00" />
<img width="860" height="53" alt="image" src="https://github.com/user-attachments/assets/b8533cc5-176d-4cb7-97c3-7d6ad5f4ec88" />
<img width="557" height="148" alt="image" src="https://github.com/user-attachments/assets/aacac08b-2543-4f88-8ddb-ce58cad2b763" />

### L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm
Now here we will calculate the value of W/L for PMOS and NMOS when Vm is given.</br>
We have to move in reverse fashion, as we need to calculate W/L ratio of PMOS and NMOS such that Switching threshold is exatly half of the power supply Vdd = 2.5V, therefore required Vm = 1.25V.</br>
We will start from the current equation itself i.e. **Idsn = -Idsp**

<img width="962" height="362" alt="image" src="https://github.com/user-attachments/assets/4abd767b-176b-42c2-9e2e-bdf52323fed2" />
Expanding Kp and Kn (Gain factor) </br>
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/950f6372-d1d7-4c18-8cfd-5b1f35cdfce5" />
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/a532b030-2296-4ff8-981d-2ab29cd88dea" />

Now here on the RHS all are constants and we will get the values from the model files except Vm, If we know Vm then we can get the W/L ratios.</br>
So now this will allow us to find out for what value of W/L ratio of PMOS will be greater than NMOS based on values of Vm.</br>
We will now see the behaviour of CMOS for below difference in W/L ratios of PMOS and NMOS.</br>

<img width="301" height="233" alt="image" src="https://github.com/user-attachments/assets/8534791b-2793-4986-bdad-4a2ef6bde1fe" />

### L4 Static and Dynamic simulation of CMOS inverter
* For (W/L)n = (W/L)p = 1.5</br>
  <img width="750" height="567" alt="image" src="https://github.com/user-attachments/assets/1c8f3e81-2023-429d-9a9e-b80e35d3ad09" />

  We can also calculate the "Rise Delay" and "Fall Delay" by using the transient analysis, just like we did earlier.</br>
  <img width="1256" height="512" alt="image" src="https://github.com/user-attachments/assets/836bb013-63a3-44aa-b0d5-d640359c35f7" />

### L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width
We will be doing the SPICE simulations for increased width of PMOS transistors and compare the results.</br>
* (W/L)p = 2(W/L)n</br>
  <img width="1181" height="507" alt="image" src="https://github.com/user-attachments/assets/7333b09a-2e41-40b2-881e-373214b16c5b" />

We can see that the Vm is now increased as the PMOS has become more stronger and it needs more current to charge the output load capacitor.</br>
* (W/L)p = 3(W/L)n</br>
  <img width="1197" height="507" alt="image" src="https://github.com/user-attachments/assets/f3bea4a2-8853-4330-8886-86e6ab224069" />

<img width="1241" height="512" alt="image" src="https://github.com/user-attachments/assets/abf77cdf-93df-45b2-8373-b9d526a1c8e6" />
<img width="1207" height="512" alt="image" src="https://github.com/user-attachments/assets/978a4960-3442-4ba5-bd1b-e8f336f8812a" />

*Note: Rise delay decreases with increase in PMOS width, this shows the time required to charge the output capacitor decreases significantly this is because we have a bigger area.* </br>

### L6 Applications of CMOS inverter in clock network and STA
The final data set we got from above experiment is shown below:

<img width="692" height="236" alt="image" src="https://github.com/user-attachments/assets/0359ac26-996d-423d-bd27-99e08b6dddaa" />

There are some conclusions we draw from this experiment: </br>
* During fabrication, there can be slight variation in sizes of PMOS and NMOS from the required one, but the robustness of CMOS inverter is such that, there is not much difference in the Vm with change in sizes.
* When (W/L)p = 2(W/L)n, we see that RISE-FALL delay are approximately equal, if we simulate then we can get the ratio factor such that the Rise delay and fall delay are equal to each other. This shows "Symmetry" of CMOS inverter.
  
  *This is a typical characteristic of Clock Inverter/buffer where we want the rise delay and fall delay to be equal.* </br>
  <img width="1110" height="653" alt="image" src="https://github.com/user-attachments/assets/30d33241-5e2f-4389-9a80-cd8d2ad5baaf" />
* Other types of cells can be used according to the data path requirement


