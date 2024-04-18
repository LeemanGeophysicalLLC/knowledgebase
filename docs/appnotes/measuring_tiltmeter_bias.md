# Application Note: Measuring Tiltmeter Bias
While manufacturing your tiltmeter, we take great care to make all components to
tight tolerances. Even with this effort, alignment of the sensors internally,
mounting to the case, and slight manufacturing variations mean that all
tiltmeters do not read zero degrees when perfectly level. This error is referred
to as sensor bias. It is the difference between the true angle and the angle
your tilt meter indicates.

<center>
  <pre>
    Bias = Indicated Angle - True Angle
  </pre>
</center>

## Measuring Tilt Meter Bias
The bias of the tilt meter can be measured using a simple rotation technique.
The bias may change very slightly depending on the temperature at which it is
measured, so we recommend performing the bias measurement in conditions
representing the operating environment as possible.

1. If the instrument has leveling feet installed, screw them up or remove them
   such that the instrument rests on its base. If it is to be rigidly bolted to
   a burial plate, bracket, or other rigid joint, perform the measurement with
   this in place.

1. Put the instrument on a horizontal surface. A very level surface is ideal,
   but a surface that measures level with a 6 inch torpedo level is good
   enough.The surface should be smooth and free of divots or roughness. Make a
   mark on the surface referenced to a location on the tiltmeter you can use
   when rotating the instrument. Feet locations, a flat surface on the case, or
   any other reference will work.

1. Power on the instrument and allow the instrument to warm up. Electrolytic
   tilt meters should be left horizontal for 30 minutes or more to warm up and
   allow any electrolyte coating the walls of the sensor to drain. MEMS
   inclinometers should be left for 15 or more minutes.

1. Record the indicated tilt value (in degrees, microradians, or counts
   depending on your instrument) in the table below. You may wish to record
   several readings and average them.

1. Rotate the instrument 180 degrees on the flat surface. Try to keep it in the
   same footprint on the surface. You may need to extend your reference mark or
   remark it using a square to get a good 180 degree reference. Be careful not
   to tip electrolytic instruments too much or they may need a settling period
   for the electrolyte to drain from the sensor side walls.

1. Record the indicated tilt value (in degrees, microradians, or counts
   depending on your instrument) in the table below.You may wish to record
   several readings and average them.

1. Repeat the procedure for the second axis of the instrument (if applicable).

1. Calculate the bias correction and record it in the table.

<table>

  <tr bgcolor="gray">
    <td></td>
    <td width="200px" style="text-align: center"><b>X Axis</b></td>
    <td width="200px" style="text-align: center"><b>Y Axis</b></td>
  </tr>

  <tr>
    <td bgcolor="gray"><b>Reading in Orientation 1</b></td>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td bgcolor="gray"><b>Reading in Orientation 2</b></td>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td bgcolor="gray"><b>Bias = (Reading 1 + Reading 2) / 2</b></td>
    <td></td>
    <td></td>
  </tr>
</table>

## Applying the Bias Correction
If you wish to correct data from your tiltmeter to the absolute angle relative
to gravity instead of looking for relative changes, you need to apply the bias
correction to the raw data. By rearranging the formula that defines bias we can
see that to get the true angle we must add the bias to the indicated angle
recorded by the instrument.

<center>
  <pre>
    True Angle = Indicated Angle - Bias
  </pre>
</center>

The bias can be applied in any unit - some instruments indicate degrees,
microradians, or counts depending upon the model. The only important thing is
that the measurements of the bias and the measurements being corrected are all
of the same unit.
