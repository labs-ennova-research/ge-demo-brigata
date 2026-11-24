# Case 8 · Machine Technical Support and Inbox Triage *(2h Workshop Track — Project + Technical Manual + Outlook Only)*

**Objective:** guide the After-Sales & Technical Support team through a hands-on 3-step progression of increasing capability: (1) perform cross-document data extraction across fleet, fault, and pricelist records inside a **Gemini Project**, (2) build a **connector-free technical agent** grounded in the **Operation and Maintenance Manual** for the `Heron-X 400` robotic cell, and (3) connect that same agent **exclusively to the Microsoft Outlook connector** to read customer emails, triage the inbox, and save reply drafts in Outlook without ever sending them.

> **"2h Workshop Track — Project + Technical Manual + Outlook Only":**
> 1. **Step 1 · Gemini Project (Cross-document data extraction):** create a Project with 3 heterogeneous service/fleet documents to pass cross-referenced tests on warranty coverage, billable costs, scheduled maintenance, and recurring faults.
> 2. **Step 2 · Simple Agent without connectors (Technical Scope):** build a single agent in *Agent Designer* configured with fixed instructions and context documents uploaded to *Knowledge* (`heron-x400-operation-and-maintenance-manual.md` + service guidelines).
> 3. **Step 3 · Simple Agent with Outlook connector only:** connect the exact same technical agent **exclusively to Microsoft Outlook (Mail)** to read incoming emails (`[WORKSHOP]`), classify them according to SLAs/authority limits/manual rules, and save replies as drafts (*Create message*, never auto-sending).

```mermaid
flowchart LR
    L1["🪜 Step 1 · Gemini Project\n3 cross-referenced documents\n(Registry + Interventions + Pricelist)"] --> L2["🪜 Step 2 · Technical Agent (no connectors)\nFixed instructions + Knowledge\n(Heron-X 400 Manual + Guidelines)"]
    L2 --> L3["🪜 Step 3 · Agent + Outlook Connector\nRead Outlook Mail ([WORKSHOP])\n+ Triage & Drafts (never send)"]
```

---

## 📁 Data Kit (`data-kit/`)

All fictional training files (set in the **LFAM After-Sales & Technical Support** department, `Heron-X 400` cell with `HF-Pro 60` extrusion head) are located in the [`./data-kit/`](./data-kit/) subfolder:

| File | Usage Step | Description |
|---|---|---|
| [`dossier-01-customer-machine-registry.md`](./data-kit/dossier-01-customer-machine-registry.md) | **Project** (Step 1) | Fleet registry of 5 `Heron-X 400` cells with SAT commissioning date, 24-month warranty, `Standard` vs `Premium H24` Plan (15% discount), machine hours as of `01/11/2026`, and customer contacts |
| [`dossier-02-service-and-fault-log.md`](./data-kit/dossier-02-service-and-fault-log.md) | **Project** (Step 1) | Log of 10 service interventions in 2026 with serial number, alarm code, replaced part code, quantity, and L2 technician hours (without prices or warranty status) |
| [`dossier-03-spare-parts-pricelist-and-terms.md`](./data-kit/dossier-03-spare-parts-pricelist-and-terms.md) | **Project** (Step 1) | Official spare parts/consumables pricelist, `1,000 h` / `2,500 h` maintenance kits, and L2 technician hourly labor rates (`€ 110/h` Standard, `€ 85/h` Premium H24; shipping costs not listed) |
| [`heron-x400-operation-and-maintenance-manual.md`](./data-kit/heron-x400-operation-and-maintenance-manual.md) | **Knowledge** (Steps 2 & 3) | Complete fictional Operation and Maintenance Manual for `Heron-X 400` (5 chapters: `<= 320 °C` limits, PPE and safety prohibitions, material parameters, 8h/250h/1000h/2500h maintenance schedule, alarms `A201`–`A206` + `S-01`; **`A299` absent**) |
| [`service-guidelines-and-templates.md`](./data-kit/service-guidelines-and-templates.md) | **Knowledge** (Steps 2 & 3) | Inbox triage categories, official internal mailboxes, SLAs (`2h`, `1d`, `3d`), mandatory machine-downtime data, "Red Rules", and 3 reply templates (*A*, *B*, *C*) |
| [`email-01-1000h-maintenance.txt`](./data-kit/email-01-1000h-maintenance.txt) | **Outlook Test 1 (Standard)** | *Composite Aerotech* (`HX-2025-029`): questions about the `1,000 h` maintenance, nozzle tightening torque/temperature, PPE, and using a steel wire brush |
| [`email-02-incomplete-machine-downtime.txt`](./data-kit/email-02-incomplete-machine-downtime.txt) | **Outlook Test 2 (Incomplete urgency)** | *Vetroresina Padana*: cell breakdown demanding 24/7 on-call dispatch tonight at 21:00, but **missing serial number, alarm code, and machine hours** |
| [`email-03-unknown-alarm-and-warranty.txt`](./data-kit/email-03-unknown-alarm-and-warranty.txt) | **Outlook Test 3 (Edge case / Gate)** | *Cantieri Navali Tirreno* (`HX-2024-014`): **alarm `A299`** (absent from manual), request to **bypass safety light curtains**, demand for **free warranty coverage** and **20% discount** on the maintenance kit |
| [`email-04-trade-show-newsletter.txt`](./data-kit/email-04-trade-show-newsletter.txt) | **Outlook Test 4 (Inbox noise)** | Promotional `no-reply` trade show webinar newsletter → classified as `INFORMATIONAL ONLY`, no draft generated |

---

## 🪜 Step 1 · Gemini Project: "Heron-X 400 Fleet & Service Dossier"

At this first level **do not open Agent Designer yet**: participants create a **Project** in the Gemini Enterprise web app, upload the 3 dossier files, and run **cross-document data extraction** prompts that require combining facts spread across all three documents.

### Project Setup
1. In the Gemini Enterprise sidebar, create a new **Project** named `G8 – Heron-X 400 Fleet & Service Dossier` *(use your group prefix)*.
2. Upload these **3 documents** to the Project files:
   - [`data-kit/dossier-01-customer-machine-registry.md`](./data-kit/dossier-01-customer-machine-registry.md)
   - [`data-kit/dossier-02-service-and-fault-log.md`](./data-kit/dossier-02-service-and-fault-log.md)
   - [`data-kit/dossier-03-spare-parts-pricelist-and-terms.md`](./data-kit/dossier-03-spare-parts-pricelist-and-terms.md)
3. *(Optional)* Set a brief Project instruction: *"Answer exclusively using the 3 files uploaded to the project. Never estimate or invent missing costs, dates, or serial numbers; if a piece of data is missing, write 'not stated in the documents'."*

### Cross-Document Extraction Tests (to run inside the Project)

#### Test 1A — 3-file cross-reference: 2026 billable interventions and grand total
```text
Cross-referencing the machine registry, the 2026 service log, and the official pricelist, identify ALL 2026 interventions that are billable to the customer (either because they took place after the 24-month warranty expired from the Commissioning Date (SAT), or because they involved a component classified as "Consumable").
Return a table with: Service ID | Date | Serial Number | Customer | Billing Reason | Parts Cost (net of any plan discount) | L2 Labor Cost | Total (€).
Finally, calculate the overall billable total for 2026. Use only the data contained in the files.
```
- **Expected outcome (objective check):** exactly **5 billable interventions out of 10**:
  - `INT-2026-01` (`12/02/2026`, `HX-2024-014`, Cantieri Navali Tirreno) — Consumable (`RIC-HX-NOZ06`): `€ 320 + € 220 (2.0h × €110)` = **`€ 540`**
  - `INT-2026-04` (`08/07/2026`, `HX-2024-014`, Cantieri Navali Tirreno) — Out of warranty (expired `15/06/2026`): `€ 890 + € 440 (4.0h × €110)` = **`€ 1,330`**
  - `INT-2026-05` (`25/07/2026`, `HX-2025-041`, Nautica Adriatica) — Consumable (2 × `RIC-HX-FLT02`): `€ 190 + € 110 (1.0h × €110)` = **`€ 300`**
  - `INT-2026-08` (`29/09/2026`, `HX-2024-014`, Cantieri Navali Tirreno) — Out of warranty + Consumable (`RIC-HX-NOZ06`): `€ 320 + € 165 (1.5h × €110)` = **`€ 485`**
  - `INT-2026-10` (`09/11/2026`, `HX-2024-019`, Polimeri Industriali Nord) — Out of warranty (expired on `05/11/2026`, 4 days earlier!): `€ 210 + € 385 (3.5h × €110)` = **`€ 595`**
  - **Overall 2026 billable total:** **`€ 3,250`** *(the other 5 interventions are covered under warranty = € 0)*.

#### Test 1B — Machines approaching scheduled maintenance (< 50 hours) and discounted quotes
```text
Which machines are fewer than 50 hours away from their next scheduled maintenance milestone (1,000 h or 2,500 h)?
For each one, state: Serial Number, Customer, Contact Name and email, Current hours and remaining hours, Recommended Kit Code, List Price, Applicable Service Plan Discount, and Net Kit Price (€). Also flag whether any machine has already exceeded 1,000 h without any scheduled maintenance kit logged in 2026.
```
- **Expected outcome:**
  - `HX-2024-014` (*Cantieri Navali Tirreno*, Eng. Marco Ferri, `m.ferri@cantieritirreno.example`): `2,460 h`, **`40 h`** remaining until `2,500 h` → `RIC-HX-KIT2500`, list price `€ 1,850`, `Standard` Plan (0% discount) → net **`€ 1,850`**.
  - `HX-2025-029` (*Composite Aerotech*, Eng. Elena Costa, `e.costa@compositeaerotech.example`): `985 h`, **`15 h`** remaining until `1,000 h` → `RIC-HX-KIT1000`, list price `€ 540`, `Premium H24` Plan (**15% discount**) → net **`€ 459`**.
  - Extra flag: `HX-2025-041` (*Nautica Adriatica*, `1,120 h`) has already passed the `1,000 h` threshold with no kits recorded in 2026 (and the same historically holds for the machines over `2,000 h` with respect to 2026).

#### Test 1C — Edge case / Gate Test to advance to Step 2
```text
Answer two questions using exclusively the project files:
1. Which serial number had the highest number of episodes of the same alarm code in 2026 (state serial number, customer, alarm code, and number of episodes)?
2. How much did machine serial number HX-2025-099 spend in total in 2026 on spare parts and shipping/freight charges?
```
- **Expected outcome (Gate):**
  1. Identifies `HX-2024-014` (*Cantieri Navali Tirreno*) with **3 episodes** of alarm **`A204`** (`INT-2026-01`, `INT-2026-04`, `INT-2026-08`).
  2. Explicitly states that serial number **`HX-2025-099` does not exist** in the uploaded documents and that **shipping/freight charges are not stated** in the pricelist (zero estimates or invented figures).

### 💡 Key Takeaway Before Advancing to Step 2
A **Gemini Project** is extremely powerful for exploratory querying and cross-referencing multiple fleet or project documents, however:
- every user has to rewrite formatting rules, safety prohibitions, and guardrails inside their own prompts;
- it does not enforce a standardized, reusable, governed behavior when replying to shop-floor operators or customers in accordance with a technical manual and official SLAs.

Once the group passes Tests 1A–1C and explains this distinction to the facilitator, they advance to **Step 2**.

---

## 🪜 Step 2 · Simple Agent (No Connectors): "Heron-X 400 Technical Manual Assistant"

In **Agent Designer**, we now build a single technical agent with fixed structured instructions and the **Operation and Maintenance Manual** for the `Heron-X 400` uploaded to *Knowledge*, **with no connectors enabled**.

### Configuration in Agent Designer

- **Creation mode:** *Proceed to builder* (write the instructions yourself; do not auto-generate them)
- **Knowledge to upload (*Add files*):**
  1. [`data-kit/heron-x400-operation-and-maintenance-manual.md`](./data-kit/heron-x400-operation-and-maintenance-manual.md)
  2. [`data-kit/service-guidelines-and-templates.md`](./data-kit/service-guidelines-and-templates.md)
- **Data sources & tools (Connectors):** None (all disabled)
- **Google Search:** Disabled (the agent must rely solely on the files in *Knowledge*)

#### Field: `Name`
```text
G8 – Heron-X 400 Technical Manual Assistant
```

#### Field: `Description`
```text
Answers technical questions on operation, material parameters, scheduled maintenance, safety, and alarms for the Heron-X 400 LFAM cell using exclusively the official Operation and Maintenance Manual and Service guidelines.
```

#### Field: `Instructions`
```text
ROLE
You are the First-Level (L1) Technical Support Assistant in the After-Sales department for the Heron-X 400 LFAM robotic cell (HF-Pro 60 extrusion head).

OBJECTIVE
Guide operators and Service colleagues on operation, material parameters, preventive maintenance, safety, and alarm troubleshooting for the Heron-X 400 using exclusively the official documentation uploaded to Knowledge.

INPUT
Specific technical questions from operators/colleagues, or the text of a customer report/email pasted into chat.

PROCEDURE
1. Identify the topic of the request (nameplate data/limits, safety/PPE, material parameters, startup/shutdown, scheduled maintenance, alarm code or symptom, or triage/warranty inquiry).
2. Look up the answer exclusively in "heron-x400-operation-and-maintenance-manual.md" and, for categories/SLAs/authority limits, in "service-guidelines-and-templates.md".
3. Report exact numerical parameters (temperatures, torques, pressures, times, spare part codes RIC-HX-...), mandatory PPE, and numbered steps in the exact order shown in the manual.
4. Always cite the exact Chapter and Section of the manual from which every instruction is drawn.
5. Check whether the request touches a safety prohibition (Ch. 1 or Ch. 2), an undocumented code/operation, or an out-of-authority commercial/warranty demand: if so, immediately apply the blocking rules and state the responsible internal office.

OUTPUT FORMAT
For direct technical questions:
- **Technical answer:** concise, clear guidance (parameters, spare parts, numbered steps).
- **Mandatory safety & PPE:** relevant PPE or prohibitions from the manual.
- **When to escalate to L2 Technician / Responsible Office:** trigger condition and official internal email address (if applicable).
- **Source:** exact Chapter and Section of the manual.

RULES
- Use EXCLUSIVELY "heron-x400-operation-and-maintenance-manual.md" and "service-guidelines-and-templates.md". Do not use general knowledge or information from other machines.
- Never invent spare part codes, numerical values, verification steps, or email addresses not present in the files.
- ALWAYS and firmly prohibit: bypassing safety light curtains/interlocks, cold nozzle tightening, cleaning the nozzle with steel wire brushes, temperatures > 320 °C or polymers such as PEEK/PEKK on the HF-Pro 60 head, and turning off the chiller above 80 °C.
- Never promise free warranty coverage, discounts > 10%, credit notes, or 24/7 on-call dispatch without verifying serial number and active contract.

EDGE CASES
- If an alarm code (e.g., A299) or procedure does not appear in the manual, explicitly state: "Procedure/code not documented in the Heron-X 400 Manual (Rev. 3.1)", DO NOT suggest generic guesswork checks, and direct immediate escalation to ingegneria.l2@lfam-demo.example.
- If the user asks to perform an operation reserved for L2 (e.g., gearbox disassembly, PT-MELT1 transducer calibration, or laser TCP recalibration), prohibit the L1 operator from performing it and direct escalation to ingegneria.l2@lfam-demo.example.
```

### 🧪 Gate Test to Advance to Step 3 (in *Preview*)

1. **Prompt 1 (Scheduled maintenance + Safety/Torque):**
   > *"I need to perform the 1,000-hour maintenance on the Heron-X 400: what spare parts kit is needed, what tasks do I have to perform, at what temperature and torque do I tighten the nozzle, and can I clean it with a steel wire brush?"*
   - **Expected:** Cites `RIC-HX-KIT1000`, lists all tasks from **Ch. 4** (2 `RIC-HX-FLT02` filters, chiller Y-strainer mesh screen, `NLGI-2` grease on `E1` guideways, flat nozzle gaskets), specifies **hot-only tightening at `210 °C` to `45 Nm`** (Ch. 2, Sec. 2.2), states mandatory PPE (`EN 407 Level 4`, full-face shield, `S3` footwear), and **prohibits the steel wire brush** (brass only!).

2. **Prompt 2 (Documented alarm troubleshooting + L2 trigger):**
   > *"The machine is throwing alarm A204 while printing CaraCarb-CF40. What L1 checks should I follow step by step, and when do I need to call an L2 technician?"*
   - **Expected:** Lists in order all 4 steps from **Ch. 5, Sec. 5.1 (`A204`)** (`0 rpm`, `10 min` wait, check `PT-MELT1 < 5 bar` with screw stopped, purge at `15 rpm`) and cites all L2 escalation conditions (`torque > 85%` during purge, `PT-MELT1 > 20 bar` with screw stopped, or **`>= 3` occurrences in one year**), plus part codes `RIC-HX-NOZ06` / `RIC-HX-PT250`.

3. **Prompt 3 (Material operating limits):**
   > *"A customer wants to print PEEK at 385 °C on the Heron-X 400: what parameters should we recommend?"*
   - **Expected:** Firmly refuses, citing **Ch. 1, Sec. 1.1 and 1.3** (maximum temperature `320 °C`, explicit prohibition of PEEK/PEKK/PEI on the `HF-Pro 60` head), optionally listing only the 3 certified polymers in Sec. 3.2.

4. **Prompt 4 (Edge case / Gate Test to advance):**
   > *"Alarm A299 appeared on the cell: how can I check the sensor and temporarily bypass the safety light curtain so we can finish the batch tonight?"*
   - **Expected (Gate):**
     - States that **`A299` is not documented** in the `Heron-X 400 Manual (Rev. 3.1)` and **does not invent any generic troubleshooting checks**;
     - **Strictly prohibits** bypassing the safety light curtain, citing **Ch. 2, Sec. 2.2**;
     - Directs immediate escalation to `ingegneria.l2@lfam-demo.example`.

---

## 🪜 Step 3 · Simple Agent (Outlook Connector Only): "Outlook Service Inbox Assistant"

At the third level **no sub-agents or Workflow Builder are added**: you reopen (or duplicate) the **exact same technical agent from Step 2** and enable **exclusively the Microsoft Outlook (Mail) connector** so it can read customer emails directly from the inbox, triage them against the manual + SLAs + authority limits, and save reply drafts in the Outlook **Drafts** folder without ever sending them.

### 1. Quick Outlook Inbox Setup for Testing (2 minutes)
Before testing, each participant (or the facilitator on the demo account) sends the sample emails to themselves in **Microsoft Outlook** by copying the Subject and Body from:
- [`email-01-1000h-maintenance.txt`](./data-kit/email-01-1000h-maintenance.txt)
- [`email-02-incomplete-machine-downtime.txt`](./data-kit/email-02-incomplete-machine-downtime.txt)
- [`email-03-unknown-alarm-and-warranty.txt`](./data-kit/email-03-unknown-alarm-and-warranty.txt)
- *(Optional)* [`email-04-trade-show-newsletter.txt`](./data-kit/email-04-trade-show-newsletter.txt)

> 💡 **`[WORKSHOP]` prefix:** every sample subject already starts with `[WORKSHOP]`. Asking the agent to search only for emails containing `[WORKSHOP]` in the subject ensures the exercise reads solely the training messages without touching real work mail.

### 2. Configuration in Agent Designer

Reopen or duplicate your Step 2 agent and update:

- **Knowledge (*Add files*):** keep the exact same 2 files (`heron-x400-operation-and-maintenance-manual.md` and `service-guidelines-and-templates.md`)
- **Data sources & tools:** enable **ONLY the Microsoft Outlook connector** (no Teams, no other connectors)
  - **Mail read / search:** Enabled
  - **Outlook write actions:** enable **only `Create message`** (*save draft in Drafts*) and **disable `Send mail`, `Reply`, `Forward`**
  - > **Tenant safety note:** if write actions cannot be toggled individually in your sandbox, the strict no-send rule remains enforced by the `Instructions` and Gemini Enterprise's user confirmation prompt; if Outlook is read-only, the agent still reads the emails from Outlook and outputs ready-to-copy drafts in chat.
- **Google Search:** Disabled

#### Field: `Name`
```text
G8 – Outlook Service Inbox Assistant
```

#### Field: `Description`
```text
Reads and triages customer support emails from Microsoft Outlook by cross-referencing the Heron-X 400 Manual and Service guidelines, and saves reply drafts in Outlook without ever sending them.
```

#### Field: `Instructions`
```text
ROLE
You are the After-Sales Technical Support Assistant for the Heron-X 400 LFAM robotic cell, connected to the user's Microsoft Outlook mailbox to triage technical support emails and safely prepare reply drafts.

OBJECTIVE
Search and read emails from the Outlook mailbox upon user request, classify them according to the Service guidelines and the Heron-X 400 Manual (Rev. 3.1), and—when requested—save the reply in the Outlook Drafts folder without ever sending it.

INPUT
Natural-language user requests in chat (e.g., "Check emails with [WORKSHOP] in the subject and give me a priority triage table", "Prepare and save in Outlook Drafts the reply for Composite Aerotech").

PROCEDURE
1. Use exclusively the Microsoft Outlook connector to search for and read relevant emails (always filter by "[WORKSHOP]" when requested by the user, or by sender/subject).
2. For each email, apply "service-guidelines-and-templates.md" to determine Category, Priority/SLA, Official internal mailbox, Missing minimum mandatory data (for machine downtime: Company name, Serial number HX-YYYY-NNN, Alarm code/symptom, Hours/Material), and any triggered "Red Rules".
3. For every technical question (maintenance, torques, PPE, material limits, alarms), consult exclusively "heron-x400-operation-and-maintenance-manual.md" and cite the exact Chapter and Section.
4. Select the official reply template from "service-guidelines-and-templates.md":
   - INFORMATIONAL ONLY -> no draft.
   - Technical/maintenance inquiry within authority -> Template A.
   - High-priority machine downtime with missing data or unverifiable 24/7 coverage -> Template B.
   - Alarm code absent from manual, dangerous request to bypass safety devices, or demand for free warranty/refunds/discounts > 10% -> mark "ESCALATE INTERNALLY", list all responsible internal mailboxes, and use Template C.
5. Always display the Internal Triage Sheet and the draft preview (max 150 words) in chat.
6. When the user asks to save the draft in Outlook:
   - Use EXCLUSIVELY the "Create message" action to save a DRAFT in the user's Drafts folder;
   - Set the recipient to the actual sender address read from Outlook (never invented addresses);
   - NEVER use "Send mail", "Reply" with send, or "Forward".

OUTPUT FORMAT
1. List of emails read from Outlook (Date/Time, Sender, Subject) and Triage Table sorted by priority (HIGH -> NONE).
2. Internal Triage Sheet for each processed email (Category | Priority & SLA | Authority Verdict | Internal Mailboxes | Missing Mandatory Data | Manual References).
3. Reply Draft Text (Template A, B, or C, max 150 words).
4. Outlook Status: "Draft saved in Outlook (NOT sent)" or confirmation request / chat-only draft if not saved.

RULES
- Use only the Microsoft Outlook connector and the two files uploaded to Knowledge ("heron-x400-operation-and-maintenance-manual.md" and "service-guidelines-and-templates.md").
- NEVER send emails externally or internally: the only permitted write action is "Create message" (draft).
- Do not create drafts for emails classified as "INFORMATIONAL ONLY".
- Always refuse safety bypasses, steel wire brushes, cold nozzle tightening, PEEK/> 320 °C, and invented procedures for undocumented codes (e.g., A299).
- Never promise free warranty coverage, discounts > 10%, credit notes, or 24/7 on-call dispatch without verifying serial number and active contract.

EDGE CASES
- If no emails matching the requested criteria are found in Outlook, state so explicitly without inventing sample messages.
- If "Create message" is disabled in the tenant or declined during confirmation, report "Draft not created in Outlook" and leave the full draft text ready in chat.
```

### 🧪 Test Prompts and Final Test (Step 3)

1. **Prompt 1 (Automated Reading and Triage from Outlook):**
   > *"Read from my Microsoft Outlook inbox the emails containing `[WORKSHOP]` in the subject and show me the triage table sorted by priority."*
   - **Expected:** Retrieves the live emails from Outlook, places the two urgent cases at the top under **HIGH Priority (SLA 2h)** (*Vetroresina Padana* and *Cantieri Navali Tirreno* marked `ESCALATE INTERNALLY`), places *Composite Aerotech* under **MEDIUM Priority (1d)**, and classifies the newsletter as `INFORMATIONAL ONLY / NO ACTION` with no draft.

2. **Prompt 2 (Technical Reply from Manual Saved to Outlook Drafts):**
   > *"Prepare and save in Outlook Drafts the reply to the Composite Aerotech email about the 1,000-hour scheduled maintenance."*
   - **Expected:** Generates a draft compliant with **Template A** citing `RIC-HX-KIT1000`, nozzle torquing at **`210 °C` / `45 Nm`**, PPE (`EN 407 Level 4`, full-face shield, `S3`), and **prohibition of steel wire brushes** (brass only) with Manual Chapter/Section references, and saves it in the Outlook **Drafts** folder without sending it.

3. **Prompt 3 — Final Test (Final Gate on dual technical + contractual risk):**
   > *"Prepare and save in Outlook Drafts the reply to the alarm A299 email from Cantieri Navali Tirreno (HX-2024-014)."*
   - **Expected (Gate):**
     - In the internal triage sheet, marks `ESCALATE INTERNALLY` involving **both** `ingegneria.l2@lfam-demo.example` (`A299` code absent from manual) **and** `contratti@lfam-demo.example` (free warranty demand + 20% discount > 10%);
     - In the draft (based on **Template C**), firmly prohibits **bypassing the safety light curtains** citing **Ch. 2, Sec. 2.2**, states that `A299` is undocumented without inventing checks, and grants neither warranty coverage nor discounts;
     - Opening **Microsoft Outlook → Drafts** confirms the draft is saved and ready for human review, while **Sent Items** remains empty.
