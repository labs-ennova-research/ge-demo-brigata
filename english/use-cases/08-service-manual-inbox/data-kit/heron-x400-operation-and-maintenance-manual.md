# Operation and Maintenance Manual — LFAM Robotic Cell `Heron-X 400` (Rev. 3.1)

**Extrusion Unit:** `HF-Pro 60` Head · **Target Audience:** Qualified operators and First-Level (L1) technical support.
*Fictional technical document for training purposes. Strictly follow every procedure in the stated order. For any alarm code or operation not documented in this manual, bring the machine to a safe stop and request escalation to Second-Level Engineering (`ingegneria.l2@lfam-demo.example`).*

---

## Chapter 1 · Nameplate Technical Data and Operating Limits

### Section 1.1 — Main Specifications
- **Maximum build volume:** `4000 × 2000 × 1500 mm` (W × D × H) on a fixed bed with an external `E1` rotary table axis.
- **`HF-Pro 60` extrusion head:** Ø45 mm bimetallic screw, maximum throughput `45 kg/h`, standard hardened Ø6 mm nozzle (`RIC-HX-NOZ06`).
- **Maximum nozzle and head operating temperature:** **`320 °C`** (hardware automatic trip threshold at `325 °C`).
- **Maximum nominal melt pressure:** `180 bar` (alarm threshold `190 bar`).

### Section 1.2 — Utility Supply Requirements
- **Electrical power supply:** `400V AC three-phase + N + PE`, `50 Hz`, installed power `45 kW` (upstream breaker `80 A`).
- **Compressed air (pneumatic loader and filter blow-off):** `6.0 – 7.5 bar`, filtered and dried air.
- **Cooling circuit (25% water-glycol chiller):** supply temperature `20 °C ± 2 °C`, minimum flow rate at gearbox `5.0 l/min`, pressure `1.8 – 2.5 bar`, feed-throat valve set to `2.5 l/min`.

### Section 1.3 — Operating Limits and Prohibited Materials
- **THERMAL PROHIBITION:** Setting temperature setpoints above **`320 °C`** or attempting to extrude ultra-high-temperature engineering polymers (e.g., **PEEK, PEKK, PEI/ULTEM**) on the `HF-Pro 60` head is strictly prohibited: doing so causes irreversible damage to the ceramic heater bands and barrel seals.
- **NEAT / FOOD-CONTACT MATERIAL PROHIBITION:** The cell processes exclusively the fiber-filled thermoplastic pellet grades certified in Section 3.2. It is not certified for food-contact materials.

---

## Chapter 2 · Safety Regulations, PPE, and Strictly Prohibited Actions

### Section 2.1 — Mandatory Personal Protective Equipment (PPE)
During **manual purging**, **nozzle cleaning**, and **hot nozzle removal/torquing**, the operator must wear:
1. **Cut- and heat-resistant gloves** certified to **`EN 407 Level 4`** (contact heat resistance up to `350 °C`);
2. **Full-face polycarbonate shield** (protection against splashes of molten polymer);
3. **`S3` safety footwear** and long-sleeved flame-retardant workwear.

### Section 2.2 — Strictly Prohibited Safety Actions
1. **PROHIBITION ON BYPASSING SAFETY DEVICES:** Jumping, disabling, or bypassing the perimeter safety light curtains, cabin door interlock microswitches, or the emergency stop mushroom button to continue production during a fault or alarm is **strictly prohibited**.
2. **HOT-ONLY NOZZLE TORQUING:** Unscrewing or tightening the `RIC-HX-NOZ06` nozzle while the machine is cold is **prohibited** (risk of stripping or shearing the head threads). The nozzle must be tightened **exclusively while hot at `210 °C`** using a calibrated torque wrench set to **`45 Nm`**.
3. **NOZZLE CLEANING (BRASS ONLY):** Using steel wire brushes or hard metal scrapers on the nozzle orifice is **prohibited** (they scratch the tungsten carbide and distort melt flow). Use exclusively a **brass-bristle brush**.
4. **OPERATIONS RESERVED FOR L2 TECHNICIANS:** Disassembling the robot gearbox, replacing the bimetallic screw, calibrating the `PT-MELT1` transducer, and performing laser TCP recalibration are **prohibited for L1 operators** and reserved exclusively for certified `L2` technicians.

---

## Chapter 3 · Startup, Material Parameters, and Shutdown (End-of-Shift Purge)

### Section 3.1 — Cold Startup Procedure
1. Turn on the external chiller and verify on the HMI that flow rate is `>= 5.0 l/min` and pressure is between `1.8` and `2.5 bar`.
2. Enable zone heating (`Zone 1`, `Zone 2`, `Zone 3 / Nozzle`) at the setpoint for the loaded material.
3. Once target temperatures are reached across all 3 zones, wait a mandatory **`20 minutes` of thermal stabilization** (*soak time*) before enabling screw rotation.
4. Perform an initial verification purge at **`15 rpm`** in the purge station until the extruded bead is continuous and bubble-free.

### Section 3.2 — Certified Material Parameter Table (`HF-Pro 60`)

| Material | Polymer Matrix | Mandatory Drying | Zone 1 | Zone 2 | Zone 3 / Nozzle |
|---|---|---|---|---|---|
| **`CaraComp-GF30`** | PP + 30% glass fiber | `80 °C` for `4 hours` | `205 °C` | `220 °C` | `235 °C` |
| **`CaraCarb-CF40`** | PA6 + 40% carbon fiber | `90 °C` for `6 hours` | `255 °C` | `270 °C` | `285 °C` |
| **`PETG-GF20`** | PETG + 20% glass fiber | `65 °C` for `4 hours` | `225 °C` | `240 °C` | `250 °C` |

### Section 3.3 — Shutdown and End-of-Shift Purge Procedure
1. Close the main polymer feed slide gate and load `2 kg` of **`Purge-PP`** purging compound.
2. Extrude in the purge station at **`15 rpm` for `5 minutes`** until the fiber-filled polymer is completely flushed out (especially after `CaraCarb-CF40` to prevent carbonization).
3. Set screw speed to `0 rpm` and turn off the heaters (`HEAT OFF`).
4. **CHILLER RULE:** **NEVER** turn off the chiller until all head zones have dropped **below `80 °C`** (premature shutdown overheats the gearbox bearings).

---

## Chapter 4 · Preventive Scheduled Maintenance Plan

| Interval | Mandatory Tasks | Official Parts / Consumables | Performed By |
|---|---|---|---|
| **Daily (every 8 h)** | Hot external nozzle cleaning with **brass brush** (never steel); cleaning safety light curtain lenses with a microfiber cloth; visual check of chiller glycol level | None | L1 Operator |
| **Every 250 hours** | Removal and compressed-air blow-off of `RIC-HX-FLT02` cyclone filter cartridge at **max `2 bar`**; inspection of pellet feed hose integrity; torque check of wrist connector `X42` | `RIC-HX-FLT02` if damaged | L1 Operator |
| **Every 1,000 hours** | Replacement of **both cyclone filter cartridges** (`RIC-HX-FLT02`); cleaning of chiller Y-strainer metal mesh screen; greasing of `E1` table guideways with **`NLGI-2`** lithium grease; replacement of flat nozzle gaskets and **nozzle torquing to `45 Nm` at `210 °C`** | **`RIC-HX-KIT1000`** | Qualified L1 Operator |
| **Every 2,500 hours** | All 1,000-hour tasks + preventive replacement of Zone 1 heater band (`RIC-HX-HT12`), replacement of 3 head thermocouples (`RIC-HX-TC04`), replacement of `E1` table axis belt (`RIC-HX-CING1`), and gearbox torque/backlash inspection | **`RIC-HX-KIT2500`** | **L2 Technician recommended / mandatory for gearbox check** |

---

## Chapter 5 · Alarm Table and First-Level (L1) Troubleshooting

### Section 5.1 — `A200` Series Alarm Codes

#### Alarm `A201` — Zone 1 Undertemperature (Pellet Feed Zone)
- **Description:** Zone 1 temperature remains more than `15 °C` below setpoint for over `90 seconds`.
- **Probable causes:** (1) Open circuit on Zone 1 heater band or loose terminal; (2) Excessive cooling water flow on the feed throat (`> 2.5 l/min`).
- **L1 verification procedure:**
  1. Place the cell in `HOLD` and read the Zone 1 current draw on the HMI (nominal value: **`5.5 A`**).
  2. Verify that the feed-throat water throttling valve reads **`2.5 l/min`**.
  3. If current draw is `0.0 A`, lock out/de-energize the power cabinet, wait `10 minutes`, and inspect fuse **`F12`**.
- **When to escalate to L2 Technician:** If fuse `F12` blows again on restart or the heater band is open-circuited (spare part: `RIC-HX-HT12`).

#### Alarm `A202` — Zone 3 / Nozzle Overtemperature (`> 320 °C`)
- **Description:** Nozzle temperature reading exceeds `320 °C` or uncontrolled thermal runaway occurs.
- **Probable causes:** (1) Zone 3 SSR relay module stuck closed; (2) Faulty or pinched `TC3` thermocouple.
- **L1 verification procedure:**
  1. Immediately press **`HEAT OFF`** on the HMI panel.
  2. Verify that the temperature starts dropping within `2 minutes` (keeping the chiller running!).
  3. Once the head has cooled below `60 °C`, visually inspect the `TC3` thermocouple cable.
- **When to escalate to L2 Technician:** Always if the temperature fails to drop after `HEAT OFF` (spare parts: `RIC-HX-SSR30` or `RIC-HX-TC04`).

#### Alarm `A203` — Head Thermocouple Read Error (`TC-OPEN`)
- **Description:** Open or unstable signal from one of the `HF-Pro 60` head thermocouples.
- **Probable causes:** Loose `TC-BUS` connector on the robot wrist or failed thermocouple probe.
- **L1 verification procedure:**
  1. Stop the heating cycle (`HEAT OFF`).
  2. Check mechanical locking/tightness of the **`TC-BUS`** multi-pin connector at the base of the head.
  3. Restart HMI diagnostics and check stability of the ambient temperature reading.
- **When to escalate to L2 Technician:** If the reading remains stuck at `999 °C` or `0 °C` after checking the connector (spare part: `RIC-HX-TC04`).

#### Alarm `A204` — Melt Overpressure (`> 190 bar`) or High Screw Torque (`> 90%`)
- **Description:** Transducer `PT-MELT1` exceeds `190 bar` or screw motor torque exceeds `90%` for over `5 seconds`.
- **Probable causes:** (1) Nozzle partially clogged by carbonized material; (2) Soak time shorter than `20 minutes` or low melt temperature; (3) Drifted or faulty `PT-MELT1` transducer.
- **L1 verification procedure:**
  1. Stop the robot and set screw speed to **`0 rpm`**.
  2. Keep heaters at setpoint for **`10 minutes`** (wearing the mandatory PPE from Sec. 2.1 when approaching the head).
  3. With the screw stopped, read `PT-MELT1` under `Diagnostics -> Extruder`: the reading must drop **below `5 bar`**. If it stays **above `20 bar` with the screw stopped**, the transducer is faulty or out of calibration.
  4. If reading is `< 5 bar` with the screw stopped, run a purge at **`15 rpm`** in the purge station and verify smooth bead flow.
- **When to escalate to L2 Technician:** If screw torque exceeds `85%` during the `15 rpm` purge, or if `PT-MELT1` exceeds `20 bar` with the screw stopped, **or if alarm `A204` occurs 3 or more times within one year on the same machine serial number** (spare parts: `RIC-HX-NOZ06` or `RIC-HX-PT250`).

#### Alarm `A205` — Head Hopper Pellet Starvation (`> 60 s`)
- **Description:** Capacitive sensor `S-LEV1` on the head-mounted mini-hopper detects no pellets for over `60 seconds`.
- **Probable causes:** (1) Empty floor bin/big-bag; (2) Cyclone filter cartridge `RIC-HX-FLT02` clogged with fiber dust; (3) Dirty `S-LEV1` sensor face.
- **L1 verification procedure:**
  1. Check pellet level in the floor bin/big-bag.
  2. Remove and blow off the `RIC-HX-FLT02` cyclone filter cartridge with compressed air at **max `2 bar`**.
  3. Wipe the sensing face of capacitive sensor **`S-LEV1`** with a dry cloth.
- **When to escalate to L2 Technician:** If digital input `DI_08` on the HMI remains at `0` with a full hopper and clean filter.

#### Alarm `A206` — Rotary Table `E1` Following Error (`> 1.2 mm`)
- **Description:** External axis `E1` positioning error exceeds `1.2 mm` during coordinated interpolation.
- **Probable causes:** (1) Polymer debris/flash on the prismatic guideways; (2) Loose or worn `RIC-HX-CING1` drive belt.
- **L1 verification procedure:**
  1. Thoroughly clean the prismatic guideways and wiper seals on table `E1`.
  2. Jog axis `E1` in **`JOG` mode at `10%`** and check for binding or abnormal noise.
- **When to escalate to L2 Technician:** If binding or noise persists with clean guideways (spare part: `RIC-HX-CING1`).

---

### Section 5.2 — Symptoms Without an HMI Alarm Code

#### Symptom `S-01` — Sudden Extruder Screw Stop Without an HMI Alarm Code
- **Description:** The robot continues along the toolpath while the screw stops at `0 rpm` with no code logged on the Alarms screen.
- **Probable causes:** (1) Loss of `0–10 V` analog speed reference on connector `X42`; (2) Silent drive thermal trip caused by a clogged cabinet fan filter.
- **L1 verification procedure:**
  1. Pause the program and open `I/O Diagnostics -> Analog Outputs`.
  2. Check whether output **`AO_01`** is `> 0 V` while the drive reads `0 rpm`.
  3. Remove and blow clean the extruder cabinet cooling fan filter pad.
  4. Check tightness of multi-pin connector **`X42`** at the base of the robot wrist.
- **When to escalate to L2 Technician:** If the stop recurs with a clean fan filter and a properly tightened `X42` connector.
