# Service Guidelines, Inbox Triage, SLAs, and Reply Templates (`Heron-X 400`)

**Operational Document for the After-Sales & Technical Support Team.**
*Every incoming email in the support mailbox (`service@lfam-demo.example`) must be classified and handled strictly in accordance with this document and `heron-x400-operation-and-maintenance-manual.md`.*

---

## 1. Triage Categories and Official Internal Mailboxes

| Category | When to apply | Target internal mailbox |
|---|---|---|
| **L1 TECHNICAL SUPPORT** | Operational queries on machine use, material parameters, scheduled maintenance, PPE, procedures, and alarms documented in the manual (`A201`–`A206`, `S-01`) | `service.l1@lfam-demo.example` |
| **L2 ENGINEERING ESCALATION** | Alarms **not documented** in the manual (e.g., unknown codes), operations reserved for L2 (gearbox, laser calibration, screw), persistent fault after L1 checks, or alarm repeating `>= 3` times | `ingegneria.l2@lfam-demo.example` |
| **SPARE PARTS & MAINTENANCE KITS** | Requests for quotes or orders for spare parts (`RIC-HX-...`) and scheduled maintenance kits (`RIC-HX-KIT1000`, `RIC-HX-KIT2500`) | `ricambi@lfam-demo.example` |
| **CONTRACTS & WARRANTIES** | Requests for free-of-charge warranty replacement after expiration or on consumables, credit notes, discounts `> 10%`, Service Plan upgrades | `contratti@lfam-demo.example` |
| **INFORMATIONAL ONLY** | Newsletters, trade show/webinar invitations, automated `no-reply` notifications | *No forwarding — no draft* |

> **Anti-hallucination rule on contacts:** use exclusively the internal email addresses listed in the table above. Do not invent personal email addresses or addresses for other departments.

---

## 2. Priority Matrix and First-Response SLAs

| Priority | First-Response SLA | Assignment criteria |
|---|---|---|
| **HIGH** | **Within 2 business hours** | Complete machine breakdown in production; undocumented alarm; dangerous request to bypass safety devices; urgent formal complaint |
| **MEDIUM** | **Within 1 business day** | Technical queries on scheduled maintenance, torques/parameters, or spare parts kit quotes while the machine is operational |
| **LOW** | **Within 3 business days** | General documentation requests or non-urgent commercial inquiries |
| **NONE** | **No reply** | `INFORMATIONAL ONLY` emails (newsletters, webinars, automated notifications) |

---

## 3. Minimum Mandatory Data for Machine Downtime / Fault Reports

To log a fault ticket or verify eligibility for `Premium H24` on-call support, the customer's email must state:
1. Customer **company name**;
2. **Machine serial number** (format `HX-YYYY-NNN`, essential to verify `Standard` vs `Premium H24` Plan and warranty status);
3. **Alarm code** displayed on the HMI (or precise description of the symptom without a code);
4. **Current machine hours** and **material being printed** at the time of the stop.

If one or more items are missing, write `"not stated"` in the internal triage sheet and explicitly request them in the reply draft as a bulleted list.

---

## 4. Authority Limits and Safety Prohibitions ("Red Rules")

First-level support **MUST NEVER**:
1. **Authorize or suggest bypassing safety devices** (safety light curtains, door interlock microswitches, emergency stops) or using temperatures `> 320 °C`, prohibited polymers (`PEEK`/`PEKK`), or procedures not included in the manual → **firm refusal** citing the exact Chapter/Section of the manual.
2. **Invent troubleshooting procedures for alarm codes absent from the manual** → explicitly state that the code is not documented and escalate to `ingegneria.l2@lfam-demo.example`.
3. **Confirm free-of-charge warranty coverage, refunds, credit notes, or discounts exceeding 10%** → mark `ESCALATE INTERNALLY` to `contratti@lfam-demo.example` without promising or pre-approving anything.
4. **Confirm a 24/7 / evening / holiday on-call technician dispatch** without first verifying the machine serial number and an active `Premium H24` Plan (`Standard` hours: Mon–Fri `08:30–18:00`).

---

## 5. Official Email Reply Templates

> **General style rules:** English, clear and courteous technical-professional tone, **maximum 150 words** in the email body, signature `After-Sales & Technical Support Team — LFAM Division`.

### Template A — Standard L1 Technical / Maintenance Reply (Within Authority)
```text
Subject: Re: <Original Subject>

Dear <Contact Name>,

Thank you for contacting us regarding your Heron-X 400 (<Serial Number>).

According to the Heron-X 400 Operation and Maintenance Manual (Rev. 3.1):
- <Specific technical guidance, parameters/torques/part codes, and Chapter/Section reference>
- <Relevant safety warnings and mandatory PPE from the manual>

<If a kit/spare part was also requested, specify that we have forwarded the request to our Spare Parts office for a formal quote.>

Please remain in touch should you need any further clarification.

Kind regards,
After-Sales & Technical Support Team — LFAM Division
```

### Template B — Machine Downtime Acknowledgment / HIGH Priority with Missing Data
```text
Subject: [HIGH PRIORITY] Re: <Original Subject>

Dear <Contact Name>,

We have logged your machine downtime report with high priority and have already alerted our Technical Support team.

To verify your Service Plan (Standard Mon–Fri 08:30–18:00 vs Premium H24 on-call coverage) and immediately provide the right procedure, please reply with:
- <Missing mandatory item 1>
- <Missing mandatory item 2>
- <Missing mandatory item 3>

We cannot confirm 24/7 on-call dispatches prior to verifying the serial number and active contract. As soon as we receive these details, we will get back to you immediately.

Kind regards,
After-Sales & Technical Support Team — LFAM Division
```

### Template C — Interim Holding Reply for L2 Escalation / Out-of-Authority Requests (`ESCALATE INTERNALLY`)
```text
Subject: Re: <Original Subject> — Case acknowledgment and safety notice

Dear <Contact Name>,

We confirm receipt of your report regarding machine <Serial Number>.

<If a dangerous/prohibited request is present: firm statement of the prohibition from the Manual — e.g., strict prohibition against bypassing safety light curtains (Ch. 2, Sec. 2.2) and requirement to keep the machine in a safe state.>
<If an alarm code absent from the manual is present: specify that the code is not documented in the L1 manual and that the report has been escalated with high priority to L2 Engineering.>
<If requests for exceptional warranty coverage, refunds, or discounts > 10% are present: specify that these commercial/contractual assessments have been forwarded to the Contracts & Warranties office, without pre-approving any coverage or discount.>

A dedicated specialist from our team will contact you as soon as possible.

Kind regards,
After-Sales & Technical Support Team — LFAM Division
```
