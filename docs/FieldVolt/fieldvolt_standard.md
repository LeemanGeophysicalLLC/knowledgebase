# FieldVolt Instrument Power Standard
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/dkdAbfvWnZs?si=eNKBI08BIgpFmHGY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

## Purpose
The FieldVolt instrument power standard was established in 2024 by Leeman
Geophysical LLC in collaboration with field practitioners in an effort to create
a standardized power interface for geophysical field equipment. Interoperability
in the field means reduced time building cables, looking up pinouts, improvising
solutions, and often damaging instruments. Anything with the FieldVolt logo by
the power port can be plugged into anything else with the FieldVolt logo using
cables with standard pinouts and work seamlessly.

## Connectors
### Manufacturer
Connectors in the FieldVolt ecosystem are Amphenol Industrial connectors. The
sealing method (potted, grommets, etc) is not determined by the standard as all
comply with the weatherproofing requirements of field equipment. 

### Nomenclature
Connectors are simply named and should be referred to/labeled as described below.

<b>IN</b> refers to connectors that are bringing power into a piece of equipment
from an external power source. For example, the power port on a datalogger is
labeled “IN”. The charging port on a portable battery box is labeled “IN”.

<b>OUT</b> refers to connectors that provide power to attached equipment. For
example, the output of a battery box is labeled “OUT”, as is the output of a
wall power supply or charger.

<b>Power Consumer</b> refers to the device (load) needing to be powered. This is
the attached instrument, actuator, etc.

<b>Power Provider</b> refers to the current source providing power to the power
consumer. This is a battery pack, wall plug, or other power source.

<b>Charging Source</b> refers to the device renewing the energy of the power
provider. This can be a device like a solar panel or wall powered charger.
Charging sources do not directly power the power consumer, but instead ensure
the continued maintenance of the power provider.

### Pin/Socket
Connectors with power output on them (i.e. connected to batteries, solar panels,
etc) are socket connections (female connectors) to help prevent accidental
shorting of connections. Connectors for power input have corresponding pins (male)
connectors.

## FieldVolt Logo and Name
The FieldVolt name shall be reproduced as shown in this document, as one word
with a capital F and V character. The Univers font shall be used for the name or
Roboto Condensed where Univers is not available. The logo for FieldVolt is
available for public download below. Versions of the logo including filled, circled,
and plain are provided and the one providing the most contrast on the surface it
is applied to should be used.

  <div style="text-align: center;">
    <img src="../fieldvolt_logo_examples.png" alt="Examples of the logo.">
  </div>

<a href="../fieldvolt_logo.svg" download>FieldVolt Logo</a>

<a href="../fieldvolt_logo_dark_Circle.svg" download>FieldVolt Logo in Dark Cricle</a>

<a href="../fieldvolt_logo_border.svg" download>FieldVolt Logo in Border</a>


## 12 VDC Field Power
12 volts DC (nominal) field power is the most common power source for
geophysical field equipment. Much of this equipment has low current requirements
as it is meant to be battery/solar operated for long periods of time and this
standard was designed with this in mind.

The 12 VDC standard provides the following assurances:  

<ul>
  <li>Be capable of providing 5A (peak) DC current at operating voltage</li>
  <li>Ensure 2% or less voltage drop over 5 meters of cable length at peak load</li>
  <li>Provide battery-safe charging (i.e. over/under voltage protection)</li>
  <li>Provide fused or otherwise current-protected outputs from power sources</li>
</ul>

Instruments connecting to 12 VDC field power should conform to the automotive industry
operating standards at minimum:  

<ul>
  <li>Operate down to 11 VDC or better</li>
  <li>Operate on 12 VDC nominal voltage</li>
  <li>Operate up to 14.3 VDC or better</li>
  <li>Tolerate a maximum continuous overvoltage of 16 VDC or better</li>
  <li>Tolerate a maximum dynamic overvoltage of 20 VDC or better</li>
</ul>


## Power Connectors
Instrument power connections use a 4-pin PT series Amphenol Industrial connector of
shell size 12. Common connectors and the pinout are listed below.

<table>
  <tr bgcolor="gray">
    <td><b>Pin</b></td>
    <td><b>Description</b></td>
  </tr>
  <tr>
    <td>A</td>
    <td>Positive</td>
  </tr>
  <tr>
    <td>B</td>
    <td>Not Connected</td>
  </tr>
  <tr>
    <td>C</td>
    <td>Negative</td>
  </tr>
  <tr>
    <td>D</td>
    <td>Not Connected</td>
  </tr>
</table>

<hr>
<b>Leeman Geo P/N:</b> 1-0001497  
<b>Amphenol P/N:</b> PT06E-12-4S(SR)  
<b>Description:</b> Wire connector that connects to a FieldVolt ready instrument power input.  
  <div style="text-align: center;">
    <img src="../PT06E-12-4S(SR).png" alt="PT06E-12-4S(SR)">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001496  
<b>Amphenol P/N:</b> PT06E-12-4P(SR)  
<b>Description:</b> Wire connector that connects to a FieldVolt power source power output.  
  <div style="text-align: center;">
    <img src="../PT06E-12-4P(SR).png" alt="PT06E-12-4P(SR)">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001495  
<b>Amphenol P/N:</b> PT02A-12-4S  
<b>Description:</b> Panel mounted connector that would be used as a FieldVolt power source power output.  
  <div style="text-align: center;">
    <img src="../PT02A-12-4S.png" alt="PT02A-12-4S">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001510  
<b>Amphenol P/N:</b> PT02A-12-4P  
<b>Description:</b> Panel mounted connector that would be used as a FieldVolt ready instrument power input.  
  <div style="text-align: center;">
    <img src="../PT02A-12-4P.png" alt="PT02A-12-4P">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001504  
<b>Amphenol P/N:</b> PT01E12-4S(SR)  
<b>Description:</b> Panel mounted connector that would be used as a FieldVolt ready instrument power input.  
  <div style="text-align: center;">
    <img src="../PT01E12-4S-SR.png" alt="PT01E12-4S-SR">
  </div>

## Charging Connectors
Charging connections use a 3-pin PT series Amphenol Industrial connector of
shell size 12. Common connectors and the pinout are listed below. This connector
is designed to power a charge controller inside the device to be charged. There
should also be a fuse or current limiting device immediately before the battery
to protect both systems.

<table>
  <tr bgcolor="gray">
    <td><b>Pin</b></td>
    <td><b>Description</b></td>
  </tr>
  <tr>
    <td>A</td>
    <td>Charge Controller Positive</td>
  </tr>
  <tr>
    <td>B</td>
    <td>Negative</td>
  </tr>
  <tr>
    <td>C</td>
    <td>Not Connected</td>
  </tr>
</table>

<hr>
<b>Leeman Geo P/N:</b> 1-0000963  
<b>Amphenol P/N:</b> PT06E-12-3S(SR)  
<b>Description:</b> Wire connector for charging source such as a solar panel, AC adapter, etc.  
  <div style="text-align: center;">
    <img src="../PT06E-12-3S(SR).png" alt="PT06E-12-3S(SR)">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001592  
<b>Amphenol P/N:</b> PT01E12-3P-SR  
<b>Description:</b> Wire connector for charging receiver such as solar charge controller.  
  <div style="text-align: center;">
    <img src="../PT01E12-3P-SR.png" alt="PT01E12-3P-SR">
  </div>

<hr>
<b>Leeman Geo P/N:</b> 1-0001494  
<b>Amphenol P/N:</b> PT02A-12-3P  
<b>Description:</b> Panel mounted connector to receive charging source.  
  <div style="text-align: center;">
    <img src="../PT02A-12-3P.png" alt="PT02A-12-3P">
  </div>

## Future
As the need for alternative voltage systems arises (high voltage DC downhole
systems for example), more connectors will be added to the standard. These
connectors shall not allow instruments which may be damaged by the different
voltages to be connected. Size, shell orientation, or other manufacturer
supported variations may be used to assure this. The connectors and standards
will not be established until deemed necessary in an effort to keep the standard
compact, easy to understand, and only containing necessary information.

## Revision History

<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Revision</b></td>
  </tr>
  <tr>
    <td>October 21 2024</td>
    <td>Add graphics and nomenclature clarifications</td>
  </tr>
  <tr>
    <td>September 2024</td>
    <td>Added Video Overview</td>
  </tr>
  <tr>
    <td>March 2024</td>
    <td>Initial Release</td>
  </tr>
</table>
