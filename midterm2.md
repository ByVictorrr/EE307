# The BJT Inverter

insert paramters for the bjt here

## Unloaded BJT inverter

$$V_{IL} = V_{BE(cut-in)} = .6V$$
$$V_O(V_i = 0V) = V_{OH} = V_{CC}$$

$$V_O(V_i = V_{CC}) = V_{OL} = V_{CE(sat)} = .1V$$
$$V_{IH} = I_{B(sat)} R_B + V_{BE(sat)}$$

### Example: For BJT inverter

Find: NM_H, NM_L

Given: $$\Beta, V_{CC}, R_B, R_C, V_{CE(SAT)}$$

Steps:
$$V_{IH} = I_{B(sat)} R_B + V_{BE(sat)}$$ (1)
$$\Beta * I_{B(sat)} = I_{C(sat)}$$
so, $$NM_H = V_{OH} - V_{IH}$$
	$$NM_L = V_{IL} - V_{OL}$$

## Loaded BJT inverter

k = Base overdrive factor 
$$k = \frac{I_{B(sat)}}{I_{B(EOS)}}$$

* Assume k = 1, if not given

### BJT inverter fan out
Fan out = max number of gates inv can drive while maintaining output logic high 

Condition for inverter to operate properly(NM_H = 0): V_{OH} >= V_{IH} 

$$V_{OH} = V_{CC} - N*k\frac{V_{CC} - V_{CE(sat)}}{\Beta} >= V_{IH}$$

$$N <= \frac{\Beta[V_{CC} - V_{IH}]}{k[V_{CC} - V_{CE(sat)}]}$$

$$N_{max} = \frac{\Beta[V_{CC} - V_{IH}]}{k[V_{CC} - V_{CE(sat)}]}$$
$$N_{max} = \frac{\Beta[V_{CC} - V_{BE(sat)}]}{k[V_{CC} - V_{CE(sat)}]} -\frac{R_B}{R_C}$$


### Example: Calculate Fan out 

Find: (a)N_{max}, (b)N($$reduces NM_H to NM_L$$)
Given: $$\Beta = 70$$

Steps:

(a)use  N_{max} eqn above
(b) $$NM_L = .6 - .1 = .5V$$
	$$NM_H = .5 = V_{OH} - V_{IH} = NM_L$$
	=> $$V_{OH} = 2V$$
	$$\frac{[V_{CC} - V_{OH}]}{R_C} >= N[ V_{OH} - V_BE(sat)] / R_B $$
	=> N = 25

# Resistor - Transistor Logic (RTL) gate

## NOR gate configuration Description
	* 2 BJTs are in parallel
	* node connecting, both collector have R_c below Vo



## Unloaded RTL gate
$$V_{IL} = V_{BE(cut-in)} = .6V$$
$$V_O(V_i = 0V) = V_{OH} = V_{CC}$$
$$V_O(V_i = V_{CC}) = V_{OL} = V_{CE(sat)} = .1V$$
$$V_{IH} = I_{B(sat)} R_B + V_{BE(sat)}$$
## Loaded RTL gate
	$$V_{OL} = .1V$$
	$$V_{IL} = .6V$$
	$$V_{IH} = V_{BE(sat)} + I_{B(sat)} R_B$$
	$$V_{OH} = V_CC - N*I_{B(sat)}R_C$$

	$$N_{max} = \frac{\Beta[V_{CC} - V_{BE(sat)}]}{k[V_{CC} - V_{CE(sat)}]} -\frac{R_B}{R_C}$$

## Wired AND in RTL

	* Anding two NOR gates by just connecting two NOR gates 
	* Wired AND in RTL is eqialent to single level logic with expanded fan-in
	
	* Shortcomings of BJT invert and RTL
		* Low noise margin(NM_L = .5V)
		* fan-out (loading) reduces V_{OH} and therefore reduces NM_H

# Diode Transistor Logic (DTL)

$$V_{OH} = V_{CC} = 5V$$
$$V_{OL} = V_{CE(sat)} = .1V$$
$$V_{IL} = V_{BE(cut-in)} + 2*V_{D(on)} - V_{D(on)}$$
		 = .6V + .7V = 1.3V
$$V_{IH} = V_{BE(sat)} + 2*V_{D(on)} - V_{D(on)}=.8V+.7V=1.5V$$

NM_H = V_{OH} - V_{IH} = 3.5V
NM_L = V_{IL} - V_{OL} = 1.2v


## Advantages of DTL
	* High noise Margins
	* Loading does not degrade V_{OH} or NM_H

## Fan-Out of DTL
	* Found when Vo of driver is V_{OL}
	* $$N_{Max} <= \frac{I_{OL}}{I_{IL}}$$

### From Load Gates:
	I_{IL} = \frac{V_{CC} - V_{CE(sat)} - V_{D(ON)} }{R_1} - \frac{V_{CC} -V_{CE(sat)} - 2 * V_{D(ON)} + V_{BB} }{R_2} 
For Driver:
	







