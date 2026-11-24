# Project Technical-Commercial Specification — `COMM-2026-088`

**Customer:** Aerospace Tooling Nord S.p.A. (Varese Plant)
**Supplier:** LFAM Department — Industrial Robotic Systems
**Ordered Machine:** 5-Axis Hybrid Printing + Milling Robotic Center **`Kestrel-500 Hybrid`** *(Serial Number: `KS-2026-011`)*, configured with `HT-380` high-temperature extrusion head and `KM-18` 5-axis CNC electrospindle (18 kW).
*Fictitious document for training purposes.*

---

## 1. Contractual Scope and Exclusions

- **Supply included under contract:**
  1. `Kestrel-500 Hybrid` robotic cell complete with automatic head changer (`HT-380` ↔ `KM-18`) and interlocked enclosed cabin.
  2. Process qualification and FAT acceptance testing on **2 fiber-reinforced polymer materials**: **`CaraCarb-CF40`** (PA6 + 40% carbon fiber) and **`PC-CF20`** (Polycarbonate + 20% carbon fiber).
  3. Installation, commissioning, SAT acceptance testing at the customer's plant, and basic operator training (3 days).
- **Express exclusions (OUT OF SCOPE):**
  - The **"Advanced Thermal Simulation"** software module is **NOT included** in the contract (requires a commercial Change Request managed by the Account Director).
  - Qualification of the **`PEKK-CF`** engineering polymer is **NOT included** in the contract and is not part of the FAT tests.
  - Any civil works or upgrades to plant utilities remain entirely the customer's responsibility and expense.

---

## 2. FAT (Factory Acceptance Test) Acceptance Specifications

Release of the **Shipment Green Light (*Go/No-Go*)** is strictly subject to meeting all of the following binding conditions:
1. **100% of safety tests** passed without reservations (emergency stop time `<= 0.50 s`).
2. **Post-5-axis CNC milling dimensional tolerance** on the `CaraCarb-CF40` test specimen: **`± 0.20 mm`**.
3. **Post-milling surface roughness** on the `CaraCarb-CF40` specimen: **`Ra <= 1.6 µm`**.
4. **Zero (`0`) open `CRITICAL` severity deviations** as of the Shipment *Go/No-Go* date (`04/12/2026`). Only `MINOR` anomalies may be accepted with a closure plan prior to shipment.

---

## 3. Mandatory Customer Site Requirements (to be verified before `14/12/2026`)

| Site Utility / Requirement | Mandatory Minimum Contractual Value |
|---|---|
| **Industrial floor load capacity** | **`>= 3,500 kg/m²`** (flatness `<= 3 mm / 2 m`) |
| **Dedicated electrical line** | `400V AC three-phase + N + PE`, **`63 A`** (`42 kW`) |
| **Compressed air line** | `6.5 – 8.0 bar`, dried and certified **`ISO 8573-1 Class 4`** (pressure dew point `<= +3 °C`) |
| **CNC dust extraction system** | Flow rate **`>= 2,200 m³/h`** with **`HEPA H13`** filtration |

---

## 4. Binding Contractual Dates

- **Machine shipment (Ex-Works):** `11/12/2026`
- **Installation start at customer site:** `14/12/2026`
- **Final SAT acceptance / Contractual Go-Live:** **`22/12/2026`**

> **Contractual note:** payment terms follow standard milestone billing (30% upon order, 50% upon FAT, 20% upon SAT). This specification extract **does not provide for or state any daily liquidated damages / late-delivery penalty**.
