# SkyGuard Cutdown
<center>
![Instrument cover photo.](product.png){: style="height:300px"}
</center>

This documentation covers part number <a href="" target="_blank" rel="noopener noreferrer">10-0000201</a>

## Overview
The SkyGuard Cut Down was developed over years of experience supporting
ballooning operations for the research community. Designed with simplicity and
reliability in mind, this device offers 16 preset time and pressure triggers to
suit a variety of mission profiles. Once the system detects a balloon launch,
the timer activates, and the pressure trigger monitors an absolute pressure
threshold for optimal cut-down timing.

Unlike traditional hotwire systems, SkyGuard’s innovative mechanical release
eliminates the risk of fire and simplifies rigging. Arming and resetting the
device is quick and safe, taking only seconds. Housed in a durable 3D-printed
enclosure with clear acrylic front and back panels, it allows easy visibility of
status LEDs at a glance. All you need to get started is a 9-volt battery!

SkyGuard is simple to use yet highly customizable. The firmware is fully open
source, letting you modify settings if the built-in presets don't meet your
specific needs. Plus, the front panel features engraved instructions, so there’s
no need to fumble with your phone in the field—everything you need is right at
your fingertips.

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

* **Heartbeat** - Green LED indicating the device is active.  

* **Timer Armed** - Yellow LED indicating that the flight timer has been armed and is running.

* **Time DIP Switches** - 4 switches to set the time before the balloon is released.

* **Pressure DIP Switches** - 4 switches to set the absolute pressure at which the balloon is released.

### What's in the Box
Upon receipt of your unit, unpack the contents of the box and inspect all parts
for any damage incurred during shipping. Immediately report any missing parts or
damage to Leeman Geophysical for replacement. Note that there are many optional
accessories available, see the accessories section of the manual for details and
usage notes.  

* SkyGuard Cutdown Assembly
* Flight Consumables Kit

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
    <td>Weight</td>
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
elastic bands for quick and easy assembly or disassembly.

### Parachute Retaining Ring
This is the topmost release ring in the system. When the release pin activates,
the parachute retaining ring is freed, allowing the balloon retaining ring to
release as well. This process ensures the rigging line drops cleanly, allowing
the cut down to fall below the parachute and avoid interfering with its
deployment.

### Balloon Retaining Ring
The balloon retaining ring supports the load of the balloon, transferring it
through the cut down unit to the payload. This ring serves as the primary
attachment point for the balloon and facilitates the lifting of the parachute
retaining ring when the release mechanism is triggered.

### Moisture Plug
The moisture plug fits securely into the top of the parachute retaining ring,
sealing the release mechanism against moisture. This protective measure helps
prevent icing or fouling, ensuring reliable operation in various weather
conditions.

## Configuration
### Timed Cutdown
If a time threshold is set, the system starts a countdown timer once it’s armed.
The release is triggered when the preset elapsed time is reached. By default,
the timer activates only after the system detects a pressure drop of 20 hPa
below the starting pressure recorded at power-on—equivalent to approximately 550
feet above the initial altitude. This ensures the cutdown can be powered on
during pre-launch preparations without starting the timer prematurely. Once the
system is armed and in flight, the yellow "Timer Armed" LED on the circuit board
will illuminate to confirm activation.

The cutdown time is set by the DIP switches labeled "Time" right below to servo.
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
Pressure cutdown is performed based on the **absolute pressure** at the
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
1. Remove the elastic bands and front/back panels from the housing.
1. Using a small pointed object like a toothpick or pen set the desired time
   and/or pressure on the DIP switches following the tables in the configuration
   section. Note that both time and pressure conditions may be set and whichever
   is reached first will trigger a release.
1. Connect the device to the balloon train following the recommendations in the
   rigging section of the manual or your SOPs.
1. Install a 9V battery onto the battery clip. For best performance in the cold
   flight environment we recommend a high performance lithium 9V. The green and
   yellow LEDS on the front will alternate to indicate the system is
   initializing. The servo will also move approximately 20 degrees then back to
   the home position.
1. Reinstall the front and back covers with the elastic bands
1. The cutdown is ready for flight as long as the green led is flashing.

## Rigging
While rigging of your cutdown likely depends on your exact balloon train design,
this is the recommended starting point for the procedure.

1. Tie the parachute retaining line to the parachute retaining ring and place it
   over the release pin.
1. Tie the balloon line to the balloon retaining ring and install it onto the
   release pin by pressing the blue button inside the cutdown.
1. Tie off the bottom payload line to the payload swivel on the bottom of the
   cutdown.

## Serial Connection
There is a header on the PCB for serial connection at 9600 Baud. With the stock
firmware, system status information is printed to the serial terminal as a table
as shown below:

To connect to the serial output, connect a 3V3 logic cable to the PCBs ground,
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

### Upload Procedure
1. Connect the serial cable as described in the Serial Connection section.
2. Using a jumper, connect the Reset pin to ground to hold the processor in
   reset.
3. Open PlatformIO in VSCode and click the "Upload" button (arrow) at the bottom
   of the screen.
4. Remove the jumper from the reset pin when you see "Uploading" appear in the
   terminal.

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

### Flight Consumables Kit 
<a href="" target="_blank" rel="noopener noreferrer">10-XXXXXXX</a>  
Extra hardware to replace that used duringa flight. Includes a top and bottom
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
    <td>November 2024</td>
    <td>Initial Release</td>
  </tr> 
</table>