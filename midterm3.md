# Current- mode Logic Families
## Basic ECL circuit (Differential amplifier)
Configuration:
	* Q1 - input transistors
	
	* Q2 - reference transistor
	
	* Emitter of both connected
	
		* R_E connected to E node to $$-V_{EE}$$

	* Two R_C's
R_C and R_E are chosen such that ffor V_r = V_i, Q1=Q2=active

Note: usually ignore base current 

$$\Delta V = V_{BE1} - V_{BE2} =  V_i - V_R $$
$$I_{C1} = \frac{\alpha* I_E}{1+exp(-\Delta V/ V_T}$$
$$I_{C2} = \frac{\alpha* I_E}{1+exp(\Delta V/ V_T}$$
$$\frac{I_{C1}}{I_{C2}} = \frac{V_{BE1} - V_{BE2} }{V_T}$$

### Case 1 (V_i = V_R) (both active)
* $$I_{C1} = I_{C2}$$
* $$V_{C1} = V_{C2} = V_{CC} - I_{C1}R_C$$

### Case 2 (V_i > V_R)
* I_{C1} rises => V_{C1} drops
* I_{C2} falls => V_{C2} incr

### Case 3 (V_i < V_R)
* I_{C2} rises => V_{C2} drops 
* I_{C1} falls => V_{C1} incr


I_E is approx constant

$$\Delta V = +120 mV$$ turns off Q2
$$\Delta V = -120 mV$$ turns off Q1

$$V_{C1} - V_{C2} is proportionsal to V_i - V_R


## Basic Integrated Circuit ECL OR/NOR Gate
Configuration:
	* Q1A, Q1B  - input transistors
	* Q2 - reference transistor($$V_R = V_{BB} $$)
	* Q3 - its base connected to V_{C1}
	* Q4 - its base connected to to V_{C2}
	* R_{E3}, R_{E4} - connected to - V_EE
	* R_{C1}, R_{C2}
	* R_{E} connected to V_E to -V_EE
	* NOR ouput - V_{E3}
	* OR  ouput - V_{E4}

Purpose of Q3 and Q4:
	* so if you add load ECL gates they can be driven
		* Between Cutoff and active region
	* They operate in active mode and lower V_{C1} and V_{C2} by BE junction drops

## How to find V_{OH} and V_{OL}
### V_OH
1.)Set V_{A} and V_{B} > V_{R}
2.)0-V_{E3} = .7 = V_{OH}
### V_OL
1.) set V_{A} = V_{OH}, V_{B} = 0
2.) Find V_E
3.) get I_E = I_{C1}
4.) I_{C1} => V_{C1}
5.)V_{OL} = V_{E3} = V_{C1} - .7
### V_BB
$$V_R = \frac{V_{OH}+V_{OL}}{2}$$

## V_{IH} and V_{IL}
* V_{IH} = V_R + .12
* V_{IL} = V_R - .12


### Disadvtanges
* power dissipation is much higher than Saturating logic fams

### Fan-out
* calculated when inputs at logic low.
* Using output at Q3
*


# Schmitt Trigger(page 473)
* They convert slowly varying voltage waveforms to well  - defined logic levels
with sharp transitions.
* $$R_{C1} > R_{C2}$$

## Case 1 ($$0<V_i < V_{tu}$$ )- [$$V_{i} = 0, Q_1 = OFF, Q_2 = SAT $$] 
* $$I_{C1} = I_{B2}
* $$V_{o} = V_{C2} = V_{OL} = V_{CC} - I_{C2}R_{C2}$$

### Steps(finding $$V_{tu}$$)
$$\frac{V_E}{R_E} = \frac{V_{CC} - (V_E + .8)}{R_{C1}} + \frac{V_{CC} - (V_E + .1)}{R_{C2}}$
solve for $$V_{E}$$
Hence:
	V_{OL} = V_E + V_{CE2} = 1.92V


## Case 2 ($$V_i = V_{tu}$$) - [$$V_{i} = V_{E} + .6, Q_1 = almost Sat, Q_2 = OFF$$]
* $$V_{CE1}  = V_{BE2} = .1V$$
* $$V_{OH} = V_{CC}$$

### Steps(finding $$V_{tu}$$)
$$V_{i} = V_{tu} = V_E + .6$$

## Case 3 ($$V_i = V_{tu}) [$$V_{BE2} = .6V, V_{BE1} decreases, Q_1  = OFF, Q_2 = active]

#### Steps(finding $$V_{tl}$$)
$$V_i is decreased$$
$$I_{C1} = I_E = \frac{V_{CC} - .6 }{R_{C1} + R_E} = .88mA$$
$$V_E = R_E * I_E$$
$$V_i = V_{tl} = V_E + .7 = 1.58

# The 555 Timer Integrated Circuit
Contains:
* Two comparators C1 and C2
* RS latch F(using !Q)
* One BJT (Q1), R_B
* Output driver (inverterting amp)
* $$V_{tu} = (2/3)V_{CC}$$
* $$V_{tl} = (1/3)V_{CC}$$
* Three resistors near comps input R_T


## Monostable Multivibrator Operation(one shot)
* $$V_{Th} = V_{cap}$$ 
*
### Stable Case V_o = 0
* S and R are logic low
* !Q = 1
* $$V_{trig} > V_{CC}/3 $$
* C is dischared by Q1 which is on

### Unstable Case V_o != 0
* $$V_{trig} < V_{CC}/3 $$
* comp C2 goes high => sets
* !Q = 0 => Q1 isnt on C doesnt dicharge
* At time T ,$$V_{Th} = V_{+,C1} == (2/3)V_{CC}$$
	* R is set and !Q = 1
$$T = RC ln(3)$$

## Astable Multivibrator Operation(running free)
* $$V_{cap} = V_{+,C1} = V_{-, C2}$$
* R_{A} connected at V_{CC}
* R_B at node connecting discharge, and R_A
* C node below R_B
* Trigger input and threshold input are both connected input.
* Both compartators C1 and C2 re logic low
* or only one of them is logic high

### !Q = high case
* Cap discharges via R_B
*
### !Q = low
* Cap charges via R_A and R_B 

### Operation (Assume !Q=0 initally)
* Cap begins to charge toward V_{CC}
	* With $$\Tau = (R_A + R_B)C$$
At $$V_C = V_{tl} = (1/3)V_{CC}$$
	* C_2 = logic low (no effect on F)
At $$V_C = V_{tu} = (2/3)V_{CC}$$ (discharging)
	* C_1 = output logic high (resetting latch)
	* Q_1 = on, cap begins to discharge 
	* toward zero with init val of (2/3)V_{CC}
		* With $$\Tau = R_B*C$$
At $$V_C = V_{CC}/3 $$ (output of C2) changes logic high 
	* !Q goes low and latch is set
Reatpeats the sequence above

$$T_{on} = (R_A + R_B) C ln(2)$$
$$T_{off} = R_B * C ln(2)$$

### Period of the square wave becomes:
$$T = T_{on} + T_{off}$$

$$Duty \;Cycle = \frac{T_{on}}{T} = \frac{R_A+R_B}{R_A + 2*R_B}$$




`











