# NgspiceSky130-Day5-CMOS power supply and device variation robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Power supply variation

### L1 Smart SPICE simulations for power supply variations
While evaluating the robustness of CMOS inverter another factor is **Power Supply Scaling**. On reducing the gate length, the operating power is also reduced. On power scaling the Cmos characteristics should not change.</br>

We will check by simulation, taking two cases.

<img width="1172" height="328" alt="image" src="https://github.com/user-attachments/assets/03dcd0b9-4dd3-4762-83b2-9cbb882e7bc3" />
<img width="723" height="442" alt="image" src="https://github.com/user-attachments/assets/e403056b-c4bb-4b18-a67c-baf5b02842ab" />
<img width="717" height="436" alt="image" src="https://github.com/user-attachments/assets/f357c6d2-fa02-43bc-bf51-184494cf8858" />
<img width="421" height="171" alt="image" src="https://github.com/user-attachments/assets/25f4e021-6818-4e30-85d9-cf300b35bd03" />

We will now plot the VTC charactersitics for Vdd= 2.5V, 2V, 1.5V, 1V, 0.5V;

<img width="742" height="568" alt="image" src="https://github.com/user-attachments/assets/87cf496c-6386-4374-9e92-1a6ef71959c1" />

### L2 Advantages and disadvantages using low supply voltage
We will now analyse the curves we got in after the simulation and see what are the advantages and disadvantages using low supply voltage.</br>
The first factor is to check the "Gain" for all the supply voltages. "Gain Factor" is change in the output voltage divided by change in the input voltage.

<img width="968" height="516" alt="image" src="https://github.com/user-attachments/assets/dd11da87-d570-4fe1-9439-bd449e39af6a" />

<img width="976" height="547" alt="image" src="https://github.com/user-attachments/assets/102b9c1b-82ce-4d72-bc7e-fb502591c636" />

There is energy lowering for low supply voltage.

<img width="1000" height="526" alt="image" src="https://github.com/user-attachments/assets/f9a05a5f-40c0-4bad-be1f-3cd16f1445f4" />
<img width="927" height="527" alt="image" src="https://github.com/user-attachments/assets/b96be82f-5993-4fd1-9cc2-c0756dc212df" />

* Advantages of low supply voltage
  
<img width="722" height="212" alt="image" src="https://github.com/user-attachments/assets/ab3ef568-d3f7-44cb-a6c5-6524ba5b72ec" />

* Disadvantages of low supply voltage
  Due to low supply voltage, the charging and discharging of load capacitor becomes very slow, due to this the Both rise delay and fall delay will increase and lead to a performance impact.

### L3 Sky130 Supply variation Labs
We will calculate the supply variation.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/94a3c1ba-3139-4838-b302-2320ce3f643e" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/56419121-44bb-4f73-9084-06b1503b6544" />

The initial supply voltage is 1.8V and we are reducing it with the step of 0.2V, so there will be 6 iterations.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/af291d32-1484-4d6b-8291-dabc5b70df65" />
We will calculte the Gain: </br>

* **Vdd=1.8V** </br>

  <img width="292" height="61" alt="image" src="https://github.com/user-attachments/assets/0f2c56cc-5fb4-4c1e-9e49-0e7ee75b964b" />

  |Gain| = 7.6229 </br>

* **Vdd=0.8V**

  <img width="267" height="52" alt="image" src="https://github.com/user-attachments/assets/112695f4-b69a-4c76-bd41-a066a08ac6b7" />

  |Gain| = 9.3844 </br>

## Static behaviour evaluation-CMOS inverter robustness-Device variation

### L1 Sources of variation - Etching process
We will see the sources of variation of VTC characteristics in a CMOS inverter.</br>
First is **Etching Process** </br>
If we see a single inverter layout, we will see the length of gate, the width(common area between polysilicon and diffusion). Due to etching process there can be a variation in length and width of CMOS.

<img width="1208" height="580" alt="Screenshot 2025-10-03 203231" src="https://github.com/user-attachments/assets/f4496266-b2a9-4e21-bb84-54e6519478e4" />

Now considering the inverter chain, the variation can differ with different inverter.

<img width="1288" height="652" alt="Screenshot 2025-10-03 203314" src="https://github.com/user-attachments/assets/a326d12c-e0b7-4daa-bf13-311ccaa8e476" />
<img width="1121" height="618" alt="Screenshot 2025-10-03 203404" src="https://github.com/user-attachments/assets/8683fe6c-a634-4720-98d4-8ef619ab52b1" />

The variation is more at the edges or sides than at the center.

<img width="1324" height="621" alt="Screenshot 2025-10-03 203542" src="https://github.com/user-attachments/assets/998d8d7c-941f-4643-a768-13896c578018" />

Therefore the variation in L and W can change the drain current of CMOS inverter.

<img width="926" height="483" alt="Screenshot 2025-10-03 203633" src="https://github.com/user-attachments/assets/b1c7130a-de89-4cf1-ab2e-064702878082" />

### L2 Sources of variation - Oxide thickness
Another source of variation is **Oxide Thickness*</br>
Let us consider the cross-sectional view of CMOS inverter. We will see the oxide under polysilicon gate, while fabricating the thickness can vary.</br>

<img width="1318" height="561" alt="Screenshot 2025-10-03 203747" src="https://github.com/user-attachments/assets/25b705ca-1d73-4127-a9bc-a69e2af0c8c2" />
<img width="826" height="377" alt="Screenshot 2025-10-03 203848" src="https://github.com/user-attachments/assets/df455509-4718-4074-9eda-bb314e6462c0" />

There is a difference between ideal thickness and actual thickness.

<img width="1205" height="597" alt="Screenshot 2025-10-03 203924" src="https://github.com/user-attachments/assets/a802cce3-df91-4e80-9b34-d2f931de9f8d" />

We know **Cox=Eox/tox**, therefore change in tox can actually change the drain current.

<img width="1162" height="461" alt="Screenshot 2025-10-03 204044" src="https://github.com/user-attachments/assets/d06ee6da-3467-41cb-8a0e-280b15faae56" />

### L3 Smart SPICE simulation for device variations
Now we will be doing the SPICE simulation for device variations, and prove the robustness of CMOS inverter inspite of different extreme conditions.</br>
We will see the characteristics for Strong PMOS and week NMOS, this means PMOS width is wider and it has least resistance. Also for weak PMOS and strong PMOS, that means the width of NMOS is more than PMOS and it has least resitance.</br>

<img width="1148" height="339" alt="Screenshot 2025-10-03 224857" src="https://github.com/user-attachments/assets/398d01a6-ffc4-4a10-86a8-3907d3214b69" />
<img width="594" height="436" alt="Screenshot 2025-10-03 224935" src="https://github.com/user-attachments/assets/41b1f2f6-c4ba-4c71-a8e6-d1fc8e3b4844" />
<img width="695" height="398" alt="Screenshot 2025-10-03 224949" src="https://github.com/user-attachments/assets/9314e15f-c027-47ba-b34e-f35d886e5aff" />
<img width="726" height="321" alt="Screenshot 2025-10-03 225121" src="https://github.com/user-attachments/assets/280f196e-1bde-417a-9955-7a0f2029ee39" />
<img width="753" height="567" alt="Screenshot 2025-10-03 225153" src="https://github.com/user-attachments/assets/33e8fc0e-5220-4dc4-8da9-4c8dd5406e02" />

### L4 Conclusion
We will draw some conclusions from the characteristics we got.

<img width="994" height="537" alt="Screenshot 2025-10-03 231012" src="https://github.com/user-attachments/assets/aec473f9-00f5-4028-b122-fa2922affcb3" />

* The Switching threshold 'Vm' is shifted right in case of strong PMOS and shifted left in case of Strong NMOS. </br>

<img width="1006" height="541" alt="Screenshot 2025-10-03 231027" src="https://github.com/user-attachments/assets/38851b7b-ec82-4400-93d8-c3c651d51ae9" />

* THere not much variation in NOise Margins in both the extreme cases, that means it behaves as a robust inverter in both the cases.</br>

<img width="519" height="169" alt="Screenshot 2025-10-03 231046" src="https://github.com/user-attachments/assets/edd63a58-b8bb-462e-84e5-b8c977d4a4d2" />

### L5 Sky130 device variations labs
We will now do the SPICE simulations for the device variations</br>

<img width="1912" height="1079" alt="Screenshot 2025-10-03 231604" src="https://github.com/user-attachments/assets/5b26708d-6351-4aa8-b2d2-758a174a6f8b" />
<img width="1919" height="1079" alt="Screenshot 2025-10-03 231715" src="https://github.com/user-attachments/assets/518ac3f8-9460-49ab-943e-e09cc37ca4ac" />

We can see that the width of PMOS is quite large than that of NMOS. SO it is clearly strong PMOS and weak NMOS case. The Vm will be right shifted.</br>

<img width="1919" height="1079" alt="Screenshot 2025-10-03 231914" src="https://github.com/user-attachments/assets/ef15e759-7036-445a-b5b1-53b0df38050a" />

<img width="1919" height="1079" alt="Screenshot 2025-10-03 232247" src="https://github.com/user-attachments/assets/841f9eea-395a-4213-93c5-8e5a06de59f0" />

