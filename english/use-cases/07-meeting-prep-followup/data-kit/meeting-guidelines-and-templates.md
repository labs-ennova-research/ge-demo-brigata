# Company Guidelines — Meeting Preparation and Follow-up (NovaServizi S.r.l.)

**Operational standard for Project Managers and Account Leads when preparing for meetings ("5-Minute Prep Sheet") and drafting post-meeting follow-up emails.**

---

## 1. When to Produce the "Prep Sheet" vs. the "Follow-up Email"

- **PREP Mode (Before the meeting):** when the input is a calendar invite and/or a prior email thread leading up to the meeting, produce the **5-Minute Prep Sheet** for internal use.
- **FOLLOW-UP Mode (After the meeting):** when the input contains raw notes, minutes, or outcomes from a completed meeting, produce the **Action Verification Table** + the **Follow-up Email Draft** for attendees.

---

## 2. Standard for the "5-Minute Prep Sheet" (Pre-Meeting)

The pre-meeting preparation sheet must contain these exact **5 sections** in order:

1. **Meeting Details and Verified Attendees:** title, date/time, location, and attendee table cross-checked against `project-stakeholder-directory.md` (Name, Company, Role, Decision-making scope). If anyone on the invite is missing from the directory, flag them as `ATTENDEE NOT IN DIRECTORY`.
2. **Current Status from Recent Emails:** objective summary (maximum 5 bullet points) of what happened in the latest project email exchanges.
3. **Unanswered Customer Questions:** explicit list of questions raised by the customer in prior emails to which the NovaServizi team has not yet provided a written answer.
4. **Open Blockers and Questions to Ask in the Meeting:** operational blockers, delays in data/material delivery, and up to 4 targeted questions to unblock them during the session.
5. **Out-of-Scope Topics (DO NOT decide in the meeting):** any request raised in the emails involving **advancing the contractual Go-Live date**, **free features/modules not included in the contract**, or **fee/budget reductions**. Such items cannot be approved in an operational meeting and must be deferred to a separate formal evaluation (commercial Change Request).

---

## 3. Governance Rules for Follow-up (Post-Meeting)

Every action item, decision, or request in the post-meeting notes must pass these checks before entering the follow-up email:

### 3.1 Owner and Attendee Validation
- Cross-check every responsible person (Owner) mentioned in the notes against `project-stakeholder-directory.md` to retrieve their official role and email address.
- If an action item **has no explicit owner** in the notes (e.g., *"we need to send..."*, *"someone must..."*), do not infer or guess who owns it: set Owner = **`UNASSIGNED`** and Status = **`TO BE CONFIRMED`**.
- If an action item is assigned to a named person who is **not listed** in `project-stakeholder-directory.md`, never invent their email address: keep their name, set Email = **`NOT IN DIRECTORY`**, and set Status = **`OWNER NOT IN DIRECTORY`**.

### 3.2 Due Date Validation
- A due date is valid only when expressed as an **exact calendar date** (`DD/MM/YYYY`).
- If the due date is missing or phrased vaguely (*"as soon as possible"*, *"shortly"*, *"by end of month"* without a specific day), quote the exact phrase in quotation marks and set Status = **`DUE DATE TO BE CONFIRMED`**.

### 3.3 Separating Confirmed Decisions from Out-of-Scope Requests
- Include under **Confirmed operational decisions** only operational choices agreed within the current project scope.
- Any customer request for **free add-on modules**, **zero-cost scope extensions**, or **changes to contractual Go-Live dates** (even if someone in the meeting said *"we will check internally"*) **must NEVER appear under Confirmed decisions**: isolate it in the dedicated section **"Out-of-scope requests / For separate evaluation (Change Request)"**, explicitly stating that it does not constitute an approved commitment.

---

## 4. Official Template — Follow-up Email Draft

- **Maximum length:** **200 words** of prose (excluding tables).
- **Recipients:** exclusively the verified email addresses from `project-stakeholder-directory.md` for the meeting attendees (never invent addresses).

```text
Subject: [FOLLOW-UP] <Meeting Title> — <Meeting Date>

Dear all,

Thank you for joining today's meeting. Below is the shared summary of aligned items and next steps for project <Project Name/Code>.

1. CONFIRMED OPERATIONAL DECISIONS
- <Decision 1>
- <Decision 2>

2. CONFIRMED ACTION PLAN
| Action | Owner | Email | Due Date |
|---|---|---|---|
| <Only actions with Status CONFIRMED> | ... | ... | ... |

3. ITEMS TO BE CONFIRMED (OPEN OWNERS OR DUE DATES)
- <List of actions with Status TO BE CONFIRMED, OWNER NOT IN DIRECTORY, or DUE DATE TO BE CONFIRMED, or "No pending items" if all actions are confirmed>

4. OUT-OF-SCOPE REQUESTS / FOR SEPARATE EVALUATION
- <Any out-of-contract requests to be submitted for separate commercial/Change Request evaluation without commitment, or omit this section if none>

Please let us know within 24 hours if you have any additions or updates on the items to be confirmed.

Best regards,
Project Management Office — NovaServizi S.r.l.
```
