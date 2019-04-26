# Complexity of Digital ICS:
	* SSI - [1,10] gates per chip(latch,ff)
	* MSI - [10,100] gates per chip(counters, regs)
	* LSI - [100,1000] gates per chip(RAM,ROM,PLA)
	* VLSI - [1000,infinity] gates per chip (uProcessor,mems, processor)
	
# Charactersistics of general inverter VTC

### Threshold voltages
* $$V_IL$$  -  is the maxiumum allowable input voltage such that the gate is off
* $$V_IH$$ - is the min allowable input voltage such that the gate is on
	* The above threshold voltages are found by setting dVo/dVi = -1
	* undefined logic level between : V_{IL} <= Vi <= V_{IH}

* $$V_{OH} = output when vi=0
* $$V_{OL} = output when vi=VoH


$$V_{tw}= V_{IH} - V_{IL}$$ 
	* A good logic gate has a small transition width

$$V_{ls} = V_{OH} - V_{OL}$$
	* A good logic gate has a large logic swimg

Noise Margin: ability of a digiital logic circuit to maintain its logic state
under varying voltage levels

Given a casecade of two inverter in order for the inv2 to have a high logic for 
the load gate vi2 >= VIH.


### Noise Margins

$$NM_H - V_{OH} - V_{IH}$$
$$NM_L - V_{IL} - V_{OL}$$

$$NM = min{NM_L, NM_H}$$

### Example : VTC of ideal inverter
 $$V_{OH} = V_{CC}$$
 $$V_{OL} = 0$$
 $$V_{IH} = V_{IL} = V_{CC}/2$$
 $$NM_H = \frac{V_{DD}}{2}$$
 $$NM_L = \frac{V_{DD}}{2}$$
 $$V_{ls} = V_{DD} $$
 $$V_{tw} = 0 $$

 $$\frac{Vo}{Vi}|_{V_{OL} and V_{OH}} = \infty $$

### Propagation Delays

 $$t_p = \frac{t_{PHL}+t_{PLH}}{2}$$ = Max pusle rate for transmition thru it
 $$t_{PHL}$$ = time at 50% output Vo falling - time at 50% input rising Vi
 $$t_{PLH}$$ = time at 50% output Vo rising - time at 50% input falling Vi
 $$t_r$$ = rise time (10%-> 90%)*Vo (just loook at output) 
 $$t_f$$ = fall time (90% -> 10%)*Vo (just look at output)

 $$Circuit Bandwith = \frac{.35}{t_r}$$


# Diode

	$$I_D = I_s ( e^{V_D/(\eta*V_T)} - 1}$$	

## Models of diode
	(1) ideal switch diode model
	(2) ideal switch with voltage offset 
		* we use this on in this course
	(3) piecewise linear 
		* $$I_{off} <= .01 I_{on} $$
		* $$V_{off} = .6V, V_{on} = .7V $$
	
### Limitation of Diode digitial Circuits
	* Cant implment, NOT, NOR or NAND gates
	* They have progrlems, voltage drop across them

# MOSFETS
	Ehancement MOS - channel isnt already built in 
					(normally off)
	Depletion MOS - channel is already present
					(normally on)

	Triode section - $$ V_{GS} > V_T and  V_{DS} <= V_{GS} - V_T$$
			* $$I_{DS} = k[2(V_{GS} - V_T)V_{DS} - V_{DS}^2]$$

	Satuation region - $$ V_{GS} > V_T and V_{DS} >= V_{GS} - V_T $$
			* $$I_{DS} =  k(V_{GS} - V_T)^2 $$

	$$k = (1/2)\mu_N C_{ox} * (W/L)$$ [A/V^2]
	k = (1/2) k' (W/L)

##Body Effect 
	* V_T = V_{T0} + \Gamma * \sqrt{V_{SB}} $$

## PMOS - like NMOS but S is the high and D is low
	Triode section - $$ V_{SG} > |V_T| and  V_{SD} <= V_{SG} - |V_T|$$
			* $$I_{SD} = k[2(V_{SG} - |V_T|)V_{SD} - V_{SD}^2]$$

	Satuation region - $$ V_{SG} > |V_T| and V_{SD} >= V_{SG} - |V_T| $$
			* $$I_{SD} =  k(V_{SG} - |V_T| )^2 $$

## MOS Equiv circuits: 
	### Transconductance: Q = saturation
	$$g_m = \frac{\Delta I_D}{\Delta V_{GS}}|_{\Delta V_{DS} = 0} = $$
	=> $$g_m = 2k*(V_{GS} - V_T)$$
	=> $$g_m = 2 \sqrt{kI_D} $$
	### Dynamic Resistance(ac): Q = Saturation
	$$r_d = \frac{\Delta I_D}{\Delta V_{GS}}|_Q}
	=> $$r_d = \frac{1}{k(V_{GS} - V_T)^2 \lambda}$$
	### Static Resistance(dc): Q= any
	$$R_DS = V_{DS} / I_{DS}$$

# MOS inverters (dsecription with body -source connected)
(Note) - Vo is taken across ML(S) and MD(D)
	## Resistive E-NMOS inverter 
		* The Resistor (load) is connected to Vdd,
		  this is then connected to the drain
		  of the E-NMOS (driver)
		* It takes up to much space
	## Saturated Enhancement load E-NMOS
		* The E-NMOS (ML) its drain con. to Vdd,
		  its gate connected V_{GG} - battery,
		  this is then connected to the drain
		  of the E-NMOS (M_D), Vi = V_GD
		* lower Voh, lower NM, small V_{ls}
		  large V_{tw}, two batteries
	## Depletion load NMOS inverter 
		* The D-NMOS(ML), its drain->Vdd,
		  MLs gate is connected to its source,
		  That source terminal connected to drain
		  of driver (MD).
		* Only uses one batt.

	$$K_R = geometric ratio \frac{k_D}{K_L}$$

	insert comparison table nmos invertes here

## Design NOR and NAND - using NMOS inverter (M_L config like inv)

	### NAND - M_{D1} ..M_{Dn} in series
		* drivers are the same trans
	### NOR - M_{D1} ..M_{Dn} in  parallel
		* driver are the same trans

# CMOS inverter 
	* insert regions 

	* I_{D,max} = I_D(Vi=Vo)	
	* $$V_M = \frac{V_{TN} + \sqrt{K_R}(V_{DD} = |V_{TP}|)}{1+K_R}$$
	
## Symmetrical CMOS inverters
	* $$V_{TN} = |V_{TP}|, k_p = k_N, Cox same, V_M = V_{DD}/2$$
	* => $$K_R = k_p/k_N = 1 => \frac{\mu_N}{\mu_p} = \frac{(W/L)_p}{(W/L)_N}$$
		* Usually $\frac{\mu_N}{\mu_p} = 2.5$$ => $$ (W/L)_p = 2.5 (W/L)_N$$
## Design NOR and NAND - using CMOS inverter
	### Two input NOR gate (2 Mps and 2 MNs)
		



	





















