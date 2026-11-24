# Job Order Status Classification Thresholds and Rules (Operations Management)

Normative reference document for compiling the Weekly Job Order Status Report.
Every job order listed in the `job-order-status` sheet must be classified into exactly one of the following three categories (evaluated in strict priority order: first Delayed, then At Risk, finally On Track).

---

## 1. DELAYED Rule (Priority 1)

A job order is classified as **DELAYED** if **both** of the following conditions hold true:
1. `expected_delivery_date` is **earlier than today's date** (`expected_delivery_date < TODAY`).
2. The `status` field is **different from `"delivered"`**.

> **Warning (Common trap):** Even if the `status` field reads `"in progress"`, if `expected_delivery_date` is already in the past relative to today, the job order **is DELAYED** and must be placed in section "1. Delayed", sorted in descending order by number of days overdue (from most overdue to least overdue).

---

## 2. AT RISK Rules (Priority 2)

A job order that is **not delayed** and has a `status` different from `"delivered"` is classified as **AT RISK** if **at least one** of the following conditions holds true:

- **Condition R1 (Progress Threshold / Approaching Deadline):**
  There are **fewer than 15 calendar days** remaining until `expected_delivery_date` (`0 <= days_remaining < 15`) **AND** the completion percentage (`progress_%`) is **strictly below 70%** (`progress_% < 70`).
- **Condition R2 (Supplier or Spare Parts Issues in Notes):**
  The `notes` field mentions issues, holds, or delays related to **suppliers** (e.g., *"supplier delay"*, *"awaiting supplier"*) or missing **spare parts** / components.

---

## 3. ON TRACK Job Orders (Priority 3)

All job orders that do **not** fall into the "Delayed" category and do **not** fall into the "At Risk" category (including job orders already in `"delivered"` status or `"in progress"` without anomalies) are classified as **ON TRACK**.
In the weekly report, for on-track job orders **only the total count** must be reported, without listing them individually.
