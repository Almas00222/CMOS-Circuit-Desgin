# NgspiceSky130-Day2-Velocity saturation and basics of CMOS inverter VTC

## SPICE simulation for lower nodes and velocity saturation effect

### L1 SPICE simulation for lower nodes
We have seen the curve for Id vs Vds, for different values of Vgs.</br>

<img width="1297" height="658" alt="image" src="https://github.com/user-attachments/assets/c10158ab-7588-4862-96a0-19125d4a3e25" />

In the above graph the area left of curve; Vds=Vgs-Vt is Linear region as current is increasing linearly, the area right is Saturation region with slight increase in current due to velocity saturation and below is the Cut off region.Also this case is when the channel length is large.</br>

Now we are taking different W and L, but the ration of W/L is same as previous, so the Id should not change. But this is not the case practically.</br>
Below is the spice deck, where only the values of W and L is changed, rest everything remains same.</br>

<img width="872" height="442" alt="image" src="https://github.com/user-attachments/assets/09eec98c-92a0-409e-a6c5-5b2a18e8289d" />

### L2 Drain current vs gate voltage for long and short channel device
Let us compare the two simulations we did.

<img width="1385" height="547" alt="image" src="https://github.com/user-attachments/assets/0dd21cb8-3868-4074-909f-accde3fa2556" />

**There are some Observations:**
* **Observation 1**- If we see Id values for different Vgs and for Vds=2.5V, there is a quadratic dependency of Id on Vgs. Whereas for short channel device, at Vds=2.5V, the current is increasing linearly due to velocity saturation.</br>

<img width="1385" height="547" alt="image" src="https://github.com/user-attachments/assets/3eb690d9-a38c-4c97-a9b2-2b0b5148ff63" />
<img width="747" height="540" alt="image" src="https://github.com/user-attachments/assets/7f388d3d-9e7c-45ad-b70b-65a1d846f961" />

Now we will plot graph of Id vs Vgs and sweeping Vds or keeping Vds constant = 2.5V.</br>

<img width="855" height="442" alt="image" src="https://github.com/user-attachments/assets/658d2ba4-4e01-4e20-9a01-e949f3f88cb9" />

The syntax explains that what will be there on left hand side will be sweeped at every value on right hand side. For example here for every value of Vdd, Vin will be sweeped. The plot we get is quadratic, it is only when Vds=2.5V </br>

<img width="776" height="641" alt="image" src="https://github.com/user-attachments/assets/fd8321e8-6235-4c84-aa42-411747b0f599" />

Let us see the same effect for short channel device. For L=0.25 micron.
<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/ffba63a2-5ce1-42c5-a7f0-0f61fe194d12" />

### L3 Velocity saturation at lower and higher electric fields
For short channel we will see more of a linear behaviour as the Vgs increases. This is due to velocity saturation effect.</br>

<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/95aa490e-3dc0-4875-b74a-836c1ae07486" />
So, for lower node we will have 4 regions of operations: **Cut Off, Linear, Saturation and Velocity Saturation**

**Velocity Saturation**
We know velocity and electric field are related to each other with equation `v=uE`, where v is velocity, E is electric field and u is mobility. Velocity increases linearly with electric field over certain electric field value after which it gets saturated. This is due to scattering at higher fields and mobility decreases. </br>

<img width="973" height="506" alt="image" src="https://github.com/user-attachments/assets/57f60dd0-b579-4e67-962d-03c21c430e49" />

Velocity saturation happens for higher gate-source voltages.</br>

<img width="1011" height="470" alt="image" src="https://github.com/user-attachments/assets/bf8911ed-1708-4c95-adc1-f6816f66a689" />

### L4 Velocity saturation drain current model
<img width="987" height="473" alt="image" src="https://github.com/user-attachments/assets/cbe1cdbb-8b18-4c19-97c6-be3e4244fb34" />

Let us take Vgs-Vt=Vgt because we will be taking Vgs as large values. Current equation we will be using as shown above, For lower values of Vds we will neglect the 'lambda' term.</br>
There is one more technology paramter which is "Vdsat", it is the velocity of gate when the device just enters the Velocity saturation region.</br>
<img width="831" height="212" alt="image" src="https://github.com/user-attachments/assets/2e70d7d1-4891-4488-90e8-93f9b5f1322c" />

<img width="1026" height="536" alt="image" src="https://github.com/user-attachments/assets/724c8f7e-e772-4006-9f39-05d7a8e06b56" />

<img width="1080" height="540" alt="image" src="https://github.com/user-attachments/assets/13ace523-0233-4dd0-802d-d1ab5f026de6" />

<img width="1006" height="538" alt="image" src="https://github.com/user-attachments/assets/2d5432ec-2438-41c5-9b52-2f658a17c006" />

<img width="1331" height="583" alt="image" src="https://github.com/user-attachments/assets/5a5755f0-0723-4aea-8f07-e277cf3fdf18" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.</br>

* **Observation 2** - The saturation current for lower nodes is low instead of being high. This is because Velocity saturation tends to saturate the device early so the peak current we see for lower nodes is much lesser than for higher nodes.</vr>
<img width="1370" height="576" alt="image" src="https://github.com/user-attachments/assets/82010154-16a3-4079-a57c-e5a7435b9507" />

### L5 Labs Sky130 Id-Vgs
We will now do simulation for lower nodes. Inside day2 design file.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2e30ad35-dbfe-42e4-a2c6-1c3e3ffd3d8b" />

<img width="1915" height="1078" alt="image" src="https://github.com/user-attachments/assets/46853bc0-6ac5-4d4e-8c34-133b54530564" />

We can see above, simulation is being done for L=0.15u and W=0.39u.</br>
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0112c1fb-efa5-4eb2-a5c2-9c34923067ab" />
<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/05b5bf4a-79e4-4b9e-b92d-938707164205" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3455d86b-dd2b-4b41-aad6-4bee2f683440" />

The above plot is Id vs Vds for different values of Vgs. We can see for lower values of Vgs it is showing quadratic behaviour and for higher values of Vgs it is showing Linear behaviour. Now if want to see the peak current for Vgs=1.8V, just 'press' left click on mouse at Vgs=1.8V.</br>

<img width="290" height="22" alt="image" src="https://github.com/user-attachments/assets/83d91519-32f9-4d17-b88a-379635529e9a" />
So we can see it is approximately 198uA.</br>

**Now let us observe Id vs Vgs**
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/38b27e55-94b1-4190-9191-e022f3e3d548" />

Here again we are taking values for L=0.15u and W=0.39u, Keeping Vds constant at 1.8V and sweeping Vgs from 0 to 1.8V with step of 0.1V.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2c4fd12f-4995-43bc-b1bd-faaa1d6291a7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/17f7032a-f654-4c22-81e9-acbc1cbe368f" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/b490e2f2-76aa-49f1-b37c-e986cb3e4126" />
In the above graph we can see that, due to short channel effect we are seeing a linear behaviour for higher Vgs and Vds being constant.</br>

### L6 Labs Sky130 Vt
Now we will calculate Threshold Voltage Vt for Id vs Vgs curve.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/1e4b97da-884d-4447-b8ae-4d83ff1aef33" />

In the curve we can see that Vt is the value when current increases drastically for small change in Vgs. To calculate we will draw tangent on the curve and see where it touches.</br>

<img width="292" height="30" alt="image" src="https://github.com/user-attachments/assets/dfd6b8ca-308f-425e-97d0-58cb1799fca4" />

It comes at around 0.76V.

## CMOS voltage transfer characteristics (VTC)

### L1 MOSFET as a switch
We will now look at the device parameters from the switch point of view.</br>

<img width="907" height="508" alt="image" src="https://github.com/user-attachments/assets/6bb70912-c36e-4031-bf01-7e05871b28a8" />
The above shows MOSFET as a switch:
* When |Vgs|<Vt, device is OFF and it acts as open switch
* When |Vgs|>Vt, device is ON and it acts as closed switch

<img width="1220" height="685" alt="image" src="https://github.com/user-attachments/assets/48869cbb-daee-4a3b-96a8-bdd0fb45a79f" />

### L2 Introduction to standard MOS voltage current parameters
We are trying to get the equivalent circuit of CMOS when Vin is 'high' and 'low', so that we can get the Voltage Transfer Characteristics (VTC) and therefore calculate the delay of the cell.</br>

* When we take Vin as 'high' and equal to Vdd, PMOS will be OFF and NMOS will be ON
<img width="1292" height="680" alt="image" src="https://github.com/user-attachments/assets/f65a1301-44f9-482e-b8dd-7b5cb3d39e47" />

* When we take Vin as 'low' or equal to '0', PMOS will be ON and NMOS will be OFF.
<img width="1347" height="696" alt="image" src="https://github.com/user-attachments/assets/c15bdbc8-99af-48e0-a23c-726e7e415b66" />

So we can see that when Vin=Vdd there is a direct path that exists between Vss and Vout, the capacitor CL discharges through the resistor.</br>
Similarly when Vin=0 there is a direct path between Vdd and Vout, CL charges.</br>
<img width="1322" height="428" alt="image" src="https://github.com/user-attachments/assets/a4f22e15-1c9a-44cf-bfa2-e27b37557439" />

Let us give the naming convention of the CMOS 

<img width="506" height="618" alt="image" src="https://github.com/user-attachments/assets/7225993f-5a53-4456-9959-3cdf52d77960" />

ALso the current in both the condition is Idsn(drain to source for NMOS) and Idsp(Drain to source for PMOS)
And **Idsp = -Idsn**, both are opposite in direction to each other.

### L3 PMOS/NMOS drain current vs drain voltage
<img width="485" height="677" alt="image" src="https://github.com/user-attachments/assets/f2026254-f2b7-4623-967a-79fbc649a8ea" />

Now if we talk about the curve between Idsn Vs Vdsn and Idsp Vs Vdsp, it is as shown below.

<img width="897" height="432" alt="image" src="https://github.com/user-attachments/assets/2e55422f-9659-4ce7-b6ac-b1fe6d41d1a0" />

### L4 Step1- Convert PMOS gate-source-voltage to Vin
We have seen various internal voltages, but actually in terms of user's perspective we can't see the internal voltages and only see the external Vin and Vout. From these we calculate the VTC and eventually we get to know the delay.</br>

**Now we will see the steps to obtain Voltage Transfer Characteristics(VTC) for static CMOS inverter:**
*Assumption: Let us assume that it is a long channel device with Vdd=2V*
* We will fix the Vgs values as shown below
  <img width="372" height="237" alt="image" src="https://github.com/user-attachments/assets/081d616c-e17f-4741-8a96-0d5eae2b2b9a" />
  
* We know that Vgsp= Vin-Vdd, So we get the above values.So we get Vin = Vgsp+Vdd, we are trying to convert all the voltages as function of Vin and Vout.
* We will try to plot the graph of PMOS in terms of Idsn, the plot will be as shown below. We can see that the corresponding Vin value of Vgsp is being plotted as shown in the above table.

  <img width="871" height="443" alt="image" src="https://github.com/user-attachments/assets/cd415d3f-042b-460e-8314-4bb28d50d663" />

### L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout
Now we be converting the Vdsp and function of output voltage Vin. We know **Vdsp = Vout-Vdd**.</br>
Let us convert Vdsp into Vout. So to get Vout there is a shift of Vdd towards left hand side.</br>

<img width="1333" height="391" alt="image" src="https://github.com/user-attachments/assets/c9709e57-c876-4521-9ff6-88fb68f9927c" />

We can see that whenever Vout=2V that means Vdsp=0V and Vdd=2V (given), then The current is zero and capacitor at the output is discharged. This is true only when PMOS is in combination with NMOS and forms a CMOS inverter.</br>
Let us take another example, when Vout=0V, that means -Vdsp=2V and Vdd=2V, so at every gate voltage of Vin we will see a finite current whenever Vout=0V. As Vout=0V, the capacitor is completely discharged and we need to charge that, so that is the charging current required. So, here we get the load curve for PMOS</br>

<img width="513" height="392" alt="image" src="https://github.com/user-attachments/assets/3a31512c-bd15-4f84-8a43-cb125285ad24" />

Now we will try to get the "load curve" for NMOS transistor from this equations.</br>
<img width="223" height="75" alt="image" src="https://github.com/user-attachments/assets/ede06e12-72e7-4da9-8341-820177ed7b4e" />

It is actually simple as Vgsn = Vin and Vdsn = Vout, directly we can get the graphs.</br>

<img width="410" height="287" alt="image" src="https://github.com/user-attachments/assets/e434b1a5-c734-43c2-9565-19714e01f38e" />
<img width="892" height="380" alt="image" src="https://github.com/user-attachments/assets/143a185e-09e5-4c51-8964-eae5b983c47c" />

### L6 Step4- Merge PMOS-NMOS load curves and plot VTC
We will now merge the above two curves and obtain the voltage transfer characteristics(VTC) for CMOS inverter.

<img width="1340" height="412" alt="image" src="https://github.com/user-attachments/assets/e06060aa-bb37-4abc-a225-7cce4569c224" />
For this we will superimpose both the Load Curves to get the VTC. We are doing this to find out the common point between Vin and Vout of both NMOS and PMOS.</br>

<img width="573" height="361" alt="image" src="https://github.com/user-attachments/assets/60499256-909d-4fad-ba5b-5a5e58d4939d" />

So the  range of Vin and Vout is 0V-2V.</br>

* When Vin = 0V, Vout = 2V; NMOS is Cut Off and PMOS is in Linear region
* When Vin = 0.5V, 1.5V<Vout<2V; NMOS is in Saturation region and PMOS is in Linear region.
* When Vin = 1V, 0.5V<Vout<1.5V; NMOS and PMOS are in Saturation region.
* When Vin = 1.5V, 0<Vout<0.5V; NMOS is Linear region and PMOS is in Saturation region.
* When Vin = 2V, Vout = 0V; NMOS is in linear region and PMOS is Cut Off

<img width="1332" height="687" alt="image" src="https://github.com/user-attachments/assets/e484815f-7533-4c87-a6c3-ca79158ac59e" />
