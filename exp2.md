#  Introduction

In this project a CMOS common source amplifier is designed and simulated
using TSMC 180 nm technology in LTspice. The circuit consists of an NMOS transistor 
that acts as the main amplifying device and a PMOS transistor used as an active load.
The circuit operates with a 1.5 V supply voltage and a bias current of approximately 200 µA.
A source resistor is included to establish the source voltage and stabilize the
operating point. Proper biasing is selected so that the NMOS transistor operates 
in the saturation region, which is required for linear amplification.

#  Circuit description  
The implemented circuit is a single stage common source amplifier.

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-10%20at%2011.22.03%20PM%20(1).jpeg)
Source Resistor (R1)
A 1 kΩ resistor is connected to the source of the NMOS transistor. This resistor sets the source voltage and helps stabilize the operating point.
NMOS Transistor (M1)

The NMOS transistor acts as the main amplifying device. The input signal is 
applied to the gate of the NMOS transistor. Small variations in the gate voltage cause chan

PMOS Transistor (M2)

The PMOS transistor acts as an active load. It is connected to
the supply voltage and provides the bias current required for the NMOS transistor. 
Using an active load improves the voltage gain compared to a simple resistor load.

Source Resistor (R1)
A resistor is connected to the source of the NMOS transistor. This resistor sets the source
voltage and helps stabilize the operating point.vides the bias current required for the NMOS transistor. 
Using an active load improves the voltage gain compared to a simple resistor load.

#  Theoretical Design Calculations

given  power =  0.5w(max)
assumed  Id =200u amp
p= VxI

P=200ux1.5
p=0.3w
0.3<0.5

id is safe
Source Voltage

The source resistor isetermined  by
0.2=  200uxRs
Rs=  1k ohm

PMOS Gate–Source Voltage

VSG  = VTP+[VOV]
VTP=0.39
VOV=0.25
VSG=0.39+0.25
VSG=0.64

Since the PMOS source is connected VDD;

VG=VDD-VSG
VG=1.5-0.64
VG=0.86
This gate bias ensures that the PMOS transistor operates in saturation and provides the required current.


Id=200u A
upcox=9.7361x10-5
ID=upcoxw/l(vgs-vt)
w=200x10^-6x2x180n/uncox(o.25)^2
w=11.82u

NMOS  gate  source  voltage

For the NMOS transistor operating in saturation:

VGS =VTH+VOV

VGS=0.36+0.25

VGS=0.61

So  gate  voltage 
VG=VGS+VS

VG=0.61+0.2

VG=0.81

NMOS  width  calculation
for  MOSFET in  saturation  region

Id=uncoxW/L(vgs-vt)/2

w/l=2ID/uncox(vgs-vt)

uncox=2.3039x10^-4
w/l=2x200u/2.3039x10^-4x0.25

w/l=23.37

W=4.995u

#  DC Operating point

simulationimage 


#Conclusion
Initially, smaller transistor widths did not provide the expected bias 
current and output behavior(ID=200uA,VOUT=0.95). By increasing the width of the NMOS and PMOS 
transistors, the required drain current and proper operating point were achieved.
The final dimensions used in the design  are  Wn=12.8u  and  Wp=37.16u


# Output Swing Analysis Using Headroom and Legroom

1. Operating Condition of the Amplifier

For proper operation of the CMOS common source amplifier,
both NMOS (M1) and PMOS (M2) must operate in the saturation region.
Because of this requirement, the output voltage cannot vary over the full supply range from 0 V to VDD

The output voltage limits are determined by two constraints:
1)NMOS legroom (lower output limit)
2}PMOS headroom (upper output limit)

#  NMOS Legroom (Lower Output Voltage Limit)
Legroom represents the minimum output voltage required to keep the NMOS transistor in saturation.
In the circuit, the source of the NMOS transistor is connected to a source resistor 
Rs=1k 0hm  So  vs =0.2

for NMOS in  saturation  VDS>VOV

Hence  minimum  output  swing is 0.2+0.25=0.45

#  PMOS Headroom (Upper Output Voltage Limit)

Headroom refers to the voltage margin required to keep the PMOS transistor in saturation.
The PMOS source is connected to the supply voltage:
​
VDD=1.5
To maintain  PMOS  saturation
VSD=>VOV

Voutmax=Vdd-Vov

Voutmax=1.5-0.25

𝑉OUT(max)=1.25V

Hence, the PMOS headroom requirement limits the maximum output voltage to 1.25 V.

Hence  available  OUTPUT  SWING  is

Vout(max)-Vout(min)

1.25-0.45

=0.8

#  Transient  anyalsis

Procedure for Transient Analysis (LTspice) – Copyable Format

1. Open the Circuit

2. Configure the Input Signal

3. Insert Transient Analysis Command.

4. Set the Simulation Time

5. Place the Simulation Command

.tran 5m

6. Run the Simulation

7. Observe the Waveforms

image

Simulated Gain

Vout(p-p)=0.206

Vin(p-p)=19.9mV

AV=Vout/Vin

Av=206.8/19.9mV

Av=10.345

Av(db)=20 logAv

Av(db)=20log(10.345)

Av(db)=20.2946


#  Conclsion

The Transient analysis shows that the amplifier produces an output 
signal approximatelyFrom the transient simulation results, it is 
observed that the output waveform has an amplitude nearly 10.34 times
higher than the input signal, confirming that the circuit functions effectively as a voltage amplifier
10.34 times larger than the input signal confirming the amplification capability of the circuit


#  AC  Anyalsis

Procedure

1. Open the Circuit

2. Set the AC Source Value

3. Insert AC Analysis Command

4. Configure Frequency Sweep

5. Place the Simulation Command

6. Run the Simulation

7. Observe the Output Response





image


Gain bandwidth product

GBP=10.345 x 316.68 Mhz
GBP=3.269Ghz

Unity gain Bandwidth
UGB=3.645 GHz

# Conclusion

The results confirm that the amplifier achieves a good balance between gain and bandwidth
while maintaining proper biasing, headroom, and device saturation. The use of a PMOS active load
improves the output resistance and overall gain performance.

Thus, the designed amplifier demonstrates satisfactory high-frequency performance and 
validates the effectiveness of the CMOS design implemented using the 180 nm technology.




# Result

The CMOS common source amplifier using an NMOS transistor as the amplifying device and a
PMOS transistor as an active load was successfully designed and simulated using TSMC 180 nm
technology in LTspice.From the DC operating point analysis, it was verified that both
NMOS and PMOS transistors operate in the saturation region, ensuring proper biasing of 
the amplifier. Adequate headroom and legroom were observed, allowing the output node to swing 
without forcing the transistors into the triode region.
The AC analysis of the circuit shows that the amplifier achieves a midband gain of 
approximately 20.278 dB, which corresponds to a linear voltage gain of about 10.345 V/V. 
The −3 dB gain point occurs at approximately 17.278 dB and the bandwidth of the amplifier
is around 315–316 MHz. Using these values, the Gain Bandwidth Product (GBP) is calculated to be 
approximately 3.27 GHz. The unity gain bandwidth observed from the frequency response is about 3.645 GHz.
From the transient analysis, when a sinusoidal input signal was applied
to the amplifier, the output waveform was found to be amplified and inverted.
The output signal amplitude was approximately 10.34 times larger than the input signal, 
confirming the amplification capability of the circuit.


# Inference

The results obtained from DC, AC, and transient analyses confirm that the designed CMOS
common source amplifier operates correctly and satisfies the expected performance 
characteristics. Proper biasing ensures that the MOS transistors remain in the 
saturation region, which is necessary for linear amplification.
The AC analysis demonstrates that the amplifier provides sufficient gain with
a relatively wide bandwidth, indicating good high-frequency performance. 
The calculated gain bandwidth product and unity gain bandwidth further show 
that the amplifier can operate effectively over a wide range of frequencies.
The transient response verifies the time-domain behavior of the circuit, showing
that the amplifier produces an amplified output signal with phase inversion, which
is characteristic of a common source configuration.
Overall, the circuit achieves a good balance between gain, bandwidth, and stability.
The use of a PMOS active load improves the effective output resistance and gain,
while the source degeneration resistor enhances bias stability and linearity. Hence,
the designed amplifier performs satisfactorily for analog signal amplification applications.




