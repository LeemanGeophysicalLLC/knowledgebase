# Tilt Meter Logger
<center>
![Instrument cover photo.](product.png){: style="height:250px"}
</center>
This documentation covers part number [10-0000041](https://leemangeophysical.com/product/ptm-tilt-meter-logger/).

## Overview
The tilt meter logger (TML) is designed to be coupled with the Leeman
Geophysical LLC PTM series of precision platform tilt meter instruments. The TML
can control all functions of the tilt meter, including low power and triggered
operation modes. The logger stores all data in simple daily text files on the
microSD card housed in the sealed and waterproof unit. The logger was designed
with outdoor operation in harsh environments in mind, so all controls are
designed to be operated with gloves. To further reduce power consumption, the
panel indicator lights can be disabled. The logger can also control power to the
tilt meter for applications with low rate logging of one sample every 15 minutes
or less for further power savings.

### What’s in the Box
* Tilt meter logger
* Power cable

###  Enclosure and Components
The TML is enclosed in a rugged and waterproof case with military grade external
connectors for the instrument and power input. All controls, USB connections,
and the microSD card are inside the enclosure and shielded from the elements.
The front panel consists of three control knobs, four indicator lights, a
microSD card slot, and USB connector.

### Front Panel
#### Lights Control
The lights control knob has two positions (off/on) and controls the panel lights
on the front panel. Generally the lights are left on during setup and retrieval
of the unit, but for ultra low power consumption applications can be turned off.
After deployment is complete and the unit is ready to be sealed, turn the
control to the off position and all panel lights will extinguish regardless of
their state. Turning the control back to on re-enables the indicator lights.

#### Logging Control
The logging control knob has two positions (off/on) and controls if data are
being recorded by the unit. Logging is generally turned on after the micro SD
card is installed, the tilt meter setup, and the unit ready to be left for
deployment. The logging control should be turned off before removal of the
microSD card or removal of power. Failure to do so may result in the most recent
data file being corrupted.

#### Interval Control
The interval control knob has six positions (Ins, 1, 5, 15, 30, 60) and controls
the rate at which data are recorded. The Ins position is for instrument control.
In this position the instrument is always receiving power and any time the
instrument sends a data packet, it is recorded by the TML. The tilt meter itself
can send packets at the user desired rate. The 1, 5, 15, 30, and 60 modes record
data at those intervals in minutes.

#### LED Indicators
* **Ready** - The green ready indicator illuminates when the system is ready to
    record data and all parameters are normal.
* **Error** - The red error indicator illuminates when an error condition is
    detected in the system.
* **Logging** - The green logging indicator illuminates when the system has
    logging enabled.
* **Writing** - The blue or yellow writing indicator illuminates when data are
     being written to the SD card.

#### microSD Card Slot
The microSD card slot is a push to install, push to release style card holder.
microSD cards should be inserted with the gold contacts facing the logo on the
front panel with the card retainer notch on the right side of the holder. Simply
insert the card and lightly press until you hear a click and the SD card is
installed. To release the card press lightly again until you hear a click, then
release and the card will be ejected.

#### USB Connection
The mini-B USB connector is provided to configure settings of the unit via a
serial terminal program. The TML is designed to operate at the same baud rate as
the connected instrument, which is user configurable in the menu of the logger
and tilt meter. We recommend powering the unit externally before connecting via
USB.
<center>
![Control Panel Layout.](top_panel.png){: style="height:250px"}
</center>


## Specifications
<table>
  <tr bgcolor="gray">
    <td>Parameter</td>
    <td>Min</td>
    <td>Typ</td>
    <td>Max</td>
    <td>Unit</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray">DC Input</td>
  </tr>

  <tr>
    <td>Voltage</td>
    <td>6</td>
    <td>12</td>
    <td>28</td>
    <td>VDC</td>
  </tr>

  <tr>
    <td>Current</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>mA</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray">Environmental</td>
  </tr>

  <tr>
    <td>Operating Temperature</td>
    <td>-40</td>
    <td>-</td>
    <td>80</td>
    <td>&#8451;</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray">Physcial</td>
  </tr>

  <tr>
    <td>Weight</td>
    <td>-</td>
    <td>0.79</td>
    <td>-</td>
    <td>kg</td>
  </tr>

  <tr>
    <td>Width</td>
    <td>-</td>
    <td>231</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Length</td>
    <td>-</td>
    <td>173</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Height</td>
    <td>-</td>
    <td>97</td>
    <td>-</td>
    <td>mm</td>
  </tr>
</table>


## Serial Command Interface
The serial menu allows a few basic parameters to be set by the user from a
serial terminal program. The serial menu operates at the user-set baud rate.
Each command should be entered followed by a newline character.
### Command Listing
<table>
  <tr bgcolor="gray">
    <td>Command</td>
    <td>Description</td>
  </tr>

  <tr>
    <td>SETBAUD XXXX</td>
    <td>Set baud rate</td>
  </tr>

  <tr>
    <td>SETTIME YYYY MM DD HH MM SS</td>
    <td>Set the time</td>
  </tr>

  <tr>
    <td>RESET</td>
    <td>Restart the unit</td>
  </tr>

  <tr>
    <td>DEFAULTS</td>
    <td>Reset the unit to factory defaults</td>
  </tr>

  <tr>
    <td>HELP</td>
    <td>Display command help in the terminal</td>
  </tr>

  <tr>
    <td>SHOW</td>
    <td>Show the current device settings</td>
  </tr>
</table>

### Command Descriptions
* **SETBAUD**  sets the baud rate of the device to any valid baud rate in the
list 1200, 2400, 4800, 9600, 19200, 38400, 57600, 74880, or 115200 baud. This
setting is persistent through power cycles.
* **SETTIME** sets the current time when the newline character is received. This
setting is time zone independent, but we always recommend collecting data in
UTC. After setting the time, a power off reset is recommended as a way to verify
the integrity of the clock backup battery.
* **RESET** forces a reboot of the unit.
* **DEFAULTS** restores the default settings from the factory.
* **HELP** displays the in terminal command descriptions for quick reference in
  the field.
* **SHOW** shows the current system settings in the terminal.

## Operation
### Operating Modes
The instrument may be operated in instrument controlled mode or time controlled
mode. In instrument mode the logger keeps power applied to the attached tilt
meter always and will record any data sent by the tilt meter and time stamp it.
The attached instrument controls the data collection rate and the logger simply
records. In timed mode the logger takes an active role by controlling the
attached tilt meter. When the desired interval is reached, the logger will
trigger a reading from the tilt meter and record it along with the timestamp.

Operating in instrument mode allows ‘rapid’ data collection - tilt measured at
rates faster than one sample per minute. In many geological settings even once
per minute is over sampling! In instrument mode the tilt meter should be
configured to emit data at the desired rate. The PTM102 is designed to emit 1,
6, 12, or 60 samples per minute. If the tilt meter is set to operate in
triggered mode, the logger will assert control pins to place it in timed output
mode when the instrument mode is selected. As the tilt meter is controlling the
data rate, there are drifts in the time (controlled by a crystal oscillator
inside the tilt instrument), so at high data rates the drift may result in
slightly over/under sampling. For example, a day of data at 1Hz may have 86403
samples depending upon the ambient conditions

Operating the logger in timed mode provides a more power efficient installation;
for any interval over 5 minutes the tilt meter is powered down in between
samples with a 5 minute warm up period before a reading is taken. This can save
significant power for remote installations recording at 30 or 60 minute
intervals. The largest disadvantage of timed mode is that data can be collected
at 1 sample per minute on the most rapid setting. Even if the tilt meter is set
to operate in timed mode, the logger can override these settings by asserting
control pins.

### RTC Backup Battery Installation/Removal
The real time clock holds the current human formatted date and time through
power cycles of the unit, such as when being stored or transported. This time is
held by a CR2032 backup battery located on the circuit board inside the tilt
meter logger. This battery is expected to last a few years without the unit
being powered. For long term storage the battery should be removed to mitigate a
leaking and corrosion risk. Changing the battery is a simple process, but the
time will need to be reset afterwards. All other settings are stored in
non-volatile memory and will be unaffected.

1. Remove power from the unit.

1. Remove the screws securing the control panel to the enclosure and gently lift
   the panel.

1. Gently remove the old CR2032 battery by sliding it out from the battery
holder and clip on the PCB. Do not exert excessive force or the battery clip
and/or circuit board may be damaged!

1. Install the new CR2032 battery by sliding the battery into the clip.

1. Reinstall the control panel.

1. Reapply power and set the correct clock time.

### Setting the Time
The time should be set after the RTC battery has been changed or if it is deemed
to have drifted unacceptably since the last time the unit was set. The time is
set with the serial command SETTIME out outlined in the serial commands section.
As an example, to set March 26, 2020 at 13:05:30 the command SETTIME 2020 03 26
13 05 30 would be sent. The time is set at the moment the newline character is
received. A message stating the setting was successful or if there was an error
will be returned to the serial prompt.

### Deployment
Every deployment is different, but this procedure seeks to provide a guideline
of best practices for deploying the logger. Contact your applications
representative for guidance on your specific application.

1. Connect the unit to a computer with a USB mini-B cable (preferably prior to
going to the field) and configure the desired settings.

1. Ensure the time setting is correct and the coin cell backup battery is
installed. (We recommend a yearly change if the unit is in storage.)

1. Ensure there is a microSD card (FAT16 formatted) with adequate space
   installed in the logger.

1. For ease of setup we recommend setting the panel controls to lights on,
   logging off, and instrument interval.

1. The tilt meter should already be installed and leveled. See the tilt meter
   manual for leveling instructions.

1. Connect the power and instrument cables. Apply power.

1. Connect to the unit in a serial terminal program. If you are unfamiliar with
serial terminal use, please see our company blog and application notes available
on our website.

1. If in instrument mode, you will see data from the instrument displayed in the
serial terminal. The logger will also display a regular time stamp and if it has
applied power to the instrument or not.

1. Set the appropriate logging interval.

1. Turn logging on and ensure that the SD card writing LED blinks and no errors
   are shown.

1. Disconnect the serial terminal, and turn the lights off if desired using the
panel light switch. This can save significant power over a long deployment with
limited solar resources.

1. Seal the weatherproof case and wait for the desired data collection interval.

### Retrieval
Retrieving the instrument is similar to deployment, but there are a few best
practices to note.

* Always ensure logging is turned off before removing the SD card - failure to
do so may result in corruption of data.

* Always remove power before disconnecting the attached instrument.

* Make a backup of the data, in the field if possible, as microSD cards can be
easily dropped and difficult to find.

### Error Codes
Error codes will be shown in the serial terminal and indicated by a solid red
error LED on the panel. Errors are set as bits of a error byte and sum if
multiple errors are present. Given that this instrument is a dedicated logger,
no SD card produces an error code to warn the operator as early as possible that
a crucial piece is missing. If you do not require logging, but need a RS232
interface, another product may be more applicable. When manipulating front panel
controls the error light may briefly illuminate and an error code be issued if
the switch is in-between positions. This is out of an abundance of caution to
warn the user if any switch is not in a well-defined state. Defaults are noted
in the table below.

<table>
  <tr bgcolor="gray">
    <td>Error Code</td>
    <td>Description</td>
  </tr>

  <tr>
    <td>1</td>
    <td>Light switch default - error with the light switch. Lights will default to the on position.</td>
  </tr>

  <tr>
    <td>2</td>
    <td>Log switch default - error with the logging switch. Unit will default to logging data.</td>
  </tr>

  <tr>
    <td>4</td>
    <td>Interval switch default - error with the interval switch. Unit will default to instrument mode</td>
  </tr>

  <tr>
    <td>8</td>
    <td>SD not present - there is no microSD card installed.</td>
  </tr>

  <tr>
    <td>16</td>
    <td>SD general error - there is an error such as a bad card or improper formatting.</td>
  </tr>

  <tr>
    <td>32</td>
    <td>Serial timeout - a reading is overdue from the attached instrument.
</td>
  </tr>
</table>

## Data Interpretation
### Filename Convention
Data are stored on the microSD card (if installed) in 24-hour files. Each file
is named with the year, month, and date of the data it contains and the serial
number of the logger that collected the data. If a file with that filename
already exists on the microSD card, the new data will be appended to the end of
the file.

<code>
YYYYMMDD_SSSSSSS.TXT
</code>

For example, the logger serial number 381 will store data from January 31 2021
in a file named 20210131_0000381.TXT and each calendar day will have its own
file regardless of the number of data points collected on that day.

### File Contents
The tilt meter logger will preserve the packet exactly as received from the
attached instrument, pre-pending the date and time stamp of the real time clock
when the packet was received. This time stamp is reported to the fractional
second to allow for any drift of the instrument clock in instrument control mode
to be observed.

<center>
![Output Format.](output_format.pdftop_panel.png){: style="height:250px"}
</center>

## Accessories
### Power Cable 7-0000123
An extra potted power cable for the tilt meter logger is great to have for
pre-installation preparations on-site or as a spare if a cable is destroyed by a
stray knife or wildlife

## Revision History
| Revision | Date         | Changes                             |
|----------|--------------|-------------------------------------|
| 1.0      | January 2022 | Initial Release                     |
| 1.1      | January 2023 | Update for newest PCBs and firmware |
| 1.2      | February 2023| Hyperlink table of contents         |
| 1.3      | April 2024   | Moved Documentation to MKDocs Format|
