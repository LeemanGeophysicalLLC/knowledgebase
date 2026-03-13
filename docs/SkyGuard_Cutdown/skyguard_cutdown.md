# SkyGuard Cutdown 
<div style="text-align: center;">
   <img alt="Instrument cover photo." src="../SkyGuard_cover_photo.png" style="height:300px">
</div>

This documentation covers part number <a href="" target="_blank" rel="noopener noreferrer">10-0000201</a>

## Overview
The SkyGuard Cut Down was developed over years of experience supporting
ballooning operations for the research community. Designed with simplicity and
reliability in mind, this device offers 16 preset time and 16 preset pressure triggers to
suit a variety of mission profiles. Once the system detects a balloon launch,
the timer activates, and the pressure trigger monitors an absolute pressure
threshold for optimal cut-down timing. The system can also be armed at power up
or arm once a launch is detected by a pressure drop.

Unlike traditional hotwire systems, SkyGuard’s innovative mechanical release
eliminates the risk of fire and simplifies rigging. Arming and resetting the
device is quick and safe, taking only seconds. Housed in a durable 3D-printed
enclosure with clear acrylic front and back panels, it allows easy visibility of
status LEDs at a glance. All you need to get started is a 9-volt battery!

SkyGuard is simple to use yet highly customizable. The firmware is fully open
source, letting you modify settings if the built-in presets don't meet your
specific needs. Plus, the front panel features engraved instructions, so there’s
no need to fumble with your phone in the field—everything you need is right at
your fingertips. The enclosures files are also freely available so you can print
your own or modify it as you wish!

Swiveling rigging points at the top and bottom reduce the risk of line fouling.
DIP switch settings are quick to adjust with a pen or toothpick, even in the
field. Built-in reverse polarity protection safeguards the device, while a
supercapacitor ensures the microcontroller stays powered during servo operation.
The SkyGuard Cut Down is rugged, reusable, and field-ready. A consumables kit is
also available, so you can reuse the system time and time again with ease.
Whether you’re launching high-altitude balloons or conducting atmospheric
research, SkyGuard is the trusted solution for safe, reliable, and efficient
payload recovery.

### Front Panel
The front panel of the instrument has two LED indicators on it and two banks of dip switches.  

<ul>
   <li><b>Heartbeat</b> - Green LED indicating the device is active.</li>
   <li><b>Timer Armed</b> - Yellow LED indicating that the flight timer has been armed and is running.</li>
   <li><b>Time DIP Switches</b> - 4 switches to set the time before the balloon is released.</li>
   <li><b>Pressure DIP Switches</b> - 4 switches to set the absolute pressure at which the balloon is released.</li>
</ul>

### Back Panel
The back panel of the instrument has two solder jumpers which are used to set the arming method or other custom behaviors.

<ul>
  <li><b>A</b> - Jumper to enable arming at power up or only after launch detection.</li>
  <li><b>B</b> - Jumper for custom functions, not used in factory programming.</li>
</ul> 

### What's in the Box
Upon receipt of your unit, unpack the contents of the box and inspect all parts
for any damage incurred during shipping. Immediately report any missing parts or
damage to Leeman Geophysical for replacement. Note that there are many optional
accessories available, see the accessories section of the manual for details and
usage notes.  

<ul>
   <li>SkyGuard Cutdown Assembly</li>
   <li>Flight Consumables Kit</li>
</ul>

## Specifications
<table>
  <tr bgcolor="gray">
    <td><b>Parameter<b></td>
    <td><b>Min<b></td>
    <td><b>Typ<b></td>
    <td><b>Max<b></td>
    <td><b>Unit<b></td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Physical<b></td>
  </tr>

  <tr>
    <td>Weight (no battery)</td>
    <td>-</td>
    <td>XX</td>
    <td>-</td>
    <td>g</td>
  </tr>

  <tr>
    <td>Width</td>
    <td>-</td>
    <td>76</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Length</td>
    <td>-</td>
    <td>55</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Height</td>
    <td>-</td>
    <td>125</td>
    <td>-</td>
    <td>mm</td>
  </tr>
</table>

## System Components
### SkyGuard Cutdown
The cut down unit features a 3D-printed enclosure housing an installed servo,
release pin, bottom swivel, and a fully populated circuit board. The front and
back acrylic panels protect the electronics from the elements, secured with
thumb screws for quick and easy assembly or disassembly.

### Top Retaining Ring
This is the topmost release ring in the system. When the release pin activates,
this ring is freed. In a typical installation the balloon would be attached to this ring, but alternative rigging scenarios are possible. The bottom retaining ring cannot release until this ring has been released.

### Bottom Retaining Ring
The bottom retaining ring is an optional ring that is installed underneath the top
retaining ring. In some rigging scenarios it may be useful to release secondary lines
or perform other auxiliary functions. In typical installations, this ring is not used.

### Moisture Plug
The moisture plug fits securely into the top of the top retaining ring,
sealing the release mechanism against moisture. This protective measure helps
prevent icing or fouling, ensuring reliable operation in various weather
conditions.

## Configuration

### Arming Conditions
When the cutdown is armed the yellow LED on the front panel illuminates and the system
timer begins counting. The arming can occur as soon as the system receives power or
after a pressure drop of approximately 20 hPa is detected indicating a launch has
been detected. It is important to note that when launch detection is used the system
timer is started at 60 seconds as opposed to 0 seconds to roughly account for rise time
before arming. This allows the system to fire immediately on arming if the time condition
is set to 1 minute which may be useful for systems like payload let down reels.

The arming mode selection is accomplished with the jumper labeled “A” on the back of the
circuit board. If the jumper is soldered closed the system will use the launch detection
method. If the jumper is desoldered or left open then the system will arm immediately on
power up. Systems are shipped to arm at power on by default.

### Timed Cutdown
If a time threshold is set, the system starts a countdown timer once it’s armed.
The release is triggered when the preset elapsed time is reached. 

The cutdown time is set by the DIP switches labeled "Time".
The times from arming to release are set as shown in the following table.

| Switch 1 | Switch 2 | Switch 3 | Switch 4 | Time (minutes) |
|----------|----------|----------|----------|----------------|
| OFF      | OFF      | OFF      | OFF      | Timer Disabled |
| ON       | OFF      | OFF      | OFF      | 1              |
| OFF      | ON       | OFF      | OFF      | 2              |
| ON       | ON       | OFF      | OFF      | 5              |
| OFF      | OFF      | ON       | OFF      | 10             |
| ON       | OFF      | ON       | OFF      | 20             |
| OFF      | ON       | ON       | OFF      | 30             |
| ON       | ON       | ON       | OFF      | 40             |
| OFF      | OFF      | OFF      | ON       | 50             |
| ON       | OFF      | OFF      | ON       | 60             |
| OFF      | ON       | OFF      | ON       | 70             |
| ON       | ON       | OFF      | ON       | 80             |
| OFF      | OFF      | ON       | ON       | 90             |
| ON       | OFF      | ON       | ON       | 100            |
| OFF      | ON       | ON       | ON       | 110            |
| ON       | ON       | ON       | ON       | 120            |

### Pressure Cutdown
Pressure cutdown is performed based on the <b>absolute pressure</b> at the
instrument. Once the pressure is below the set point which has been selected
with the 4 DIP switches labeled "Pressure" the release will be actuated. Since
there is no way to know altitude information to determine sea level pressure the
absolute pressure is used always.

| Switch 1 | Switch 2 | Switch 3 | Switch 4 | Pressure (hPa)    |
|----------|----------|----------|----------|-------------------|
| OFF      | OFF      | OFF      | OFF      | Pressure Disabled |
| ON       | OFF      | OFF      | OFF      | 10                |
| OFF      | ON       | OFF      | OFF      | 100               |
| ON       | ON       | OFF      | OFF      | 150               |
| OFF      | OFF      | ON       | OFF      | 200               |
| ON       | OFF      | ON       | OFF      | 250               |
| OFF      | ON       | ON       | OFF      | 300               |
| ON       | ON       | ON       | OFF      | 350               |
| OFF      | OFF      | OFF      | ON       | 400               |
| ON       | OFF      | OFF      | ON       | 450               |
| OFF      | ON       | OFF      | ON       | 500               |
| ON       | ON       | OFF      | ON       | 600               |
| OFF      | OFF      | ON       | ON       | 700               |
| ON       | OFF      | ON       | ON       | 800               |
| OFF      | ON       | ON       | ON       | 900               |
| ON       | ON       | ON       | ON       | 1000              |

## Operation

### Before Going to the Field
Before going to the field for your launch we recommend accomplishing as much as possible back in the lab. Rigging may also be able to be accomplished before going to the field depending upon your exact requirements. Note that you can manually turn the servo with your fingers to release/attach the top/bottom retainers which may make rigging easier.

<ol>
   <li>Remove the thumb screws and front/back panels from the housing.</li>
   <li>Using a small pointed object like a toothpick or pen, set the desired time and/or pressure on the DIP switches following the tables in the configuration section and engraved on the panels. Note that both time and pressure conditions may be set, and whichever is reached first will trigger a release.</li>
   <li>Verify that the arming mode is set as you wish with the “A” jumper on the back of the circuit board.</li>
   <li>Reattach the front cover over the dip switches with the thumb nuts. There are small O-rings installed on the threads of the nylon screws to help prevent them from vibrating loose during turbulent flights. <b>DO NOT over-tighten the thumb screws!</b> They are nylon and just need to be finger tight or they could be twisted off in the brass threaded inserts of the case.</li>
</ol>

### Rigging
While rigging of your cutdown likely depends on your exact balloon train design,
this is the recommended starting point for the development of your procedure.

<ol>
  <li>Attach the balloon lift line to the top retaining ring using a robust line such as high test fishing line (monofilament or other).</li>
  <li>Pass the free end of the ballon lift line through the hole in the top of the parachute. Be sure the hole is large enough for the top retaining ring (and bottom if used in your configuration) to pass through it.</li>
  <li>Attach the load lift lines to to the bottom swivel using a similar robust line to the line used for the ballon lift lines.</li>
</ol>

### Launch
Launching procedures should be adjusted to your system’s needs, but as a general guide this procedure may be used as a starting point for yours.

<ol>
  <li>Install a 9V battery (lithium 9V batteries are recommended for best performance at high altitudes) into the back of the unit and reattach the cover with the thumb screws being very careful not to over-tighten them. The O-rings should be present on each thumb screws to reduce the chance of them coming loose during flight.</li>
  <li>Ensure that the green light is blinking and the servo moves approximately 45 degrees during its power on check and then back to its home position. If your cutdown is set to immediately arm the yellow LED should illuminate.</li>
  <li>Launch your balloon and payload as you normally would</li>
 </ol>

### Recovery
If your payload is to be recovered you may wish to recover the cutdown for reuse. Once the
payload is located the cutdown can simply be cut out of the rigging and saved for later use.
We do recommend removing the battery to avoid any potential leakage damaging the cutdown during long term storage. This does not need to be done immediately in the field as it may
be easy to lose screws or parts of the unit, but should be done before putting the
equipment away.

### Reuse
Refurbishing of the unit to fly again is a simple process, largely just comprised of
verifying that nothing was damaged in the last flight. You will need a new flight
consumables kit to replace the parts of the release that flew away with the balloon
and rigging, but other than those and the battery no other parts need to be changed.
If any parts of the system are damaged (release pin bent, windows cracked, etc.) new
parts can be purchased from us by contacting support TODO LINK THIS or you can produce
parts using the freely available files in the SkyGuard Mechanical Repository. TODO LINK THIS

We recommend attaching a battery and verifying proper operation of the servo and
electronics before re-flying the unit.


## Serial Connection
There is a header on the PCB for serial connection at 9600 Baud. With the stock
firmware, system status information is printed to the serial terminal as a table
as shown below:

TODO ADD

To connect to the serial output, connect a 3V3 logic cable TODO ADD STORE LINK to the PCBs ground,
transmit, and receive pins as shown below:

If you are unfamiliar with serial terminal operations, be sure to check out our
guide in [Application Note 0005: Establishing Serial Communication with Instruments Using a Terminal Program](https://docs.leemangeophysical.com/appnotes/AN0005/).

## Customizing the Firmware
The firmware for the cutdown in open-source and available on the GitHub
repository. It is stated in the license, but emphasized that the software is
provided as-is and to be used/modified at your own risk! We have installed the
Arduino bootloader on the cutdown and have it set up as a 3.3V 8MHz Pro-Mini. We
recommend using [VSCode](https://code.visualstudio.com/) with the
[PlatformIO](https://platformio.org/) extension to edit and upload the firmware.
You will need a 3V3 USB cable to accomplish the programming or to read out
serial outputs.

TODO - verify - do we actually ship a boot loader?

### Upload Procedure
<ol>
   <li>Connect the serial cable as described in the Serial Connection section.</li>
   <li>Using a jumper, connect the Reset pin to ground to hold the processor in reset.</li>
   <li>Open PlatformIO in VSCode and click the "Upload" button (arrow) at the bottom of the screen.</li>
   <li>Remove the jumper from the reset pin when you see "Uploading" appear in the terminal.</li>
</ol>

## Enclosure and Hardware
The SkyGuard Cutdown enclosure is designed using Autodesk Fusion 360, and the
design files are freely available in the mechanical GitHub repository for those
who wish to explore or modify the mechanical components. The repository includes
the Autodesk Fusion 360 project file as well as 3D-printable STL files, allowing
users to fabricate their own parts if needed. The circuit board and servo are
securely mounted within the enclosure using plastic self-threading high-low
screws. 

Key components, such as the machined swivel and release rings, are available as
replacement parts. To purchase replacements, please contact our support team or
purchase the commonly used parts on our website.

The bottom swivel may need to be removed when replacing the enclosure. To remove
the swivel, use an external snap ring tool to detach the snap ring securing it.
It is strongly recommended to first remove the circuit board to prevent
clearance issues that could potentially damage its components during the
process. 

## Accessories
If you will be recovering your SkyGuard for multiple uses, we have accessories
that you may be interested in keeping on-hand.

TODO put the real links here

### Flight Consumables Kit 
<a href="" target="_blank" rel="noopener noreferrer">10-0000202</a>  
Extra hardware to replace that used during a flight. Includes a top and bottom
release ring and water plug.

### SkyGuard Cutdown Housing 
<a href="" target="_blank" rel="noopener noreferrer">10-XXXXXXX</a>   
After a number of flights your housing may get damaged from landing on hard
surfaces. This kit includes an empty housing and front/back panels with elastic
bands to let you renew your cutdown for many more flights.

### 3V3 Serial Cable
<a href="" target="_blank" rel="noopener noreferrer">10-XXXXXXX</a>   
Program new firmware to the cutdown or just monitor the serial output for testing.

## Revision History
<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>
  
  <tr>
    <td>March 2026</td>
    <td>Update for PCB revision and new operational recommendations</td>
  </tr> 

  <tr>
    <td>November 2024</td>
    <td>Initial Release</td>
  </tr> 
</table>