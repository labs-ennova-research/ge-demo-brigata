# Food Cost Calculation Rules, Margins, and Event Quoting

This document defines the restaurant's financial policies for menu cost validation and client quote generation.

---

## 1. Official Definitions and Formulas

1. **Raw Material Food Cost (`FC_RM`)**:
   Total wholesale purchase cost (calculated on ordered **Gross Weight**) of all food ingredients in the menu, including structural ingredients (eggs, cream, stock vegetables, deglazing wine, etc.).
   > **+10% Safety Margin**: applies **exclusively to off-list ingredients** not found in the official price list (see Section 3 of `supplier-price-list-and-yields.md`), calculated on their Gross Weight. Listed ingredients do NOT get the +10% markup.
2. **Base Pantry Allowance (`BPA`)**:
   To cover salt, minor spices, base stocks, table bread, and espresso, always add a flat allowance of **`€2.50` per cover**.
3. **Beverage Cost (`BC`)** *(when wine pairing is included)*:
   Total cost of required bottles rounded **up** to the next whole bottle (never order fractional bottles from suppliers), plus **`€1.50` per cover** for mineral water.
4. **Total Direct Cost per Guest (`Direct_Cost_Per_Guest`)**:
   `Direct_Cost_Per_Guest = (FC_RM / Number_of_Guests) + BPA + (BC / Number_of_Guests)`

---

## 2. Target Food Cost % and Price Multipliers by Event Tier

The restaurant applies a distinct **target Food & Beverage Cost %** depending on the service formality requested by the client:

| Formality Level | Target Food Cost % | Direct Cost Multiplier | Recommended Price Range (per person, excl. VAT) |
|---|---|---|---|
| **Casual / Convivial** | 33% | `Direct Cost × 3.0` | €45.00 – €65.00 |
| **Elegant / Special Dinner** | 28% | `Direct Cost × 3.5` | €70.00 – €105.00 |
| **Formal / Business / Ceremony** | 25% | `Direct Cost × 4.0` | €95.00 – €150.00 |

> **Commercial rounding rule**: always round the final recommended selling price per guest to the **nearest `€5.00`** (e.g., `€83.40` → **`€85.00` per person**).

---

## 3. Budget Traffic Light Rules and Variance Management

Whenever the client specifies a **maximum budget per person** (or the formality tier imposes the ceiling shown in the table above), the Controller assigns a budget traffic light to the menu:

- 🟢 **GREEN (On Track)**: **both** conditions must hold true: (a) the recommended selling price (rounded to the nearest `€5`) is ≤ the client's budget; AND (b) the actual Food Cost % (`Direct_Cost_Per_Guest / rounded selling price`) is ≤ the tier target. If (a) is true but (b) is false, the traffic light MUST be YELLOW.
- 🟡 **YELLOW (Warning — +1% to +12% over budget, or within budget but above target Food Cost %)**: The menu slightly exceeds budget or margin targets. The workflow does not block the menu, but must propose **1 concrete optimization** on the costliest course (e.g., trimming a luxury ingredient's portion by 15% or swapping a prime cut for an equally refined, more cost-effective alternative).
- 🔴 **RED (Over Budget — > +12% over budget)**: The menu is financially unsustainable at current pricing. The workflow must highlight the alert prominently and prescribe **2 mandatory corrective actions** (one on the costliest Main or First Course, and one on the wine pairing) to bring Food Cost % back within the target threshold.

---

## 4. Extra Costs for Allergen / Dietary Variants

- When guests requiring a differentiated menu (e.g., vegetarian, gluten-free, crustacean-free) number **up to 2 people**, variant costs are absorbed into overall Food Cost with no client surcharge.
- Whenever variants require opening a dedicated certified supplier lot (e.g., certified gluten-free artisanal pasta or a dedicated protein substitute), include a **one-off `+€3.00` internal surcharge per special cover** in the direct cost calculation.

---

## 5. Mandatory Verification After Corrective Actions

After proposing any corrective action (portion reduction, ingredient swap, or wine change), the Controller must **recalculate the entire financial chain**: `FC_RM`, `Direct_Cost_Per_Guest`, theoretical selling price, rounded selling price, and actual Food Cost %, and then **re-run the two-condition traffic-light check** from Section 3. The traffic light cannot turn green merely because the rounded price matches the client's budget — the Food Cost % target condition must also pass. If either condition remains false, the traffic light stays yellow and an additional adjustment must be proposed.
