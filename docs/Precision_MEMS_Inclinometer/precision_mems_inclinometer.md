# Precision MEMS Inclinometer
<center>
![Instrument cover photo.](product.png){: style="height:250px"}
</center>
This documentation covers part number [10-0000042](https://leemangeophysical.com/product/mems-inclinometer/).

## Overview
The precision MEMS inclinometer is the most advanced non-electrolytic tilt
sensing device available to the geophysical market. This device with an
approximate resolution of 0.00179&deg; is accurate enough for many sensitive
geophysical applications, but operates over a large tilt range of &pm;30&deg;.
This broad range of operation makes deployment and leveling much faster than
more precise tilt meters. The differential MEMS technology also means the device
is lower cost, making it semi-disposable in harsh environments. The inclinometer
has a built-in data logger and well as RS232 output, user configurable
parameters, factory calibration, real-time clock, magnetometer, grounding
points, and more! The unit is IP67 rated, so deployment outdoors is as simple as
plugging in the weather-tight connector and leveling the unit.

### Enclosure and Components
The inclinometer is housed in a precision machined and anodized Aluminum
enclosure. There are three leveling feet with 1/4"-28 thread that allow the
inclinometer to be placed on a surface and leveled or mounted to a mounting
plate. The lid to the device is held in place with three thumbscrews and seals
to the top of the enclosure with a rubber O-ring. On the rear of the enclosure
there is a flat surface against which a field compass can be placed to measure
the orientation of the inclinometer. On top of this flat are two \#4-40
threaded holes that allow the attachment of a ground wire if desired.
Replacement O-rings and hardware are available for order by contacting Leeman
Geophysical LLC or via our website.

### Inner Panel
The inner panel of the unit provides visual feedback and component access to the
user. There are four user accessible components. The battery holder accommodates
one CR-2032 battery which provides power to the real time clock to maintain the
date and time while the unit is powered off. The microSD card cage allows
installation and removal of a microSD card storage media for in-unit logging.
Finally, there are two indicator lights (red and green) that provide visual
feedback. The red light is used to indicate errors and the green light indicates
when a reading is being written to the SD card and/or sent via the serial
interface.

<center>
![Inner panel layout with the enclosure lid removed.](top_view.png){: style="height:250px"}
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
    <td>4.75</td>
    <td>12</td>
    <td>32</td>
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
    <td>375</td>
    <td>-</td>
    <td>g</td>
  </tr>

  <tr>
    <td>Width</td>
    <td>-</td>
    <td>94</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Length</td>
    <td>-</td>
    <td>97.5</td>
    <td>-</td>
    <td>mm</td>
  </tr>

  <tr>
    <td>Height</td>
    <td>-</td>
    <td>39.7</td>
    <td>-</td>
    <td>mm</td>
  </tr>
</table>

## Installation
Always consult local codes, guidelines, and professional guidance for installation.

### Connector Wiring

The only external connector on the unit is the 4-pin Nano M8 connector. This connector provides power, ground, and RS-232
communications with the instrument. Mating cables, adapters, and more are available from Leeman Geophysical LLC.

| Wire Color | M8 Pin | Description                         |
|------------|--------|-------------------------------------|
| Brown      | 1      | Power                               |
| White      | 2      | RS-232 RX to instrument from device |
| Blue       | 3      | Ground                              |
| Black      | 4      | RS-232 TX from instrument to device |

### Backup Clock Battery Installation/Removal
1. Remove power from the unit.

1. Remove the three thumb screws securing the lid to the enclosure and remove
   the lid.

1. Gently remove the old CR2032 battery by holding down on the white plastic of
the battery clip and lifting the underside edge of the battery. Do not exert
excessive force or the battery clip and/or circuit board may be damaged!

1. Install the new CR2032 battery by sliding the battery into the clip and
   gently pressing lock it in.

1. Reinstall the lid, ensuring that the O-ring gasket is properly seated.
   Tighten the three thumbscrews in an equal manner until finger tight.

1. Reapply power and set the correct clock time.

### SD Card Installation/Removal

1. Remove power from the unit.

1. Remove the three thumb screws securing the lid to the enclosure and remove
   the lid.

1. Pull the top of the card card towards the rear of the unit, it will move
   several millimeters, then stop.

1. Hinge the card card up from the back of the unit towards the center.

1. Remove/install a microSD card into the clip of the hinged part of the cage.

1. Fold the cage back down and gently press towards the center of the unit,
   clipping the cage into place.

1. If desired, power the inclinometer and verify operation of the unit.

1. Reinstall the lid, ensuring that the O-ring gasket is properly seated.
   Tighten the three thumbscrews in an equal manner until finger tight.


## Operation
### Coordinate System

<center>
![Coordinate system and sign for the magnetometer and inclination measurements.](axes.png){: style="height:350px"}
</center>

The tilt coordinate system is right-handed with the x-axis parallel to the flat
along the back of the instrument and the y-axis perpendicular to the flat
pointing towards the front foot. Tilts clockwise around the y-axis as viewed
from the back of the instrument result in a positive x tilt reading. Tilts
clockwise around the x-axis as viewed from the connector side of the instrument
result in a positive y tilt reading. The on-board magnetometer has a coordinate
system with z projecting upward out of the lid of the instrument. x and y are
parallel with the instrument x and y plane.

### Power Consumption and Warm-up
In an effort to reduce power consumption as much as possible, the instrument
will put all sensors to sleep when no readings are scheduled to be taken for 60
seconds. When a reading is scheduled within 60 seconds, the instruments will be
put into active mode. Instruments remain in active mode when the data rate
divisor is set to 0 such that a reading can be commanded at any time.

Empirical tests indicate that the sensors do experience some drift as they warm
up, hence the implementation of the 60 second warm up program. If your
application requires different warm up or power parameters, contact us to
discuss custom firmware modifications for your environment.

### Serial Menu
The serial menu allows a few basic parameters to be set by the user from a
serial terminal program. The serial menu operates at the user-set baud rate.
Unlike other units, this unit does not have in-menu help to reduce code space
and power consumption. Each command should be entered followed by a newline
character.

| Command                  | Description                                          |
|--------------------------|------------------------------------------------------|
| SB *XXXX*                | Set baud rate (1200, 2400, 4800, 9600, 19200)        |
| ST *YYYY MM DD HH MM SS* | Set the time                                         |
| SR                       | Set the data rate divisor (0-3600)                   |
| R                        | Force a manual read of the instrument                |
| S                        | Show the current device settings                     |
| SN *XXX*                 | Set the number of data points to be averaged (1-255) |

* **SB** sets the baud rate of the device to any valid baud rate in the list
1200, 2400, 4800, 9600, or 19200 baud. This setting is persistent through power
cycles.

* **ST** sets the current time when the newline character is received. For
example to set March 26, 2020 at 13:05:30 the command *ST 2020 03 26 13 05 30*
would be sent. This setting is time zone independent, but we always
recommend collecting data in UTC. After setting the time, a power off reset is
recommended as a way to verify the integrity of the clock backup battery.

* **SR** sets the data rate divisor in the range 0-3600 seconds. When the
  current Unix second is divisible by this divisor a reading will be taken.
  Setting the divisor to 0 means no readings will be taken and a *R*
  command must be issued to read. Recommended settings are those divisible into
  3600 seconds (1 hour) evenly. Common settings are 1, 5, 30, 60, 300, 900,
  1800, and 3600.

* **R** forces a manual read of the sensors as soon as the command is issued.
This is commonly used in externally triggered systems with the data rate divisor
set to 0, but can also be used with non-zero data rate divisors for triggering
readings between timed readings, such as event based triggering.

* **S** shows the current system settings in the terminal.

* **SN** sets the number of readings to average together in the range 1-255.
Averaging more readings takes longer, so generally is not suitable for faster
data rates - a lag will be observed.

### Deployment
Every deployment is different, but this procedure seeks to provide a guideline
of best practices for deploying the precision MEMS inclinometer. Contact your
applications representative for guidance on your specific application.

1. Connect the unit to a computer with a programming cable (preferably prior to
going to the field) and configure the desired settings. \item Ensure the time
setting is correct and the coin cell backup battery is installed. (We recommend
a yearly change if the unit is in storage.)

1. If data are to be logged internally, ensure there is a microSD card (FAT16
   formatted) with adequate space installed in the card cage.

1. In the field choose the deployment site and mounting strategy. Set the unit
on a firm, flat surface, bolt it to a mounting plate, or otherwise secure it.
Always consider siting on the unit to be out of the low flooding area,
inconspicuous, and away from large tilt inducers such as trees.

1. Level the unit as nearly as feasible. The more level the unit is, the more
operation will be in the linear band and the less likely a tilt corrected
analysis strategy will need to be used for the magnetometer data. The
inclinometer itself can be used for leveling when the data are viewed on a
computer or a precision circular bubble level, available from Leeman
Geophysical, can be used for quick and easy leveling.

1. Connect the power/data cable. Apply power and verify that the unit is
logging. The unit will always log a data point on startup, so powering up with
the lid removed should result in a green flash as the first data point is
recorded. Any red lights indicate an error and should be addressed.

1. Seal the unit with the provided O-ring and lid, being careful to only finger
   tighten the screws.


### Error Codes
Error codes are flashed on the red LED under the lid and printed to the serial
terminal. Some errors which would result in incomplete data will continually
restart the unit in an effort to fix the problem, while others will warn once
and then continue operation.

| Error Code | Description                                                                                                                              |
|------------|------------------------------------------------------------------------------------------------------------------------------------------|
| 1          | Magnetometer error - unit will restart in an attempt to fix the issue.                                                                   |
| 2          | Temperature error - unit will restart in an attempt to fix the issue.                                                                    |
| 3          | SD error - warns once, then continues operation. This allows for external logging without the requirement of an SD card being installed. |
| 4          | Clock error - unit will restart in an attempt to fix the issue.                                                                          |

### Filename Convention
Data are stored on the microSD card (if installed) in 24-hour files. Each file
is named with the year, month, and date of the data it contains in a 8.3 format.
If a file with that filename already exists on the microSD card, the new data
will be appended to the end of the file.

<code>
YYYYMMDD.TXT
</code>

## Calibration
Each unit is calibrated at the factory before leaving the facility and the
calibrations stored in the unit. Full calibration data is also provided with
each unit to allow user applied corrections to be made to the data as necessary.

### Tilt Calibration
Tilt calibrations may be performed on any stage in which tilt is retrained to
one axis and is known precisely. The device under test is subjected to a range
of tilts in the operating range of interest and the raw values from the sensors
recorded and used to determine a calibration factor. Tilts are the most accurate
and linear in the $\pm3^\circ$ range, acceptable in the $\pm30^\circ$ range, and
often need non-linear corrections beyond that range.

### Temperature Compensation
Temperature may effect the scale and offset of the tilt sensor calibration.
While differential MEMS technology is not as prone to large temperature
sensitivity offsets, they are observable. Factory provided temperature data may
be used, or more often, a field calibration is determined by cross plotting
temperature and tilt as this also corrects for thermal expansion of the mounting
surface. This method may be undesirable if the temperature induced tilt is to be
part of the study.

### Cross-Axis Calibration
Cross axis errors (detailed later) may be accounted for by tilting the
instrument only in one axis and observing any tilt signal on the other axis. A
correction may then be applied in the form of a linear correction or coordinate
rotation as necessary.

### Magnetometer Offsets
Magnetometer offsets are of the hard-iron and soft-iron variety. An ideal
magnetometer, if spun in every axis, would create an x, y, z point cloud that is
a sphere, centered at the origin, with a radius with a magnitude equal to that
of the Earth's magnetic field. The offset from the origin is called the
hard-iron offset and must be corrected for the data to be useful. The degree to
which the sphere varies from a perfect sphere is the soft-iron offset and may be
corrected for precision applications as outlined in application notes. The
factory determined hard-iron offset is applied in the instrument, but we
recommend collecting calibration data at each deployment site in case other
corrections need to be applied in post-processing.

## Data Interpretation
Data are recorded on the microSD card and output through the RS-232 system with
identical formats. Custom formats may be created for your application upon
request. Data are tab delimited and decoded as follows.

<code>
477941	1	2000/01/01T00:08:27	2331	1302	452	2330558	80908	-8420	4714	-4011
</code>

| 477941              | 1    | 2000/01/01T00:08:27 | 2331        | 1302          |
|---------------------|------|---------------------|-------------|---------------|
| Millisecond Counter | NAVG | Time stamp          | Temperature | X Tilt Counts |

| 452           | 2330558 | 80908  | -8420                 | 4714                  | -4011
|---------------|---------|--------|-----------------------|-----------------------|-----------------------|
| Y Tilt Counts | X Tilt  | Y Tilt | X Magnetometer Counts | Y Magnetometer Counts | Z Magnetometer Counts |


* **Millisecond Counter** - Milliseconds since power was applied to the
  processor in the instrument. This number will overflow (reset to zero) after
  approximately 50 days.

* **NAVG** - How many tilt readings were averaged in this sample.

* **Time stamp** - Time the reading of the sensors began for this entry.

* **Temperature** - Temperature of the unit in degrees Celsius multiplied by
  100.

* **X Tilt Counts** - Raw 16-bit value of the x tilt sensor. Often used when
  applying a custom calibration in post processing.

* **Y Tilt Counts** - Raw 16-bit value of the y tilt sensor. Often used when
  applying a custom calibration in post processing.

* **X Tilt** - Small angle x tilt calibrated to degrees multiplied by 100000.
Calibration provided by factory is applied and valid for small tilts.

* **Y Tilt** - Small angle y tilt calibrated to degrees multiplied by 100000.
  Calibration provided by factory is applied and valid for small tilts.

* **X Magnetometer Counts** - Raw 16-bit value of the magnetometer x axis
sensor. Generally these values are just used as counts as calibration to Gauss
is not needed for orientation information. Hard iron offset (set at the factory)
is applied to this reading.

* **Y Magnetometer Counts** - Raw 16-bit value of the magnetometer y axis
sensor. Generally these values are just used as counts as calibration to Gauss
is not needed for orientation information. Hard iron offset (set at the factory)
is applied to this reading.

* **Z Magnetometer Counts** - Raw 16-bit value of the magnetometer z axis
sensor. Generally these values are just used as counts as calibration to Gauss
is not needed for orientation information. Hard iron offset (set at the factory)
is applied to this reading.


### Tilt Interpretation
Tilt can be subject to many technical factors as well as the environmental tilt.
Leeman Geophysical has application notes on many of these topics and can assist
you in determining which factors may need to be accounted for in your data. The
list below is intended to help plan your field deployment strategy and guide
your analysis. For most analyses under $\pm30^\circ$ the factory calibration,
applied in the instrument, is all that is required.

* **Temperature Scale Factor** - Temperature can modify the calibration of the
tilt sensors making them slightly more or less sensitive. This factor is
generally very small in our differential MEMS instrument and often neglected.

* **Temperature Offset Factor**  - Temperature can change the zero point of the
tilt sensor, often observed as several to tens of thousandths of a degree for
small environmental temperature changes. Often this factor is corrected combined
with temperature induced deformation.

* **Temperature Induced Deformation** - Changes in temperature can result in the expansion and
contraction of the instrument enclosure, feet, mounting surface, or object under
study. This effect is difficult to distinguish from temperature offset factor
corrections and both are generally done at once by observing the correlation
between temperature and tilt.

* **Cross-Axis Tilt** - Imperfections in how the tilt sensing elements are
mounted relative to each other and to the enclosure can result in cross-talk
between the axes. This small correction can be applied via coordinate system
rotations if necessary.

* **Off-Axis Tilt** - Tilts on one axis, especially large tilts, can incline the
other axis sensor from the horizontal plane resulting in offsets. These are
generally treated as cross-axis tilt errors as they are indistinguishable in the
data, but arise from a different mechanism.

* **Mounting Error** - Mounting the instrument to a surface which is not stable
  will result in tilt readings not resulting from the process under study.

### Orientation Interpretation
The magnetometer in the instrument has a hard-iron correction applied to offset
the errors resulting from the instrument itself. Environmental factors, metal,
and nearby power wiring can result in further offsets or in soft-iron
corrections. For more information on these corrects, see our application notes
or contact support. We recommend collecting a set of magnetometer calibration
data at deployment by setting the instrument to 1Hz logging and slowly rotating
it into all orientations, creating a sphere of magnetometer data points to be
use for correction determination.

Assuming a horizontal mounting of the instrument with minor tilts, orientation
of the instrument with respect to magnetic north is easy to calculate:

$$\text{azimuth} = \text{arctan}\frac{m_y}{m_x}$$


For applications with significant tilts, a tilt correction must be applied and
all three of the magnetometer's axes utilized. For more information on this
correction, see our application notes or contact support.

## Dimensions
![Dimension drawing of the instrument](dimensions.png)


## Revision History
| Revision | Date          | Changes                                                                 |
|----------|---------------|-------------------------------------------------------------------------|
| 1.0      | February 2022 | Initial Release                                                         |
| 1.1      | December 2023 | Update address and change inaccurate description of file output columns |