# KLINI Surface Inclinometer
  <div style="text-align: center;">
    <img src="../product.png" alt="KLINI surface inclinometer with the M8 connector hat." style="height:250px;">
  </div>

This documentation covers the **KLINI 200S-M30** surface inclinometer, part
number 10-0000233.

## About This Manual

### Firmware Versions Covered
This manual covers instrument firmware **1.1**, **1.2**, and **1.3**.
Where an instruction depends on the firmware version, a short note such as
*Firmware 1.2 and later* follows it. A summary of changes between versions is in
the [Firmware Change Log](#firmware-change-log).

### Finding Your Firmware Version
The installed firmware version is reported in three places:

<ul>
  <li>The <b>SHOW</b> serial command prints a line such as <code># Firmware: 1.2</code>.</li>
  <li>Every data file written to the microSD card starts with a header line such as <code># Firmware 1.2</code>.</li>
  <li>The Wi-Fi settings page shows <code>FW 1.2</code> next to the serial number.</li>
</ul>

## Overview
The KLINI is a two-axis surface inclinometer with a built-in data logger. Each
unit measures tilt on two perpendicular axes, records it to a microSD card at a
configurable interval, and can stream the same readings over an RS-232 serial
connection. Every reading also includes the internal board temperature and the
supply voltage. A battery-backed real-time clock timestamps the data, and a
temporary Wi-Fi access point provides a browser-based settings page, a live
readout for leveling, and firmware updates.

### Model Designations
KLINI models are named by performance class, deployment type, sensing
technology, and measurement range. For example, **200S-M30** is:

<table>
  <tr bgcolor="gray">
    <td><b>Field</b></td>
    <td><b>Example</b></td>
    <td><b>Meaning</b></td>
  </tr>
  <tr>
    <td>Series</td>
    <td>200</td>
    <td>Resolution class (see below)</td>
  </tr>
  <tr>
    <td>Deployment</td>
    <td>S</td>
    <td>Surface instrument</td>
  </tr>
  <tr>
    <td>Technology</td>
    <td>M</td>
    <td>MEMS tilt sensors</td>
  </tr>
  <tr>
    <td>Range</td>
    <td>30</td>
    <td>Specified measurement range, &pm;30&deg;</td>
  </tr>
</table>

<table>
  <tr bgcolor="gray">
    <td><b>Series</b></td>
    <td><b>Resolution Class</b></td>
  </tr>
  <tr>
    <td>KLINI 100</td>
    <td>100 &micro;rad and coarser</td>
  </tr>
  <tr>
    <td>KLINI 200</td>
    <td>10 to 100 &micro;rad</td>
  </tr>
  <tr>
    <td>KLINI 300</td>
    <td>1 to 10 &micro;rad</td>
  </tr>
  <tr>
    <td>KLINI 400</td>
    <td>1 &micro;rad and finer</td>
  </tr>
</table>

The 200S-M30 uses two single-axis MEMS inclinometers, one per axis, which are
most linear near level.


In firmware 1.3 and later, the `SHOW` command and the data file header report
the 200S-M30's sensor type as `A`. Firmware 1.1 and 1.2 report a component
designation instead.

### Enclosure and Components
The instrument is housed in a Cerakote-coated 6061 aluminum enclosure sealed
with an O-ring, and is rated IP67 when the connector is properly mated. The
instrument is supplied without feet or mounting hardware. The base has three
M8&times;1.25 threaded holes for optional leveling feet, and optional mounting
plates are available; see [Mounting](#mounting).

The top of the enclosure (the "hat") is available in two versions: an **M8
connector hat** for external power and serial communication, and a **power
hat** that holds AA batteries for self-contained operation (see
[Parts and Accessories](#parts-and-accessories) and [Dimensions](#dimensions)).
Battery run time depends on the logging interval and power settings.

The internal components are reached by removing the lid; see
[Opening and Closing the Enclosure](#opening-and-closing-the-enclosure).

The following user-serviceable components are inside the instrument:

<ul>
  <li><b>microSD card slot</b> – removable storage for logged data.</li>
  <li><b>CR2032 coin cell</b> – keeps the real-time clock running while the unit is unpowered.</li>
  <li><b>Configuration button</b> (blue) – starts Wi-Fi configuration mode, or restores default settings if held during power-up.</li>
  <li><b>Status light</b> – a multi-color light that reports logging and error status.</li>
  <li><b>Power switch</b> – a slide switch on the circuit board that turns the instrument on and off.</li>
</ul>

## Specifications
<table>
  <tr bgcolor="gray">
    <td><b>Parameter</b></td>
    <td><b>Min</b></td>
    <td><b>Typ</b></td>
    <td><b>Max</b></td>
    <td><b>Unit</b></td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Tilt Measurement</b></td>
  </tr>
  <tr>
    <td>Axes</td>
    <td colspan="3">2 (X and Y)</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Specified measurement range</td>
    <td>-30</td>
    <td>-</td>
    <td>30</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Factory calibration range</td>
    <td>-10</td>
    <td>-</td>
    <td>10</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Sensitivity near level (one count)</td>
    <td>-</td>
    <td>0.00179 (31)</td>
    <td>-</td>
    <td>&deg; (&micro;rad)</td>
  </tr>
  <tr>
    <td>Noise (one reading, 16-measurement average), rms</td>
    <td>-</td>
    <td>0.0034 (60)</td>
    <td>0.005 (85)</td>
    <td>&deg; (&micro;rad)</td>
  </tr>
  <tr>
    <td>Error within &pm;10&deg;, rms</td>
    <td>-</td>
    <td>0.007</td>
    <td>0.02</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Error within &pm;10&deg;, maximum</td>
    <td>-</td>
    <td>0.02</td>
    <td>0.05</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Error within &pm;30&deg;, maximum</td>
    <td>-</td>
    <td>0.2</td>
    <td>0.45</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Cross-axis sensitivity</td>
    <td>-</td>
    <td>0.8</td>
    <td>3.5</td>
    <td>%</td>
  </tr>
  <tr>
    <td>Zero offset (not calibrated; see <a href="#factory-calibration">Factory Calibration</a>)</td>
    <td>-</td>
    <td>1.2</td>
    <td>4</td>
    <td>&deg;</td>
  </tr>
  <tr>
    <td>Sensitivity temperature drift, over operating range</td>
    <td>-</td>
    <td>&pm;0.9</td>
    <td>-</td>
    <td>%</td>
  </tr>
  <tr>
    <td>Zero temperature drift, -20 to 85 &#8451;</td>
    <td>-</td>
    <td>&pm;0.85</td>
    <td>-</td>
    <td>&deg;</td>
  </tr>


  <tr>
    <td colspan="5" bgcolor="gray"><b>Data Acquisition</b></td>
  </tr>
  <tr>
    <td>Logging interval</td>
    <td colspan="3">Manual, 1 s, 5 s, 10 s, 30 s, 1, 2, 5, 10, 15, 30, or 60 min</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Tilt readings averaged per sample</td>
    <td>1</td>
    <td>16</td>
    <td>255</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Storage</td>
    <td colspan="3">microSD card up to 32 GB, one comma-delimited file per day</td>
    <td>-</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Interfaces</b></td>
  </tr>
  <tr>
    <td>Serial</td>
    <td colspan="3">RS-232, 8 data bits, no parity, 1 stop bit, 1200–115200 baud (default 9600)</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Wi-Fi</td>
    <td colspan="3">Temporary access point for configuration only</td>
    <td>-</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>DC Input</b></td>
  </tr>
  <tr>
    <td>Voltage</td>
    <td>5</td>
    <td>12</td>
    <td>24</td>
    <td>VDC</td>
  </tr>
  <tr>
    <td>Voltage, absolute maximum</td>
    <td>4.5</td>
    <td>-</td>
    <td>28</td>
    <td>VDC</td>
  </tr>
  <tr>
    <td>Power, normal operation (1 s logging)</td>
    <td>-</td>
    <td>0.15</td>
    <td>-</td>
    <td>W</td>
  </tr>
  <tr>
    <td>Power, low-power mode</td>
    <td>-</td>
    <td>20</td>
    <td>-</td>
    <td>mW</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Environmental</b></td>
  </tr>
  <tr>
    <td>Operating temperature</td>
    <td>-40</td>
    <td>-</td>
    <td>70</td>
    <td>&#8451;</td>
  </tr>
  <tr>
    <td>Storage temperature</td>
    <td>-40</td>
    <td>-</td>
    <td>85</td>
    <td>&#8451;</td>
  </tr>
  <tr>
    <td>Ingress protection</td>
    <td colspan="3">IP67 with connector mated</td>
    <td>-</td>
  </tr>

  <tr>
    <td colspan="5" bgcolor="gray"><b>Physical</b></td>
  </tr>
  <tr>
    <td>Weight</td>
    <td>-</td>
    <td>1.28</td>
    <td>-</td>
    <td>kg</td>
  </tr>
  <tr>
    <td>Enclosure diameter</td>
    <td>-</td>
    <td>130 (5.13)</td>
    <td>-</td>
    <td>mm (in)</td>
  </tr>
  <tr>
    <td>Height, M8 connector hat (to connector top)</td>
    <td>-</td>
    <td>88 (3.46)</td>
    <td>-</td>
    <td>mm (in)</td>
  </tr>
  <tr>
    <td>Height, AA battery hat</td>
    <td>-</td>
    <td>111 (4.38)</td>
    <td>-</td>
    <td>mm (in)</td>
  </tr>
  <tr>
    <td>Leveling foot thread (feet optional)</td>
    <td colspan="3">M8&times;1.25</td>
    <td>-</td>
  </tr>
</table>

The specified measurement range is the range over which the instrument is
intended to be used. The factory calibration is fitted and certified over
&pm;10&deg;, where the sensors are most linear; see [Calibration](#calibration).
Error figures are relative to the factory calibration reference, at room
temperature, after calibration. Noise is measured at a 1 s logging interval.

## Parts and Accessories
<table>
  <tr bgcolor="gray">
    <td><b>Part Number</b></td>
    <td><b>Description</b></td>
  </tr>
  <tr>
    <td>10-0000233</td>
    <td>KLINI 200S-M30 surface inclinometer</td>
  </tr>
  <tr>
    <td>10-0000235</td>
    <td>RS232 M8 Kit (interface cable) – M8 cable and RS-232 adapter with wall-power and battery-clip power connections, for setting up, operating, and communicating with the instrument in the lab or field</td>
  </tr>
  <tr>
    <td>10-0000236</td>
    <td>Power hat – AA battery top for self-contained operation</td>
  </tr>
  <tr>
    <td>10-0000244</td>
    <td>KLINI Mounting Plate Kit – flat plate for bolting the instrument to a horizontal surface such as a floor, pad, or the top of an instrument enclosure</td>
  </tr>
  <tr>
    <td>10-0000241</td>
    <td>KLINI Right Angle Mounting Plate Kit – 90&deg; plate for mounting the instrument to a vertical surface such as a post or wall</td>
  </tr>
</table>

Accessories and replacement O-rings are available from Leeman Geophysical LLC;
contact us for ordering.

## Installation
Always consult local codes, guidelines, and professional guidance for
installation.

### Connector Wiring
The 4-pin M8 connector on the connector hat provides power, ground, and
RS-232 communication. The RS232 M8 Kit
(10-0000235) provides a ready-made interface cable.

<table>
  <tr bgcolor="gray">
    <td><b>Wire Color</b></td>
    <td><b>M8 Pin</b></td>
    <td><b>Description</b></td>
  </tr>
  <tr>
    <td>Brown</td>
    <td>1</td>
    <td>Power</td>
  </tr>
  <tr>
    <td>White</td>
    <td>2</td>
    <td>RS-232 RX to instrument from device</td>
  </tr>
  <tr>
    <td>Blue</td>
    <td>3</td>
    <td>Ground</td>
  </tr>
  <tr>
    <td>Black</td>
    <td>4</td>
    <td>RS-232 TX from instrument to device</td>
  </tr>
</table>

### Opening and Closing the Enclosure
The lid is held by a threaded retaining ring and sealed with an O-ring.

To open the enclosure:

<ol>
  <li>Remove power from the unit, or turn off the power switch once the lid is off.</li>
  <li>Loosen the top retaining ring and lift the lid off.</li>
  <li>If the lid has pressure-sealed shut, gently pry it up using the slot provided, with a knife edge or flat-blade screwdriver. Take care not to mar the finish.</li>
</ol>

To close the enclosure:

<ol>
  <li>Check the O-ring for nicks, cracks, flattening, or debris, and replace it if necessary. A small dab of vacuum grease helps hold the O-ring in place and improves the seal.</li>
  <li>Set the lid on top of the enclosure and rotate it until the flat on the lid lines up with the flat on the case and the lid drops into its seat.</li>
  <li>Tighten the retaining ring until snug. <b>Do not overtighten the ring</b>; little pressure is needed to seal the O-ring.</li>
</ol>

Replacement O-rings are available from Leeman Geophysical LLC. The O-ring is an
oil-resistant Buna-N O-ring, 1/16" fractional width, dash number 044.

### Clock Backup Battery
The CR2032 coin cell keeps the clock running while the instrument is
unpowered. If the cell is missing or exhausted and power is removed, the clock
loses its time; see [Troubleshooting](#troubleshooting). We recommend
replacing the cell yearly for units in storage.

To replace the cell, remove power and
[open the enclosure](#opening-and-closing-the-enclosure). Then
remove the old cell and fit the new CR2032 with the positive (+) side up,
taking care not to bend its holder. Close the enclosure, apply power, and
[set the clock](#setting-the-clock).

### microSD Card
Data are logged only when a microSD card is installed. Without a card the
instrument still measures and can stream readings over the serial port.

Use a microSD card of up to 32 GB, formatted FAT32 (the standard format for
cards of this size). To install or remove the card:

<ol>
  <li>Remove power and <a href="#opening-and-closing-the-enclosure">open the enclosure</a>.</li>
  <li>If desired, disconnect the internal cable from the M8 connector to set the lid aside: press in on the plug's tab and unplug it. The plug is keyed, so it can only be reconnected the correct way.</li>
  <li>Slide the metal card holder shield toward the center of the instrument, then hinge it up.</li>
  <li>Remove or insert the card.</li>
  <li>Hinge the shield down and slide it toward the outside of the instrument until it clicks.</li>
  <li>Reconnect the M8 connector cable if you disconnected it, and close the enclosure.</li>
</ol>

Remove power before removing the card. Readings are held in memory and written
to the card in groups (see [Data Files](#data-files)), so removing power or the
card can discard up to the last 10 readings or 5 minutes of data, whichever is
less.

### Mounting
The instrument can be installed in several ways:

<ul>
  <li><b>Leveling feet (optional)</b> – fit three M8&times;1.25 leveling feet into the base and set the instrument on an existing firm, flat surface such as a concrete pad, adjusting the feet to level it.</li>
  <li><b>Mounting Plate Kit</b> – bolt the instrument flat to a horizontal surface such as a floor or the top of an instrument enclosure.</li>
  <li><b>Right Angle Mounting Plate Kit</b> – mount the instrument at 90&deg; to a vertical surface such as a post or wall.</li>
  <li><b>Direct burial</b> – bury the instrument without a plate.</li>
</ul>

The leveling feet need a suitable surface to rest on. Unless you are already
installing on a pad or similar surface, use one of the mounting plates or
direct burial. See [Parts and Accessories](#parts-and-accessories).

### Deployment
Every deployment is different; this procedure is a guideline. Contact us for
guidance on your application.

<ol>
  <li>Before going to the field, connect the unit to a computer (see <a href="#serial-interface">Serial Interface</a>) and configure the logging interval and other settings.</li>
  <li>Set the clock (we recommend UTC) and confirm the backup battery is installed.</li>
  <li>If data are to be logged internally, install a microSD card with adequate free space.</li>
  <li>Choose a stable site away from large tilt sources such as trees, and out of low areas that may flood. Install the unit using one of the <a href="#mounting">mounting methods</a>.</li>
  <li>Level the unit as closely as practical; the instrument is most accurate within &pm;10&deg; of level. A bubble level gets the instrument very close. For finer leveling, use the <a href="#live-view">live view</a> in Wi-Fi configuration mode or streamed serial data. See <a href="../../appnotes/AN0001/">AN0001: Using a Tiltmeter as a Precision Level</a>.</li>
  <li>If georeferenced tilt is needed, measure and record the instrument's orientation with a compass against the flat on the back of the case (see <a href="#coordinate-system">Coordinate System</a>).</li>
  <li>Connect the power and data cable, apply power, and make sure the power switch is on. The status light shows red, green, then blue during startup. Within about 15 seconds the light should begin its regular status blink (see <a href="#status-light">Status Light</a>).</li>
  <li>Confirm logging, then <a href="#opening-and-closing-the-enclosure">close and seal the enclosure</a>.</li>
</ol>

## Operation

### Coordinate System
  <div style="text-align: center;">
    <img src="../axes.png" alt="Top view of the instrument showing the positive and negative X and Y tilt directions." style="height:350px;">
  </div>

The diagram shows the instrument from above. The Y axis runs through the
single mounting tab: +Y points toward that tab and -Y away from it. The X axis
is perpendicular to it, with +X to the right when the tab is at the top.
Tilting the instrument in the direction of an arrow gives a positive or
negative reading on that axis, as labeled: lowering the +X side gives a
positive X reading, and lowering the +Y side (the mounting tab) gives a
positive Y reading.

The flat on the back of the case is a convenient reference for measuring the
instrument's orientation with a compass. The flat is on the -Y side, opposite
the mounting tab, and runs parallel to the X axis: a bearing taken along the
flat toward the +X side is the direction of +X. The direction of +Y is then
90&deg; counterclockwise from +X when viewed from above (for example, if +X
points east, +Y points north). If you want to georeference the tilt
data (for example, to resolve tilt into north and east components), record the
orientation at installation, noting whether the bearing is magnetic or true.

The sign convention of the degree outputs is set by the factory calibration
coefficients. If the coefficients are changed, the sign may change; see
[Calibration](#calibration).

### Startup
When power is applied the instrument:

<ol>
  <li>Loads its saved settings.</li>
  <li>Flashes the status light red, green, then blue.</li>
  <li>Prints <code># Startup Command Window Open</code>, waits 5 seconds for serial commands, then prints <code># Startup Command Window Closed</code>. This window guarantees a chance to send commands after power-up, which matters in low-power mode (see <a href="#low-power-mode">Low-Power Mode</a>). Otherwise, commands are accepted at any time.</li>
  <li>Takes its first reading immediately, then continues at the logging interval.</li>
</ol>

**Caution:** holding the configuration button while applying power restores
default settings. See [Restoring Default Settings](#restoring-default-settings).

### Sampling and Timing
Readings are taken on even clock boundaries for the selected interval. For
example, with a 5-minute interval, readings are taken at :00, :05, :10, and so
on. The first reading after power-up is taken immediately, whatever the time.

Each reading averages a configurable number of tilt measurements on each axis
(default 16). Larger averages reduce noise but take longer.

When the interval is set to **manual** (`0s`), readings are taken only on
request with the [READ](#serial-commands) command, and each one is written to
the card immediately. *Firmware 1.2 and later.* In firmware 1.1, `0s` samples
continuously as fast as the instrument can and is not recommended; use `1s` for
the fastest regular logging.

Timestamps come from the internal clock and have no time-zone marker; the
clock keeps whatever time you set. We recommend UTC. The settings page labels
its time field UTC, but it sets the clock to the time you enter.

### Low-Power Mode
Low-power mode (off by default) reduces power consumption by sleeping between
readings. It takes effect only when the logging interval is 10 seconds or
longer. The instrument wakes about 3 seconds before each reading.

While asleep, the instrument does not receive serial commands or respond to the
configuration button. It is awake only briefly around each reading. To
communicate with a unit in low-power mode, remove and reapply power, then send
your command during the 5-second
[startup command window](#startup), for example `LOWPOWER 0` to turn low-power
mode off, or `CONFIG` to start Wi-Fi configuration mode. Alternatively, hold
the configuration button until the status light turns solid blue; this can take
up to about a minute.

### Serial Interface
Connect to the instrument with any terminal program; see
[AN0005: Establishing Serial Communication with Instruments Using a Terminal Program](../appnotes/AN0005.md).
Use the unit's baud rate (default 9600), 8 data bits, no parity, and 1 stop
bit. Type each command and end it with Enter (a newline; a carriage return is
ignored). Commands are case sensitive and must be typed in upper case.

The instrument replies <code>OK</code> when a command succeeds and
<code>!</code> when it is rejected, for example because of an invalid value.
Informational lines begin with <code>#</code>.

When serial streaming is on (the default), each reading is also printed as a
line in the same column order as the data files:

<code>
2026-09-25T17:13:17,24.188,12.014,-1002,-760,-1.794,-1.361
</code>

Streamed lines show temperature with three decimal places; data files use two.
See [Data Interpretation](#data-interpretation) for the columns.

### Serial Commands
Settings changed by command are saved immediately and kept through power
cycles.

<table>
  <tr bgcolor="gray">
    <td><b>Command</b></td>
    <td><b>Description</b></td>
    <td><b>Valid Values</b></td>
    <td><b>Default</b></td>
  </tr>
  <tr>
    <td>SHOW</td>
    <td>Show status, settings, calibration, SD card state, and errors</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>HELP</td>
    <td>List commands</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>READ</td>
    <td>Take a reading now. <i>Firmware 1.2 and later.</i></td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>SETRATE <i>interval</i></td>
    <td>Set the logging interval</td>
    <td>0s, 1s, 5s, 10s, 30s, 1m, 2m, 5m, 10m, 15m, 30m, 60m</td>
    <td>1s</td>
  </tr>
  <tr>
    <td>TILTNAVG <i>n</i></td>
    <td>Set the number of tilt measurements averaged per reading</td>
    <td>1–255</td>
    <td>16</td>
  </tr>
  <tr>
    <td>SETTIME <i>YYYY MM DD hh mm ss</i></td>
    <td>Set the clock (24-hour time)</td>
    <td>Years 2000–2099</td>
    <td>-</td>
  </tr>
  <tr>
    <td>SETBAUD <i>rate</i></td>
    <td>Set the serial baud rate</td>
    <td>1200, 1800, 2400, 3600, 4800, 7200, 9600, 14400, 19200, 28800, 38400, 57600, 115200</td>
    <td>9600</td>
  </tr>
  <tr>
    <td>STREAM <i>0|1</i></td>
    <td>Turn serial output of readings off (0) or on (1)</td>
    <td>0, 1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>LOWPOWER <i>0|1</i></td>
    <td>Turn low-power mode off (0) or on (1)</td>
    <td>0, 1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>LOWVCUTOFF <i>0|1</i></td>
    <td>Turn the low-voltage cutoff off (0) or on (1)</td>
    <td>0, 1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>SETLOWV <i>cutoff reconnect</i></td>
    <td>Set the low-voltage cutoff and reconnect voltages in volts</td>
    <td>Both above 0; reconnect greater than cutoff</td>
    <td>11.6, 12.0</td>
  </tr>
  <tr>
    <td>SETLEDBRIGHT <i>level</i></td>
    <td>Set the status light brightness</td>
    <td>1 or LOW, 2 or MED, 3 or HIGH</td>
    <td>HIGH</td>
  </tr>
  <tr>
    <td>CONFIG</td>
    <td>Start Wi-Fi configuration mode. <i>Firmware 1.2 and later.</i></td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>RESET</td>
    <td>Restart the instrument</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>DEFAULTS</td>
    <td>Restore default settings, keeping serial number and calibration</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>

<ul>
  <li><b>SHOW</b> prints the serial number, firmware version, whether the clock is set, the current time, all settings, the calibration coefficients, the status light pattern, the SD card state and free space, and any active errors.</li>
  <li><b>READ</b> takes one reading immediately, prints it if streaming is on, and logs it. With the interval set to <code>0s</code> the reading is written to the card at once. It can also be used between scheduled readings, for example for event-triggered measurements. <i>Firmware 1.2 and later.</i> In firmware 1.1 this command is not available.</li>
  <li><b>SETRATE</b> sets the logging interval. <code>0s</code> selects manual readings (see <a href="#sampling-and-timing">Sampling and Timing</a>).</li>
  <li><b>TILTNAVG</b> sets how many tilt measurements are averaged into each reading.</li>
  <li><b>SETTIME</b> sets the clock when the command is received. For example, to set 26 March 2026 at 13:05:30, send <code>SETTIME 2026 03 26 13 05 30</code>. After setting the clock we recommend removing power briefly and checking the time with SHOW, which confirms the backup battery.</li>
  <li><b>SETBAUD</b> saves a new baud rate, which takes effect at the next power-up or RESET. Reconnect your terminal at the new rate.</li>
  <li><b>STREAM</b> controls whether readings are printed on the serial port. Logging to the card is not affected.</li>
  <li><b>LOWPOWER</b> controls <a href="#low-power-mode">low-power mode</a>.</li>
  <li><b>LOWVCUTOFF</b> and <b>SETLOWV</b> control the <a href="#low-voltage-cutoff">low-voltage cutoff</a>.</li>
  <li><b>CONFIG</b> starts <a href="#wi-fi-configuration-mode">Wi-Fi configuration mode</a>. In firmware 1.1, use the configuration button instead.</li>
  <li><b>RESET</b> replies <code>OK</code>, then restarts the instrument.</li>
  <li><b>DEFAULTS</b> restores default settings; see <a href="#restoring-default-settings">Restoring Default Settings</a>.</li>
</ul>

The instrument also accepts calibration commands (described under
[Calibration](#calibration)) and factory commands. **SETVINCAL**,
**SETTEMPCAL**, and **SETTEMPCOMP** are for factory use; changing them affects
the accuracy of the voltage, temperature, and tilt readings.

### Setting the Clock
Set the clock with the `SETTIME` command, or from the settings page in
[Wi-Fi configuration mode](#wi-fi-configuration-mode) (**Time (UTC)**, then
**Set Time**). `SHOW` reports `RTC Set: YES` once the clock holds a valid time.
In firmware 1.3 and later, while the clock has lost its time and has not been
set, `SHOW` and the live view list the error `RTC Time Invalid` and the status
light shows a red single blink. The settings page also rejects an invalid date
or time.

### Wi-Fi Configuration Mode
Wi-Fi configuration mode provides a settings page, a live readout, and firmware
updates from any phone or computer with a web browser. Logging and serial
output stop while the mode is active.

To start configuration mode, either:

<ul>
  <li>press the configuration button once the startup sequence has finished, or</li>
  <li>send the <code>CONFIG</code> command. <i>Firmware 1.2 and later.</i></li>
</ul>

The status light turns solid blue. The instrument creates a Wi-Fi network
named `CONFIG` followed by the serial number (for example `CONFIG538`). The
network password is included in your unit's paperwork, or you can obtain it by
contacting us. You can change it on the settings page (**Security**, minimum 8
characters).

Connect to the network and browse to the address printed on the serial port as
`# AP IP:` (normally `http://192.168.4.1`).

Configuration mode ends when you press **Save** or **Exit** on the settings
page, or 5 minutes after it started, whichever comes first. The instrument then
resumes normal operation. The 5-minute limit counts from when the mode started,
not from your last action, so save changes promptly.

#### Settings Page
The settings page provides the same settings as the serial commands:

<ul>
  <li><b>Logging</b> – log interval (<b>Disabled</b> is the manual <code>0s</code> setting), serial streaming, baud rate, and tilt averaging.</li>
  <li><b>Time (UTC)</b> – sets the clock from the date and time you enter.</li>
  <li><b>Power</b> – low-power mode, low-voltage cutoff, cutoff and reconnect voltages, and status light brightness.</li>
  <li><b>Calibration</b> – the calibration coefficients. Do not edit these unless instructed; see <a href="#calibration">Calibration</a>.</li>
  <li><b>Security</b> – the configuration network password. Leave blank to keep the current password.</li>
</ul>

Pressing **Save** stores all fields on the page and ends configuration mode. In
firmware 1.3 and later, invalid entries (for example a zero calibration slope,
or a cut-on voltage below the cutoff) are outlined in red, and the reason
appears in a red bubble when you select or point at the field. **Save** is
blocked until they are corrected. If an invalid value reaches
the instrument anyway, it shows **Settings Not Saved** and changes nothing.
Baud rate changes take effect at the next power-up.

#### Live View
The **Live** page shows the current time, X and Y tilt in degrees, supply
voltage, internal temperature, and any active errors, updated once per second.
Live values are single unaveraged measurements shown to two decimal places,
which is convenient for leveling. Logged data are averaged and more precise.

### Status Light
During normal operation the status light shows a short pattern every 10
seconds. In low-power mode the light stays off while the instrument sleeps, so
the pattern appears only when it wakes, which can be up to about a minute
apart. Brightness is set with `SETLEDBRIGHT` or on the settings page. `SHOW`
reports the current pattern by the name in the second column.

If more than one condition applies, the pattern highest in the table is shown.

<table>
  <tr bgcolor="gray">
    <td><b>Pattern</b></td>
    <td><b>SHOW Name</b></td>
    <td><b>Meaning</b></td>
  </tr>
  <tr>
    <td>Red double blink</td>
    <td>Red Double</td>
    <td>An error is active. <code>SHOW</code> lists it; see <a href="#troubleshooting">Troubleshooting</a>.</td>
  </tr>
  <tr>
    <td>Red single blink</td>
    <td>Red Single</td>
    <td>A warning; readings are still being logged. Either the clock has lost its time and has not been set, so timestamps are wrong (<code>SHOW</code> lists <code>RTC Time Invalid</code>; <a href="#setting-the-clock">set the clock</a>), or the card has 50 MB or less free (<code>SHOW</code> lists <code>Storage Nearly Full</code>; copy data off and clear or replace the card). <i>Firmware 1.3 and later.</i></td>
  </tr>
  <tr>
    <td>Yellow single blink</td>
    <td>Yellow Single</td>
    <td>No microSD card installed, with low-power mode on and an interval longer than 10 s.</td>
  </tr>
  <tr>
    <td>Green single blink</td>
    <td>Green Single</td>
    <td>No microSD card installed; readings are not logged.</td>
  </tr>
  <tr>
    <td>Yellow double blink</td>
    <td>Yellow Double</td>
    <td>Logging to the microSD card, with low-power mode on and an interval longer than 10 s.</td>
  </tr>
  <tr>
    <td>Green double blink</td>
    <td>Green Double</td>
    <td>Logging to the microSD card.</td>
  </tr>
  <tr>
    <td>Short red flash, then yellow</td>
    <td>Red/Yellow Fast</td>
    <td>A card is installed but has not yet been confirmed. This is normal briefly after a card is inserted while the instrument is powered: the instrument checks a new card within about a second, or when it next wakes in low-power mode. If it persists, check the card.</td>
  </tr>
</table>

Other indications:

<table>
  <tr bgcolor="gray">
    <td><b>Pattern</b></td>
    <td><b>Meaning</b></td>
  </tr>
  <tr>
    <td>Red, green, then blue, half a second each</td>
    <td>Startup (see <a href="#startup">Startup</a>).</td>
  </tr>
  <tr>
    <td>Three green blinks</td>
    <td>Default settings restored: after <code>DEFAULTS</code>, or at power-up (before the startup colors) when the configuration button is held or the saved settings were found invalid. See <a href="#restoring-default-settings">Restoring Default Settings</a>.</td>
  </tr>
  <tr>
    <td>Solid blue</td>
    <td>Wi-Fi configuration mode.</td>
  </tr>
  <tr>
    <td>No light</td>
    <td>The instrument is off (power switch or supply), the low-voltage cutoff is active, or it is asleep in low-power mode.</td>
  </tr>
</table>

In firmware 1.1 and 1.2, an unset clock or a nearly full card does not change
the status light, and a card that cannot be written to or is full shows the red
and yellow pattern instead of a red double blink. Those versions also update
the logging and no-card patterns only when they next write to the card, which
can be several minutes later in low-power mode. Those versions also report
the yellow double blink in `SHOW` as `Red/Yellow Fast`, and the red and yellow
pattern as `Unknown Pattern`.

### Low-Voltage Cutoff
The low-voltage cutoff (off by default) protects batteries from deep
discharge. When enabled, the supply voltage is checked every minute. If it
falls to the cutoff voltage or below, the instrument writes any buffered
readings to the card and shuts down. It checks again every 10 minutes and
resumes operation only when the voltage has recovered to the reconnect voltage.
No readings are taken while the cutoff is active. The defaults are 11.6 V
cutoff and 12.0 V reconnect.

### Restoring Default Settings
Send `DEFAULTS`, or hold the configuration button while applying power. The
status light blinks green three times to confirm. The serial number and all
calibration coefficients are kept; every other setting returns to its default.

The instrument also restores defaults by itself at power-up if its saved
settings are found to be invalid, again blinking green three times before the
startup colors. In firmware 1.3 and later it keeps the calibration
coefficients in this case, provided they are themselves valid. In firmware 1.2,
any invalid saved value caused the calibration to be lost as well.

The defaults are:

<table>
  <tr bgcolor="gray">
    <td><b>Setting</b></td>
    <td><b>Default</b></td>
  </tr>
  <tr><td>Logging interval</td><td>1 s</td></tr>
  <tr><td>Tilt averaging</td><td>16</td></tr>
  <tr><td>Serial baud rate</td><td>9600</td></tr>
  <tr><td>Serial streaming</td><td>On</td></tr>
  <tr><td>Low-power mode</td><td>Off</td></tr>
  <tr><td>Low-voltage cutoff</td><td>Off, 11.6 V cutoff, 12.0 V reconnect</td></tr>
  <tr><td>Status light brightness</td><td>High</td></tr>
  <tr><td>Configuration network password</td><td>Factory password</td></tr>
</table>

The clock is not changed.

### Firmware Updates
Leeman Geophysical provides firmware updates as a single `.bin` file. Settings,
the serial number, and calibration coefficients are kept through updates
between the firmware versions covered by this manual.

<ol>
  <li>Record your settings with <code>SHOW</code> and keep the output.</li>
  <li>Start <a href="#wi-fi-configuration-mode">Wi-Fi configuration mode</a> and connect to the instrument's network.</li>
  <li>Click <b>Firmware update</b> at the bottom of the settings page, or browse to <code>http://192.168.4.1/firmware</code> (use the address printed on the serial port if it differs).</li>
  <li>Choose the <code>.bin</code> file and upload it. Keep the instrument powered and nearby until the page reports <b>Firmware Installed</b> (when updating from firmware 1.3 or later) or <b>Update successful - rebooting now.</b> (from firmware 1.1 or 1.2). The instrument then restarts and its Wi-Fi network disappears.</li>
  <li>After the restart, run <code>SHOW</code> to confirm the new firmware version and your settings.</li>
</ol>

If an upload fails or is interrupted, the instrument keeps running its
previous firmware. When the installed firmware is 1.3 or later, the page
reports **Update Failed** in that case; always confirm the version with
`SHOW` after an update. Try again, and contact us if the problem persists.

## Calibration
Each instrument is calibrated at the factory, and the calibration coefficients
are stored in the instrument and applied to every reading. A calibration
report is supplied with each unit.

### Factory Calibration
The factory calibration determines each axis's sensitivity by tilting the
instrument through known angles on a precision tilt stage. The certified
coefficients are fitted over &pm;10&deg;, the range the instrument is designed
to operate in. The report also shows performance over the stage's full sweep
as a range check.

The calibration establishes **sensitivity**, not absolute level. Where the
instrument reads zero depends on how it sits on its mounting surface and on
small offsets in the sensors. The instrument is not certified to read zero when
exactly level; set or record your zero at installation. To measure the offset
directly, see [AN0003: Measuring Tiltmeter Bias](../appnotes/AN0003.md).

### How Readings Are Calculated
For each axis the instrument converts the raw sensor count to degrees with:

$$\theta = \arcsin\left(k_{\text{eff}} \cdot \text{raw} + b_{\text{eff}}\right)$$

$$k_{\text{eff}} = k + \left(a_k T + c_k\right), \qquad b_{\text{eff}} = b + \left(a_b T + c_b\right)$$

where $k$ is the slope (g per count), $b$ the offset (g), $T$ the internal
temperature in &#8451;, and $a_k$, $c_k$, $a_b$, $c_b$ the temperature
compensation terms. The factory sets the temperature compensation terms to zero
unless otherwise stated in your calibration report, so the conversion reduces
to $\theta = \arcsin(k \cdot \text{raw} + b)$. If the value inside the
arcsine falls outside &pm;1, the reading is limited to &pm;90&deg;.

Near level this is very nearly linear: one count corresponds to about
0.00179&deg; (31 &micro;rad).

### Viewing the Calibration
`SHOW` lists the coefficients as `X slope`, `X offset`, `Y slope`, `Y offset`,
followed by the temperature compensation terms. Each data file header lists
the same values.

In firmware 1.1 and 1.2 these values are displayed rounded to six decimal
places, so a slope such as -0.0000311099 appears as `-0.000031`. The
instrument stores and uses the full value; the rounding affects the display
only. Use the values on your calibration report. *Firmware 1.3 and later*
display the full value.

### Changing the Calibration
You may need to change the coefficients to apply a calibration from a
recalibration, or to restore factory values. Use:

<code>
SETTILTCAL X slope offset
</code>

with the axis (`X` or `Y`), the slope in g per count, and the offset in g,
exactly as printed on your calibration report. For example:

<code>
SETTILTCAL Y -3.110999e-05 0
</code>

The instrument replies `OK` and saves the values immediately. Confirm the
change by comparing a streamed or logged reading with the formula above.

Slopes must be non-zero; offsets may be zero. Firmware 1.3 and later reject a
zero slope: the command replies `!`, and the settings page marks the field as
invalid and will not save.

**Caution for firmware 1.1 and 1.2:** never enter a slope of zero. In firmware
1.2, a zero slope makes the saved settings invalid at the next power-up, and
the instrument restores all defaults *without* keeping its calibration. In
firmware 1.1, a zero slope makes that axis read zero. In either case the
factory coefficients must be re-entered.

Changing the sign of a slope reverses the direction of that axis.

## Data Interpretation

### Data Files
Data are stored in a `LOGS` folder on the microSD card, one file per day,
named by date from the instrument's clock:

<code>
LOGS/YYYYMMDD.csv
</code>

If the file for the day already exists, new data are appended. A new file
begins with a header recording the serial number, firmware version, tilt
sensor type, averaging, logging interval, and all calibration coefficients.
The header is written only when the file is created; it is not repeated if
settings change later that day.

Readings are held in memory and written to the card every 10 readings or every
5 minutes, whichever comes first, and immediately for manual (`0s`) readings
in firmware 1.2 and later.

An example file:

<code>
# KLINI data log SN:538<br>
# Firmware 1.2<br>
# X Tilt Sensor Type: ...<br>
# Y Tilt Sensor Type: ...<br>
# Tilt Points Averaged: 16<br>
# Log Interval: 1s<br>
# X Tilt Calibration Slope: ...<br>
...<br>
timestamp,temperature_C,vin_V,tilt_x_raw,tilt_y_raw,tilt_x_deg,tilt_y_deg<br>
2026-09-25T17:13:17,24.19,12.014,-1002,-760,-1.794,-1.361
</code>

The sensor type line shows a model designation such as `A` in firmware 1.3 and
later, and a component designation in firmware 1.1 and 1.2.

| timestamp | temperature_C | vin_V | tilt_x_raw | tilt_y_raw | tilt_x_deg | tilt_y_deg |
|-----------|---------------|-------|------------|------------|------------|------------|
| 2026-09-25T17:13:17 | 24.19 | 12.014 | -1002 | -760 | -1.794 | -1.361 |

<ul>
  <li><b>timestamp</b> – date and time of the reading from the instrument clock, <code>YYYY-MM-DDThh:mm:ss</code>, with no time-zone marker. We recommend setting the clock to UTC.</li>
  <li><b>temperature_C</b> – internal board temperature, &#8451;.</li>
  <li><b>vin_V</b> – supply voltage measured inside the instrument, volts.</li>
  <li><b>tilt_x_raw</b>, <b>tilt_y_raw</b> – averaged raw sensor counts. Use these to apply a different calibration in post-processing.</li>
  <li><b>tilt_x_deg</b>, <b>tilt_y_deg</b> – tilt in degrees with the stored calibration applied, three decimal places.</li>
</ul>

To convert degrees to microradians, multiply by 17,453.3. For more on working
with count data, see
[AN0002: Understanding Tiltmeter Count Readings](../appnotes/AN0002.md).

### Tilt Interpretation
Tilt data include instrument effects as well as the tilt under study. The
factors below should guide deployment and analysis. Our
[application notes](../appnotes.md) cover several of them, and we are happy to
help.

<ul>
  <li><b>Zero offset</b> – the reading when level includes small sensor and mounting offsets. Most studies use changes in tilt, so record the initial reading or remove it in processing.</li>
  <li><b>Range</b> – the instrument is most accurate within &pm;10&deg;. Beyond this, errors increase; the report's range check shows the behavior of your unit.</li>
  <li><b>Temperature</b> – temperature changes can alter the sensor offset and sensitivity and cause thermal expansion of the enclosure and mounting. These effects are usually corrected together by comparing tilt with the logged temperature.</li>
  <li><b>Cross-axis tilt</b> – small misalignments between the sensing axes and the enclosure produce a small signal on one axis when the other tilts.</li>
  <li><b>Mounting</b> – an unstable mounting surface produces tilt unrelated to the process under study.</li>
</ul>

## Troubleshooting
Run `SHOW` for the error list and SD card status.

<table>
  <tr bgcolor="gray">
    <td><b>Symptom</b></td>
    <td><b>What to do</b></td>
  </tr>
  <tr>
    <td>No response on the serial port</td>
    <td>Check wiring, power, and the baud rate (default 9600; a changed rate applies after restart). If low-power mode is on, remove and reapply power and send the command during the 5-second startup window. If the baud rate is unknown, try each supported rate.</td>
  </tr>
  <tr>
    <td>Command returns <code>!</code></td>
    <td>The command or a value was not accepted. Commands are upper case and values must be in the valid range. <code>READ</code> and <code>CONFIG</code> are not available in firmware 1.1.</td>
  </tr>
  <tr>
    <td>SHOW reports <code>RTC Set: NO</code> or the error <code>RTC Time Invalid</code> (firmware 1.3 and later), or timestamps are in the year 2000</td>
    <td>The clock lost its time while unpowered. Replace the backup battery and set the clock. In firmware 1.3 and later the status light shows a red single blink until the clock is set.</td>
  </tr>
  <tr>
    <td>Green or yellow single blink; no data files</td>
    <td>No microSD card detected. Install a card.</td>
  </tr>
  <tr>
    <td>Red double blink with <code>SD Mount Failed</code> or <code>File Open Failed</code></td>
    <td>Check the card is seated and formatted FAT32. Try another card.</td>
  </tr>
  <tr>
    <td>Red double blink with <code>SD Write Failed</code> (firmware 1.3 and later)</td>
    <td>Readings could not be written to the card and are not being saved. Copy data off, and clear, reformat, or replace the card.</td>
  </tr>
  <tr>
    <td>Red double blink with <code>Storage Full</code> (firmware 1.3 and later), or SD status <code>FULL / BLOCKED</code></td>
    <td>5 MB or less remains on the card. Copy data off and clear or replace the card; a full card cannot store new readings.</td>
  </tr>
  <tr>
    <td>Red single blink with <code>Storage Nearly Full</code> (firmware 1.3 and later), or SD status <code>NEAR FULL</code></td>
    <td>50 MB or less remains; readings are still being logged. Copy data off and clear or replace the card before it fills.</td>
  </tr>
  <tr>
    <td>Short red and yellow flashes that persist</td>
    <td>A card is installed but writes are not being confirmed. In firmware 1.1 and 1.2 this is how a full or failing card appears. Check the SD status with SHOW. Copy data off, and clear, reformat, or replace the card.</td>
  </tr>
  <tr>
    <td>Red double blink with <code>RTC Error</code>, <code>Temperature Sensor Error</code>, <code>Input Voltage Sensor Error</code>, or <code>GPIO Initialization Failed</code></td>
    <td>A hardware check failed at startup. Remove power, wait, and reapply. If the error persists, contact support.</td>
  </tr>
  <tr>
    <td>Three green blinks at power-up that you did not cause</td>
    <td>The saved settings were invalid and defaults were restored. Check your settings and calibration coefficients with SHOW against your calibration report.</td>
  </tr>
  <tr>
    <td>Instrument stops logging on battery power</td>
    <td>The low-voltage cutoff may be active. Check the battery; logging resumes when the voltage reaches the reconnect voltage.</td>
  </tr>
  <tr>
    <td>Cannot find the <code>CONFIG</code> Wi-Fi network</td>
    <td>Confirm the light is solid blue. Configuration mode ends after 5 minutes; start it again.</td>
  </tr>
  <tr>
    <td>Tilt reads &pm;90&deg; or a constant value</td>
    <td>Check the calibration coefficients with SHOW against your calibration report.</td>
  </tr>
</table>

## Firmware Change Log
Changes that affect customers. Firmware 1.1 was the first customer release.

<table>
  <tr bgcolor="gray">
    <td><b>Version</b></td>
    <td><b>Changes</b></td>
  </tr>
  <tr>
    <td>1.3</td>
    <td>
      <ul>
        <li>SHOW, the data file header, and the settings page display calibration coefficients at full precision.</li>
        <li>Saving the settings page keeps calibration coefficients exactly.</li>
        <li>The tilt sensor type is reported as a model designation.</li>
        <li>A card that cannot be written to, or has 5 MB or less free, is now reported as an error (<code>SD Write Failed</code>, <code>Storage Full</code>) with a red double blink, instead of the red and yellow pattern.</li>
        <li>Calibration commands and the settings page reject a zero slope.</li>
        <li>If saved settings are found invalid at power-up, valid calibration coefficients are kept when defaults are restored.</li>
        <li>An unset clock is reported as the error <code>RTC Time Invalid</code> and shown by a red single blink, and the settings page rejects an invalid date or time.</li>
        <li>A card with 50 MB or less free is reported as <code>Storage Nearly Full</code> in <code>SHOW</code> and the live view, and shown by a red single blink.</li>
        <li>A failed or interrupted firmware upload is reported on the update page.</li>
        <li><code>SHOW</code> reports the yellow double blink and red and yellow patterns by their correct names.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>1.2</td>
    <td>
      <ul>
        <li>Added the READ command for on-demand readings.</li>
        <li>Added the CONFIG command to start Wi-Fi configuration mode over the serial port.</li>
        <li>The <code>0s</code> interval now means manual readings only, each written to the card immediately (1.1 sampled continuously).</li>
        <li>Saved settings are checked at startup; invalid settings are replaced with defaults.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>1.1</td>
    <td>
      <ul>
        <li>First customer release.</li>
        <li>Tilt is calculated with the arcsine conversion described in <a href="#how-readings-are-calculated">How Readings Are Calculated</a>.</li>
      </ul>
    </td>
  </tr>
</table>

## Dimensions
All dimensions in inches, for reference only. Leveling feet are M8&times;1.25.
The drawing shows the enclosure with the power hat (left) and with the M8
connector hat (right).

  <div style="text-align: center;">
    <img src="../dimensions.png" alt="Dimension drawing of the enclosure with the AA battery hat and with the M8 connector hat." style="height:500px;">
  </div>

## Revision History
<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>
  <tr>
    <td>September 2026</td>
    <td>Initial release.</td>
  </tr>
</table>
