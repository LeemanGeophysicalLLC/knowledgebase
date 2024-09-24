<center>
![Instrument cover photo.](product.png){: style="height:300px"}
</center>

This documentation covers part number <a
href="https://leemangeophysical.com/product/drivecommand-dac/"
target="_blank" rel="noopener noreferrer">10-0000196</a>.

## Overview
The DriveCommand DAC system is a control signal generator designed to generate
precise ramp and saw commands for a servo control systems. Common applications
include creating load and displacement ramps in servo hydraulic control for
materials testing, creating test signals for equipment verification, and more.
This 16-bit digital to analog converter has been specifically designed to allow
users to provide rates in engineering units with two preset calibrations
(kN/second or mm/second for example). The unit may be completely controlled from
front panel physical controls or over a USB serial connection. This addition to
the drive command ecosystem makes machine control easy and allows on the fly
adjustment of controlled variables as experimental or production conditions
evolve.

### What's in the box
Upon receipt of your unit, unpack the contents of the box and inspect all parts
for any damage incurred during shipping. Immediately report any missing parts or
damage to Leeman Geophysical for replacement.  

* DriveCommand DAC System
* Universal DC Power Supply
* USB A-B cable
* BNC to banana jack adapter
* 1 ft BNC cable

## Controls and Indicators

### Front Panel
<center>
![Labeled Front Panel](FrontPanel.png){: style="height:220px"}
</center>

**LCD Screen** - A 4x20 character LCD with backlight shows the current rate of
change, calibration in use, limits, and signal type. The screen is also used for
setting parameters of the device.

**Encoder Knob** - A rotary encoder with push button switch is used to change
settings via the on-screen menu or adjust rate on the fly (if enabled).

**Zero** - Push button to reset the output of the DAC to the minimum value.

**Run/Stop Switch and Indicators** - Sets if the output is stopped (no value
change regardless of ramp rate setting) or running, changing at the prescribed
rate. Switch returns to neutral position after activation and LEDs indicate the
state of the system.

**Up/Down Switch and Indicators** - Indicates if the ramp will be in the up or
down direction. The sign can be inverted in the device settings. Switch returns
to neutral position after activation and LEDs indicate the state of the system.

**X10/X0.1 Switch** - Order of magnitude switch to increase or decreases the
current rate of output change by a factor of 10. Switch returns to neutral
position after activation.

**Upper Limit Indicator** - Illuminates when the output of the device has
reached the upper voltage limit set.

**Lower Limit Indicator** - Illuminates when the output of the device has
reached the lower voltage limit set. 

**Output BNC connector** - Buffered output of the DAC may be used by any
connected equipment or as a monitoring output for the voltage output.

**Voltmeter** - Shows a numerical and graphical representation of the output
voltage of the device. The range of the meter maybe set with dip switches on
the back as described in setting range section.

### Back Panel
<center>
![Labeled Back Panel](BackPanel.png){: style="height:220px"}
</center>

**Fuse** - 1.5 amp fast acting fuse protects the device from overcurrent.

**DC Input Jack** - Standard DC input with the center positive provides power to the unit from the included 12 volt DC power supply.

**USB** - USB type B connector is provided to modify settings or control the device from a computer.

**Output BNC connector** - Buffered output of the DAC may be used by any
connected equipment or as a monitoring output for the voltage output.

## Specifications
* Output Range: ±10 volts DC or ±5 volts DC
* Output Drive: Loads up to 50 mA
* Ramp Rate: User selectable
* Control: Panel or Serial

## Assembly
The DriveCommand DAC system arrives pre-assembled and configured for operation
in the +/- 5VDC output range. Once your unit is unpacked, simply click the
appropriate wall plug adapter onto the 12 VDC power supply and the unit is ready
for configuration and installation.

## Configuration
From the factory the DriveCommand DAC has sensible defaults, but you will likely
need to customize the system to fit your application. There are many settings to
help better match the unit to your control system. We recommend setting these
parameters and testing the DAC to ensure proper operation BEFORE connecting it
to external hardware and attempting to control actuators. 

If you are unsure of what settings should be used, contact the manufacturer of
the controlled hardware and/or our support team. Most importantly always ensure
there is a safe way to rapidly disable the controlled equipment during testing.

### Setting the Output Range
The DAC has two output ranges, ±10 volts DC or ±5 volts DC. These full scale
output (FSO) ranges match the control signal ranges most commonly found in
associated servo control equipment. Range switching is internally accomplished
with a relay switching between gain settings on an amplifier that is connected
to the output of the digital to analog converter. **When the range setting is
changed the unit must be calibrated and the voltmeter configuration switches
reset.** Changing the range is one of the few settings that can only be altered
via the serial connection and not through menu options. The setting is persistent
and will survive power cycles.

Using the correct setting provides the most resolute output possible for your
system. The ±10 volts DC has a theoretical resolution of 0.3 mV/bit
and the ±5 volts DC a theoretical resolution of 0.15 mV/bit.

1. Using a serial terminal program (see application note) connect to the device
   at either the default (115200) or a custom baud rate that you have set.

1. Issue the command *SETRANGE X* with *X* replaced by either 10 or 5 for the
   ±10 volts DC or ±5 volts DC range respectively.

1. Power down the unit and follow the "Changing the Voltmeter Configuration"
   instruction.

1. Once complete, recalibrate the output of the unit by following the
   "Calibrating the Output" instruction.

### Changing the Voltmeter Configuration
The front panel voltmeter provides a quick visual indication of where in the
output range the current value is via the numerical display and the graphic
bar chart in an arc across the top of the meter face. The range of the meter
should be set to match the range of the output of the DAC for best and most
intuitive performance.

1. Remove power from the unit.

1. Using a #1 phillips screwdriver, remove the 11 screws holding the top case
   onto the unit. Remove the top case.
  <center>
  ![Labeled Screw Positions](TopPanelScrews.png){: style="height:250px"}
  </center>

1. Using a small object like a toothpick, change the dip switches on the back
   of the voltmeter to match the table below.
  <center>
  ![Voltmeter switches](MeterSwitches.png){: style="height:250px"}
  </center>

1. Reassemble the unit.

1. Apply power and test.

<table>
  <tr bgcolor="gray">
    <td>Range</td>
    <td>SW1</td>
    <td>SW2</td>
    <td>SW3</td>
    <td>SW4</td>
    <td>SW5</td>
  </tr>

  <tr>
    <td>±10 volts DC</td>
    <td>ON</td>
    <td>ON</td>
    <td>OFF</td>
    <td>ON</td>
    <td>OFF</td>
  </tr>

  <tr>
    <td>±5 volts DC</td>
    <td>ON</td>
    <td>ON</td>
    <td>OFF</td>
    <td>OFF</td>
    <td>OFF</td>
  </tr>
</table>

### Calibrating the Output
After the range setting has been changed, the DriveCommand DAC must be re-calibrated.
The calibration can also be done at any time as part of a regular calibration program
or when the output is in question. Calibration requires a high resolution voltmeter,
a BNC wire or BNC-banana jack adapter, and a serial connection to the instrument.
  <center>
  ![Calibration Setup](Calibration.png){: style="height:350px"}
  </center>

1. Using a serial terminal program (see application note) connect to the device
   at either the default (115200) or a custom baud rate that you have set.

1. Connect a precision voltmeter to one of the BNC connectors using either a stripped
   BNC wire or a banana jack adapter. We recommend a 6 1/2 digit meter for calibration,
   but at a minimum the meter needs millivolt resolution at the minimum and maximum
   output values of the DAC.

1. Let the unit warm up. We recommend about 15 minutes at operating ambient conditions
   to stabilize. If the unit just experience a large temperature change like coming in
   from outdoors, ensure it has reached equilibrium with the operating environment.

1. Issue the command *RUNCAL*. The instrument will indicate that it is now outputting
   a voltage corresponding to 0 bits on the DAC. Record this voltage in a notebook or
   spreadsheet.

1. Press return and the instrument will go to the next calibration value of 16383 bits.
   Record the voltage output.
   
1. Continue the process for 32767, 49150, and 65535 bits output.

1. Plot a graph of bits (y-axis) vs volts (x-axis) and fit a line to the data. The data
   should be a very close fit. NOTE: We have provided a Google Sheet that you may copy
   and use for performing the fit.

1. Issue the *SETDACCAL XX.XXX XX.XXX* command with the first set of *X* being replaced
   by the slope of the best fit line and the second the intercept. We recommend setting
   these to 3 decimal places.

1. Use the *SETOUT XX.XXX* command to set the output to voltages at the end members and
   center of the range. A good calibration should produce outputs within 1 mV of the
   desired set point easily. (We like using a pattern like 9.8765 volts so it is easy to
   recognize.)

### Inverting the Output
There is no standard for sign of voltage with respect to "up" and "down" in a
control system. You may find that the output sign of the DAC does not match
that which makes the most sense for your attached equipment. In this case you
may elect to invert the polarity of the output signal. This does not affect the
limits, rate, calibration, or any other setting.

Inverting the output may be done via the serial command interface or via the
menu. See the relevant section of the manual on menu operation or serial
commands for further instruction. In the uninverted state, "up" corresponds to a
positive voltage change and "down" corresponds to a negative voltage change. In
the inverted state the opposite is true. 

## Installation

### Mechanical Installation
The DriveCommand DAC fits in standard 19 inch rack mount slots and is 2U tall.
Use the appropriate rack mounting hardware for your rack style. The unit can be
mounted in 2 or 4 post racks, but only utilizes the front mounting holes.

### Driver Installation
For serial communication with the DriveCommand DAC you will need to ensure that
the FTDI Virtual COM Port (VCP) drivers have been installed on the computer
before connecting the USB port. The drivers may be found at
[https://ftdichip.com/drivers/vcp-drivers/](https://ftdichip.com/drivers/vcp-drivers/)
and installed at no cost. Drivers are available for Windows, Mac, and Linux
systems.

To communicate with the DAC you will need to either use a serial terminal
program or use serial communications packages in your preferred programming
language such as C, Python, LabView, etc. For more information on using a serial
terminal program please see our application note on serial communications.

## Operation

### Entering a Calibration
The DriveCommand DAC stores two calibrations to allow conversion from
engineering units to a voltage output. These are useful if your connected
equipment has multiple feedback sources with transducers which have different
calibrations. A common example is a servo hydraulic system which has load and
displacement feedback. Calibration A may be set to represent the calibration of
the load cell and calibration B the calibration of a displacement transducer.
This allows for quick switching between generating command signals relevant to each
of those respective feedbacks.

Calibrations may be set via the menu interface or via the serial interface. See
the relevant sections of the manual for further instructions on menu and serial
use. Calibrations are a persistent setting, meaning that they do survive power
cycles and are stored in semi-permanent EEPROM memory.

Calibrations of the transducers and associated signal processing equipment must
be done external to this system.Choosing the engineering unit wisely can help
make entering rates a more pleasant experience. For example, if most rates are
going to be displacement in microns per second entering the calibration in volt
per micron is most likely the easiest choice. Millimeters would work as well,
but would involve more places after the decimal and make the unity change of the
encoder knob (if enabled) on the front less useful. 

### Selecting a Calibration
The DriveCommand DAC will default to using calibration A on power up each power
cycle. Calibration B may be selected at any time via the onboard menu interface
or via a serial command. Calibration use changes take effect immediately. 

### Creating a Ramp Output
To create a ramp output, which will monotonically increase or decrease voltage
until a limit is reached, first set the desired rate see "Changing Rate". Next,
ensure that the ramp mode is enabled. This is indicated in the lower left corner
of the main screen or via the *STATUS* serial command. Ramp mode maybe selected
via the onboard menu or serial command interface. Once the desired direction, up
or down, has been selected via serial command or front panel switches, the ramp can be
started with either the *RUN* command or front panel switch.

The voltage will ramp at the set rate in engineering units per volt using the
provided calibration. Once the voltage output reaches the upper or lower limit,
the unit will enter stop mode and the output value will hold at its current
value.

### Creating a Saw Output
To create a saw output which will monotonically increase or decrease voltage
until a limit is reached, then reverse direction and continue to monotonically
increase or decrease, the procedure is much the same as creating a ramp. The
only exception is that saw mode should be selected via the menu interface or
serial command interface. Saw output will continue indefinitely and is commonly
used in cyclic testing, system verification, or in slow dynamics investigations.

### Setting Limits
The limits of the system are set in units of voltage, not engineering units.
This is because the absolute position, load, or other physical value of the
attached equipment is generally not known. The limits may be set via the menu
interface or serial command interface. 

The lower limit must always be lower than the upper limit but can be negative or
positive in sign. The upper limit must always be above the lower limit but can
also be negative or positive in sign. In ramp mode when a limit is reached the
unit will stop changing its output. In Saw mode when a limit is reached the unit
will reverse direction and continue the cycle. 

### Zeroing the Output
Zeroing the output of the DAC is commonly done when an output waveform is
complete and we desire to reset the apparatus, or a transducer has been
physically re-zeroed and the output of the system needs to be zeroed as well.
Zeroing can be accomplished via the front panel or the serial command
interface. In all cases you should be sure that the connected equipment is in
a safe state for the control voltage to experience a rapid change.

To zero the DAC via the front panel, simply press the zero push button. This
is a momentary contact push button which will instantaneously set the output to
the minimum output for the current range setting.

To zero the DAC via the serial command interface, issue the *ZERO* command. If you do
not wish to zero the output all the way to the minimum value for the range
setting, you can issue the *SETOUT* command to set the output
instantaneously to any desired value. 

It is important to note that the zero function sets the output to the lowest output
for the current range, ignoring the voltage limits. This means the output will be set
to -5 VDC or -10 VDC respectively.


### Changing Rate
The output rate is set in engineering units per second and uses either
calibration A or calibration B as selected by the user to convert engineering
units to volts for the output rate. The output rate may be changed via the front
panel encoder knob, menu setting, by sitting via the serial connection, or
using the order of magnitude switch.

To change the output rate via the front panel knob the rate knob enable must
be set. This can be done via the menu or the serial command interface. Once
this is enabled, the encoder on the front panel will increase or decrease the
output rate in increments of unity.

For a more fine-grained control, the menu interface with the encoder may be used
to set the output rate to any desired value. This is a relatively quick process
to do and takes effect as soon as the setting is saved from the menu interface.
See "Using the Menu" for more details on the menu operation.

The rate can also be set via serial command as described in the serial commands
section. For many rates or schedules of different rates, this is the recommended
option.

Finally, the rate can be changed by an order of magnitude using the order of
magnitude switch on the front panel. This is especially useful in materials
testing fields where rates of deformation are commonly stepped by an order of
magnitude to determine frictional properties of solids. 


### Using the Menu
Most settings on the DriveCommand DAC can be changed with the front panel menu
using the LCD screen and encoder as well as via the serial commands from a
computer. To use the on-screen menu you long press and hold the encoder button
until the menu appears. The scroll through the settings short press the encoder
button. To change the setting that is currently showing on screen press and
hold. Once you are satisfied with the setting long press the encoder button to
save the setting.

If the setting is numeric, it is set one digit at a time by rotating the encoder
knob to change the numeral and short pressing to go to the next digit. Once the
end is reached, the cursor will wrap back to the beginning. Long press the
encoder button to save the set value. If the numeric value is signed, the first
field will be a +/- sign changed by rotating the encoder knob. Only valid
settings will be saved. Invalid settings will revert back to the last valid
setting.

The menu settings and cycle are as follows:

* Main Screen
* Rate - Set the unsigned numeric value of the rate of change in engineering units/second
* Mode - Set the output mode to RAMP or SAW
* Upper Limit - Set the signed numeric value of the upper output limit in volts
* Lower Limit - Set the signed numeric value of the lower output limit in volts
* Use Calibration - Set if calibration A or B is used to convert engineering units/second to volts/second
* Calibration A - Set the unsigned numeric value of calibration A in volts/engineering unit
* Calibration B - Set the unsigned numeric value of calibration B in volts/engineering unit
* Invert Output - Inverts the sign of the output voltage to match the sign convention of any attached equipment
* Rate Knob Enable - Enables or disables the encoder knob to change the output rate in steps of 1 engineering unit/second

### Serial Commands
The serial menu operates at the user-set baud rate. Each command should be
entered followed by a newline character.

<table>
  <tr bgcolor="gray">
    <td>Command</td>
    <td>Description</td>
  </tr>

  <tr>
    <td>DEF</td>
    <td>Restores the device settings to the default. The DAC calibration
    slope/intercept and serial number are not reset.</td>
  </tr>

  <tr>
    <td>HELP</td>
    <td>Show an onboard help menu containing the serial commands and
    their basic description.</td>
  </tr>

  <tr>
    <td>INVOUT X</td>
    <td>When set to 1 the direction of the output is inverted. The increase
    or up setting will result in a decrease in the output voltage. Setting to
    0 returns the operation to a non-inverted state.</td>
  </tr>

  <tr>
    <td>RTKB X</td>
    <td>Setting to 1 enables the output rate of the device to be stepped in increments
    of 1 using the encoder on the front panel. Setting to 0 disables the encoder rate
    stepping to avoid accidental adjustment.</td>
  </tr>

  <tr>
    <td>RUN</td>
    <td>Starts the device changing its output voltage at the rate prescribed.
    This is identical to selecting run mode with the front panel switch</td>
  </tr>

  <tr>
    <td>RUNCAL</td>
    <td>Performs a calibration of the DAC by setting to output to predefined values.
    See calibration procedure.</td>
  </tr>

  <tr>
    <td>SETBAUD XX</td>
    <td>Sets the baud rate to 1200, 2400, 4800, 9600, 19200, 38400, 57600, or 115200 baud.
    Changes take effect immediately.</td>
  </tr>

  <tr>
    <td>SETCAL X XX.XX</td>
    <td>Set the calibration A or B (the first X) in volts per unit.</td>
  </tr>

  <tr>
    <td>SETDACCAL XX.XX XX.XX</td>
    <td>Set the slope and intercept coefficients for the DAC calibration in numbers of
    bits per volt and bits offset. See calibration procedure.</td>
  </tr>

  <tr>
    <td>SETDIR X</td>
    <td>Set the direction of output to up (UP) or down (DN). This is identical to actuating
    the front panel switch.</td>
  </tr>

  <tr>
    <td>SETLLIM XX.XX</td>
    <td>Set the lower limit in volts. The lower limit must be below the upper limit
    and within the selected output range.</td>
  </tr>

  <tr>
    <td>SETMODE X</td>
    <td>Set the waveform mode to RAMP or SAW. Ramp monotonically increases or decreases 
    the output voltage at the given rate until a limit is reached and then the output
    change is stopped. SAW continuously inverts the direction of the ramping upon
    reaching a limit.</td>
  </tr>

  <tr>
    <td>SETOUT XX.XXX</td>
    <td>Manually set the output to a given voltage value.</td>
  </tr>

  <tr>
    <td>SETRANGE XX</td>
    <td>Set the output range of the device to be ±10 volts DC or ±5 volts DC.</td>
  </tr>

  <tr>
    <td>SETULIM XX.XX</td>
    <td>Set the upper limit in volts. The upper limit must be above the lower limit
    and within the selected output range.</td>
  </tr>

  <tr>
    <td>SHOW</td>
    <td>Display the current system configuration in the serial terminal window.</td>
  </tr>

  <tr>
    <td>STATUS</td>
    <td>Show the current instrument status. This command may be used to programmatically
    interrogate the device for remote control. Returns a comma delimited string of unit
    state (RUN/STOP), direction (UP/DOWN), waveform (RAMP/SAW), ramp rate, at upper limit
    (0/1), and at lower limit (0/1).</td>
  </tr>

  <tr>
    <td>STOP</td>
    <td>Stop the change of the output of the device at the current value.</td>
  </tr>

  <tr>
    <td>USECAL X</td>
    <td>Select if calibration A or calibration B should be used when
    determining the output rate of change.</td>
  </tr>

  <tr>
    <td>ZERO</td>
    <td>Return the output of the system to the minimum DAC output value.
    This is identical to actuating the front panel button.</td>
  </tr>
</table>

## Maintenance
The DriveCommand DAC requires no regular maintenance to provide years of
reliable operation. If your organization requires regular calibration of
instruments, we recommend calibrating the system bi-annually for the first year
of ownership and annually afterwards assuming satisfactory drift in the first
calibrations. Calibration is also required after the range setting is changed or
the unit is moved to dramatically different ambient operating conditions.

## Troubleshooting
Below are common issues encountered in operation of the DriveCommand DAC and
their solutions. If you need assistance with a problem, please contact our
support team.

### Unit Does Not Power On
* Check that the units power supply is plugged into a live wall socket.
* Verify that the international plug adapter of choice is firmly seated onto the
  AC-DC power adapter.
* Check that the power supply connector is firmly inserted into the DC power
  port on the back of the unit.
* Check if the 1.5A fast acting fuse is blown and replace if necessary.

### Encoder Does Not Change Rate
* Encoder rate functionality has been disabled, use the menu or serial commands
  to re-enable it.

### Output Voltage is Incorrect
* Verify that the correct range is set using the serial interface.
* Calibrate the unit.
* Disconnect any connected equipment and see if problem persists. If not, the
  connected equipment has too high of a current demand and the output of the DAC
  needs buffering before the equipment.

### Voltmeter Range is Incorrect
* Set the voltmeter range using dip switches on the back following the
  configuration table.

### Voltmeter is Flashing
* Flashing indicates that the voltage is out of the set range. It is possible
when at the extreme values for flashing to occur.
* Voltmeter range may be set incorrectly. Set the voltmeter range using dip
  switches on the back following the configuration table.
* Unit may be out of calibration - recalibrate the DAC.
