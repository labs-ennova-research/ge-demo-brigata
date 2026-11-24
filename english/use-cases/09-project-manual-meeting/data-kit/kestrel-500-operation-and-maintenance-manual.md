# Operation and Maintenance Manual — Hybrid Robotic Center `Kestrel-500 Hybrid` (Rev. 2.4)

**Configuration:** `HT-380` High-Temperature Extrusion Head + `KM-18` 5-Axis CNC Electrospindle (18 kW).
*Fictitious technical document for training purposes. Every installation, operating procedure, or technical response to the customer must strictly comply with this manual. For undocumented alarm codes or machining operations, escalate to L2 Engineering (`luca.visconti@lfam-demo.example` / `sara.fontana@lfam-demo.example`).*

---

## Chapter 1 · Machine Specifications and Mandatory Installation Site Requirements

### Section 1.1 — Main Technical Data
- **Net working envelope (printing + 5-axis milling):** `5000 × 2500 × 1800 mm`.
- **Total cell mass (including cabin and base frame):** `14,200 kg`.
- **`HT-380` extrusion head:** maximum continuous temperature **`360 °C`** (hardware cutoff `365 °C`), maximum throughput `38 kg/h`.
- **`KM-18` CNC electrospindle:** power `18 kW`, **`HSK-63F`** tool interface, maximum speed **`18,000 rpm`**, dedicated liquid chiller (`22 °C ± 1 °C`).

### Section 1.2 — Binding Installation Site Requirements
Before positioning the `Kestrel-500 Hybrid` cell, the customer's site must meet **all** of the following certified requirements:
1. **Industrial flooring:** minimum certified load capacity **`3,500 kg/m²`**, flatness `<= 3 mm` over `2 m`.
   - **INSTALLATION CONSTRAINT:** if floor load capacity is below `3,500 kg/m²`, installation is **PROHIBITED** unless a **load-distribution plate** (or slab reinforcement) designed and certified by a licensed structural engineer is installed.
2. **Electrical power supply:** `400V AC three-phase + N + PE`, `50 Hz`, dedicated **`63 A`** breaker protection, absorbed power `42 kW`.
3. **Compressed air system:** line pressure **`6.5 – 8.0 bar`**, filtered and dried air certified to **`ISO 8573-1 Class 4`** (pressure dew point **`<= +3 °C`**). Moisture or oil in the air damages the automatic head changer and the pneumatic bearings of the `HSK-63F` taper.
4. **CNC dust extraction system:** minimum flow rate **`2,200 m³/h`** equipped with certified **`HEPA H13`** filter cartridges suitable for capturing fine carbon-fiber and glass-fiber dust.

---

## Chapter 2 · Safety, Automatic Head Change and Prohibited Operations

### Section 2.1 — Safety and Mandatory PPE
- Automatic head changing (`HT-380` ↔ `KM-18`) is permitted **exclusively** in the `HOME-PARK` parking position, with cabin doors closed and interlocked and taper-lock air pressure **`>= 6.5 bar`**.
- **Mandatory PPE** during milling tool changes, cabin cleaning, and dust filter replacement:
  1. **`EN 388 Level D` cut-resistant gloves** (handling carbide end mills);
  2. **Sealed dust-proof safety goggles**;
  3. **`FFP3` respirator mask**, mandatory whenever handling or vacuuming carbon-fiber dust.

### Section 2.2 — EXPRESSLY PROHIBITED Operations, Materials and Practices
1. **PROHIBITION ON MILLING METALS (INCLUDING ALUMINUM):** Milling metallic materials — including **aluminum alloys**, steel, brass, or titanium — on the `KM-18` electrospindle is **strictly prohibited**. The cell is engineered exclusively for fiber-reinforced thermoplastics and non-metallic composite materials: milling metals causes seizure of the spindle's ceramic bearings and creates a fire ignition hazard inside the dust extraction ducts.
2. **PROHIBITION ON TEMPERATURES > `360 °C`:** Extruding polymers requiring temperatures above **`360 °C`** (such as neat `PEEK` at `390–400 °C`) is **prohibited**.
3. **PROHIBITION ON BLOWING DUST WITH COMPRESSED AIR:** Using open compressed-air blowguns to clean carbon-fiber dust off the cabin or workpiece is **strictly prohibited**: carbon microfibers are **electrically conductive**, penetrate drives, and cause short circuits inside electrical cabinets. Use **exclusively an `ATEX / HEPA H13` certified industrial vacuum extractor**.

---

## Chapter 3 · Operational Setup, CNC Spindle and Calibration

### Section 3.1 — Mandatory `KM-18` Spindle Warm-up Cycle
After any standstill longer than `4 hours`, before starting any precision milling operation, run the automatic bearing warm-up cycle (**duration `15 minutes`**):
1. `5 minutes` at **`3,000 rpm`**;
2. `5 minutes` at **`8,000 rpm`**;
3. `5 minutes` at **`14,000 rpm`**.

### Section 3.2 — `HSK-63F` Tool Holder and `TP-OPT1` Touch Probe
- Before every tool mount, wipe the `HSK-63F` taper with a lint-free cloth and verify that drawbar clamping force is **`>= 18 kN`**.
- **Workpiece zeroing:** perform using the **`TP-OPT1`** optical touch probe (nominal repeatability `± 0.08 mm`).
- **Thermal compensation and axis laser realignment:** operation **strictly reserved for L2 Technicians** using a certified laser interferometer (prohibited for line operators).

---

## Chapter 4 · Scheduled Preventive Maintenance Plan

| Frequency | Mandatory Operations | Official Spare Parts / Kits | Performer |
|---|---|---|---|
| **End of shift (every 8 h)** | Full vacuuming of cabin and build table using **`ATEX / HEPA H13`** vacuum extractor *(never compressed air!)*; `HSK-63F` taper cleaning; manual drain of compressed-air FRL condensate trap | None | L1 Operator |
| **Every 500 hours** | Replacement of **`HEPA H13`** extraction filter cartridge (`RIC-K5-HEPA`, wearing `FFP3` mask); replacement of air-line coalescing oil-removal cartridge (`RIC-K5-AIR4`); `HSK-63F` drawbar force check (`>= 18 kN`); guideway lubrication unit oil level check | **`RIC-K5-KIT500`** | Qualified L1 Operator |
| **Every 2,000 hours** | Full 500 h service + overhaul of `KM-18` electrospindle rotary seals, ceramic bearing condition inspection (`RIC-K5-BRG18`), dryer tube replacement (`RIC-K5-TUB8`), and certified calibration of `TP-OPT1` touch probe | **`RIC-K5-KIT2000`** | **Mandatory L2 Technician** |

---

## Chapter 5 · Diagnostics and Main Alarms (`K401`–`K406`)

### Alarm `K401` — `HSK-63F` Taper Clamping Failure
- **Causes:** Taper-lock air pressure `< 6.5 bar`, chips on taper, or dirty `S-HSK2` limit switch sensor.
- **L1 Procedure:** Check pressure on FRL gauge (`>= 6.5 bar`), wipe taper with a lint-free cloth, check `S-HSK2` signal on diagnostics screen. If persistent → escalate to L2.

### Alarm `K402` — `KM-18` Electrospindle Bearing Overtemperature (`> 65 °C`)
- **Causes:** Spindle chiller fault (`22 °C`) or ceramic bearing wear.
- **L1 Procedure:** Immediately stop milling, check chiller supply temperature (`22 °C ± 1 °C`) and verify no flow alarms are active. **Mandatory escalation to L2 Technician** before resuming machining (suspected spare part: `RIC-K5-BRG18`).

### Alarm `K403` — `HEPA H13` Extraction Filter Clogging (`ΔP > 1,200 Pa`)
- **Causes:** `RIC-K5-HEPA` cartridge saturated with carbon/glass fiber dust.
- **L1 Procedure:** Stop the extractor, put on **`FFP3` mask, sealed goggles, and `EN 388 Level D` gloves**, replace cartridge `RIC-K5-HEPA`, and reset the filter hour counter on the HMI.

### Alarm `K404` — Compressed Air Line Pressure Drop (`< 6.2 bar`)
- **Causes:** Plant air supply drop, condensate buildup in FRL unit, or low setpoint on pressure switch `PS-AIR1`.
- **L1 Procedure:**
  1. Verify that the plant air line supplies at least a stable `6.5 bar`.
  2. Drain the FRL condensate bowl and inspect for any traces of oil (if present, replace `RIC-K5-AIR4`).
  3. Check on the HMI the threshold of pressure switch **`PS-AIR1`** (nominal calibration value: **`6.8 bar`**).
- **L2 Escalation:** If upstream pressure is stable (`>= 7.0 bar`) yet the alarm persists or pressure switch `PS-AIR1` requires recalibration.

### Alarm `K405` — `HT-380` Extrusion Head Overtemperature (`> 360 °C`)
- **Causes:** Incorrect setpoint above limit or faulty `TC-HT3` thermocouple.
- **L1 Procedure:** Immediately press **`HEAT OFF`**, check the loaded material profile (no polymer above `360 °C`), inspect cable `TC-HT3` once the head is cold. If temperature does not drop within `2 minutes` → escalate to L2.

### Alarm `K406` — `TP-OPT1` Optical Touch Probe Signal Error
- **Causes:** Optical window fouled with composite dust or low battery.
- **L1 Procedure:** Clean the receiver and probe optical windows with isopropyl alcohol and a soft cloth; if the red LED flashes, replace the `3.6V` lithium battery part no. **`RIC-K5-BAT1`**.
