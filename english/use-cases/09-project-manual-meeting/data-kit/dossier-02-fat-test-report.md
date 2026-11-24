# Internal Pre-FAT Test Report — Project `COMM-2026-088` (`Kestrel-500 Hybrid`)

**Test execution date:** `12/11/2026` · **Machine serial number:** `KS-2026-011` · **Location:** Supplier Testing Workshop.
*Note: this report records only the values measured during the 6 internal tests `FAT-01` – `FAT-06`. Minimum contractual requirements are defined in `dossier-01-customer-order-specification.md`; lead roles and official email addresses are listed in `dossier-03-stakeholder-directory-and-plan.md`.*

---

## Pre-FAT Test Summary Table

| Test ID | Verification Scope | Value Measured in Workshop / Documents | Outcome | Anomaly Severity | Verification Lead | Operational Notes |
|---|---|---|---|---|---|---|
| `FAT-01` | Safety light curtains, emergency stop, and head-change interlock test | Measured stop time: **`0.42 s`**; `HSK-63F` taper interlock active | `PASSED` | `None` | Sara Fontana | Compliant with EN ISO 10218-2 |
| `FAT-02` | Printing of `CaraCarb-CF40` qualification specimen (`285 °C`, throughput `32 kg/h`) | Uniform bead, zero voids, `0%` delamination | `PASSED` | `None` | Luca Visconti | Specimen cooled and routed to `FAT-03` milling |
| `FAT-03` | 5-axis CNC milling on `CaraCarb-CF40` specimen (dimensional tolerance check) | Maximum error measured on CMM: **`± 0.34 mm`** | **`FAILED`** | **`CRITICAL`** | Luca Visconti | Thermal compensation drift on `KM-18` electrospindle; L2 laser realignment and retest required by `26/11/2026` |
| `FAT-04` | Post-milling surface roughness measurement on `CaraCarb-CF40` specimen | Average measured roughness: **`Ra 1.35 µm`** | `PASSED` | `None` | Luca Visconti | Surface finish suitable for mold layup |
| `FAT-05` | Printing of `PC-CF20` specimen (`295 °C`) + 5 automatic head-change cycles | Head change completed in `48 s`; **1 false `K404` alarm** recorded (air pressure `6.1 bar` at peak) | **`PASSED WITH RESERVATION`** | **`MINOR`** | Sara Fontana | Calibration of pressure switch `PS-AIR1` to `6.8 bar` required prior to shipment |
| `FAT-06` | Documentary readiness review of customer plant site (*Aerospace Tooling Nord*) | Floor load capacity declaration submitted by customer: **`2,800 kg/m²`**; `63 A` electrical line OK; dust extraction `2,400 m³/h` (`HEPA H13`) OK; **compressed air quality certificate (`ISO 8573-1`) not yet received** | **`FAILED`** | **`CRITICAL`** | Giulia Moretti | Blocker for the `14/12/2026` installation: structural verification / load-distribution plate + submission of compressed air certificate by Eng. Chiara Galli required |

---

## Report Closing Notes
- The Pre-FAT plan comprises exclusively **6** tests (`FAT-01` – `FAT-06`). No additional numbered tests exist beyond `FAT-06`.
- No tests were performed on out-of-contract polymers.
