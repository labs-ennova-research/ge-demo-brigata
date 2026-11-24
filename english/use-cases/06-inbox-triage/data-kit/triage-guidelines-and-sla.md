# Official Guidelines — Inbox Triage, SLAs, and Authority Limits (NovaServizi S.r.l.)

**Internal operational document for handling incoming emails from customers, partners, and suppliers.**
Every incoming message must be classified and handled strictly in accordance with the rules set out in this document.

---

## 1. Triage Categories and Official Internal Mailboxes

Each email must be assigned to **one single** primary category (plus a second department in copy if the message covers two distinct areas):

| Category | When to apply it | Official internal mailbox |
|---|---|---|
| **SALES** | Quote requests, activation of add-on modules, plan or license upgrades, sales appointments | `commerciale@novaservizi-demo.example` |
| **ADMINISTRATION** | Invoice clarifications, courtesy copies, payment due dates, IBAN or billing details updates, credit notes | `amministrazione@novaservizi-demo.example` |
| **OPERATIONAL SUPPORT** | Platform malfunctions, login errors, operational outages, slowdowns, or technical anomalies | `supporto.urgente@novaservizi-demo.example` |
| **CONTRACTS & LEGAL** | Cancellations, terminations, contract renewals, changes to notice period clauses, formal disputes, or penalties | `ufficio.legale@novaservizi-demo.example` |
| **INFORMATIONAL ONLY** | Newsletters, press digests, automated "no-reply" notifications, read receipts, or generic webinar invitations | *No forwarding — no reply required* |

> **Anti-hallucination rule on contacts:** Never invent personal email addresses or addresses of other departments not listed in the table above.

---

## 2. Priority Matrix and First-Response SLAs

| Priority | First-Response SLA | Objective assignment criteria |
|---|---|---|
| **HIGH** | **Within 2 business hours** | Total or multi-user operational platform outage; contractual/legal deadline within 48 hours; formal complaint addressed to Executive Management |
| **MEDIUM** | **Within 1 business day** | Commercial upgrade/quote requests; specific checks on invoices or charges; partial anomalies where core operations remain unaffected |
| **LOW** | **Within 3 business days** | General informational inquiries (FAQs); company details updates or IBAN changes; requests for historical document copies |
| **NONE** | **No reply** | Messages classified as `INFORMATIONAL ONLY` (newsletters, automated notifications, external promotions) |

---

## 3. Mandatory Minimum Data per Category

Before confirming substantive processing of a request, check that the customer's email includes the required minimum data:

- **ADMINISTRATION (invoice checks):** Invoice number + Company name + Specific reason for the inquiry.
- **OPERATIONAL SUPPORT (faults/outages):** Company name + **Contract Code** (format `NS-XXXX`, required to verify *Standard* vs. *Premium* service level) + Description of the error or exact system screenshot/error message.
- **SALES (upgrades/new modules):** Company name + Requested module or number of user licenses.

If any mandatory minimum data item is missing, the reply draft must **explicitly ask the customer for it** in a clear bulleted list.

---

## 4. Authority Limits and Escalation Rules ("Red Rules")

First-line email operators have **NO financial or legal authority** over the following items:

1. **Refunds, write-offs, or credit notes** of any amount.
2. **Commercial discounts exceeding 10%** off the current price list (discounts up to 10% still require a formal quote from the `SALES` department).
3. **Contractual waivers**, cancellation of penalties, or reduction/waiver of cancellation notice periods (`60 days`).
4. **Confirmation of 24/7 or holiday technical on-call coverage** unless an active **Premium** plan contract is documented and verified in the email.

> **Mandatory procedure for out-of-authority requests (`ESCALATE INTERNALLY`):**
> If a customer requests any of items 1–3 (even if demanding urgent written confirmation the same day):
> - Mark the internal outcome as **`ESCALATE INTERNALLY`** and list the relevant internal mailboxes (`amministrazione@novaservizi-demo.example` for credit notes/write-offs; `ufficio.legale@novaservizi-demo.example` for clauses/notice periods; `commerciale@novaservizi-demo.example` for discounts).
> - Use **Template C exclusively** (neutral holding reply): confirm only receipt of the message and internal handoff to the relevant departments, **without ever promising, pre-approving, or implying acceptance** of refunds, discounts, or contractual waivers.
