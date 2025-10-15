# NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)

## Introduction to Circuit Design and Spice Simulations

### L1 Why do we need SPICE simulations?
The circuit includes PMOS and NMOS gates connected to form logic gates such as NAND, NOR, OR, AND, etc.</br>

<img width="542" height="526" alt="image" src="https://github.com/user-attachments/assets/bf9b9eed-3cf4-41be-bcfe-8b3ea7eadcb0" />

The above inverter will have the following characteristics. We'll run a SPICE simulation to determine the delay and thus obtain the W/L ratio for a specific transistor.</br>

<img width="965" height="695" alt="image" src="https://github.com/user-attachments/assets/e2264a62-e4b1-4506-bb0f-eded09d303f3" />

**WHY DO WE NEED SPICE?**</br>
The clock tree synthesis, crosstalk, and clocking are all built using SPICE (a simulation program with an emphasis on integrated circuits). Without SPICE, there would be no delay, and without delay in the physical design process, crosstalk is meaningless.</br>

Let's assume we've synthesized a clock tree for the circuit shown below, with buffers and varying capacitive loads at the output.</br>

<img width="1206" height="392" alt="image" src="https://github.com/user-attachments/assets/a0dbe0ed-6981-4966-8d1d-7bf4d223ef61" />

After the SPICE simulation, we obtain a "Delay Table," which includes the input step and output load. The intersection of the input step and output load is considered the delay. Delay tables for level 1 and level 2 buffers are presented. They were calculated using schematic design and simulation.</br>

<img width="1410" height="668" alt="image" src="https://github.com/user-attachments/assets/422a8a28-f4e6-469a-97d4-535f02762e3d" />

The source of the delay tables above is schematic design using SPICE simulation. SPICE simulation is used to characterize any CMOS logic.</br>

### L2 Introduction to the Basic Element of Circuit Design – the NMOS Transistor
The NMOS transistor consists of a p-type substrate heavily doped with an n+ region. It has an isolation region that isolates the transistor from other transistors. The N+ regions are the source and drain. Above this is an oxide layer, and above that is a metal layer, which is the gate terminal.</br>

<img width="1195" height="507" alt="image" src="https://github.com/user-attachments/assets/fafb4e04-8d70-42dd-bae3-7570c38be028" />

**Threshold Voltage**
This is a very important term; all characteristics depend on the threshold voltage.</br>
Initially, we'll assume Vgs = 0, meaning the source and drain terminals are grounded. The case is also grounded. The P-substrate and N+ junction act as a PN junction diode, and since there is no potential, the resistance is high. Channels are not formed.</br>

<img width="1322" height="528" alt="image" src="https://github.com/user-attachments/assets/8e2fee4c-8616-4886-859c-d6c08d166541" />

Now we apply a positive potential; Vgs>0. We'll see that the gate is now positively charged, causing negative charges to accumulate on the substrate surface.</br>

<img width="1345" height="555" alt="image" src="https://github.com/user-attachments/assets/ef79f61f-5540-4ffb-aec8-06fa9354759a" />

### L3 High Inversion and Threshold Voltage
Due to the accumulation of negative charges, a depletion region is formed, which will deplete the majority of charge carriers, i.e., positive carriers.</br>

<img width="831" height="402" alt="image" src="https://github.com/user-attachments/assets/335a3525-699e-4c66-8161-2201df2b9070" />

Now we'll increase the gate voltage even further. We'll see that positive charge carriers will repel each other, and the width of the depletion region will increase. As the gate voltage increases further, we'll reach a point where the surface inverts into an n-type material. This is called "surface inversion" or "strong inversion." The gate voltage Vgs at which strong inversion occurs is called the "threshold voltage."</br>

<img width="1332" height="551" alt="image" src="https://github.com/user-attachments/assets/03776359-fd17-4e04-9fd5-9212422217df" />

What happens if we increase Vgs even more? Since there are no longer any negative charges that could be attracted to the positive potential Vgs, negative charges from the n+ region will be attracted, and a channel will form on the surface.</br>

<img width="1358" height="573" alt="image" src="https://github.com/user-attachments/assets/f8c47353-dbf7-4026-b4d9-89ebff6cd24d" />

<img width="1350" height="618" alt="image" src="https://github.com/user-attachments/assets/183a52c0-755d-43c6-9731-9043b047e679" />

Current can now flow from the source to the drain. The channel spans the gap between the source and drain regions. But since there's no drain voltage, electrons don't move, and this is now the "cutoff region."</br>

Let's see what happens if we change the potential of the "Body" pin.</br>

<img width="1311" height="532" alt="image" src="https://github.com/user-attachments/assets/0aa83b1f-12c2-4765-bd3f-caa35daac877" />

There will be increase in depletion region between source and body terminal. </br>

<img width="1283" height="607" alt="image" src="https://github.com/user-attachments/assets/1dd9f64e-5345-4dc9-98b2-6dcde19765ef" />

### L4 Threshold voltage with positive substrate potential
If we increase Vgs, we will see that the depletion region increase in both the cases. But, in second case as there is Vsb +ve, few charges from channel will be pulled towards the source.</br>

<img width="1247" height="617" alt="image" src="https://github.com/user-attachments/assets/65d128ea-03af-4dd4-af13-28b261e0fe66" />

Due to this the surface inversion will be slower in second case. Therefore some extra potential has to be apllied in second case to create inversion.</br>

<img width="1356" height="658" alt="image" src="https://github.com/user-attachments/assets/98b3483c-2c33-4244-b96d-6098ee9b0163" />

<img width="632" height="235" alt="image" src="https://github.com/user-attachments/assets/8025a009-e2dd-4e83-a4d6-c1725668e6fc" />

The parameters such as Gamma comes from foundaries after simulation of which in SPICE we get the value for Vt (Threshold Voltage).</br>

<img width="1327" height="643" alt="image" src="https://github.com/user-attachments/assets/8955fdc9-1230-4562-b513-4eca06eb5d3c" />

## NMOS resistive region and Saturation region of operation

### L1 Resistive region of operation with small drain-source voltage
Previously, we saw Cut Off region operation, now we will see the "Resistive region"/"Linear Region" of operation by applying Drain-source voltage.
If we keep on increasing the Gate-source voltage, the channel width keeps on increasing.</br>

<img width="1305" height="508" alt="image" src="https://github.com/user-attachments/assets/29f349a8-c77e-4d13-a323-82b1fa6bfb74" />

This shows that the net Induced charges is propotional to (Vgs-Vt). Now let's apply very small Vds at start. And keep Vt=0.45V, Vgs also small initially.</br>

<img width="1317" height="567" alt="image" src="https://github.com/user-attachments/assets/aed1572f-fd2b-492d-82ca-bd1ce4a94b1e" />

We can see that the source is grounded and Drain is at some potential, so there will be a voltage gradient accross the channel.</br>

<img width="1318" height="577" alt="image" src="https://github.com/user-attachments/assets/bf52a8c7-5553-4c74-888c-cdb43b09e3bc" />

Also, the Effective channel length is much lesser than the original channel length.</br>

<img width="797" height="510" alt="image" src="https://github.com/user-attachments/assets/c35a777b-b625-495c-bb37-9f92dfd92a64" />

Here, y axis represents the width of transistor and x axis is the voltage across the channel.</br>
On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.</br>

<img width="817" height="558" alt="image" src="https://github.com/user-attachments/assets/a472661e-b9bd-4cfb-8437-ea5be2474fe2" />

### L2 Drift current theory
We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. Now if we see the induced chagre equation, it is proportional to the effective channel voltage.</br>

<img width="411" height="150" alt="image" src="https://github.com/user-attachments/assets/f303fe6e-388f-4395-9650-e7121cd5aff4" />

<img width="390" height="451" alt="image" src="https://github.com/user-attachments/assets/14f8c404-0d02-4d21-8d67-b20ff1801eae" />

There are two types of currents; Dift and Diffusion current, Here there is Drift current as there is potential difference across the channel.</br>

<img width="1285" height="618" alt="image" src="https://github.com/user-attachments/assets/e1ba1c63-b342-4377-9fe8-1a2e58c93e02" />

To get the drain current, we will see the top view of transistor.</br>

<img width="1311" height="687" alt="image" src="https://github.com/user-attachments/assets/6c473806-a163-4120-974a-73e11da97839" />

### L3 Drain current model for Linear region of operation
As there is change of voltage across the channel length, this will result in change of velocity which is a function of mobility and electrci field.</br>

<img width="448" height="651" alt="image" src="https://github.com/user-attachments/assets/6518460a-1e4c-481f-8341-d99a1fa9a376" />

We will integrate the above equation, where limits of dV will be from 0 to Vds and limits of dx will be from 0 to L.</br>

<img width="442" height="428" alt="image" src="https://github.com/user-attachments/assets/382f07af-71b5-4f00-894d-bdab05e92d0e" />

<img width="377" height="48" alt="image" src="https://github.com/user-attachments/assets/f6f5158c-850f-4272-b381-0b57dc30e7a9" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.</br>

<img width="387" height="211" alt="image" src="https://github.com/user-attachments/assets/ee457e12-6af7-4389-a11a-036ba5a4b652" />

But, here we cannot say that it is in Linear region, since the Drain current is the quadratic function of Vds. We will calculate the Id with the given values.</br>

<img width="708" height="432" alt="image" src="https://github.com/user-attachments/assets/853ed5fa-0257-4a73-91dd-09007f16d273" />

When (Vgs-Vt)>=Vds, It is in "Linear region".</br>

<img width="683" height="443" alt="image" src="https://github.com/user-attachments/assets/bdfa5383-5b3b-452f-b437-0768814f2551" />

### L4 SPICE conclusion to resistive operation
We need to find the impact of Vgs and Vds on the drain current equation. We will consider different values of Vgs and Vds. If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.</br>

<img width="591" height="172" alt="image" src="https://github.com/user-attachments/assets/d9735c9f-3a26-49aa-bc9b-62e64d65babe" />

Now the main question arises: how to calculate Id for different Vgs values ​​and, at each Vgs value, scale Vds to (Vgs - Vt) using the linear equation for Id?

To do this, we need to perform a SPICE simulation.

### L5 Cutoff Region Condition
There is also a region of operation where the drain-source voltage exceeds (Vgs - Vt). This region of operation is called the "saturation region."
We know that the channel voltage is equal to Vgs - Vds. Now let's increase Vds.</br>

<img width="1367" height="625" alt="image" src="https://github.com/user-attachments/assets/d29ecff9-3641-49c7-9348-fa7537ff7118" />

When Vgs-Vds is greater than Vt, a conductive channel is formed.</br>
When Vgs-Vds equals Vt, an inversion occurs on the drain side, since Vds equals Vt, so the channel on the drain side begins to disappear.</br>

<img width="1380" height="611" alt="image" src="https://github.com/user-attachments/assets/b51e39ef-093f-463d-8faa-7c6bb23cc68d" />
<img width="1352" height="621" alt="image" src="https://github.com/user-attachments/assets/8d325d80-10d4-47e3-aed0-2caaf0715a36" />

Now, when the channel begins to disappear, this is called the "clipping region."</br>

<img width="1492" height="602" alt="image" src="https://github.com/user-attachments/assets/40146460-641e-4f89-a950-acebeba103e3" />

When Vgs-Vds<Vt, we won't see any channels on the drain side.</br>

<img width="1310" height="582" alt="image" src="https://github.com/user-attachments/assets/e62baac0-53e1-4c61-a9d6-e26a0a4b8ec1" />

This state is called the "saturation region," where the MOSFET is saturated and cannot conduct further.</br>

<img width="391" height="102" alt="image" src="https://github.com/user-attachments/assets/4c0aca6a-e230-47d1-9e30-9416785487be" />

### L6 Drain Current Model for the Saturation Region
In the saturation region, the channel voltage will remain constant, as Vgs - Vt, and the drain current will be independent of Vds.</br>
To obtain the drain current equation in the saturation region, replace Vds with Vgs-Vt.</br>

<img width="467" height="360" alt="image" src="https://github.com/user-attachments/assets/3df0adef-9616-499c-97de-477da403178b" />

Now we see that, according to the equation, the MOSFET acts as an ideal current source. But this is incorrect: as Vds increases, the drain depletion region increases, further reducing the channel length. Therefore, we observe a slight dependence of Vds on Id.</br>

<img width="1476" height="586" alt="image" src="https://github.com/user-attachments/assets/899bf2cb-f752-43ad-8750-5fc9d6b62f50" />

This is called "channel length modulation."</br>

<img width="876" height="168" alt="image" src="https://github.com/user-attachments/assets/b3d388c1-7074-49c9-a019-7d0ff212271f" />

## Introduction to SPICE

### Basic SPICE L1 Setup
First, let's look at the SPICE setup.</br>

<img width="1412" height="611" alt="image" src="https://github.com/user-attachments/assets/5872cd9a-70d1-46cf-9fe4-f5247f8d3415" />

Some parameters are constant, and since they come directly from the founders, we don't need to display them. They are circled in yellow.</br>

<img width="1313" height="591" alt="image" src="https://github.com/user-attachments/assets/c7f8c503-a596-40a7-85e8-b00b1eef4cf9" />

<img width="922" height="536" alt="image" src="https://github.com/user-attachments/assets/260175cb-7abc-4fc6-a332-6b73b7954cae" />

So, when we pass the SPICE model parameters and the SPICE netlist to the SPICE program, we get the device characteristics in terms of Id and Vds with different Vgs values.</br>

**SPICE Netlist**
We need to pass the device to SPICE Engine with a specific Thus, the circuit equivalent of this MOSFET is shown below. </br>

<img width="1262" height="585" alt="image" src="https://github.com/user-attachments/assets/ec870ea4-f7ce-4e99-939a-d6e8646c499e" ​​​​/>

### Description of the L2 circuit in SPICE syntax
Now let's write the syntax for this specific circuit into a SPICE netlist. To do this, we need to complete a few steps:
* **Define the nodes**

<img width="653" height="410" alt="image" src="https://github.com/user-attachments/assets/726a94e6-1333-41dc-a4c0-d9c766b00f9b" />

* **Name the nodes**
* **Write the code**
`Since the modfet has 4 pins, it sits between 4 different nodes, similarly, the resistor sits between 2 nodes.`

<img width="1307" height="418" alt="image" src="https://github.com/user-attachments/assets/fe360627-afb9-41d7-917d-95b7ac8ca6b7" />
<img width="1211" height="371" alt="image" src="https://github.com/user-attachments/assets/5d8f624b-296a-499a-9cc2-c9fd0946fb52" />
<img width="1213" height="412" alt="image" src="https://github.com/user-attachments/assets/c7d30d08-94c4-4891-95b3-4fc8c95fa3c9" />
<img width="1132" height="381" alt="image" src="https://github.com/user-attachments/assets/b9dad3c6-2cc6-48a5-9409-a7eb90f39301" />
<img width="1197" height="385" alt="image" src="https://github.com/user-attachments/assets/e091f59b-d7b8-4913-9ee3-0a2cc5d324f0" />

The fashion in which it is written is "Drain", "Gate", "Source", and "Substrate" (DGSS).</br>

<img width="1252" height="471" alt="image" src="https://github.com/user-attachments/assets/f9599207-d326-4da5-b92b-53d80a85c4cb" />
<img width="1172" height="406" alt="image" src="https://github.com/user-attachments/assets/15ce1ea6-b8d3-47f6-9ef9-978ddd83bbc6" />
<img width="1242" height="402" alt="image" src="https://github.com/user-attachments/assets/36660836-b886-4c2e-9649-d13863d65f7f" />

this is a long channel mosfet.

Similarly we can write for Resistor.</br>
<img width="1263" height="416" alt="image" src="https://github.com/user-attachments/assets/880832b5-5f1b-49f3-9c01-25ef9bdc55c4" />
<img width="1247" height="463" alt="image" src="https://github.com/user-attachments/assets/1d36164e-cf12-49e3-84b5-8f2928f4a8b9" />
<img width="1345" height="370" alt="image" src="https://github.com/user-attachments/assets/fb1e6449-cf20-48d7-9888-eadc40c5319c" />
<img width="1342" height="422" alt="image" src="https://github.com/user-attachments/assets/53c100fd-845e-474d-b3a3-9a53bfc0ee45" />
<img width="637" height="308" alt="image" src="https://github.com/user-attachments/assets/6498b3c6-8eda-40ee-adf7-c9a6e332675f" />

### L3 Define Technology parameters
Now we will look for model of this particular NMOS. For this we have model paramters, and it becomes easy to model from the parameters. That is where the technology file comes into picture. The models for the name NMOs will be found in file which has the attribute of the similar name.</br>

<img width="1312" height="592" alt="image" src="https://github.com/user-attachments/assets/4fa6b7c5-61d6-45f7-ba68-ad15a67426eb" />

Inside the brackets, technology paramteters will exist. Similarly for pmos also.</br>

<img width="542" height="107" alt="image" src="https://github.com/user-attachments/assets/cbef3e32-99d7-4998-9957-e89c4ba96c57" />

Now, we just plug in this packaged file in `.mod` file and call this file in top level SPICE netlist.</br>

<img width="553" height="475" alt="image" src="https://github.com/user-attachments/assets/f7752179-bfcb-420b-a1df-0af1a648be2c" />
<img width="603" height="197" alt="image" src="https://github.com/user-attachments/assets/23ce231b-f774-437b-ae5a-d3f0836d0a57" />

<img width="635" height="257" alt="image" src="https://github.com/user-attachments/assets/163cf011-37b0-450d-b7d4-4a915bc70653" />

In the above image, the highlighted part is comment in SPICE.</br>
Now, we need to sweep the Vgs and Vds for SPICE simulations.</br>

### L4 First SPICE simulation
* Open Virtual box
* Type `cd`
* `git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git`
  inside the `sky130_fd_pr` directory we will see cells, models and tech files.</br>

![Alt ​​​​text](1.png)

In the `cell` files, we'll see the `nfet` and `pfet` cells we'll be using.</br>

In the `nfet` file, we'll see the SPICE libraries at various angles. Let's choose one of these typical angles.</br>

We'll see all the model parameters needed for the process.</br>
![Alt ​​​​text](2.png)

We have various values ​​for W and L, which are described in advance. For the simulation, we need to select any value from the library.</br>

![Alt ​​​​text](3.png)

Now go to the `models` -> `lib.spice` file. We'll see the library files for nfet and pfet. Angle files are available, including typical angle files, slow-fast angle files, and fast-fast angle files.</br>

![Alt ​​​​text](4.png)

Inside `design` --> open the file day1.</br>

![Alt ​​​​text](5.png)

Above, we see Vdd changing from 0 to 1.8 V in 0.1 V steps, and Vgs changing from 0 to 1.8 V in 0.2 V steps.

Let's run a SPICE simulation:
![Alt ​​​​text](6.png)

![Alt ​​​​text](7.png)

We'll get a plot of Id versus Vds for different Vgs values.</br>

![Alt ​​​​text](8.png)
![Alt ​​text](10.png)

To check the Id value for the corresponding Vds and Vgs, simply left-click and see.</br>

![Alt ​​​​text](9.png)

### SPICE Lab L5 with Sky130 Models
If we go to the `models` folder, we'll see the `all.spice` file. Opening it, we see a width and length scale.</br>
![Alt ​​​​text](11.png)

We see that the W and L values ​​are in microns.</br>
