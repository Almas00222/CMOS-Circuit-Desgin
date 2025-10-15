# NgspiceSky130-Day4-CMOS Noise Margin robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Noise Margin

### L1 Introduction to Noise Margin
Now we will learn CMOS inverter's robustness towards the Noise Margin. Also we see the Noise margin evaluation for CMOS inverter. </br>
**Noise Margin**: It is a measure of how much unwanted electrical noise a logic circuit can tolerate on its input without producing an incorrect output. </br>

For example if we consider an ideal Inverter, for inputs 0/1 it gives output as 1/0. The slope of switch is infinite. </br>

<img width="557" height="451" alt="image" src="https://github.com/user-attachments/assets/2465a4e2-199d-4698-aa7d-58f0b42f0c6f" />

But practically the slope won't be infinite, due to presence of resistances and capacitances there will be delay. Therefore we will get a finite slope </br>

<img width="368" height="316" alt="image" src="https://github.com/user-attachments/assets/f8f2f3f3-dc21-45eb-90b7-c9f2fdb8ef94" />

We will now see that whenever the input is between 0 to VIL(input low voltage); the output will be VOH(output high). </br>
And whenever the input is between VIH(input high voltage) and Vdd; output will be VOL(output low voltage). </br>
<img width="405" height="342" alt="image" src="https://github.com/user-attachments/assets/8e3c22bf-b012-4a75-a08d-910511ed2980" />

### L2 Noise Margin voltage paramters
Considering the more practical scenarios and non idealities of an inverter, the curve we get is as shown below. So here the when the 0<Vin<VIL --> output is VOH<Vout<Vdd ; and when the input is VOL<Vin<Vdd --> output is 0<Vout<VOL. Also **VOL<VOH<Vdd** as VOH will be output high for the next inverter which will be connected and **0<VOL<VIL** as it will be the output low for the next inverter. </br>

Also, the slope is approximately -1, as for increase in input, output is reducing. </br>

<img width="356" height="337" alt="image" src="https://github.com/user-attachments/assets/d848d4c0-de9b-4b6b-8c6a-f3006bae557c" />

### L3 Noise margin equation and summary
Now we will calculate the noise margin equation, for that we will plot the voltages on the same scale.</br>

<img width="733" height="443" alt="image" src="https://github.com/user-attachments/assets/c25a3266-d8f3-4e16-8afa-298756b3a59d" />
In the above scale: </br>
* **Noise amrgin High NH** - value between VIH and VOH. </br>
* **Noise Margin Low NL** - value between VIL and VOL. </br>

So, any value which lies in between noise margins is considered either 1/0 and considered to be tolerable. Apart from this region the value is "Undefined" and the logic level can swing between 'high' and 'low'.

<img width="783" height="423" alt="image" src="https://github.com/user-attachments/assets/80791538-0e36-46a8-9bf1-043e740dd778" />

<img width="822" height="481" alt="image" src="https://github.com/user-attachments/assets/6443e129-644a-4d0d-a4c4-0439ba4165de" />

### L4 Noise margin variation with respect to PMOS width
We will evaluate the noise margin depending upon the PMOS width and ultimately prove that how CMOS inverter is robust to the noise margins.</br>
First, we will find the points where the slope = -1 and extend the lines towards x-y axis.</br>

<img width="1207" height="542" alt="image" src="https://github.com/user-attachments/assets/5ab8cb26-4ab7-4e77-9a04-be82cfcdac12" />
The larger the Noise margin, stronger is CMOS inverter and immune to Noises.</br>

<img width="1175" height="523" alt="image" src="https://github.com/user-attachments/assets/98daed0b-5528-4d72-8a99-06806511d1b8" />
<img width="1197" height="503" alt="image" src="https://github.com/user-attachments/assets/89b5f850-df64-4e6e-abcb-366cc3755d13" />
<img width="1203" height="517" alt="image" src="https://github.com/user-attachments/assets/13199ec4-704c-4812-aba2-38257330e40b" />

For (W/L)p=4(W/L)p and (W/L)p=5(W/L)p noise margins are same, so even if we increase the widths further noise margin will be static. 

<img width="677" height="226" alt="image" src="https://github.com/user-attachments/assets/fca7bcac-471c-4114-8c64-4b97cba1f5b0" />

Here also we can verify the robustness of CMOS inverter. </br>

Also we come to know the ranges for "Digital design" and "Analog design" in the CMOS inverter.</br>

<img width="741" height="546" alt="image" src="https://github.com/user-attachments/assets/3e9a0cf6-a232-4ff2-ad4c-214b03803af3" />
<img width="772" height="542" alt="image" src="https://github.com/user-attachments/assets/56c5c94d-b59f-456c-ba92-b22fab03b6d9" />

### L5 Sky130 Noise margin labs
We will now plot Noise margins

![Alt text](32.png)

We are taking the W/L ratios of PMOS to NMOS as 2.77 and sweeping the Vin from 0 to 1.8V with stepsize of 0.01V.

![Alt text](33.png)
![Alt text](34.png)
![Alt text](35.png)
![Alt text](36.png)

We will take the point where the slope is -1 ; x axis will give VIL and VIH, whereas y axis will give VOH and VOL.

**Noise margin NH = VOH - VIH = 1.70952-0.98778 = 0.72** </br>
**Noise margin NL = VIL - VOL = 0.7733-0.09523 = 0.67807** </br>
