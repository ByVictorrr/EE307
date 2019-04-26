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

#### Example : VTC of ideal inverter
 $$V_{OH} = V_{CC}$$
 $$V_{OL} = 0$$
 $$V_{IH} = V_{IL} = V_{CC}/2$$

 $$\frac{Vo}{Vi}|_{V_{OL} and V_{OH}} = \infty $$

### Propagation Delays

 $$t_p = \frac{t_{PHL}+t_{PLH}}{2}$$ = Max pusle rate for transmition thru it
 $$t_{PHL}$$ = time at 50% output Vo falling - time at 50% input rising Vi
 $$t_{PLH}$$ = time at 50% output Vo rising - time at 50% input falling Vi
 $$t_r$$ = rise time (10%-> 90%)*Vo (just loook at output) 
 $$t_f$$ = fall time (90% -> 10%)*Vo (just look at output)

 $$Circuit Bandwith = \frac{.35}{t_r}$$


## Diode

	$$I_D = I_s ( e^{V_D/(\eta*V_T)} - 1}$$	

### Models of diode
	(1) ideal switch diode model
	(2) ideal switch with voltage offset 
		* we use this on in this course
	(3) piecewise linear 
		* $$I_{off} <= .01 I_{on} $$
		* $$V_{off} = .6V, V_{on} = .7V $$
	
### Limitation of Diode digitial Circuits
	* Cant implment, NOT, NOR or NAND gates
	* They have progrlems, voltage drop across them

## MOSFETS
	Ehancement MOS - channel isnt already built in 
	Depletion MOS - channel is already present

### MOS inverters
	


















