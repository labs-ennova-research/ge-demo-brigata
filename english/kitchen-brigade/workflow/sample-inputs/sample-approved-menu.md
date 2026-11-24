# 🧪 Sample Inputs for Testing the No-Code Workflow

Paste any of these blocks into the **`Approved_menu`** field of the **Manual trigger** — either in the **Test** tab (click **Start a test run**) or in a Gemini Enterprise chat after typing `@Kitchen Brigade Operational Workflow`.

> ⚠️ **Do not paste these into the "What would you like to change?" prompt box** on the left side of the Workflow Builder: that chat modifies the workflow definition rather than executing a run.

Every input block must contain **everything the steps need**: occasion, season, guest count, allergies/dietary needs, formality, budget, and approved menu. The workflow never asks follow-up questions: if a detail is omitted, it makes a reasonable assumption and states it explicitly.

---

## Scenario 1 — Direct Continuation of the `chatagent` Demo (🟡 Traffic Light + Allergen Management)

```text
Occasion: Elegant autumn dinner (refined, not overly stiff)
Season: Autumn
Formality level: Elegant
Number of guests: 6 people total
Dietary requirements and allergies:
  * 1 guest is vegetarian
  * 1 guest has a severe crustacean allergy
Indicative client budget: €90.00 per person (wines included)

APPROVED MENU:
- Starter: Warm Delica / Mantovana pumpkin flan with a light 24-month Parmigiano Reggiano fondue and toasted crushed hazelnuts.
- First Course: Carnaroli Riserva risotto with fresh porcini mushrooms and thyme.
- Main Course:
  * For 5 guests (including the guest allergic to crustaceans): Wild sea bass fillet in an aromatic herb crust.
  * Variant for the vegetarian guest: Baked eggplant, pumpkin, and buffalo ricotta millefeuille.
- Side Dish: Roman-style pan-seared fresh artichokes with wild mint.
- Dessert: 70% dark chocolate mousse with an organic citrus heart.
- Wines: Franciacorta for the starter, Timorasso for the first and main courses, Moscato d'Asti for dessert.
```

---

## Scenario 2 — Food Cost Stress Test (🔴 RED Traffic Light)

Luxury ingredients (amberjack, red prawns, beef tenderloin, Barolo) paired with a tight budget (`€65.00`/person). Step 3 must trigger the red alert and propose 2 mandatory corrective actions (one on the costliest food course, one on the wine pairing).

```text
Occasion: Formal corporate lunch
Season: Spring
Formality level: Formal
Number of guests: 10 people
Dietary requirements: 1 guest with lactose intolerance
Maximum client budget: €65.00 per person (wines included)

REQUESTED MENU:
- Starter: Fresh amberjack crudo with red prawns and organic citrus
- First Course: Carnaroli Riserva risotto with green asparagus and red prawns
- Main Course: Beef tenderloin with fresh porcini mushrooms
- Side Dish: Green asparagus glazed with cultured butter
- Dessert: Tiramisu with mascarpone and 70% dark chocolate
- Wines: Metodo Classico Sparkling Wine + Aged Red Wine (Barolo DOCG) + Passito Dessert Wine
```

---

## Scenario 3 — 20-Cover Tasting Dinner (Scale Test)

Useful for verifying whole-bottle rounding rules (dessert wine: 1 bottle per 8 guests, rounded up) and multi-guest vegetarian handling.

```text
Occasion: Friday Evening Tasting Dinner
Season: Autumn
Formality level: Elegant (target €85.00 per person)
Number of guests: 20 (including 2 vegetarians)
Budget: €85.00 per person

MENU:
1. Starter: Roasted fresh octopus over yellow-flesh potato velouté (for the 2 vegetarians: Golden artichokes over potato velouté)
2. First Course: Artisanal bronze-die pasta with Delica pumpkin cream, fresh porcini mushrooms, and crushed pistachios
3. Main Course: Red-wine braised beef cheek (for the 2 vegetarians: Fresh artichoke and 24-month Parmigiano Reggiano flan)
4. Side Dish: Oven-roasted yellow-flesh potatoes with aromatic herbs
5. Dessert: Buffalo ricotta cremoso with 70% dark chocolate and organic citrus zest
6. Wines: Elegant DOCG Red Wine (Chianti Classico) + Dessert Wine
```

---

## Note on Schedule Mode

The **Schedule** trigger has no input fields and cannot accept a pasted menu. Running the workflow on an automated schedule would require an external data source (such as a Google Drive document paired with its connector) and step prompts written to read from it. For this demo, always use the Manual trigger.
