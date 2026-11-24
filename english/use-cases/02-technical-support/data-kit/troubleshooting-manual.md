# Troubleshooting Manual — LFAM Extruders and Robotic Cells (Rev. 4.2)

Restricted document for Level 1 (L1) technical support operators.
Strictly follow the inspection order specified. **If an alarm code does not appear in this manual, do not attempt guesswork procedures and escalate immediately to Level 2 (L2).**

---

## Section 1 · E100 Series Alarm Codes (Extrusion and Temperature Control Unit)

### Alarm `E101` — Zone 1 Undertemperature (Pellet Feed)
- **Description:** The temperature of Barrel Zone 1 has dropped more than 15 °C below setpoint.
- **Probable causes:**
  1. Zone 1 heater band open-circuited or loose terminal.
  2. Excessive water flow in the feed throat cooling circuit.
- **Verification procedure:**
  1. Place the machine in `HOLD` state and check the current drawn by Zone 1 on the HMI panel (nominal value: `4.2 A`).
  2. Check that the feed throat water throttling valve is set to `2.5 l/min`.
  3. If the current reading is `0.0 A`, power off the main cabinet, wait 10 minutes, and inspect fuse `F11` in the machine-side cabinet.
- **When to call the technician (L2):** If fuse `F11` blows again upon restart or if the heater band shows ground leakage (suspected spare part: `800W Heater Band code RIC-HT01`).

---

### Alarm `E102` — Zone 3 Overtemperature (Nozzle)
- **Description:** Nozzle temperature reading above 320 °C or uncontrolled thermal runaway.
- **Probable causes:**
  1. Zone 3 solid-state relay (SSR) stuck closed.
  2. Drift or short circuit on thermocouple `TC3`.
- **Verification procedure:**
  1. Immediately press the `HEAT OFF` heater emergency stop button on the HMI.
  2. Observe whether the temperature on `TC3` begins dropping within 2 minutes.
  3. Visually inspect the `TC3` thermocouple cable to ensure it is not pinched against the nozzle block.
- **When to call the technician (L2):** Always, if the temperature does not drop after `HEAT OFF` (requires replacing `25A SSR Module code RIC-SSR25` or `Type J Thermocouple code RIC-TC03`).

---

### Alarm `E103` — Pellet Starvation in Dryer Hopper
- **Description:** The minimum-level capacitive sensor on the head-mounted hopper has detected no material for over 60 seconds.
- **Probable causes:**
  1. Main big-bag or day bin empty.
  2. Pneumatic loader cyclone filter clogged with fiber dust.
  3. Capacitive sensor lens coated with electrostatic dust.
- **Verification procedure:**
  1. Check the material level in the floor-standing bin.
  2. Open the loader inspection lid and blow out the filter cartridge with compressed air at max `2 bar`.
  3. Wipe the surface of capacitive sensor `S-LEV1` with a dry cloth.
- **When to call the technician (L2):** Only if, with a full hopper and clean sensor, digital input `DI_08` on the diagnostics page remains at `0`.

---

### Alarm `E104` — Melt Overpressure / High Extruder Screw Torque
- **Description:** The head melt pressure transducer exceeds `180 bar` or the screw servomotor torque exceeds `92%` for more than 5 seconds.
- **Probable causes:**
  1. Partial nozzle obstruction caused by foreign matter or carbonized material.
  2. Actual melt temperature too low due to nozzle thermocouple (`TC3`) calibration drift.
  3. Wear or failure of melt pressure transducer `PT-MELT1`.
- **Verification procedure:**
  1. Stop the robot path and set screw speed to `0 rpm`.
  2. Keep heaters enabled at setpoint for 10 minutes to equalize heat across the head.
  3. With the screw stopped, read the `PT-MELT1` sensor value on the diagnostics page: it must drop below `5 bar`. If it stays above `25 bar` with the screw stopped, the transducer is out of calibration or faulty.
  4. If the zero-speed pressure is normal (`< 5 bar`), run a low-speed manual purge (`15 rpm`) in the purge zone and verify that the bead exits smoothly and straight.
- **When to call the technician (L2):** If torque exceeds `85%` again during the `15 rpm` purge, or if transducer `PT-MELT1` reads above `25 bar` with the screw stopped (suspected spare parts: `Hardened Nozzle code RIC-NOZ04` or `200bar Melt Pressure Transducer code RIC-PT200`).

---

### Alarm `E105` — Gearbox Cooling Chiller Flow Fault
- **Description:** Coolant flow rate on the extruder gearbox below `4.0 l/min`.
- **Probable causes:**
  1. Clogged Y-strainer on the chiller supply line.
  2. Low glycol level in the external chiller tank.
- **Verification procedure:**
  1. Check the chiller display to confirm no active alarms are present and the pressure gauge reads at least `1.8 bar`.
  2. Close the shut-off valves, remove, and clean the metal mesh screen of the Y-strainer located on the left side of the cell.
  3. Restore flow and verify on the HMI that flow rate returns above `5.5 l/min`.
- **When to call the technician (L2):** If the chiller pump runs but pressure remains below `1.0 bar` after cleaning the strainer.

---

### Alarm `E108` — External Axis Following Error (Rotary Table E1)
- **Description:** External axis `E1` position error exceeding `1.5 mm` during interpolated motion.
- **Probable causes:**
  1. Buildup of milling chips or polymer flash on the table's prismatic guideways.
  2. Loose drive belt on the `E1` axis gearbox.
- **Verification procedure:**
  1. Thoroughly clean the rotary table guideways and wipers.
  2. Jog axis `E1` at 10% speed in JOG mode and verify there are no abnormal noises or binding.
- **When to call the technician (L2):** If mechanical noise persists with clean guideways (rack-and-pinion preload inspection required).

---

### Alarm `E110` — Enclosure Safety Light Curtain Tripped
- **Description:** Perimeter photoelectric safety curtain beam interrupted during automatic cycle.
- **Probable causes:**
  1. Operator entered the guarded area without requesting door access.
  2. Dust or chips settled on the TX/RX optical columns.
- **Verification procedure:**
  1. Confirm that nobody is inside the cell perimeter.
  2. Clean the optical column lenses with a microfiber cloth.
  3. Press the blue `BARRIER RESET` button outside the cell and then `ACK` on the HMI.
- **When to call the technician (L2):** If the red `OSSDs OFF` LEDs on the curtain remain steadily lit even when the area is clear and lenses are clean.

---

## Section 2 · Symptoms Without an Alarm Code on the Panel

### Symptom `S-01` — Extruder stops mid-print with no alarm code on the HMI
- **Symptom description:** The robot continues moving along the print toolpath, but the extruder screw stops abruptly without generating any fault on the Alarms page.
- **Probable causes:**
  1. Intermittent loss of the `0–10 V` analog enable/speed reference signal between the robot controller and extruder drive (terminal block `X42`).
  2. Silent trip of the extruder drive's internal thermal protection caused by a clogged cabinet fan filter.
- **Verification procedure:**
  1. Pause the robot program and open `I/O Diagnostics -> Analog Outputs`.
  2. Check whether output `AO_01 (Screw Speed Reference)` shows a value greater than `0 V` while the drive reads `0 rpm`.
  3. Inspect the fan filter on the extruder electrical cabinet door: if clogged with machining dust, remove and blow clean the filter pad.
  4. Check the tightness of multipole connector `X42` at the base of the robot wrist.
- **When to call the technician (L2):** If the cabinet filter is clean and connector `X42` is securely tightened but the stoppage recurs (requires replacing `Robot Wrist Hybrid Cable code RIC-CAB42`).
