# 3D Compass Kit
<center>
![Instrument cover photo.](product.png){: style="height:300px"}
</center>

This documentation covers part number <a
href="https://leemangeophysical.com/product/3d-compass-kit/"
target="_blank" rel="noopener noreferrer">10-0000031</a>.

## Overview
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/iJughN5KhfI?si=JTtONQ5zNE1sD1Py" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>
The 3D Compass Kit is an innovative educational tool that brings the Earth’s magnetic field to life in three dimensions. Powered by an Arduino microcontroller and vibrant Neopixel LEDs, this kit allows you to visually explore not only the directional north but also the vertical components of the Earth’s magnetic field. Whether you’re using it in a classroom or as a fun desk toy, the 3D Compass Kit offers an engaging hands-on experience that makes learning about geomagnetism exciting and accessible.

Ideal for students and hobbyists alike, this kit also lets you experiment with
the magnetic fields of everyday objects using additional magnets. Complete with
an educational lab activity, it’s perfect for enhancing STEM education by
combining physics, earth science, and more in one engaging package.

### What's in the box
Upon receipt of your unit, unpack the contents of the box and inspect all parts
for any damage incurred during shipping. Immediately report any missing parts or
damage to Leeman Geophysical for replacement.  

* Laser cut acrylic panels
* Aluminum standoffs
* Nylon screws
* Sparkfun RedBoard (Arduino)
* Circuit Board with LEDs and Magnetometer

## Operation
### Tools Required
* Philips Screwdriver
* Super Glue (optional)

### Parts List
* Base Panel (1x)
* Top Panel (1x)
* Red Board (1x)
* LED+Magnetometer Board (1x)
* Aluminum Standoffs (7x)
* M3 x 6mm Nylon Screws (9x)
* M3 x 12mm Nylon Screws (4x)
* Acrylic Bracket (x1)

### Assembly
<b>NOTE: Be gentle tightening screws as the screws and plates are plastic and
are easily stripped. Just snug the screws so that nothing is loose.</b>

1. Remove and inventory the contents of your kit - make sure you received all
   parts of the kit and that they are undamaged.

1. Place the bottom plate flat on the table and align the holes in the Arduino
   Red Board to the holes in the plate. Secure the Red Board with the provided
   plastic screws.
<center>
![Assembly Step 1](assembly1.png){: style="height:300px"}
</center>

1. Screw in four of the aluminum standoffs into the corner holes of the bottom
   plate on the same side as the Red Board.
<center>
![Assembly Step 2](assembly2.png){: style="height:300px"}
</center>

1. Place the top plate onto the standoffs as shown - note the offset of the slot
   on the right side of center.
<center>
![Assembly Step 3](assembly3.png){: style="height:300px"}
</center>

1. Secure the top plate with the four longest 12mm plastic screws.
<center>
![Assembly Step 4](assembly4.png){: style="height:300px"}
</center>

1. Screw in three standoffs into the holes in the top plate.
<center>
![Assembly Step 5](assembly5.png){: style="height:300px"}
</center>

1. Bend the inner circuit board so that it is perpendicular to the outer ring.
   Attach the clear bracket to the back of the small circular circuit board with
   two 6mm plastic screws.  

<b>NOTE: Exercise caution when bending the board into place, as to not break any
of the wire connections.</b>
<center>
![Assembly Step 6](assembly6.png){: style="height:300px"}
</center>

1. Attach the circuit board to the standoffs with three 6mm plastic screws.
<center>
![Assembly Step 7](assembly7.png){: style="height:300px"}
</center>

1. With the small circular board and bracket perpendicular to the large circle,
   Insert the clear tab of the bracket into the slot on the top plate. You can
   secure this connection with superglue if preferred, or you may leave it loose
   for future disassembly.
<center>
![Assembly Step 8](assembly8.png){: style="height:300px"}
</center>
<center>
![Assembly Step 9](assembly9.png){: style="height:300px"}
</center>

1. Run the wires from the back of the circuit board through the holes in the top
   plate as shown. In this orientation the red, black and orange wires will go
   through the left slot, and the blue, white and yellow wires will feed through
   the right slot.

1. Plug the wires into the Arduino Red Board as indicated below. Double check
these connections before turning on the unit as incorrect connections may damage
the unit and are not covered as a manufacturer’s defect! <b>NOTE: Given the
confined work space, A pair of needle nose pliers or tweezers may help to plug
in the connections.</b>
<table>
  <tr bgcolor="gray">
    <td><b>Wire Color</b></td>
    <td><b>Arduino Connection</b></td>
  </tr>
  <tr>
    <td>Red</td>
    <td>5V</td>
  </tr>
  <tr>
    <td>Orange</td>
    <td>3.3V</td>
  </tr>
  <tr>
    <td>Black</td>
    <td>GND</td>
  </tr>
  <tr>
    <td>White</td>
    <td>13</td>
  </tr>
  <tr>
    <td>Yellow</td>
    <td>SCL</td>
  </tr>
  <tr>
    <td>Blue</td>
    <td>SDA</td>
  </tr>
</table>
<b>There are multiple places in which ground wire can be connected, all will work. Plugging the black GND wire into the GND connection closest to the VIN pin on the left is easiest.</b>

1. After double checking the connections again, plug in the mini B USB cable and
   power adapter. Follow the use instructions.

### Using the 3D Compass
The 3D compass is powered by a USB plug, so any computer, USB charger, or even
USB battery pack can be used to power the device. As soon as the unit receives
power, the large ring will begin to light up green. This is the calibration
procedure of the compass to compensate for any magnetic materials in the area
and is done each time the unit is turned on. During this time rotate the compass
and tilt it in all directions. Be sure to get upside down too! Once the ring is
completely green, the calibration is complete. The rings will then turn blue and
red. If the compass is inaccurate try moving further from magnetic interference
and recalibrating the compass. Recalibration can be done by pressing the reset
button on the Red Board or by unplugging and replugging the USB cable.

The leds turn from blue to red as they get closer to the direction of the
magnetic field vector. The large ring indicates the direction of north while the
smaller ring shows how much the magnetic field is dipping at your location. Be
sure to check out the maps of magnetic dip and see how your readings compare!

If you plug the compass into a computer you might notice the green led
calibration process restart a couple of times while the computer is opening a
serial connection to the compass. You can use a program like the Arduino IDE
(freely downloaded from the Arduino.cc website) to open a serial monitor and
view the data from the magnetometer! The data returned are the x, y, z,
components of the magnetic field followed by the estimated azimuth and dip of
the magnetic field. The serial connection uses the following parameters:

* Baud: 115200
* Data Bits: 8
* Parity: None
* Stop Bits: 1

### Serial Data Output
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/YmWsDpi6fkA?si=gtbciKoJMhUOdzMu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

## Teachers Guide
### Lab Activity
* <a href="https://docs.google.com/document/d/11WL_dLieHmjVp8e9vElReFWHcICVVR45H1unIoNnP1c/edit?usp=drive_link" target="_blank" rel="noopener noreferrer">Lab Activity</a>

## Revision History
<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>
  <tr>
    <td>October 2024</td>
    <td>Moved documentation to MkDocs format</td>
  </tr>
</table>