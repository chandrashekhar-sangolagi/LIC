# C S AMPLIFIER

Introduction

The Common Source is a type of MOSFET configuration in which source terminal act as common terminal and 
input is applied across gate and output is taken across drain terminal ,The amplifier provides voltage gain and introduce.
phase shift of 180 blw input and output signal .for proper amplification the MOSFET must operate in saturation region 
which is achieved by setting dc bias point or Q point .

Here three anyalsis are performed
1) DC anyalsis - to find operating bias point
2)transient anyalsis -to get gain of mosfet
3) AC anyalsis - to frequency response and to get bandwidth 

#Design of circuit 

DESIGN CALCULATIONS

Given:
Supply voltage,
VDD = 1.5 V
Chosen drain current,
ID = 200 uA

Assume MOSFET operates in saturation region. SO

VDS ≈ VDD / 2

VDS = 1.5 / 2
VDS = 0.75 V 

 Power Dissipation

P = VDD × ID
P = 1.5 × (200 × 10⁻⁶)
P = 0.3 mW

This power is very small, hence the circuit operates safely.
Given:

Drain current,
ID = 200 uA = 200 × 10⁻⁶ A, un = 273.8094 x 10^-4 ,Cox = 8.616 × 10^-3 ,VGS = 0.9 V ,VT = 0.366 V ,L = 180 nm

Vov = VGS − VT
Vov = 0.9 − 0.366
Vov = 0.534 V

unCox = un × Cox
unCox = 273.8094 × (8.616 × 10⁻³)
unCox ≈ 2.359 x10^-4

For MOSFET operating in saturation region,

ID = (1/2) µnCox (W/L) (Vov)²

W/L = 2ID / [µnCox (Vov)²]

W = 5.95 × (180 × 10^-9)

W ≈ 1.07u


schematic



#DC ANYALSIS 

Procedure 

1)Click on New Schematic to create a new circuit
2)Click on Component and place the NMOS transistor on the screen.
3)connect a DC voltage source and set it as VDD = 1.5 V
4)Connect a resistor (RD) between drain and VDD
5)Connect the source terminal directly to ground
6) connect a voltage source to gate and  set it to 0.9v
7)Connect all components properly using wires
8)Now click on simute
9)Select “Operating Point”
10)Click ok and place the .op command on the schematic
11)Click on the Run button


DC O.P IMAGE


Conclusion 
 As per design calculations w= 1.07u, rd=3.75k ,we vary w value to get desired operating point 0.75V and id 
of 200u A ,so final w for id =200u A and voltage of 0.75v is 1.572u


Transient anyalsis 

Procedure

1)apply input voltage as SINE(0.9 10m 1000) to gate terminal
2)Add transient command .tran 5m
3)Run simulation and plot Vin and Vout


output image GRAPH


INPUT IMAGE GRAPH


Conclusion

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


image


Procedure

after connecting the components as required
Add AC analysis command .ac dec 100 0.1 100G.
Run the simulation.
Plot output voltage and observe frequency response.

Conclusion 
using the measured gain Av =2.295 and calculated band width of approximately 428.5khz
the Unitgain bandwidth was found to be about 0.983 khz which closely matches the unity gain frequency
observed in the simulation part 


#Result
The common source MOSFET amplifier designed with a channel length of 180 nm was analyzed using transient
simulation to determine its voltage gain characteristics. From the observed waveforms, the input peak-to-peak 
voltage was approximately 19.8 mV, while the output peak-to-peak voltage was approximately 44.3 mV.
Using these values, the calculated voltage gain of the amplifier is approximately –2.24. 
The negative sign indicates that the output signal is inverted with respect to the input,
confirming the expected 180° phase shift characteristic of a common source configuration.
The results show that the circuit provides proper amplification under small-signal operation 
and that the MOSFET is correctly biased in the active region, validating the successful design and functioning of the amplifier.

#inference

TThe experimental results clearly indicate that the common source MOSFET amplifier is functioning as expected.
The output signal amplitude is greater than the input signal amplitude, confirming successful voltage amplification. 
Additionally, the observed phase inversion between the input and output waveforms verifies the characteristic
180° phase shift of a common source configuration. The measured voltage gain of approximately –2.24 demonstrates
moderate amplification suitable for small-signal applications. The smooth and undistorted waveform further suggests that
the MOSFET operates in the saturation region with proper biasing conditions. Hence, the experiment validates both the
theoretical behavior and practical performance of the designed amplifier circuit.



