# Waveform Blinky PCB Assembly Guide

<div style="text-align:center;">
  <img src="../product.png" alt="Instrument cover photo." style="height:400px">
</div>

### Required Equipment
<ul>
  <li>Soldering Iron</li>
  <li>Solder</li>
  <li>Flush cutters</li>
  <li>Popsicle sticks</li>
  <li>Card Scraper</li>
  <li>Tweezers</li>
  <li>Safety glasses</li>
  <li>Wire strippers (optional)</li>
  <li>Solder Paste/Heat gun (for reflow assembly if desired)</li>
</ul>

### Kit Components
<ol>
  <li>x1 - Circuit Board (PCB)</li>
  <li>x5 - 10k Ohm Resistor</li>
  <li>x1 - 110K Ohm Resistor</li>
  <li>x3 - 100K Ohm Resistor</li>
  <li>x2 - 150 Ohm Resistor</li>
  <li>x3 - LMC648 Op-Amp</li>
  <li>x3 - 1uF Capacitor</li>
  <li>x2 - Red LED</li>
  <li>x1 - 9V Battery Clips</li>
</ol>

<div>
  <img src="../ToC.png" alt="Table of Contents" style="height:400px" />
</div>

### Safety Considerations
<ul>
  <li>Assembling this kit requires the use of hot and sharp tools.</li>
  <li>Wear safety glasses when assembling this kit. Clipped leads can shoot away quickly and cause eye injury.</li>
  <li>This kit and the solder you are using may contain lead. Wash hands thoroughly after assembling and do not eat while working or ingest any kit materials.</li>
  <li>Always ensure your work area is clean and safe. Never leave a hot or sharp instrument unattended.</li>
</ul>

## Assembly 
### Applying Solder Paste
Using the kit contents checklist - layout and inventory your kit. Make sure you
have all  parts before beginning! The first stage in populating surface mount
components is to add solder paste via the included stencil. (If you would like
to hand solder these components, that can be done with tweezers and an iron as
well instead.)  


<ol>
    <li>
        Tape the PCB down to a flat surface. Be sure to avoid covering up the target component footprints.
        <img src="../step1.png" alt="Step 1" style="height:300px; max-width: 100%; display: block;">
    </li>

    <li>
        Lay the stencil over the PCB until all the holes line up evenly with the footprints. Carefully hold down the aligned stencil and tape the top and bottom down.
        <img src="../step2.png" alt="Step 2" style="height:300px; max-width: 100%; display: block;">
    </li>

    <li>
        Next you will cover the footprints generously with room temperature solder paste. Use an old card as a squeegee and squeegee across the stencil. This process is similar to silk screening a t-shirt logo. Paste should be left only on the desired component footprints.
        <img src="../step3.png" alt="Step 3" style="height:220px; max-width: 100%; display: inline-block;">
        <img src="../step4.png" alt="Step 4" style="height:220px; max-width: 100%; display: inline-block;">
    </li>

    <li>
        You will now carefully peel back the tape holding the stencil down, and gently lift it off of the PCB. This process (steps 3-5) may take a few attempts to get an even layer of paste on all the footprints. Your blinky should now be properly pasted and ready for components.
        <img src="../step5.png" alt="Step 5" style="height:300px; max-width: 100%;">
    </li>
</ol>

### Placing Surface Mount Components
<ol>
  <li>
    It’s time to start placing the surface mount devices (SMD)! Start by locating both of your 150 Ohm resistors. Resistors like these are not polar and can be placed in any orientation as long as each side of the resistor is touching a corresponding copper pad, and the black side is facing up. Using a pair of tweezers, gently place 2 of them onto the footprints labeled R8 and R9. View the image below for their locations.<br>
    <img src="../placement1.png" alt="Placement 1" style="height:200px; max-width: 100%; display: inline-block;">
    <img src="../placementA.png" alt="Placement A" style="height:200px; max-width: 100%; display: inline-block;">
  </li>

  <li>
    Locate your (qty5) 10k resistors and place them onto the footprints labeled R4, R6, R7, R10, and R11 in the same manner as the previous step. Again, these are non-polar components.<br>
    <img src="../placement2.png" alt="Placement 2" style="height:200px; max-width: 100%; display: block;">
  </li>

  <li>
    Next you will place the 110k resistor on the footprint R5.<br>
    <img src="../placement3.png" alt="Placement 3" style="height:200px; max-width: 100%; display: block;">
  </li>

  <li>
    For the last of the resistors you will take the (qty3) 100k resistors and place them on the footprints R1, R2, and R3.<br>
    <img src="../placement4.png" alt="Placement 4" style="height:200px; max-width: 100%; display: block;">
  </li>

  <li>
    Finally you will take the (qty3) 1uF Capacitors and place them on the footprints C1, C2, and C3. Although some capacitors are polar, these like the resistors are not. They can be placed in any orientation so long as each edge makes contact with the pads of the footprints.<br>
    <img src="../placement5.png" alt="Placement 5" style="height:200px; max-width: 100%; display: block;">
  </li>
</ol>


All of the SMD components are now placed and the PCB is ready to be reflowed.
This can be done in multiple ways. While it is common in large production to use
a dedicated reflow oven with 4 or more different temperature zones and a
conveyor to move the PCBs through them, the same thing can be done carefully
with a heat gun or a toaster oven.  Solder generally has a reflow temperature
profile that specifies what temperature they should be at during the reflow
timeline. In industrial operations, this is very important, but for learning how
to reflow we can relax a bit more as long as we don’t burn the PCB!  
<img src="../reflowchart.png" alt="Reflow Profile Chart" style="height:400px; max-width: 100%; display: block;">


### Heatgun Reflow Process
Using a heat gun to reflow your PCB is a less precise method, but often works
much faster for low component quantity PCBs. Set your heat gun to about 350°C
and set the air flow to a low setting to avoid blowing components off of the
PCB. Move the heat gun back and forth slowly over the components until the paste
changes from a dull gray to its shiny silver melted state. After the paste has
melted, continue to apply heat for about 5 seconds to ensure it has properly
reflowed. Repeat this process for each component until all of them have
reflowed.  

<b>Note:</b>Any crooked parts placed on the board will be pulled into line by
the surface tension of the melted solder, so long as all component contacts are
touching their respective footprint pad. If there is not good contact before
reflowing, or if there are uneven quantities of paste between pads, your
component may be pulled harder by one pad, pulling it into an upright position.
This is called tombstoning and is fixed by reflowing the solder again with the
heat gun, and using a pair of tweezers to push down the part onto the
disconnected pad.  
<div style="display: flex; align-items: center; gap: 40px; flex-wrap: wrap;">
  <div style="text-align: center;">
    <div><b>Tombstoned:</b></div>
    <img src="../tombstone.png" alt="Tombstoned Example" style="height:150px; max-width:100%;">
  </div>
  <div style="text-align: center;">
    <div><b>Correct:</b></div>
    <img src="../goodreflow.png" alt="Correct Reflow Example" style="height:150px; max-width:100%;">
  </div>
</div>

### Toaster Oven Reflow Process
<b>CAUTION:</b> DO NOT USE AN OVEN USED FOR FOOD, THIS PROCESS IS TOXIC.  

This alternate method of reflowing is a little bit more precise, but takes more
care as a mistake can burn your board, rendering it useless. For this method we
will replicate the same process as a standard reflow oven. By using a timer and
a temperature sensor to monitor and adjust our oven, we will match the reflow
chart for our paste as accurately as possible.  

Here is a four stage reflow process to follow for leaded solder paste:  
(Modeled after the SMD291AX250T4 solder paste)  

<ol>
  <li>
    <b>Preheat:</b> 0°C - 150°C over two minutes (302°F)
  </li>
  <li>
    <b>Soak:</b> 150°C - 183°C over 1.5 - 2 minutes (361°F)
  </li>
  <li>
    <b>Reflow:</b> 183°C - 220°C over 30 seconds (428°F)
  </li>
  <li>
    The PCB should reflow at some time within step three. Watch closely for when
    the board has fully reflowed and turn off the oven after 5 seconds. Leave it
    to cool for 1 minute, and then open the door.
  </li>
</ol>


Note:

<ul>
  <li>If available, use a smoke absorbing filter when opening the door to eliminate fumes from the solder flux.</li>
  <li>Do not remove the PCB until the board is cool enough to pick up by hand. Picking up the board too soon may mean your solder is still molten and your parts will slide off.</li>
</ul>

### Through Hole Components Soldering
<ul>
   <li>
   You will now begin hand-soldering all of the Through Hole Devices (THD).
   Start by locating the two light emitting diodes (LEDs). LEDs are polar
   components. Though it will fit in its footprint in two different
   orientations, only one will function properly.Their orientation is marked
   with a flat edge on the LED, and/or a short lead. The shorter lead closest to
   this flat edge is the Cathode, and is connected to the negative side of the
   circuit. For our purpose, you can simply match the flat edge on the LED to
   the flat line of the footprint.  
    <div>
    <img src="../leds_top.png" alt="LEDs Top" style="height:220px; display: inline-block;">
    <img src="../leds_placement.png" alt="LED Placement" style="height:220px; display: inline-block;">
    </div>
   </li>

   <li>
   Flip over the PCB. Pull the leads tight and bend them out as pictured. Solder
   the connections and clip the leads. If a bridge of solder forms between the
   two leads, use the iron to remelt and try to separate them completely.  
    <div>
    <img src="../leds_bottom.png" alt="LEDs Bottom" style="height:220px;">
    </div>
   </li>


   <li>
   Take the last remaining components the (qty3) LMC648 Op-Amps and solder them
   into the remaining footprints U1, U2 and U3. These components are polar, and
   the notch in the silkscreen on the board should be aligned with the notch on
   the chip itself. You may find these chips easier to solder on one at a time.
    <div>
    <img src="../opamp_placement.png" alt="Op-Amp Placement" style="height:220px;">
    </div>
   </li>

   <li>
   The final step in assembly you Waveform Blinky is to solder on the battery
   clip. The footprint for this is designed to create a strain relief for the
   wires. To install the wires feed them up through the bottom of the board in
   the holes closest to the edge, then feed the stripped wire down into the inner
   holes. Solder the wires and them pull then Tight.  
   Red -> +In  
   Black -> -In  
    <div>
    <img src="../battery_clip.png" alt="Battery clip" style="height:220px;">
    </div>
   </li>
</ul>

### Trouble Shooting
<ul>
    <li>Check your connections for unsoldered or bridged solder joints. The pads should be fully covered with no exposed copper.</li>
    <li>Make sure all of the polar parts are soldered on in the correct orientation.</li>
    <li>Make sure the power wires are soldered on correctly.</li>
    <li>Ensure your battery is not faulty.</li>
</ul>

## How it Works
As soon as a power supply is applied to this circuit, the Waveform blinky begins
to alternate the lighting of two LEDs. This circuit utilizes some clever analog
design tricks to do this with no programming and no computer. In this case,
there are a total of 6 operation amplifiers (Op-Amps) serving to generate a sign
wave, buffer it, and read the signal with a comparator to produce an
alternating output to activate the two lights. Op-Amps are a versatile component
used in many electronics. Simply by changing the configuration of the components
and connections around the op-amp, you can drastically alter its function.
Although there are many simpler ways to configure the LEDs to blink in this way,
this circuit serves as a demonstration of the diverse utility of op-amps, and
provides test points to aid in the study of the signal chain for educational
purposes.  
In the first stage of the blinky PCB (Function Generation), an op-amp creates a
sine wave through an old but effective circuit called an RC Phase shift
Oscillator. Popular in many fields of electronics, this chunk of the circuit
works by creating a regenerative feedback loop. It utilizes a network comprised
of resistors and capacitors to create a phase shift in the signal. This is a
type of intentional interference that creates an oscillation. The op-amp in the
loop serves to boost the signal so that it does not dissipate over time, which
in turn maintains a constant amplitude. After this sine wave is generated, it is
fed into another op-amp which is configured as a voltage follower, or buffer.
The buffer that the signal is fed into serves to take in external power and uses
it to fortify the signal. Using a buffer between a signal and its destination
ensures that the current draw on the signal cannot alter it. The other voltage
follower in this circuit serves to buffer the 4.5V coming out of the 10k voltage
divider. As voltage is simply a measure of difference in charge between two
points, the middle point of the 9V battery can be called 0V or ground, and we
can call the positive terminal of the battery 4.5VDC in reference to our virtual
ground. The negative terminal in this configuration would then become -4.5VDC.
These power rails are then used to power all the other op-amps in the circuit.
Continuing on down the signal chain, the signal is finally fed into two op-amps
which together act as a comparator. When there is no feedback loop from an
op-amps output to its input, the output fully saturates to the positive power
rail as long as the positive input is greater than the negative input. So, with
the negative input of one of our op-amps, and the positive of the other both
referenced to our virtual ground (the sine waves midpoint), we feed the signal
into the remaining inputs. As the signal rises above the midpoint, the op-amp
with the signal fed to the positive input will saturate, which will activate its
LED. As the signal dips below the midpoint, the output of the amplifier with the
signal connected to the negative terminal will turn on. This creates an
alternating blinking pattern at the frequency of the sine wave generated at the
beginning of the circuit.  

![schematic](schematic.png){: style="height:350px"}  
![layout](layout.png){: style="height:315px"}  

## Revision History
<table>

  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>

  <tr>
    <td>August 2024</td>
    <td>Initial Release</td>
  </tr>

</table>