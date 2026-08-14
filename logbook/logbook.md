**ENGINEERING LOGBOOK & DEBUGGING JOURNAL**

8/14/26

**1. Clock Module (LM555 Timers)**

Problem: Pressing the manual step button for the clock cycle trigger multiple clock cycles instead of a single pulse.

Cause: Mechanical push buttons trigger multiple micro which lead to high frequency signals sent to the output of the 555 timer.

Solution: Used 0.1 and 0.001 microfarad capacitors to deliver signals. Also utilized the SR latch within the 555 IC, in which it only takes the first signal given. 

**2. (74LS173)**

Problem: Register A and Register B occasionally latched corrupted data or glitched during clock transitions.

Cause:Floating control inputs on the 74LS173 registers picking up inputs and leaving it to float due to having no outputs.

Solution: Tied pins 1 and 2 of the 74LS173 to ground to stop floating inputs.

**3. Voltage Drops**

Problem: System supply voltage dropped significantly when driving register outputs to the bus and clock module.

Cause: Each IC needs a minimum of 4v to properly input and output data.

Solution: The 555 timer module will have its own dedicated power source, as well as the "A" and "B" registers.

**4. Short Circuit**

Problem: The ES245N IC in the "B" register could not output data to the 74LS173 ICS.

Cause: A pin was incorrectly tied to ground which cause a short circuit and overheated the chip.

Solution: Replaced with a new ES245N.

**5. Another Short Circuit**

Problem: When testing binary outputs from the LED bus to the registers, the second 74LS173 was unable to output data to the LEDS. 

Cause: A pin incorrectly tied to ground.

Solution: Replaced with new 74LS173
