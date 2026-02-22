# C S AMPLIFIER

Introduction

The Common Source is a type of MOSFET configuration in which source terminal act as common terminal and 
input is applied across gate and output is taken across drain terminal The amplifier provides voltage gain and introduce.
phase shift of 180 blw input and output signal for proper amplification the MOSFET must operate in saturation region 
which is achieved by setting dc bias point or Q point 

Here three anyalsis are performed

1)DC anyalsis - to find operating bias point
   

2)transient anyalsis -to get gain of mosfet

3)AC anyalsis - to anyalze frequency response and get bandwidth

 Design of circuit :

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/Screenshot%202026-02-22%20215435.png)

DESIGN CALCULATIONS

Given:
Supply voltage
VDD = 1.5 V

Chosen drain current
ID = 200 uA

Assume MOSFET operates in saturation region. SO

VDS = VDD / 2

VDS = 1.5 / 2=0.75

 Power Dissipation

P = VDD × ID,
P = 1.5 × (200 × 10⁻⁶),
P = 0.3 mW

0.3<0.5 (Circuit operates safely)


Given:

ID = 200 uA = 200 × 10⁻⁶ A, un = 273.8094 x 10^-4 ,Cox = 8.616 × 10^-3 ,VGS = 0.9 V ,VT = 0.366 V ,L = 180 nm

Vov = VGS − VT

Vov = 0.9 − 0.366
Vov = 0.534 V

unCox = un × Cox

unCox = 273.8094 × (8.616 × 10⁻³)
unCox = 2.359 x10^-4

For MOSFET operating in saturation region

ID = (1/2) unCox (W/L) (Vov)²

W/L = 2ID / [µnCox (Vov)²]

W = 5.95 × (180 × 10^-9)

W =1.07u






# DC ANYALSIS 

Procedure :

1)Click on New Schematic to create a new circuit

2)Click on Component and place the NMOS transistor on the screen.

3)connect a DC voltage source and set it as VDD = 1.5 V

4)Connect a resistor (Rd) between drain and VDD

5)Connect the source terminal directly to ground

6)connect a voltage source to gate and  set it to 0.9v
   
7)Connect all components as per the circuit and do necessary groundings

8)Now click on simulate

9)Select Operating Point

10)Click ok and place the .op command on the schematic

11)Click on the Run button

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-02-22%20at%202.29.36%20PM.jpeg)


Conclusion :

 As per design calculations w= 1.07u, rd=3.75k , But for W =1.07u we do not get expected id value and operating point So we vary W keeping L constant 
 to get desired operating point 0.75V and id of 200u A ,So final w for id 200u A and voltage of 0.75v is 1.572u


# Transient anyalsis 

Procedure:

1)apply input voltage as SINE(0.9 10m 1000) to gate terminal

2)Add transient command .tran 5m

3)Run simulation and plot Vin and Vout


Output graph :

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-02-22%20at%202.27.22%20PM%20(1).jpeg)


Input graph :
![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-02-22%20at%202.28.08%20PM%20(1).jpeg)


Conclusion :

Gain calculations

Vin=909.8-800
   =19.8mV
Vout=772.3-728.0
vout =44.3mv
Av = Vout/Vin
   44.3/19.8=2.295
Avdb=20 logav
 =20log2.295=7.21

Gain calculation(theortical)

Av =gm x rd
gm =2id/vgs-vt
gm =0.74 x10^-3
rd =3.75 x10^3
Av = 0.74x 3.75=2.7
Avdb =20 log Av =8.6

practical gain is almost equal to theortical gain

# Ac anyalsis

Procedure :

1)Now connecting circuit as per procedure

2)Add AC analysis command .ac dec 100 0.1 100G

3)Run the simulation

4)Plot output voltage and observe frequency response

Output Expected graph :

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-02-22%20at%202.26.31%20PM.jpeg)

Conclusion :
using the measured gain Av =2.295 and calculated band width of approximately 428.5khz
the Unitgain bandwidth was found to be about 0.983 khz which closely matches the unity gain frequency
observed in the simulation part 


# Result
The common source MOSFET amplifier designed with a channel length of 180 nm was analyzed using transient simulation 
to determine the voltage gain characteristics of the amplifier. From the waveform analysis the input peak-to-peak
voltage was determined to be approximately 19.8 mV, while the output peak-to-peak voltage was determined to be approximately
44.3 mV. Using these values, the calculated voltage gain of the amplifier is approximately –2.295. 
The negative sign of the voltage gain indicates that the output signal is inverted with 
respect to the input thus verifying the 180° phase shift characteristic of the common source configuration.
The results indicate that the circuit is capable of providing the necessary amplification for the small signal operation and
that the MOSFET is biased in the active region, thus verifying the successful design and operation of the amplifier.

# Inference
The results obtained from the experiment clearly show that the common source MOSFET amplifier is working as expected
The amplitude of the output signal is higher than the amplitude of the input signal  which confirms the successful voltage
amplification The 180 phase inversion of the  output signals also confirms the  property of thecommon source amplifier 
The voltage gain of around –2.295 obtained from the experiment clearly shows that the amplifier has moderate gain, 
which is suitable for small signal amplification the smooth waveform also confirms that the
MOSFET is working in the saturation region with the correct biasing conditions

