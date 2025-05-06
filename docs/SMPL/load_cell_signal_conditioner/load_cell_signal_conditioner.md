# SMPL Load Cell Signal Conditioner
<center>
  <img src="../product.png" alt="Instrument cover photo" height="400px">
</center>

This documentation covers part number <a href="https://leemangeophysical.com/product/smpl-load-cell-signal-conditioner/" target="_blank" rel="noopener noreferrer">7-0000132/7-0000200</a>

## Overview
### Introduction 
Load cells are essential tools in laboratories and field systems, enabling
precise weight or force measurements across a wide range, from a few grams to
many tons. However, their low-level analog output, often just a few millivolts,
poses a challenge for direct use in modern data acquisition systems.

The SMPL Load Cell Signal Conditioner solves this problem by amplifying and
offsetting the load cell signal, allowing it to interface cleanly with DAQ
systems, recorders, and other electronics. With adjustable gain and DC offset,
the module makes it easy to scale the sensor output to match the full input
range of your measurement system—often ±10 V—maximizing resolution and improving
signal-to-noise ratio.

In addition to signal scaling, the board supplies clean, regulated excitation
power to the load cell, critical for maintaining accurate and stable readings.
Poor-quality excitation can introduce ripple and drift into your signal, so the
SMPL board includes a precision onboard voltage reference.

Finally, common-mode and differential-mode input filtering provisions allow you
to customize the system’s response using your RC components. Whether you're
removing noise from the power supply, adding an anti-aliasing filter, or just
smoothing out slow signals, the filtering section gives you full control. A
[free calculator](https://docs.google.com/spreadsheets/d/1DdEotpbUV5XIYL3xFno1M7-Wk8nh88F_E0GF7yTAQg0/edit?usp=sharing)
 is available to help select component values for your specific
application.
 
### What’s in the Box

When your unit arrives, unpack it and inspect all components for any shipping damage.
If anything is missing or damaged, contact Leeman Geophysical immediately for a replacement.

Included:

- SMPL Load Cell Signal Conditioner (assembled PCBA)

[Optional accessories](../accessories.md) such as cables and mounting hardware are available separately.

### Specifications
<table>
  <tr bgcolor="gray">
    <td><b>Parameter</b></td>
    <td><b>Min</b></td>
    <td><b>Typ</b></td>
    <td><b>Max</b></td>
    <td><b>Unit</b></td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>DC Input</b></td>
  </tr>

  <tr>
    <td>Voltage +</td>
    <td>12</td>
    <td>15</td>
    <td>17</td>
    <td>VDC</td>
  </tr>

   <tr>
    <td>Voltage -</td>
    <td>-12</td>
    <td>-15</td>
    <td>-17</td>
    <td>VDC</td>
   </tr>

  <tr>
    <td>Current (V+) No Transducer</td>
    <td>-</td>
    <td>20</td>
    <td>-</td>
    <td>mA</td>
  </tr>

  <tr>
    <td>Current (V-) No Transducer</td>
    <td>-</td>
    <td>17</td>
    <td>-</td>
    <td>mA</td>
  </tr>


  <tr>
    <td colspan="5" bgcolor="gray"><b>Transducer Excitation</b></td>
  </tr>

  <tr>
    <td>Voltage</td>
    <td>-</td>
    <td>5</td>
    <td>-</td>
    <td>VDC</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Physical</b></td>
  </tr>

  <tr>
    <td>Weight</td>
    <td>-</td>
    <td>26</td>
    <td>-</td>
    <td>g</td>
  </tr>

  <tr>
    <td>Width</td>
    <td>-</td>
    <td>50.8</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Length</td>
    <td>-</td>
    <td>101.6</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Height</td>
    <td>-</td>
    <td>12.7</td>
    <td>-</td>
    <td>mm</td>
  </tr>
</table>

## Connections

### SMPL Connections
The SMPL Load Cell Signal Conditioner has four SMPL 4-wire connectors:

- **A Power (x2)** – Analog power input. These two connectors are electrically identical and allow power to be daisy-chained between multiple boards.
- **Load Cell** – Input from the load cell or other strain-based sensor.
- **Output** – Amplified and offset analog signal output.

The pinout for each connector is listed in the
[SMPL Standard](../smpl_standard.md) section and is also printed on the back of
the PCB using silkscreen labels for easy reference.

### Through-Hole Solder Pad Connections
All signals are also broken out to strain-relieved through-hole pads on the
upper left-hand corner of the board. These pads allow for direct wiring without
the use of SMPL cables.

To use these:

1. Insert the wire up through the open strain relief hole from the bottom of the board.
1. Then insert the stripped end down through the corresponding solder pad.
1. Solder the connection and pull the wire gently back down through the open hole to provide strain relief.

This method protects solder joints from vibration or accidental tugs on the wire.

## Hookup Guide

1. **Ensure all power is off.**  
   ⚠️ **Do not power on the system until all setup and adjustments are complete. Powering the board too early may damage the transducer or circuit.**

2. **Connect power** to the PCB using one of the following methods:
   - Either of the two 4-pin SMPL connectors labeled **A Power**
   - Through-hole terminals: **VDC+**, **VDC-**, and **GND**

3. **Connect the load cell** using:
   - The 4-pin SMPL connector labeled **Load Cell**, or
   - Through-hole terminals: **VExc+**, **VExc-**, **IN+**, and **IN-**  
     (Note: Reversing **IN+** and **IN-** will invert the output signal polarity.)

4. **Connect the output** to your data acquisition or measurement system using:
   - The 4-pin SMPL connector labeled **Output**, or
   - Through-hole terminals: **OUT** and **GND**

5. **Continue to the [Adjustment Procedures](#adjustment-procedures)** section before applying power.

## Adjustment Procedures

The two primary parameters you’ll need to configure on the SMPL Load Cell Signal
Conditioner are **gain** and **offset**. These allow you to scale and shift the
load cell signal to match the input range of your data acquisition system.

- **Gain** controls how much the input signal is amplified.  
- **Offset** shifts the entire signal up or down by a fixed DC voltage.

These should be set during initial setup and may be fine-tuned depending on your
specific sensor and DAQ system.

### Gain Adjustment Procedure

In the default configuration, gain is controlled by a potentiometer labeled **Gain**
on the PCB. You can also configure the system for a fixed gain using resistors.

#### Variable Gain Adjustment (Default)

The default potentiometer-based gain setting allows adjustment over a typical range of
approximately **240x to 1100x**, suitable for many common load cells. If you require
a custom adjustment range, please [contact us](../../support.md) for a custom board suited to your
application.

If the circuit board was previously configured for fixed gain, you’ll need to
remove any resistors installed at R1 or R2, and re-close the two solder jumpers
near R9 to re-enable the variable gain circuit.

**Steps**:

1. Ensure the system is fully connected as described in the [Hookup Guide](#hookup-guide).
2. Power on the system and monitor the output using a multimeter or DAQ input.
3. Apply a known load to the load cell or sensor. If you have a precision millivolt source, it may be used as well.
4. Adjust the **Gain** potentiometer:
   - Turn **clockwise** to increase gain.
   - Turn **counterclockwise** to decrease gain.
5. Continue adjusting until the output voltage matches the expected value based on your known input.

The effective gain of the system can be measured across the test points labeled
**Rg** on the PCB. These test points represent the resistance controlling the
gain of the instrumentation amplifier—either set by the onboard potentiometer or
fixed resistors R1 and R2 (see
[Fixed Gain Configuration](#fixed-gain-configuration)).

🛑 **Note:** Always ensure the circuit is unpowered before measuring resistance
across the Rg test points. Measuring while powered may damage your multimeter or
produce incorrect results. The effective gain of the system can then be
calculated using the [transfer function](#transfer-function).

#### Fixed Gain Configuration

For applications requiring a more stable and known gain value (less susceptible to temperature drift),
you can disable the variable gain and set a fixed gain using resistors.

You'll need to then pick the closest standard value (E-Series) resistor to the
calculated value. Checkout our handy explanation of the E-Series resistors over
in [this blog post](https://leemangeophysical.com/why-standard-resistor-values-are-strange/).
If you do not want the gain to be any higher than the ideal gain, err on
choosing a resistor larger than the calculated value such that the gain would be
slighlty less than the calculated gain.

We recommend using 1% or better resistors with low thermal coefficients for the
best results. The resistor may be a through hole resistor and soldered into
position R2 (standing on end) or an 0603 surface mount resistor soldered to
position R1 on the circuit board. There is a silkscreen printed area to write
the applied gain value on for future reference on the front of the circuit
board.

**To disable variable gain**:

Remove solder bridges on the two jumpers adjacent to the potentiometer, near component **R9**.

<div style="text-align: center;">
  <img src="../gain_jumpers.png" alt="Remove the solder bridge jumpers near R9 to disable the variable gain potentiometer and enable fixed gain using R1 or R2. The gain resistance can still be measured across the test points labeled Rg." style="height: 250px;">
  <p><em>Remove the two solder bridge jumpers near R9 to disable variable gain. This enables the use of a fixed gain resistor at R1 or R2. The resulting gain resistance can still be measured across the test points labeled <strong>Rg</strong>.</em></p>
</div>


**To set a fixed gain**:

- Populate either of the following:
  - **R1**: 0603 surface-mount resistor
  - **R2**: Axial through-hole resistor (vertical mount)

Both positions are in parallel and serve the same purpose—use whichever is more convenient.

<div style="text-align: center;">
  <img src="../gain_fixed_positions.png" alt="Fixed gain can be set by populating the axial resistor footprint R2 or the 0603 surface mount footprint R1." style="height: 250px;">
  <p><em>Fixed gain can be set by populating the axial resistor footprint R2 or the 0603 surface mount footprint R1.</em></p>
</div>


#### Transfer Function

\[
G = 12 \times \left(1 + \frac{49400\ \Omega}{R_g}\right)
\]

Where:

- \(G\) is the voltage gain
- \(R_g\) is the total resistance between the two gain nodes

### Offset Adjustment Procedure

By default, the offset feature is disabled when you receive your board. To
enable it, move the solder jumper labeled **Offset** from the **GND (3)** pad to
the **Variable (1)** pad.

<div style="text-align: center;">
  <img src="../offset_jumper.png" alt="Offset jumper on the PCB. Bridge connections 3 and 2 for no offset. Bridge connections 2 and 1 for variable offset." style="height: 250px;">
  <p><em>Offset jumper on the PCB. Bridge connections 3 and 2 for no offset. Bridge connections 2 and 1 for variable offset.</em></p>
</div>

Once enabled, the **Offset** potentiometer allows you to apply a DC offset to the output signal:
- Turning the potentiometer **clockwise** increases the offset voltage.
- Turning it **counterclockwise** decreases the offset voltage.

> 🔧 **Tip:** Always adjust the system gain first, then apply offset. The final
> output offset is affected by the gain setting, so changing gain after offset
> may require re-adjustment.

### Setting the Offset Voltage Range

Two 3-position solder jumpers near the Offset potentiometer define the **minimum
and maximum** voltage that the potentiometer can apply.

<div style="text-align: center;">
  <img src="../offset_range.png" alt="Two 3-position jumpers set the offset range limits. The top jumper controls the minimum voltage; the bottom sets the maximum." style="height: 250px;">
  <p><em>Two 3-position jumpers near the offset potentiometer define the minimum and maximum offset voltage range. The top jumper sets the lower limit (default –1.024 V), and the bottom jumper sets the upper limit (default +1.024 V).</em></p>
</div>

#### Minimum Offset Voltage
- Set by the top jumper nearest the PCBs edge  
- Default: **–R** (–1.024 V reference voltage)  
- Optional settings:
  - **G** — 0 V (ground)
  - **–V** — Negative system supply voltage  
- ⚠️ *Recommended to leave at –R unless a larger negative offset range is required. The reference voltage is the most stable.*

#### Maximum Offset Voltage
- Set by the bottom jumper nearest the PCBs center    
- Default: **+R** (+1.024 V reference voltage)  
- Optional settings:
  - **EX** — 5 V excitation voltage to the load cell
  - **+V** — Positive system supply voltage  
- ⚠️ *Recommended to leave at +R unless your application requires a wider offset swing. The reference is again the most stable and predictable.*

These jumpers allow you to customize the offset range for your system for
maximum flexibility.


### Reversing Polarity

If the output signal from your load cell is inverted from what you expect, you
can reverse the polarity in hardware using onboard solder jumpers—no rewiring
required.

To do this, move the two solder jumpers near the **Load Cell** and **Output**
connectors to the opposite positions they are in. This swaps the signal polarity
by routing the sensor’s **+IN** to the amplifier’s **–IN** input, and vice versa,
effectively inverting the output voltage.

This feature is helpful if your system interprets tension as compression (or
vice versa), or if your load cell was wired with reversed signal polarity.

<div style="text-align: center;">
  <img src="../polarity_jumpers.png" alt="Input polarity of the transducer can be reversed by moving the solder bridges on the jumpers to the positions most inner to the centerline of the PCB." style="height: 250px;">
  <p><em>Input polarity of the transducer can be reversed by moving the solder bridges on the jumpers to the positions closest to the centerline of the PCB.</em></p>
</div>


## Using the Output Filter

The SMPL Load Cell Signal Conditioner includes an optional passive low-pass
filter on the **output** of the system, after all amplification and offset
stages. This filter helps suppress high-frequency noise and improve signal
quality, especially when long cables or sensitive digitizers are used.

The output filter consists of:
- Two series resistors
- Three capacitors

These components form both a **differential-mode** and **common-mode** RC low-pass filter.

### Default Filter Configuration

The board is shipped with the following default components installed:

- **Resistors**: 240 Ω  
- **Capacitors**: 0.1 µF  

This configuration provides:
- **Differential-mode corner frequency**: ~2.2 kHz  
- **Common-mode corner frequency**: ~6.6 kHz  

You can easily modify the filter characteristics by replacing the resistors
and/or capacitors. To do so, desolder the default components and solder in new
values based on your desired cutoff frequency.

A free calculator is available to help determine the appropriate component
values for your application:
[SMPL Filter Calculator (Google Sheets)](https://docs.google.com/spreadsheets/d/1DdEotpbUV5XIYL3xFno1M7-Wk8nh88F_E0GF7yTAQg0/edit?usp=sharing)

### Bypassing the Filter

If output filtering is not needed, if you are troubleshooting, or using your own
external filtering, the onboard filter can be bypassed. Close the **two filter
bypass jumpers** located adjacent to the filter components to short the
resistors and bypass the RC network entirely.

<div style="text-align: center;">
  <img src="../filter_bypass.png" alt="The output filter section includes two resistors and three capacitors forming common and differential low-pass filters. Two adjacent solder jumpers can bypass the filter." style="height: 250px;">
  <p><em>The output filter section includes two resistors and three capacitors forming common and differential low-pass filters. Close the adjacent solder jumpers to bypass the filter entirely.</em></p>
</div>

> **Recommendation:** For many systems, the default filter offers a good balance
> of noise reduction and signal speed. Only bypass or modify the filter if your
> application requires a different response.

## Troubleshooting

Having trouble with your signal? This section covers common issues and how to resolve them.

### No Change in Output When Load is Applied

- Check all wiring connections — Ensure power, load cell, and output cables
  are fully inserted or correctly soldered.
- Measure the Output test point relative to GND — If a signal is present here
  but not at your DAQ or meter, the issue is likely with the output wiring or the receiving device.
- Ensure the offset of the system has been set correctly or remove the offset
  feature for testing.
- Confirm the load cell is receiving excitation voltage — Measure the voltage
  between **VExc+** and **VExc–**. It should be close to 5 V.
- Check for a faulty or overloaded sensor — If possible, test your load cell
  with a known working signal conditioner or simulate its output.

### Offset Potentiometer Has No Effect

- Ensure the offset jumper is set to Variable — See [Offset Adjustment Procedure](#offset-adjustment-procedure).
- Confirm the offset range jumpers are correctly set.

### Gain Potentiometer Has No Effect

- Confirm both Rg jumpers are closed — These enable the onboard variable gain
  circuit. See [Gain Adjustment Procedure](#gain-adjustment-procedure).
- Inspect R1 and R2 for residual solder or partially installed resistors — Leftover
  fixed-gain components can interfere with the potentiometer.
- Ensure the system is powered during testing — The gain control only affects the
  output when the circuit is active.
- Power off the circuit and measure Rg — If resistance does not change when
  adjusting the potentiometer, it may be damaged or disconnected.

### General Troubleshooting Tips

- Double-check your power supply — Make sure it meets the required voltage and
  current specifications. Unstable or low supply voltage can cause erratic behavior.
- Use a known, testable load — Apply a repeatable, known weight or force to confirm
  system functionality before field use.
- Inspect for solder bridges or cold joints — This is especially important if you've
  modified jumpers, installed filtering components, or changed gain settings.
- Reset to default jumper settings — If you're unsure of the current configuration,
  return all jumpers to their documented default positions.

If you are still experiencing issues after completing these checks,
[contact support](../../support.md) for assistance.
We're happy to help troubleshoot your setup.

## Board Revisions and Compatibility

All circuit boards labeled **Revision 5.0 or later** are fully compliant with
the SMPL connector standard and follow the pinout and configuration described in
this documentation.

Earlier versions of the Load Cell Signal Conditioner board (pre-5.0) may have:
- Minor differences in SMPL connector pinout
- Different default jumper configurations
- Component value variations in filter or gain stages

If you are using a board without a visible revision label, or one marked as an
earlier revision, please [contact support](../../support.md) for assistance in
identifying and configuring your board correctly.

## Revisions
<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>

  <tr>
    <td>May 2025</td>
    <td>Update and clarify documentation</td>
  </tr>

  <tr> <td>May 2024</td> <td>Moved Documentation to MkDocs Format</td> </tr>
</table>