# Displacement Calibration Apparatus
  <div style="text-align: center;">
    <img src="../product.png" alt="Instrument cover photo." style="height: 300px;">
  </div>

This documentation covers part number <a href="https://leemangeophysical.com/product/displacement-transducer-calibration-system/" target="_blank" rel="noopener noreferrer">10-0000027</a>


## Overview
The displacement calibration rig makes it easy to accurately calibrate
lineartransducers with a total range of up to two inches. With proper setup it
allows for repeatable calibration in just a few minutes. The calibration
software automatically creates the calibration curve and a data file with every
calibration point.

## Setup
The displacement calibration rig is a sensitive instrument that requires
alignment after shipping and periodically before use. The tools required to
calibrate the device are included with the kit.
  <center>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/NtjN4-EOunA?si=mLN9Re8VEQxInxQp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </center>

## Alignment Process
The alignment process of the displacement apparatus involves aligning the
digital indicator on the base to be exactly perpendicular to the stage. Without
correct alignment, calibration of the DCDTs will not be accurate due to cosine
error. Typically misalignment showing greater than 0.002” will need to be
corrected.   

<b>Tools Needed:</b>
<ul>
  <li>0.5” and 1.0” Gauge Blocks</li>
  <li>1.27mm Hex Key</li>
</ul>

<ol>
  <li>
    Adjust the stage so that it is a small amount behind center using the
    adjustment screw, then zero the readout on the digital indicator.
  </li>

  <li>
    Gently pull back the quill and place the 0.5” gauge block as shown. Make sure
    the surfaces of the block are clean.
    <div style="text-align: center;">
      <img src="../Astep2Image.png" alt="Setting Gauge Block." style="height: 300px;">
    </div>
  </li>

  <li>
    Note the measurement shown on the readout. In the image above the block is
    measuring at 0.501”, which is higher than its actual width.
  </li>

  <li>
    Repeat steps 2 and 3 with the 1” gauge block. If the readings are different
    than expected alignment is necessary. Typically the alignment is acceptable
    if the error is roughly 0.001”, and alignment is necessary if it is greater
    than 0.005”.
  </li>

  <li>
    For minor misalignments (&lt;0.003”) often the quill at the top of the indicator
    can be tapped gently to realign it. If this doesn’t work, further alignment is
    necessary. This can be accomplished by slightly loosening the screws on the
    bottom of the plate that hold the indicator with a hex key and gently
    rotating it. This is usually made easier by leaving one screw tight, and
    barely loosening the others.
    <div style="text-align: center;">
      <img src="../Astep5image.png" alt="Realignment" style="height: 300px;">
    </div>
  </li>
</ol>

<ul>
  <li>Checking alignment involves repeating steps 1-4 of the process each time the alignment is changed. The goal of the alignment is to have each gauge block measure as their calibrated length on the indicator. (0.5” block measures as 0.5000”, and 1.0” block as 1.0000”) but an error of ±0.002” is typically acceptable.</li>
  <li>Once the correct alignment is achieved the screws can be tightened. After tightening the screws, check the alignment again to make sure it hasn’t moved.</li>
</ul>

## DCDT Calibration
A video of this process is available on our website or here.
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/iZCyS38wjKE?si=B7F-TkoeCBiC43oz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

<ol>
  <li>
    Place the DCDT in the holder so that a small amount of the DCDT is protruding
    from the front. (This can vary depending on the model.) Then gently tighten
    the thumbscrews on top to hold it in place.
    <div style="text-align: center;">
      <img src="../Bstep1image.png" alt="Inserting DCDT" style="height: 300px;">
    </div>
  </li>

  <li>
    Take the included core nuts and install them onto the DCDT core. The larger
    nut should be installed onto the core with the flange facing backwards. The
    core can then be put through the hole in the core plate on the slider. Screw
    on the second nut loosely so that the core can still move.
    <div style="text-align: center;">
      <img src="../Bstep2image.png" alt="Installing DCDT Core" style="height: 300px;">
    </div>
  </li>

  <li>
    Move the carriage so that the core slides into the DCDT. Once inserted the
    core nuts can be tightened. This ensures the core is properly aligned.
    <div style="text-align: center;">
      <img src="../Bstep3image.png" alt="Inserting DCDT Core" style="height: 300px;">
    </div>
  </li>

  <li>
    Using the adjustment screw, move the stage so that it is centered on its base
    and the edges are flush. Zero the indicator by pressing the zero button.
    <div style="text-align: center;">
      <img src="../Bstep4image.png" alt="Zeroing the Device" style="height: 300px;">
    </div>
  </li>

  <li>
    Apply power to the transducer and connect it to the computer via your data
    acquisition system.
  </li>

  <li>
    Using the calibration software, name the transducer and specify the units it
    will be calibrated in. (The supplied unit displays in inches, so this will be
    the unit.)
    <div style="text-align: center;">
      <img src="../Bstep6image.png" alt="Transducer Setup" style="height: 300px;">
    </div>
  </li>

  <li>
    Select the input channel that the transducer is on by selecting Browse in the
    input channel menu.
    <div style="text-align: center;">
      <img src="../Bstep7image.png" alt="Select the input channel" style="height: 300px;">
    </div>
  </li>

  <li>
    Select the sampling rate of the system. If the system is capable of 10,0000
    samples/second this is best, but lower sampling rates will also work. Next,
    select the seconds to average. One second is typically acceptable, but in
    systems with significant noise, higher averaging times may be beneficial.
  </li>

  <li>
    Once all sampling parameters have been set, select Start in the calibration
    menu. Move the transducer core on the carriage until the voltage displayed on
    the screen is close to zero (±100 mV), then secure the carriage by tightening
    the knob on its side. This centers the core in the transducer.
  </li>

  <li>
    Begin calibration by adjusting the stage until the indicator reads near one
    of the extremes of the transducer range. (For a 1” transducer this will be
    ±0.5”). This instrument is capable of calibrating transducers with a total
    range up to 2”.
  </li>

  <li>
    To begin recording, keep the mouse cursor in the “Calibration Points” box on
    the screen and press the button on the cable connecting the indicator to the
    computer. This should cause a point to appear on the graph.
    <div style="text-align: center;">
      <img src="../Bstep11image.png" alt="Begin Recording" style="height: 300px;">
    </div>
    To complete the calibration curve, rotate the adjustment screw on the stage a
    couple of turns in the desired direction and press the button to record
    again. Repeat this process until the entire range of the transducer has been
    recorded. This will create the calibration curve. Moving the same displacement
    with each measurement isn’t necessary because the displacement is precisely
    recorded by the digital indicator. Complete the calibration by repeating the
    process in reverse to fill out the plot.
    <div style="text-align: center;">
      <img src="../B2step11image.png" alt="Complete Calibration Curve" style="height: 300px;">
    </div>
  </li>

  <li>
    When the calibration curve is complete, select the Complete button in the
    calibration menu, then click Save and choose the save location of the file.
    You can then open the calibration file using Notepad. This will display the
    parameters of the calibration and the calibration points.
    <div style="text-align: center;">
      <img src="../Bstep12image.png" alt="Complete Calibration Curve" style="height: 300px;">
    </div>
  </li>
</ol>

## Revision History
<table>

  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>

  <tr>
    <td>May 2025</td>
    <td>Fixed new image display issue with MkDocs</td>
  </tr>

  <tr>
    <td>September 2024</td>
    <td>Initial Release</td>
  </tr>

</table>