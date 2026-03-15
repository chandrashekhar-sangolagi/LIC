# Introduction

In this project a CMOS common source amplifier is designed and simulated
using TSMC 180 nm technology in LTspice. The circuit consists of an NMOS transistor 
that acts as the main amplifying device and a PMOS transistor used as an active load.
The circuit operates with a 1.5 V supply voltage and a bias current of approximately 200 µA.
A source resistor is included to establish the source voltage and stabilize the
operating point. Proper biasing is selected so that the NMOS transistor operates 
in the saturation region, which is required for linear amplification.

# Circuit description  
The implemented circuit is a single stage common source amplifier.

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-10%20at%2011.22.03%20PM%20(1).jpeg)


## NMOS Transistor (M1)

The NMOS transistor acts as the main amplifying device. The input signal is 
applied to the gate of the NMOS transistor. Small variations in the gate voltage cause chan

## PMOS Transistor (M2)

The PMOS transistor acts as an active load. It is connected to
the supply voltage and provides the bias current required for the NMOS transistor. 
Using an active load improves the voltage gain compared to a simple resistor load.

## Source Resistor (R1)


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

The Source resistor(Rs) is determined  by

0.2 =  200uxRs

Rs=  1k ohm

# Overdrive Voltage Verification

The overdrive voltage determines the strength of inversion and the current capability of the device.

## Calculation

VGS = VG − VS  

VGS = 0.81 − 0.2 

VGS = 0.61 V

Vov = VGS − VTH  

Vov = 0.61 − 0.36 

Vov = 0.25 V

# Result

VGS = 0.61 V  

Vov = 0.25 V

## Acceptable Overdrive Range

Minimum Vov: > 0  

Maximum Vov: < VDS = 0.75 V

Thus,

0 < Vov < 0.75

The selected value **Vov = 0.25 V** falls within this acceptable region.

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

## Width calculation


Id=200u A

upcox=9.7361x10-5

ID=upcoxw/l(vgs-vt)

w=200x10^-6x2x180n/uncox(o.25)^2

w=11.82u

## NMOS  gate  source  voltage

For the NMOS transistor operating in saturation:

VGS =VTH+VOV

VGS=0.36+0.25

VGS=0.61

So  gate  voltage 
VG=VGS+VS

VG=0.61+0.2

VG=0.81

## NMOS  width  calculation

for  MOSFET in  saturation  region

Id=uncoxW/L(vgs-vt)/2

w/l=2ID/uncox(vgs-vt)

uncox=2.3039x10^-4
w/l=2x200u/2.3039x10^-4x0.25

w/l=23.37

W=4.995u

# DC Operating point

## Procedure

1. Open the designed CMOS common source amplifier circuit in LTspice.

2. Ensure that all the circuit components such as NMOS transistor, PMOS transistor, resistors, voltage sources, and supply voltage are properly connected according to the circuit schematic.

3. Assign the required DC voltage values for the power supply (VDD) and bias voltage sources used in the circuit.

4. Click on “Simulate” in the LTspice menu and select “Edit Simulation Command”.

5. In the simulation command window, select the “Operating Point” option.

6. Click “OK” and place the .op command on the schematic.

7. Run the simulation by clicking the “Run” button.



 
![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-10%20at%2011.22.03%20PM.jpeg)


## Conclusion


Initially, smaller transistor widths did not provide the expected bias 
current and output behavior(ID=200uA,VOUT=0.95). By increasing the width of the NMOS and PMOS 
transistors, the required drain current and proper operating point were achieved.
The final dimensions used in the design  are  Wn=12.8u  and  Wp=37.16u


## Output Swing Analysis Using Headroom and Legroom

1. Operating Condition of the Amplifier

For proper operation of the CMOS common source amplifier,
both NMOS (M1) and PMOS (M2) must operate in the saturation region.
Because of this requirement, the output voltage cannot vary over the full supply range from 0 V to VDD

The output voltage limits are determined by two constraints:
1)NMOS legroom (lower output limit)
2}PMOS headroom (upper output limit)

##  NMOS Legroom (Lower Output Voltage Limit)
Legroom represents the minimum output voltage required to keep the NMOS transistor in saturation.
In the circuit, the source of the NMOS transistor is connected to a source resistor 
Rs=1k 0hm  So  vs =0.2

for NMOS in  saturation  VDS>VOV

Hence  minimum  output  swing is 0.2+0.25=0.45

##  PMOS Headroom (Upper Output Voltage Limit)

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

# Transient  anyalsis

## Procedure 

1. Open the Circuit

2. Configure the Input Signal

3. Insert Transient Analysis Command.

4. Set the Simulation Time

5. Place the Simulation Command

.tran 5m

6. Run the Simulation

7. Observe the Waveforms
   
Input image

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-12%20at%201.34.51%20AM%20(6).jpeg)

Output image

![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/output%201.jpg)

## Simulated Gain

Vout(p-p)=0.206

Vin(p-p)=19.9mV

AV=Vout/Vin

Av=206.8/19.9mV

Av=10.345

Av(db)=20 logAv

Av(db)=20log(10.345)

Av(db)=20.2946


##  Conclsion

The Transient analysis shows that the amplifier produces an output 
signal approximatelyFrom the transient simulation results, it is 
observed that the output waveform has an amplitude nearly 10.34 times
higher than the input signal, confirming that the circuit functions effectively as a voltage amplifier
10.34 times larger than the input signal confirming the amplification capability of the circuit


# AC  Anyalsis

## Procedure

1. Open the Circuit

2. Set the AC Source Value

3. Insert AC Analysis Command

4. Configure Frequency Sweep

5. Place the Simulation Command

6. Run the Simulation

7. Observe the Output Response


![Image description](![Image description](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-10%20at%2011.22.03%20PM%20(2).jpeg))


## Gain bandwidth product

GBP=10.345 x 316.68 Mhz
GBP=3.269Ghz

## Unity gain Bandwidth
UGB=3.645 GHz

## Conclusion

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



# Source Degenerated Common Source Amplifier (TSMC 180nm)



# Introduction

Analog CMOS amplifiers are fundamental building blocks in many electronic systems such as signal processing circuits, sensors, and communication systems. Among various amplifier configurations, the **common source amplifier** is widely used because it provides good voltage gain and relatively simple implementation.

In order to improve linearity and stabilize the operating point, **source degeneration** is introduced. Source degeneration introduces local negative feedback through a source transistor or resistor, which improves stability and reduces distortion.

In this experiment, a **Source Degenerated Common Source MOS Amplifier** is designed using **TSMC 180 nm CMOS technology**. The design is evaluated through simulation to study important amplifier characteristics such as gain, bandwidth, unity gain bandwidth, and output swing.


# Objective

To design and analyze a **Source Degenerated Common Source MOS amplifier** using **TSMC 180 nm CMOS technology** and evaluate its performance in terms of:

- Voltage Gain
- Bandwidth
- Unity Gain Bandwidth
- Output Voltage Swing
- DC Operating Point



# Circuit Diagram

![Circuit Diagram](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-15%20at%209.35.01%20PM.jpeg)

*Figure: Source Degenerated Common Source Amplifier*

The circuit consists of three MOS transistors:

- **M1 (NMOS)** – Main amplifying transistor
- **M2 (PMOS)** – Active load transistor
- **M3 (NMOS)** – Source degeneration transistor

The input signal is applied at the **gate of M1**, while the amplified output is obtained from the **drain node (Vout)**.


# Design Specifications

| Parameter | Value |
|----------|------|
| Technology | TSMC 180 nm |
| Supply Voltage VDD | 1.5 V |
| Power Constraint | ≤ 0.5 mW |
| Load Capacitance CL | 1 pF |
| Channel Length L | 180 nm |


# Bias Current Calculation

The bias current is determined using the power constraint.


P ≤ VDD × ID


Substituting the given values:


0.5 mW ≥ 1.5 × ID


ID ≤ 0.33 mA


Chosen operating current:


ID = 200 µA



# Assumption of Overdrive Voltage

VOV = 0.25 V

### Justification

- Maintains balance between **power consumption and gain**
- Ensures MOS transistor operates in **strong inversion region**
- Lower VOV improves **transconductance (gm)**

## Bottom NMOS (M3)

The lower NMOS transistor establishes the required bias current for the cascode stage.

| Parameter | Calculation | Value |
|-----------|-------------|-------|
| VGS3 | VTHn + Vov | 0.36 + 0.25 = **0.61 V** |
| Gate Voltage | Bias value | **0.61 V** |
| Source Voltage | Ground | **0 V** |


Thus **M3 operates in saturation** and provides the required current source.


## Cascode NMOS (M1)

The cascode transistor improves the output resistance and increases the gain of the amplifier.

| Parameter | Calculation | Value |
|-----------|-------------|-------|
| Gate Voltage | Given | **0.81 V** |

### Saturation Verification

| Condition | Result |
|----------|--------|
| VDS1 ≥ Vov | **0.566 ≥ 0.25 ✔** |

Hence **M1 operates in saturation**, ensuring proper cascode operation.


## PMOS Active Load (M2)

The PMOS transistor acts as an active load and provides the bias current for the amplifier.

| Parameter | Calculation | Value |
|-----------|-------------|-------|
| Source Voltage | VDD | **1.5 V** |
| Gate Voltage | Given | **0.86 V** |
| VSG2 | VS − VG | **1.5 − 0.86 = 0.64 V** |

Thus the **PMOS active load operates in saturation**.




# Width Calculation

Using MOSFET saturation equation:
(NMOS Width)


ID = (μnCox /2) × (W/L) × (VOV)^2


After substituting parameters:


W ≈ 11.83 um

Using MOSFET saturaion equation:
(pmos width)

Id =(upcox/2)xw/Lxvov^2

after substituting parameters we get 

w =5um


# DC Operating Point Analysis

## Introduction

DC operating point analysis is performed to determine the **steady-state voltages and currents** of the circuit without any time-varying signals. This analysis ensures that all MOS transistors operate in the **saturation region**, which is necessary for proper amplification.

## Procedure

1. Construct the circuit in LTspice using TSMC 180nm transistor models.
2. Apply the required DC supply voltage \(VDD = 1.5V\).
3. Assign the calculated bias voltages to the circuit nodes.
4. Run **.op analysis** to obtain the DC operating point.
5. Observe node voltages and device currents.

## Simulation Result

![DC Operating Point](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/op%201.jpg)

# Conclusion

From simulation:

 We got expected VOUT ≈ 0.85 V after adjusting width values durin g
 Simulation


# Width Scaling in Simulation

| Transistor | Width |
|-----------|------|
| PMOS | 36.58 µm |
| NMOS1 | 60.3 µm |
| NMOS3 | 16.3 µm |

This confirms that the amplifier is properly biased and operating in the saturation region.



# Output Swing

## Maximum Output Voltage

For PMOS to remain in saturation:

VDD − VOUT ≥ VOV



1.5 − VOUT ≥ 0.25



VOUT,max ≈ 1.25 V


## Minimum Output Voltage

For NMOS to remain in saturation:

VOUT − VS ≥ VOV



VOUT,min ≈ 0.50 V

# Output Swing Range

| Parameter | Value |
|----------|------|
| VOUT,min | 0.50 V |
| VOUT,max | 1.25 V |
| Q-point | 0.875 V |


# Headroom and Legroom

### Headroom

Headroom represents the voltage margin between **Vout and VDD**. It ensures the PMOS transistor stays in saturation.

### Legroom

Legroom is the voltage margin between **Vout and ground**, ensuring NMOS devices operate correctly.



# Transient Analysis

## Introduction

Transient analysis is used to observe the **time-domain response** of the amplifier when an input signal is applied. This helps determine whether the amplifier correctly amplifies the input waveform.

## Procedure

1. Apply a sinusoidal input signal at the gate of M1.
2. Set simulation command:

.tran 5m

3. Run the transient simulation.
4. Observe the input and output waveforms.
5. Measure peak-to-peak voltages.

## Simulation Result

# Input Graph

![Transient Response](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/input.jpg)

# Output graph 

![Transient Response](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/output%201.jpg)


| Parameter | Value |
|----------|------|
| VOUTpp | 53.98 mV |
| VINpp | 19.18 mV |



The voltage gain is obtained using:

AV = VOUT / VIN

AV = 53.98 / 19.18


AV ≈ 2.811 V/V



# Gain in dB


Gain(dB) = 20 log10(AV)



Gain ≈ 8.98dB



# Theoretical Gain Calculation

## Channel Length Modulation

Typical values assumed:


λn = 0.1 V⁻¹
λp = 0.05 V⁻¹




# Step 1: Transconductance


gm = 2ID / VOV


gm = (2 × 200×10⁻⁶) / 0.25



gm ≈ 1.6 mS

Since M1 and M3 carry the same current:

gm1 = gm3 = 1.6 mS

# Step 2: Output Resistance

NMOS output resistance

ro1 = 1 / (λn ID)



ro1 ≈ 50 kΩ


PMOS output resistance


ro3 = 1 / (λp ID)



ro3 ≈ 100 kΩ



# Step 3: Effective Output Resistance


ro,eff = ro1 || ro3


ro,eff = (50k × 100k) / (50k + 100k)



ro eff ≈ 33.33 kΩ


# Step 4: Voltage Gain (With Source Degeneration)


AV = − gm1 × ro,eff / (1 + gm1 ro2)



AV ≈ −0.658 V/V



# Theoretical Gain in dB


AV(dB) = 20 log10(|AV|)


AV(dB) ≈ −3.63 dB


# Conclusion

The **Source Degenerated Common Source Amplifier** was successfully designed and simulated using **TSMC 180 nm technology**. The circuit shows proper amplification and stable operation under the given design conditions.

A small variation is observed between the **theoretical gain** and the **simulated gain**. This difference occurs due to non-ideal effects such as **channel length modulation, parasitic capacitances, and practical MOSFET model parameters** used in simulation.

Overall, the circuit meets the design requirements and demonstrates effective analog signal amplification.


# AC Analysis

## Introduction

AC analysis determines the **frequency response** of the amplifier. It provides information about **midband gain, bandwidth, and cutoff frequencies**.

## Procedure

1. Add AC analysis command:


.ac dec 100 0.1 5G


2. Apply a small signal AC input.
3. Run simulation.
4. Plot the magnitude response.
5. Measure midband gain and cutoff frequencies.

## Simulation Result

![AC Analysis](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/ac%201.jpg)




# −3 dB Frequency


f3dB ≈ 6.60690 MHz



# Unity Gain Bandwidth


UGB = 17.742 MHz




# Gain Bandwidth Product


GBP = AV × f3dB

GBP = 2.811*6.60690

GBP =18.571 MHz


UGB =GBP


# Conclusion

The AC analysis of the designed CMOS amplifier was successfully performed. 
The voltage gain obtained from simulation is **Av ≈ 2.811** and the -3 dB bandwidth is **6.6069 MHz**. 

Using these values, the Gain Bandwidth Product (GBP) is calculated as **18.571 MHz**, which is 
close to the simulated **Unity Gain Bandwidth (UGB) ≈ 17.742 MHz**. 

This confirms that the circuit is functioning correctly and the simulation results match the theoretical expectations.



# Result

A **Source Degenerated Common Source Amplifier** was successfully designed and simulated using **TSMC 180 nm CMOS technology**.

The circuit operates correctly in the saturation region and satisfies the specified power constraint. Transient analysis confirms signal amplification, while AC analysis demonstrates adequate bandwidth.

The simulated gain is approximately **8.49 dB**, which is higher than the theoretical estimate due to device non-idealities and simulation model effects.


# Inference

From the performed analyses, the **Source Degenerated Common Source Amplifier** operates correctly under the given design specifications. The DC operating point confirms that all transistors remain in the **saturation region**, ensuring proper amplifier functionality.

Transient analysis shows that the output signal has a larger amplitude than the input signal, verifying that the circuit provides **voltage amplification**. The practical gain obtained from simulation is approximately **2.81 V/V (8.49 dB)**.

AC analysis indicates that the amplifier operates over a **wide bandwidth in the MHz range**. It is also observed that the **Unity Gain Bandwidth (UGB) is approximately equal to the Gain Bandwidth Product (GBP)**, which is consistent with theoretical amplifier behavior.

Overall, the circuit satisfies the design requirements and demonstrates stable amplification performance.




# Common Source Amplifier with PMOS Active Load and Diode-Connected NMOS Bias (TSMC 180 nm)



# Objective

The objective of this experiment is to design and study a **Common Source MOS amplifier** using a **PMOS active load** and a **diode-connected NMOS transistor for biasing** in **TSMC 180 nm CMOS technology**.

The performance of the circuit is evaluated in terms of:

- DC operating point
- Output voltage swing
- Voltage gain
- Bandwidth
- Unity gain bandwidth
- Gain bandwidth product



# Circuit Diagram

![Circuit Diagram](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-16%20at%2012.17.33%20AM%20(2).jpeg)

*Figure: Common Source Amplifier with PMOS Active Load and Diode Connected NMOS Bias*

---

# Design Specifications

| Parameter | Value |
|--------|--------|
| Technology | TSMC 180 nm |
| Supply Voltage \(V_{DD}\) | 1.5 V |
| Power Constraint | ≤ 0.5 mW |
| Load Capacitance \(C_L\) | 1 pF |
| Channel Length \(L\) | 180 nm |

---

# Bias Current Calculation

From the power constraint,


P ≤ VDD × ID


Substituting the values,


0.5 mW ≥ 1.5 × ID



ID ≤ 0.33 mA


To satisfy the power constraint while maintaining proper operation of the amplifier,


ID = 200 µA


This current ensures low power consumption and stable biasing.



# Assumption of Overdrive Voltage

The overdrive voltage for the MOS transistors is assumed as:

VOV1 = 0.2 V
VOV2 = 0.2 V


### Why VOV = 0.2 

A moderate value of overdrive voltage is selected because it:

- Provides sufficient **transconductance (gm)** for amplification  
- Maintains a stable **drain current (ID)**  
- Leaves adequate **voltage headroom for output signal swing**


# DC Bias Analysis

Overdrive voltage relation:


VOV = VGS − VTH


Given

VTH ≈ 0.36 V


For the bias transistor M3,


VGS3 = VOV3 + VTH

VGS3 = 0.2 + 0.36



VGS3 = 0.56 V


Thus,


VG3 = 0.56 V


For the amplifying transistor M1,


VGS1 = VOV1 + VTH


VGS1 = 0.2 + 0.36



VGS1 = 0.56 V


Gate voltage:


VG1 = VS + VGS1



VG1 = 0.56 + 0.56

VG1 = 1.12 V

# Width Calculation

MOS saturation current equation:


ID = (µnCox / 2) × (W/L) × (VOV)^2


Rearranging,


W = (2 × ID × L) / (µnCox × VOV²)


The calculated NMOS width is approximately


W ≈ 7.80 µm




# PMOS Width Calculation

Using the same current equation,


W ≈ 18.47 µm



# Output Swing Analysis

For PMOS transistor to remain in saturation,

VSD ≥ VOV


Since,


VSD = VDD − VOUT


Therefore,


VDD − VOUT ≥ VOV2


Maximum output voltage:


VOUT,max = VDD − VOV2



VOUT,max = 1.5 − 0.2



VOUT,max = 1.30 V



# Minimum Output Voltage

For NMOS saturation,


VDS ≥ VOV


VDS = VOUT − VRS


Where


VRS = 0.56 V


Thus,


VOUT,min = VRS + VOV1
``

VOUT,min = 0.56 + 0.2


VOUT,min = 0.76 V

# Output Swing

| Parameter | Value |
|--------|--------|
| \(V_{OUT,max}\) | 1.30 V |
| \(V_{OUT,min}\) | 0.76 V |


Vswing = VOUT,max − VOUT,min



Vswing = 1.30 − 0.76



Vswing = 0.54 V


# Symmetrical Bias Point

For symmetrical signal swing,


VOUT(Q) = (VOUT,max + VOUT,min) / 2


VOUT(Q) = (1.30 + 0.76) / 2


VOUT(Q) ≈ 1.03 V

# Headroom and Legroom

**Headroom**

Voltage margin between the output node and \(V_{DD}\) ensuring the PMOS transistor remains in saturation.

**Legroom**

Voltage margin between the output node and ground ensuring the NMOS transistor remains in saturation.

Adequate headroom and legroom prevent distortion and signal clipping.


# DC Analysis


## Introduction

DC Operating Point analysis is used to determine the *steady-state voltages and currents* in the circuit without any time-varying input signal. This analysis helps verify whether the MOS transistors are operating in the *desired region (saturation region)*, which is required for proper amplifier operation.

## Procedure

1. Open *LTspice* and create a new schematic.
2. Add the *NMOS and PMOS transistors* and include the TSMC 180 nm model library.
3. Construct the *Source Degenerated Common Source Amplifier circuit* according to the design.
4. Apply the supply voltage *VDD = 1.5 V*.
5. Set the required bias voltages for the transistors.
6. Include the model file using


.lib tsmc018.lib

7. Add the operating point command

.op

8. Run the simulation.
9. Observe node voltages and currents to confirm that the transistors operate in the *saturation region*.


![Operating Point](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-16%20at%2012.17.32%20AM.jpeg)

Important simulation values:


Vout ≈ 1.02 V
ID ≈ 203 µA


# Conclusiom

 Width Optimization in Simulation

| Transistor | Final Width |
|--------|--------|
| NMOS1 | 32.8 µm |
| NMOS3 | 32.8 µm |
| PMOS | 80 µm |

so for above width we get expected output 


- Channel length modulation
- Mobility degradation
- Accurate BSIM transistor models used in TSMC technology

Therefore device dimensions are slightly adjusted during simulation.



# Transient Analysis

## Introduction

Transient analysis is used to observe the *time-domain behavior* of the amplifier
when a time-varying input signal is applied. It helps verify whether the circuit properly
*amplifies the input signal* and allows measurement of input and output waveforms.

## Procedure

1. Apply a *sinusoidal input signal* to the gate of transistor M1.
2. Set the amplitude and frequency of the input signal.
3. Add the transient analysis command


.tran 5m


4. Run the simulation.
5. Plot the *input and output voltage waveforms*.
6. Measure the *peak-to-peak input and output voltages*.

   # VOUT IMAGE 

![Transient Waveform](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-16%20at%2012.17.32%20AM%20(1).jpeg)

# VIN IMAGE

![Transient Waveform](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-16%20at%2012.17.33%20AM%20(1).jpeg)

| Parameter | Value |
|--------|--------|
| \(V_{OUT,pp}\) | 306.30 mV |
| \(V_{IN,pp}\) | 19.69 mV |

Voltage gain


Av = VOUT / VIN

Av ≈ 15.556 V/V


# Practical Gain in Decibels

Gain(dB) = 20 log10(Av)


Gain ≈ 23.83 dB


# Theoretical Calculations

### Channel Length Modulation


λ = 0.1 V⁻¹( value is commonly used for short channel CMOS technoogies )


### Transconductance


gm = 2ID / VOV


ID = 200 µA
VOV = 0.2 V


gm = 2 mS

 since  transistor M1 and M3 carry the same current 
 the same current and same vov so gm1=gm3

 
### Output Resistance


ro = 1 / (λ ID)

ro = 1 / (0.1 × 200 × 10⁻⁶)

ro ≈ 50 kΩ

### Voltage Gain


Av = − gm1 ro2 / (1 + gm1/gm3)


Since

gm1 = gm3



Av = − (2 mS × 50 kΩ) / 2

Av = −50 V/V


Magnitude


|Av| = 50


### Gain in Decibels


Av(dB) = 20 log10(50)

Av(dB) ≈ 33.97 dB
 

# Conclusion

A small variation is observed between the **theoretical gain** and the **simulated gain**. 
This difference occurs due to non-ideal effects such as **channel length modulation, parasitic 
capacitances, and practical MOSFET model parameters** used in simulation.

Overall, the circuit meets the design requirements and demonstrates effective analog signal amplification.



# AC Analysis

## Introduction

AC analysis is used to study the *frequency response of the amplifier. It helps determine important parameters such as **bandwidth, −3 dB frequency, unity gain bandwidth, and gain bandwidth product*.

## Procedure

1. Apply a *small signal AC input* at the input of the amplifier.
2. Add the AC analysis command in LTspice


.ac dec 100 0.1 5G


3. Run the simulation.
4. Plot the *frequency response (gain vs frequency)* of the output signal.
5. Identify the *−3 dB cutoff frequency* from the graph.

![AC Response](https://github.com/chandrashekhar-sangolagi/LIC/blob/main/WhatsApp%20Image%202026-03-16%20at%2012.17.33%20AM.jpeg)


frequency at -3db

fH ≈ 225.89 GHz


# Gain Bandwidth Product


GBP = Av × f−3dB

GBP= 15,627x225.89



GBP ≈ 3.545 GHz


# Unity Gain Bandwidth

Unity gain bandwidth occurs when gain becomes **0 dB**.

UGB ≈ 4.018 GHz

Thus,

GBP ≈ UGB


# Conclusion 

The simulated gain is close to the theoretical gain of the amplifier. 

After adding the load capacitor (CL = 100 pF), the frequency response of the circuit changes

and the **Gain Bandwidth Product (GBP)** becomes approximately equal to the **Unity Gain Bandwidth (UGB)**.

This confirms the expected behavior of the amplifier and validates the design through simulation. 



# Result

The **Source Degenerated Common Source Amplifier** was successfully
designed and simulated using **TSMC 180 nm CMOS technology**. The circuit operates
in the saturation region and provides proper voltage amplification.

The simulated results show that the amplifier achieves the expected gain and frequency 
response. It is also observed that the **Gain Bandwidth Product (GBP)** is approximately 
equal to the **Unity Gain Bandwidth (UGB)** after including the load capacitance.

Thus, the designed amplifier satisfies the given design specifications and demonstrates stable amplification behavior.


# Inference

A common source amplifier using **PMOS active load and diode connected NMOS bias** was
successfully designed using **TSMC 180 nm technology**.  

The amplifier provides a practical gain of approximately **23 dB**, while maintaining 
proper biasing and output swing. The AC analysis confirms a high unity gain bandwidth in the 
**GHz range**, demonstrating good high-frequency performance. The theoretical calculations 
and simulation results show reasonable agreement considering practical device effects.




