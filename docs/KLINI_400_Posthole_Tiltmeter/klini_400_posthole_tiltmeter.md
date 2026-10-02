# KLINI 400 Posthole Tiltmeter

This documentation covers the **KLINI 400 Posthole Tiltmeter**, a KLINI 400
(1 &micro;rad-and-finer resolution class) two-axis instrument built for
posthole/borehole deployment. The case currently shipping is **2" OD,
approximately 34" long**; additional case variants are planned for the
future, so treat "the case" throughout this manual as describing the
current one unless a later revision says otherwise.

## About This Manual

### Firmware Versions Covered
This manual covers instrument firmware **1.0.0** — the first version
installed on shipped units. The KLINI 400 Posthole Tiltmeter runs its own
firmware, developed and versioned independently of the KLINI Surface
Inclinometer's 1.1/1.2/1.3 line — the two share a family name and some
sensor hardware, but not a codebase, a version number, or an enclosure.
Nothing in the Surface Inclinometer manual should be assumed to apply here
unless this manual says so.

### Finding Your Firmware Version
<ul>
  <li>The power-up banner prints a line such as <code># Firmware: 1.0.0 (built Sep 29 2026 15:47:33)</code>.</li>
  <li>The <b>VERSION</b> serial command reports the same line on demand.</li>
</ul>

> **Don't confuse this with the `Version:` line in `SHOW`'s EEPROM dump** —
> that number (e.g. `20`) is the internal settings-storage layout revision,
> not the firmware version. It changes far more often than `FW_VERSION`
> does and isn't meaningful on its own; use `VERSION` for the real firmware
> identity.

## Overview
The KLINI 400 Posthole Tiltmeter measures tilt on two perpendicular axes (X and
Y) using **two independent sensing technologies per axis**: an electrolytic
(fluid-based) tilt sensor and a MEMS inclinometer, both read through the
same command interface and both independently calibrated to nanoradians.
Each reading is reported alongside the on-board temperature. The instrument
also carries a 3-axis magnetometer (for a gross orientation/heading check
after installation), an environmental sensor (temperature, humidity,
pressure), and two built-in leveling motors that can drive the instrument
back toward level either on command or fully automatically.

Everything — configuration, data retrieval, leveling, and calibration — goes
through a single serial command interface (§"Operation" below); there is no
local display, SD card, or Wi-Fi interface on this instrument (unlike the
KLINI Surface Inclinometer — do not assume those apply here).

The current case is a cylindrical, 6061 aluminum tube, 2" OD and
approximately 34" long, designed for shallow deployments (100m or less).
Weight is TBD.

## Specifications

<table>
  <tr bgcolor="gray">
    <td><b>Parameter</b></td>
    <td><b>Value</b></td>
    <td><b>Source / Notes</b></td>
  </tr>
  <tr>
    <td colspan="3" bgcolor="gray"><b>Tilt Measurement</b></td>
  </tr>
  <tr>
    <td>Axes</td>
    <td>2 (X and Y)</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Sensing technologies</td>
    <td>Electrolytic tilt sensor + MEMS inclinometer, independent, both per axis</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Tilt output resolution</td>
    <td>Sub-microradian (factory-calibrated slope on shipped units: 0.61-0.76 nrad/count)</td>
    <td>Measured across 3 fielded units' factory calibration reports; see "Calibration" below</td>
  </tr>
  <tr>
    <td>Tilt ADC</td>
    <td>24-bit (&plusmn;8,388,608 counts full scale)</td>
    <td>Kept in its highest-resolution power mode at all times by design</td>
  </tr>
  <tr>
    <td colspan="3" bgcolor="gray"><b>Other Sensors</b></td>
  </tr>
  <tr>
    <td>Magnetometer</td>
    <td>3-axis, &micro;T output, used for a gross orientation/heading check (<code>ORIENT</code>)</td>
    <td>Not a precision heading reference - see "Checking Orientation" below</td>
  </tr>
  <tr>
    <td>Environmental</td>
    <td>Temperature, humidity, pressure (pressure reported in whole pascals)</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Board temperature</td>
    <td>Reported with every electrolytic reading</td>
    <td>-</td>
  </tr>
  <tr>
    <td colspan="3" bgcolor="gray"><b>Electrical / Communication</b></td>
  </tr>
  <tr>
    <td>Serial interface</td>
    <td>RS232 (9600 baud) or RS485 (1200 baud), both 8N1 - set at the factory, not user-selectable</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Motor current limit (default)</td>
    <td>200 mA</td>
    <td>Adjustable, <code>SCURLIM</code></td>
  </tr>
  <tr>
    <td>Measured operating current (bench)</td>
    <td>~54 mA idle, ~138-145 mA during a leveling motor pulse, at 12V supply</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Connector</td>
    <td>Blue Trail Cobalt 4-pin bulkhead</td>
    <td>Posthole case only - the deep-hole variant uses a different connector</td>
  </tr>
  <tr>
    <td colspan="3" bgcolor="gray"><b>Mechanical</b></td>
  </tr>
  <tr>
    <td>Case (current)</td>
    <td>Cylindrical, 6061 aluminum, 2" OD &times; ~34" long</td>
    <td>Additional case variants are planned; this describes the current shipping case only</td>
  </tr>
  <tr>
    <td>Depth rating</td>
    <td>Shallow deployments, 100m or less</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Weight</td>
    <td>TBD</td>
    <td>-</td>
  </tr>
</table>

## Installation

### Electrical Connection
The communication mode (RS232 or RS485) is set at the factory by an internal
strap and is not customer-adjustable; confirm which mode your unit is set to
with the factory or by checking `SHOW`'s `Comm mode` line after power-up.

| Mode | Baud | Format |
|---|---|---|
| RS232 | 9600 | 8 data bits, no parity, 1 stop bit (8N1) |
| RS485 | 1200 | 8 data bits, no parity, 1 stop bit (8N1) |

Any standard serial terminal works (PuTTY, `screen`, CoolTerm, etc.). Both
bare LF and CRLF line endings are accepted when sending commands.

### Connector (Posthole Case)
The posthole case uses a **Blue Trail Cobalt 4-pin bulkhead connector**. The
deep-hole case variant uses a different connector — this pinout applies to
the posthole case only.

| Pin | Wire | Function |
|---|---|---|
| A | Black | GND |
| B | Red | VDC |
| C | White | Instrument RX (from logger) |
| D | Yellow | Instrument TX (to logger) |

"Instrument RX"/"Instrument TX" are named from the instrument's point of
view — wire the logger's TX to pin C and its RX to pin D.

### Powering Up
For about the first 2 seconds after power is applied, the instrument is in
its firmware-update bootloader: it sends nothing and ignores anything it
receives. About 2 seconds after that it prints a startup banner, for
example:

```
# Tiltmeter starting up...
# Firmware: 1.0.0 (built Sep 29 2026 15:47:33)
# Comm mode: RS232
# Register Commands... DONE
# Reading EEPROM settings... DONE
# Serial number: SN001
# Packet format: WIDE_CSV
# Columns: t_ms,type,mems_x,mems_y,elec_status,elec_ch0,elec_ch1,pcb_temp,env_temp,env_humidity,env_pressure,mag_x,mag_y,mag_z,mems_x_nrad,mems_y_nrad,elec_x_nrad,elec_y_nrad
# Starting I2C... DONE
# Starting SPI... DONE
# Setting up GPIO pins... DONE
# Starting X MEMS Tilt Sensor... # DONE
# Starting Y MEMS Tilt Sensor... # DONE
# Starting Magnetometer... # DONE (address 0x20)
# Starting PCB Temperature Sensor... # DONE
# Starting Environmental Sensor... # DONE
# Starting GPIO Expander... # DONE
# Starting ADC... # DONE
# Setting up Motors... DONE
# 10 second command window open
```

A sensor that isn't found reports `# NOT DETECTED` in place of `# DONE`
(`# FAIL` for the GPIO expander, which drives the leveling motors). The
magnetometer's address can be anywhere from `0x20` to `0x23`.

Lines starting with `#` are informational text, never data to parse. For
about 10 seconds after this banner, the instrument holds off automatic
telemetry so you have a clear window to send setup commands (like checking
`SHOW`) before data starts flowing. Commands are answered normally during
the window, which ends with:

```
# Initial command window closed - beginning operation
```

The first `ELEC`/`TEMP` records follow immediately, and leveling (including
full-auto leveling) only runs from this point on. After that, telemetry
follows the configured intervals, and commands can still be sent at any
time — replies interleave with the telemetry stream. `RESET` and `BOOTLOAD`
go through the same sequence, so the banner appears about 4 seconds after
the `OK`.

If the settings stored in the instrument are missing or invalid, for example
after a firmware update that changes the settings layout, the banner shows
`# Settings blob invalid or missing; loading defaults` after
`# Reading EEPROM settings...`. **All settings and calibration return to
factory defaults when this happens**, so check calibration with `SHOW`
before trusting the data (see the next section).

### Checking a Unit Before Deployment
Before lowering the instrument into the hole, confirm it's the unit you
think it is and that its calibration is loaded:

```
SHOW
```

Check the reported **Serial number** against the unit's physical marking,
and confirm `Elec angle cal points (X,Y)` reads `2,2` or higher (not `0,0`
— an uncalibrated axis reports `elec_x_nrad`/`elec_y_nrad` as a flat `0`,
which looks deceptively like "perfectly level" rather than "not
calibrated"). See "Calibration" below for how to verify the calibration
itself, not just that one is present.

### Checking Orientation After Installation
Once the instrument is set in the hole, `ORIENT` gives a one-shot "gross
orientation" report — not part of the regular telemetry, run it whenever you
want a check:

`ORIENT` takes a fraction of a second to reply, because it wakes the MEMS
sensors and averages several magnetometer readings. A typical report:

```
ORIENT
# ==================== ORIENTATION ====================
# MEMS tilt X: 1234 bits ( 2.21 deg )
# MEMS tilt Y: -567 bits ( -1.01 deg )
# Magnetometer raw (uT): X=48.32  Y=3.11  Z=-12.04
# Magnetometer, tool axes (uT):  X=3.11  Y=12.04  Z(up)=-48.32
# Tilt from vertical: 2.43 deg
# Estimated tilt-corrected magnetic azimuth of tool +Y: 353.64 deg
# NOTE: sign convention field-verified to ~3-25 deg - see sensors.cpp
# ======================================================
OK
```

**Finding +X on the case:** a small dimple on the instrument's top cap marks
the **+X direction** — use it to know which way the instrument is facing
before it goes in the hole, and to set a known rotational reference as you
lower and backfill/grout it.

Keep three things in mind, all of which **depend on how the instrument is
physically oriented in the hole**:

- Tool axes are right-handed with **Z up** (not down-hole), and the heading
  reported is the azimuth of the tool's **+Y** axis, not +X — think of it as
  a map grid where Y points toward the reference direction. It's
  **magnetic**, not true, north — apply your site's declination if you need
  true north.
- The sign convention was checked against a real 4-point compass calibration
  (+Y held pointed N, E, S, W in turn); residual error was roughly 3-25
  degrees after that check — small compared to the gross ~180-degree error
  the same check caught and fixed, but real. Treat `ORIENT` as a gross
  orientation check, not a precision heading, until that residual is
  characterized further — the original check was run indoors, where nearby
  steel structure is expected to add magnetic distortion beyond the sign
  convention itself.
- The MEMS tilt shown by `ORIENT` uses a fixed, generic conversion, **not**
  the per-unit factory calibration table that the data stream's
  `mems_x_nrad`/`mems_y_nrad` columns and the `RTILT` command use. It's a
  quick gross check, not a precision reading — for the calibrated value,
  read the telemetry stream or `RTILT` instead.

The dimple tells you where +X is **on the instrument**; it doesn't by itself
tell you what compass direction +X ends up facing once the instrument is
down the hole — that depends on how it was lowered and oriented going in.
Record the installation orientation (e.g. with a known alignment relative to
the dimple as you lower it, and/or an `ORIENT` reading immediately after
setting the instrument, before backfilling or grouting) if you need to relate
the X/Y data to a real-world direction later.

## Operation

### Serial Command Basics
- Commands are **case-sensitive** and must be typed in **UPPERCASE** exactly
  as documented.
- Arguments are separated by single spaces.
- A successful command replies `OK`. An invalid one (wrong argument count,
  an out-of-range value, or a prerequisite sensor that isn't available)
  replies `!`.
- A command the instrument doesn't recognize gets **no reply at all** — if
  you send something and nothing comes back, suspect a typo or wrong
  firmware version before suspecting a wiring problem. A command typed in
  lowercase counts as unrecognized.
- Keep each command line under 70 characters. Past 69 characters the
  instrument cuts the line: the first 69 characters run as one command and
  the rest is treated as a new line.
- **Check settings after changing them.** Numbers are read up to the first
  character that isn't a digit, and anything that isn't a number reads as
  `0`, with no error. For example, `SELECINT 1O00` (letter O instead of
  zero) sets a 1 ms interval and replies `OK`. Axis and sensor names are
  matched on their first letter only (`X`/`Y`, `E`/`M`). `SHOW` reports
  every stored value.
- Commands that take time (sensor reads, `ORIENT`, `MOTOR`) hold up
  everything else until they finish, including telemetry. Anything sent
  meanwhile is buffered and handled afterward.
- Telemetry rows are **not** prefixed with `#`; every other line the
  instrument sends is. That's the cheapest way to separate the two
  programmatically.

### Telemetry Format
Every reading is one CSV row:

```
t_ms,type,mems_x,mems_y,elec_status,elec_ch0,elec_ch1,pcb_temp,env_temp,env_humidity,env_pressure,mag_x,mag_y,mag_z,mems_x_nrad,mems_y_nrad,elec_x_nrad,elec_y_nrad
```

| Column | Meaning | Units |
|---|---|---|
| `t_ms` | Milliseconds since the instrument's firmware started (**not** wall-clock time — there is no real-time clock). Restarts from 0 after every power cycle, `RESET` or `BOOTLOAD`. | ms |
| `type` | Record type — see table below | - |
| `mems_x`, `mems_y` | Raw MEMS tilt sensor counts | counts |
| `elec_status` | Electrolytic ADC status word | - |
| `elec_ch0`, `elec_ch1` | Raw electrolytic tilt counts (X, Y) | counts |
| `pcb_temp` | Board temperature | &deg;C |
| `env_temp`, `env_humidity`, `env_pressure` | Environmental sensor readings | &deg;C, %RH, Pa (whole pascals, e.g. `97853.00` = 978.53 hPa) |
| `mag_x`, `mag_y`, `mag_z` | Magnetometer readings | &micro;T |
| `mems_x_nrad`, `mems_y_nrad` | Calibrated MEMS tilt | nanoradians |
| `elec_x_nrad`, `elec_y_nrad` | Calibrated electrolytic tilt | nanoradians |

Only the columns relevant to a given record's `type` are filled in; the rest
are blank. A calibrated (`_nrad`) column reads a flat `0` until its
calibration table is loaded — that's expected on an uncalibrated axis, not a
fault; see "Checking a Unit Before Deployment" above.

| `type` | Populated columns | Sent |
|---|---|---|
| `MEMS` | `mems_x`, `mems_y`, `mems_x_nrad`, `mems_y_nrad` | On `RMEMS`, or automatically on the configured MEMS interval (off by default) |
| `ELEC` | `elec_status`, `elec_ch0`, `elec_ch1`, `elec_x_nrad`, `elec_y_nrad` | On `RELEC`, or automatically every 1 second by default |
| `TEMP` | `pcb_temp` | Alongside every automatic `ELEC` record |
| `ENV` | `env_temp`, `env_humidity`, `env_pressure` | On `RENV`, or automatically every 60 seconds by default. The first automatic `ENV` comes one full interval after power-up. |
| `MAG` | `mag_x`, `mag_y`, `mag_z` | On `RMAG`, or automatically on the configured magnetometer interval (off by default) |

MEMS and magnetometer automatic streaming ship **disabled**. Turn them on
with `SMEMSINT`/`SMAGINT` if you want them in the regular data stream, or
just use `RMEMS`/`RMAG`/`ORIENT` to read those two sensors on demand without
changing anything.

### Example Data Row
A single `ELEC` record, with the `TEMP` record always sent alongside it:

```
25137,ELEC,,,1283,-8388608,-748487,,,,,,,,,,0,-458768
25138,TEMP,,,,,,25.41,,,,,,,,,,
```

Reading this: at `t_ms=25137`, the electrolytic sensor's status word was
`1283`, X read `-8388608` raw counts (the ADC's negative full-scale value —
this particular bench unit was sitting pinned at an extreme tilt when this
row was captured), Y read `-748487` raw counts, X's calibrated reading was
`0` (no calibration table loaded for X at that moment), and Y's calibrated
reading was `-458768` nrad. The following row, 1ms later, reports the board
at 25.41&deg;C. All other columns are blank because neither record type
populates them.

### Self-Leveling
The instrument can drive its own leveling motors to correct tilt, either on
command or fully automatically.

**`LEVEL`** (optionally `LEVEL X` or `LEVEL Y`) runs the self-leveling
motors on one or both axes right now. It prints
`# Enabling 12V for motor operation` and replies `OK` about half a second
later. Each motor pulse is reported as it fires, and each axis ends with a
result line:

```
# LEVEL X pulse: tilt=1715910 step=100ms speed=255 settle=5000ms
# LEVEL X pulse: tilt=420113 step=100ms speed=255 settle=5000ms
# LEVEL X converged: tilt=29575 via target_band
# LEVEL X: DONE
```

The result is `DONE`, `TIMEOUT`, or
`UNAVAILABLE - electrolytic sensor not detected`. A run takes from several
seconds to a couple of minutes per axis, mostly spent waiting for the sensor
to settle after each pulse. Telemetry keeps streaming during the run.
`LEVEL` sent during the 10-second startup window is accepted but doesn't
start until the window closes.

- **`LEVELSTOP`** stops a run and brakes the motors (`# LEVEL: STOPPED`),
  usually within about 100ms even mid-pulse. A telemetry reading or another
  command in progress can delay it slightly.
- **Don't send `MOTOR` or `SCURZERO` during a run** (see the command
  reference). In firmware 1.0.0 neither is refused, and `MOTOR` switches the
  motor supply off when it finishes, so the rest of the run can't move and
  ends in `TIMEOUT`. Check `SHOW`'s `Level state` line; it reads `IDLE` when
  no run is in progress.
- **Full-auto leveling** (`SLEVELAUTO 1`) makes the instrument level itself
  whenever tilt drifts outside a configured bound, with no command needed —
  it's **off by default**. An automatic run starts with
  `# LEVEL: auto-trigger bounds exceeded, starting` and then reports the
  same way as `LEVEL`. The trigger bound is set deliberately wide (83%
  of the sensor's full counting range on shipped units) — it's meant as a
  rare "something has moved a lot, go fix it" safety net, not a routine
  fine-leveling trigger. After a successful auto-correction it waits at
  least a minute before checking again; after one that times out without
  converging, it waits much longer (30 minutes by default) rather than
  repeatedly cycling the motors on a problem a quick retry won't fix.
- A leveling pulse is current-limited (`SCURLIM`, 200mA by default) — if a
  pulse draws more current than that, it stops immediately rather than
  continuing to drive against whatever's causing the extra load. Repeated
  current-limit trips are worth investigating mechanically before assuming
  it's a settings problem (see "Troubleshooting").
- Leveling bounds and timing are normally set once at the factory and
  shouldn't need routine adjustment. The full list of leveling settings is
  in the command reference below if you do need to check or change one.

## Full Command Reference

### Leveling

| Command | Args | Description |
|---|---|---|
| `LEVEL` | `[X\|Y]` | Runs the self-leveling motors. No argument levels X then Y; `X` or `Y` runs just that axis. Fails (`!`) if already leveling (send `LEVELSTOP` first), or if the electrolytic sensor or motor driver isn't available. See "Self-Leveling" above for the output. |
| `LEVELSTOP` | - | Immediately stops any in-progress leveling and brakes the motors. |
| `SLEVELAUTO` | `<0\|1>` | Enables/disables fully-automatic leveling. |
| `SLEVELUB` / `SLEVELLB` | `<X\|Y> <value>` | Upper/lower auto-trigger bound (raw counts) for an axis. |
| `SLEVELDB` | `<X\|Y> <value>` | Deadband (&plusmn; counts considered "level") for an axis. |
| `SLEVELTARGET` | `<X\|Y> <value>` | Target band: landing within this on one reading is accepted immediately. Must be less than the deadband. |
| `SLEVELCYCLES` | `<X\|Y> <1-255>` | How many times the reading must cross zero (inside the deadband, outside the target band) before an axis is accepted, instead of waiting for a lucky sample inside the target band. |
| `SLEVELDIR` | `<X\|Y> <0\|1>` | Reverses the leveling motor's pulse direction for an axis (set at the factory). |
| `SLEVELSPD` | `<X\|Y> <0-255>` | Leveling motor pulse strength (PWM), fixed for every pulse. |
| `SLEVELMINPULSE` / `SLEVELMAXPULSE` | `<X\|Y> <1-5000>` | Floor/ceiling (ms) for the adaptive pulse duration — it shrinks or grows automatically pulse to pulse rather than using one fixed strength. |
| `SLEVELSETTLE` | `<X\|Y> <0-65535>` | How long (ms) to wait after a full-strength pulse before trusting the next reading. |
| `SLEVELMAXMS` | `<X\|Y> <0-2147483647>` | Safety timeout (ms) for one axis's leveling attempt (default 120000). Larger values are accepted but stored as 2147483647; `HELP` shows the range as `0-4294967295`. |
| `SLEVELCOOLDOWN` | `<0-65535>` | Minimum time (ms) between full-auto attempts, after a successful one. |
| `SLEVELFAILCOOLDOWN` | `<0-2147483647>` | Minimum time (ms) before full-auto retries after a `TIMEOUT` (default 1800000, 30 minutes). Larger values are stored as 2147483647, as for `SLEVELMAXMS`. |
| `SLEVELCHKMS` | `<0-65535>` | How often (ms) full-auto checks whether leveling is needed. |

### Reading Sensors On Demand

| Command | Description |
|---|---|
| `RMEMS` | Sends one `MEMS` telemetry record right now. |
| `RELEC` | Sends one `ELEC` telemetry record right now. |
| `RENV` | Sends one `ENV` telemetry record right now. |
| `RMAG` | Sends one `MAG` telemetry record right now. |
| `ORIENT` | One-shot orientation report — see "Checking Orientation" above. |
| `RTILT` | Calibrated tilt (nrad) for MEMS X/Y and electrolytic X/Y, printed as text, not a telemetry row. |
| `RCUR` | Raw motor current-sense count and calibrated current (mA). |

### Status and Diagnostics

| Command | Description |
|---|---|
| `SHOW` | The full status report: serial number, detected hardware, current settings, and what's actually stored on flash (with a CRC check). |
| `HELP` | Condensed on-instrument reference for every command, for use without this manual handy. |
| `VERSION` | Firmware version and build date/time — see "Finding Your Firmware Version" above. |
| `SETSN` | `<value>` — sets the instrument's serial number (metadata only, up to 19 printable characters, no spaces). Normally set once, at commissioning. |
| `I2CSCAN` | Scans the internal I2C bus and lists every address that responds — useful if a sensor is reported "NOT DETECTED" at boot. |

### Sensor Configuration

| Command | Args | Description |
|---|---|---|
| `SMEMSEN` / `SELECEN` | `<0\|1>` | Enables/disables the MEMS or electrolytic tilt sensor. Disabling is immediate; re-enabling needs a `RESET` to actually resume reading (see note below). `SELECEN 0` is refused while leveling, since leveling depends on the electrolytic sensor. |
| `SELECAVG` / `SMEMSAVG` / `SMAGAVG` | `<1-255>` | Samples averaged per reading, per sensor. |
| `SELECINT` / `SMEMSINT` / `SMAGINT` / `SSOHINT` | `<0-65535>` | Automatic telemetry interval (ms) for electrolytic/MEMS/magnetometer/environmental data. `0` disables automatic sending for that sensor. |
| `SPKTFMT` | `<format id>` | Telemetry packet format. Only `0` (`WIDE_CSV`, the format this manual documents) exists today. |

> **Note:** disabling a sensor takes effect immediately, but re-enabling it
> only updates the stored setting — the sensor doesn't actually resume
> reading until the next `RESET` or power cycle. Until then, `RMEMS`/`RELEC`
> (and automatic records, if enabled) report all-zero readings.

### Motor and Current Sense

These are normally used only at the factory or during bench troubleshooting.

| Command | Args | Description |
|---|---|---|
| `SCURLIM` | `<1-3000>` | Motor current limit, mA (default 200). Don't set `0`: firmware 1.0.0 accepts it, but every pulse then stops immediately with `# Current limit exceeded`, so leveling can't move. |
| `SCURSCALE` | `<1-65535>` | Current-sense scale, mA per raw count &times; 1000. |
| `SCUROFFSET` | `<raw count>` | Current-sense zero offset, raw counts. |
| `SCURZERO` | - | Stores the current-sense reading right now as the zero offset. Use only when `SHOW` reports `Level state: IDLE`. |
| `MOTOR` | `<X\|Y> <U\|D> <speed 0-255> <ms 0-1000>` | Jogs one leveling motor up (`U`) or down (`D`; any letter other than `U` means down) for up to 1 second. It prints a live current reading about every 200ms, and stops early with `# Current limit exceeded` if the limit trips. **Not for use during a leveling run:** firmware 1.0.0 doesn't refuse it, and it switches the motor supply off when it finishes, which makes the rest of the run time out. Send `LEVELSTOP` first. |

### Calibration Tables

See "Calibration" below for how these are used. Loading calibration is
normally done at the factory.

| Command | Args | Description |
|---|---|---|
| `SANGPT` | `<ELEC\|MEMS> <X\|Y> <index 0-11> <raw> <angle_nrad>` | Loads one raw-to-angle calibration point. |
| `SANGCNT` | `<ELEC\|MEMS> <X\|Y> <count 0-12>` | Sets how many loaded points are valid. |
| `RANGTBL` | `<ELEC\|MEMS> <X\|Y>` | Lists the loaded points. |
| `SNULLPT` | `<X\|Y> <index 0-5> <temp_centiC> <null_raw>` | Loads one electrolytic zero-point temperature-compensation point (temperature in hundredths of a degree C). |
| `SNULLCNT` | `<X\|Y> <count 0-6>` | Sets how many zero-point points are valid. |
| `RNULLTBL` | `<X\|Y>` | Lists the zero-point table. |
| `SSCALETC` | `<X\|Y> <coefficient x1e6>` | Electrolytic sensitivity temperature coefficient, fraction per &deg;C &times; 10<sup>6</sup> (0.075%/&deg;C = 750). |
| `SCALREFT` | `<X\|Y> <temp_centiC>` | Temperature the angle table was captured at (default 2000 = 20.00&deg;C). |

### Electrolytic ADC

| Command | Args | Description |
|---|---|---|
| `SADCGAIN` | `<channel 0-3> <1\|2\|4\|8\|16\|32\|64\|128>` | ADC gain for a channel (channel 0 = X, 1 = Y; default 1). Changing it changes the raw counts, so the leveling bounds and calibration no longer match. |
| `SADCOFF` | `<channel 0-3> <0-16777215>` | ADC offset correction register for a channel. |

### Firmware Update and Reset

| Command | Description |
|---|---|
| `BOOTLOAD` | Restarts into the serial bootloader for a firmware update. Refused while leveling — send `LEVELSTOP` first. Resumes normal operation on its own if no update follows within about 2 seconds. |
| `RESET` | Restarts the instrument (like a power cycle). Replies `OK` first, then resets; the startup banner follows about 4 seconds later. Settings and calibration are kept. Refused while leveling. |
| `FACTORYRESET CONFIRM` | Erases all settings and calibration data and restores factory defaults — **except the serial number**, which is preserved. **Irreversible** short of reloading your calibration data; the literal second argument `CONFIRM` is required as a typo safeguard. Refused while leveling. |

## Calibration

### How Readings Are Calculated
Each axis's raw sensor counts are converted to a calibrated angle in
nanoradians using a table of (raw count, angle) points, loaded at the
factory. A table needs at least two points to represent a real slope; with
none loaded, that axis's `_nrad` output is a flat `0` (see "Checking a Unit
Before Deployment" above). The electrolytic sensor additionally supports an
optional temperature-compensation model (a table correcting the sensor's
zero point for temperature, plus a single sensitivity-vs-temperature
coefficient) — the MEMS sensor has no temperature compensation modeled at
all.

### What's Loaded on Your Unit
Each instrument ships with a single-slope, zero-offset electrolytic
calibration per axis — the slope from that unit's own factory calibration
report at its reference temperature (~20&deg;C), with **no temperature
compensation currently loaded**. This is a deliberate choice to keep the
on-instrument conversion simple; it is not the only thing the factory
calibration process measures.

Your factory calibration report, if you have one, characterizes real
temperature-dependent drift beyond what's loaded into the instrument today —
in factory calibration testing, the zero-point (intercept) alone was seen to
drift by as much as several hundred thousand nanoradians across a -20&deg;C
to 40&deg;C sweep, axis- and unit-dependent. If your deployment sees
meaningful temperature swings and that level of residual matters for your
application, two options:

- Ask the factory to load the full temperature-compensated model (the
  `SNULLPT`/`SSCALETC` commands in the reference above exist for this).
- Every telemetry row already reports raw counts **and** board temperature
  together, so the full correction from your calibration report can always
  be applied afterward in your own post-processing, even if the instrument
  itself isn't doing it in real time.

### Viewing the Calibration
```
SHOW
```
reports how many calibration points are loaded per axis/sensor
(`Elec angle cal points (X,Y)`, `MEMS angle cal points (X,Y)`,
`Elec null cal points (X,Y)`) and the scale temperature coefficient, if any.
To see the actual loaded points:
```
RANGTBL ELEC X
RANGTBL ELEC Y
```
(substitute `MEMS` for the MEMS table, or `RNULLTBL <X|Y>` for the
temperature-compensation table).

### Changing the Calibration
Loading a new table: `SANGPT` loads one point at a time (in increasing
raw-count order), then `SANGCNT` sets how many of the loaded points are
valid. See the command reference above for exact syntax. `FACTORYRESET`
clears all calibration data along with every other setting (serial number
excepted) — reload calibration afterward before trusting the data.

## Data Interpretation

### Raw Counts vs. Calibrated Tilt
Use the `_nrad` columns for anything quantitative — they're the
factory-calibrated values. The raw `mems_x`/`mems_y`/`elec_ch0`/`elec_ch1`
columns are there for diagnostics and for redoing the calibration yourself
if you ever need to (see "Calibration" above); they are not directly
comparable between units or even between the electrolytic and MEMS sensors
on the same unit, since each is calibrated independently.

### What a Positive Reading Means
The factory calibration makes increasing raw counts correspond to increasing
(more positive) nanoradians, consistently for both axes. What that positive
direction corresponds to **physically** — which way the instrument tips for
a positive X or Y reading — depends entirely on how the instrument is
mounted and oriented in the hole. The dimple on the top cap marks +X on the
instrument itself, but there is no fixed "positive = this compass direction"
rule beyond that; record the installation orientation (see "Checking
Orientation After Installation" above) if you need to relate sign to a
real-world direction.

### Temperature and Environmental Columns
`pcb_temp` is the board's own temperature, reported with every automatic
electrolytic reading — useful both as a health check and, per "Calibration"
above, as an input if you want to apply temperature compensation yourself
in post-processing. `env_temp`/`env_humidity`/`env_pressure` come from a
separate environmental sensor and are reported on their own slower
interval.

## Troubleshooting

| Symptom | Likely cause / what to check |
|---|---|
| No reply to a command at all | The instrument doesn't recognize it — check spelling and that it's in UPPERCASE. Confirm you're talking to the right port/baud (see "Electrical Connection"). |
| Command replies `!` | Rejected: wrong argument count, an out-of-range value, or a sensor/motor it needs isn't available right now (e.g. sent while already leveling). |
| A sensor reports "NOT DETECTED" at boot | Run `I2CSCAN` to see what actually responds on the internal bus, to help narrow down a wiring or sensor fault. |
| `_nrad` column reads a flat `0` | That axis/sensor has no calibration table loaded — see "Checking a Unit Before Deployment." Not a sensor fault. |
| `LEVEL` reports `TIMEOUT` | The axis didn't converge within its safety timeout. If the `# LEVEL ... pulse` lines show the tilt barely changing, check whether `MOTOR` was sent during the run (it turns the motor supply off; see "Self-Leveling") and whether `SCURLIM` is `0`. If the tilt grows instead of shrinking, the motor direction (`SLEVELDIR`) is wrong for that axis. Otherwise, bench-check that axis for mechanical freedom of motion before assuming it's a settings problem. |
| Leveling stops immediately / `# Current limit exceeded` | The motor pulse drew more current than `SCURLIM` allows and was cut off. Check `SHOW` for `Current limit (mA): 0` (every pulse trips at 0), then check for a mechanical obstruction or an axis at the end of its travel before raising the limit. |
| A setting replied `OK` but the instrument behaves oddly (e.g. telemetry floods, motor doesn't move) | Firmware 1.0.0 accepts mistyped numbers without an error; see "Serial Command Basics." Check the value in `SHOW` and set it again. |
| Settings or calibration suddenly back to defaults | The banner showed `# Settings blob invalid or missing; loading defaults` (for example after a firmware update). Reload calibration; see "Calibration." |
| Nothing at all for the first few seconds after power-up | Expected: the bootloader is silent for about 2 seconds, and the banner follows about 2 seconds later. |
| Communication is unreliable or garbled | Confirm the comm mode (RS232 vs RS485) and matching baud rate (`SHOW` reports which mode the instrument detected) and check cabling against the connector pinout above. |
| Need to start over completely | `FACTORYRESET CONFIRM` restores factory defaults (serial number preserved) — reload your calibration afterward; see "Calibration." |

## Firmware Change Log
Only firmware actually installed on a customer unit is listed here.

<table>
  <tr bgcolor="gray">
    <td><b>Version</b></td>
    <td><b>Status</b></td>
    <td><b>Notes</b></td>
  </tr>
  <tr>
    <td>1.0.0</td>
    <td>Released</td>
    <td>First released version. Dual-sensor (electrolytic + MEMS) tilt
    sensing on two axes, magnetometer-based gross orientation check,
    environmental monitoring, adaptive self-leveling (manual and
    full-auto) with current-limited motor protection, per-axis raw-to-angle
    calibration with optional electrolytic temperature compensation, and
    the full serial command interface documented in this manual.</td>
  </tr>
</table>

### Known Issues in Firmware 1.0.0
These are scheduled for correction in a later firmware release. Until then:

<ul>
  <li><code>MOTOR</code> and <code>SCURZERO</code> are not refused during a leveling run. <code>MOTOR</code> turns the motor supply off when it finishes, so the rest of the run can't move and ends in <code>TIMEOUT</code>. Send <code>LEVELSTOP</code> first.</li>
  <li><code>SCURLIM 0</code> is accepted, and then every leveling pulse stops immediately. Use 1&ndash;3000.</li>
  <li><code>SLEVELMAXMS</code> and <code>SLEVELFAILCOOLDOWN</code> store at most 2147483647 ms, although <code>HELP</code> shows 4294967295.</li>
  <li>Mistyped numbers are accepted without an error (for example, <code>SELECINT 1O00</code> sets 1 ms). Confirm changes with <code>SHOW</code>.</li>
  <li>Rarely, a leveling pulse can run longer than intended. Leveling corrects for the overshoot on later pulses.</li>
</ul>

## Revision History
<table>
  <tr bgcolor="gray">
    <td><b>Date</b></td>
    <td><b>Changes</b></td>
  </tr>
  <tr>
    <td>September 2026</td>
    <td>Initial release, covering firmware 1.0.0.</td>
  </tr>
  <tr>
    <td>October 2026</td>
    <td>Corrected to match firmware 1.0.0 as shipped: full startup sequence, <code>ORIENT</code> example values, pressure units (Pa), <code>SLEVELMAXMS</code>/<code>SLEVELFAILCOOLDOWN</code> ranges and <code>LEVEL</code> output. Added the motor, current-sense, calibration-table and ADC commands to the command reference, new troubleshooting entries, and known issues.</td>
  </tr>
</table>
