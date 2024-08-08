# SMPL BNC Breakout
<center>
![Instrument cover photo.](product.png){: style="height:300px"}
</center>

This documentation covers The following part number:  

<a href="https://leemangeophysical.com/product/smpl-bnc-connector-breakout/" target="_blank" rel="noopener noreferrer">7-0000179</a>

## Overview
BNC cables are the duct tape of the low frequency signal world. They are one of
the most common connectors found in ADC systems. The SMPL BNC Breakout makes it
easy to connect ANY 4 pin SMPL connector to anything else in the world with a
BNC connector. This breakout features a plastic shelled BNC to keep the
connector isolated from a metal enclosure and solder jumpers to allow you to
connect any of the 4 SMPL pins to either the inner or outer contacts of the BNC.
Want to connect more than 1 SMPL pin? No problem, just close multiple jumpers!

### What's in the Box
Upon receipt of your unit, unpack the contents of the box and inspect all parts
for any damage incurred during shipping. Immediately report any missing parts or
damage to Leeman Geophysical for replacement.  

* SMPL BNC Breakout PCB Assembly

### Tool Requirements
* Soldering Iron  

* Solder  

## Configuration 
There are a total 8 solder jumpers on the PCB assembly. These jumpers are found
in 2 rows and 4 columns where the columns **(A-D)** correspond to the pins of
the SMPL push connector, and the rows **I** and **O** relate to the 2
connections of the BNC connector. The **I** jumpers connect to the center pin of
the BNC, and the **O** jumpers connector to the outer sleeve. The grid of
jumpers formed by the rows and columns describe which two pins will be connected
when a jumper is soldered closed. This connector assembly remains isolated from
the panel in which it is mounted via the plastic housing of the connector. If it
is desired to connect the outer sleeve of the BNC to the panel, you can solder a
wire to the small through hole connection located at the top left of the jumper
array, and connect it to the other end to the panel with your chosen method.

<center>
![PCB Render Front.](pcbrender.png){: style="height:350px"}
</center>

### Panel Cutout
<center>
![Panel Cutout](bncpanelcutout.png){: style="height:350px"}
</center>

## Revisions
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
