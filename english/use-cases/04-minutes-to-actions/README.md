# Case 4 · From Minutes to Actions

**Objective:** turn a meeting transcript into decisions, verified action items (cross-referencing owners against the participant directory and validating deadlines), and send out the follow-up email.

---

## 📁 Data Kit (`data-kit/`)

All fictional ready-to-use workshop files are located in the [`./data-kit/`](./data-kit/) subfolder:

| File | Usage | Description |
|---|---|---|
| [`meeting-transcript-1.txt`](./data-kit/meeting-transcript-1.txt) | **Test Prompt 1** | Progress review meeting (22 turns) with 3 decisions and 4 action items, all with an explicit owner and calendar deadline |
| [`meeting-transcript-2.txt`](./data-kit/meeting-transcript-2.txt) | **Test Prompt 2 (Edge case)** | Meeting with 5 action items: one **without an owner** (*"someone should contact the spindle supplier"*), one assigned to **Roberto Galli** (**not listed** in `participants.md`), and one with a vague deadline (*"shortly"*) |
| [`participants.md`](./data-kit/participants.md) | **Data bucket** (`Verifier` sub-agent) | Tabular directory (`name, role, email`) of authorized project participants |

---

## 🪜 Step 1 · Chat Agent: "Minutes Extractor"

### Configuration in Agent Designer

- **Knowledge to upload:** None (the user pastes the transcript in chat)
- **Connectors / Google Search:** Disabled

#### Field: `Name`
```text
G4 – Minutes Extractor
```

#### Field: `Description`
```text
Extracts decisions, action items with owner, deadline, and validity status, and open items from a meeting transcript.
```

#### Field: `Instructions`
```text
ROLE
You are a PMO assistant who analyzes operational meeting transcripts.

OBJECTIVE
From a meeting transcript, extract decisions, action items, and open items.

INPUT
The text of a meeting transcript pasted by the user.

PROCEDURE
1. Read the entire transcript and separate decisions already made, operational action items to be carried out, and open items still unresolved.
2. For each action item, identify who was explicitly assigned (Owner) and by what date (Deadline).
3. Assign each action item the Status "OK" if it has both an explicit Owner and a specific calendar date; otherwise assign "TO VERIFY".

OUTPUT FORMAT
1. Decisions (bulleted list).
2. Actions: table Action | Owner | Deadline | Status. Status is either OK or TO VERIFY.
3. Open items (bulleted list).

RULES
- An action item without an explicit assignee has Owner "UNASSIGNED" and Status TO VERIFY.
- A vague deadline ("shortly", "as soon as possible") must be reported in quotes with Status TO VERIFY.
- Do not infer the owner from whoever spoke last or whoever seems qualified.

EDGE CASES
- If a participant says "someone should do X" without anyone accepting or being named, the Owner must be "UNASSIGNED".
```

### 🧪 Gate Test to advance to Step 2
1. **Prompt 1:** Paste [`meeting-transcript-1.txt`](./data-kit/meeting-transcript-1.txt) → **Expected:** 3 decisions and 4 action items, all with Status `OK`.
2. **Prompt 2 (Edge case / Gate):** Paste [`meeting-transcript-2.txt`](./data-kit/meeting-transcript-2.txt) → **Expected:** The action *"contact the spindle supplier for the spare parts price list"* is marked `UNASSIGNED` with Status `TO VERIFY` (not attributed to whoever spoke before or after), and the deadline `"shortly"` is reported in quotes with Status `TO VERIFY`.

---

## 🪜 Step 2 · Root Agent: "Meeting Follow-up"

### Multi-Agent Architecture

```mermaid
flowchart TD
    R["🎯 Meeting Follow-up (Root Agent)\nNo data source"] --> S1["📝 Extractor\nNo data source"]
    R --> S2["✅ Verifier\n☁️ Bucket: participants.md"]
    R --> S3["✉️ Copywriter\nNo data source"]
```

---

### 1. Main Agent (Root)

- **Data source:** None

#### Field: `Name`
```text
G4 – Meeting Follow-up
```

#### Field: `Description`
```text
Coordinates extracting action items from meeting minutes, verifying owners and deadlines against the participant list, and drafting the follow-up email.
```

#### Field: `Instructions`
```text
ROLE
You coordinate the meeting minutes verification process and prepare the follow-up for the team.

PROCEDURE
1. Always call Extractor first, passing it the meeting transcript.
2. Pass the extracted actions table to Verifier to cross-reference owners against the participant list and check deadlines.
3. Pass the decisions, verified actions, and open items to Copywriter to draft the follow-up email.

OUTPUT FORMAT
- Control summary at the top: total number of extracted actions and **number of actions to clarify**.
- Complete verification table (from Verifier).
- Draft follow-up email (from Copywriter).

RULES
- Always call the sub-agents in this exact order: Extractor -> Verifier -> Copywriter.
- Do not fix or arbitrarily assign actions whose owner is missing or not on the list.
```

---

### 2. Sub-agent 1: `Extractor`

- **Data source:** None

#### Field: `Name`
```text
Extractor
```

#### Field: `Description`
```text
Extracts decisions, the actions table (Action, Owner, Deadline, Status), and open items from the meeting transcript.
```

#### Field: `Instructions`
Use the exact same instructions from **Step 1**.

---

### 3. Sub-agent 2: `Verifier`

- **Data source:** points to the bucket hosting the data ([`data-kit/participants.md`](./data-kit/participants.md))

#### Field: `Name`
```text
Verifier
```

#### Field: `Description`
```text
Cross-references action owners against participants.md to attach their email address and flags owners not on the list or deadlines without a specific date.
```

#### Field: `Instructions`
```text
ROLE
You are the project action compliance verifier.

OBJECTIVE
Cross-reference every extracted action against the official participant directory and validate deadlines and assignments.

INPUT
The extracted actions table from Extractor.

PROCEDURE
1. For each action, check that the Owner is listed in participants.md and add their email address.
2. If the Owner is "UNASSIGNED", keep "UNASSIGNED" and mark the outcome as UNASSIGNED (to clarify).
3. If the Owner is a named person who does not appear in participants.md, explicitly mark "OWNER NOT IN LIST".
4. If the deadline is not a specific calendar date (e.g., "shortly"), explicitly mark "DEADLINE TO BE DEFINED".

OUTPUT FORMAT
- Count of valid actions vs. actions with anomalies.
- Verified table with columns: Action | Owner | Email | Deadline | Verification Outcome (OK / UNASSIGNED / OWNER NOT IN LIST / DEADLINE TO BE DEFINED).

RULES
- Use only participants.md to verify names and email addresses.
- Do not alter or fix the data: flag anomalies as found.
```

---

### 4. Sub-agent 3: `Copywriter`

- **Data source:** None

#### Field: `Name`
```text
Copywriter
```

#### Field: `Description`
```text
Drafts the meeting follow-up email, separating the confirmed actions table from the 'To Clarify' section.
```

#### Field: `Instructions`
```text
ROLE
You are the post-meeting follow-up minutes copywriter.

OBJECTIVE
Write a follow-up email ready to send to the team.

INPUT
The decisions, open items, and verified actions table from Verifier.

PROCEDURE
1. Write a brief summary of the Decisions made.
2. Insert the table of valid confirmed actions (with Owner, Email, and Deadline).
3. Add a dedicated section titled "To Clarify" listing all actions flagged by Verifier (UNASSIGNED, OWNER NOT IN LIST, DEADLINE TO BE DEFINED).

OUTPUT FORMAT
Follow-up email structured into:
- Email subject
- Decisions made
- Confirmed Actions table
- "To Clarify" section (with flagged actions)
Maximum 200 words excluding the table.

RULES
- Use only the data received from the coordinator.
- Do not invent email addresses or due dates for flagged actions.
```

### 🧪 Gate Test to advance to Step 3
- **Prompt (Gate):** Paste [`meeting-transcript-2.txt`](./data-kit/meeting-transcript-2.txt)
- **Expected:** The report header shows **3 actions to clarify** out of 5; `Roberto Galli` is flagged as `OWNER NOT IN LIST`, the spindle supplier action as `UNASSIGNED`, and the layout update as `DEADLINE TO BE DEFINED`. All three appear in the **"To Clarify"** section of the draft email.

---

## 🪜 Step 3 · Workflow: "Meeting Follow-up"

> **Architectural note:** In Gemini Enterprise, a no-code agent created in Agent Designer cannot be invoked inside a workflow (only ADK or A2A agents are supported). We therefore rebuild the Step 2 sub-agents as a **sequential chain of `Gemini Agent` blocks**, reusing the same instructions via copy-paste along with the data bucket connection.

### Configuration in Workflow Builder

| # | Step | Type | Data Source (Bucket) | Configuration / Prompt |
|---|---|---|---|---|
| **0** | **Trigger** | `Manual` | — | Input field: `transcript` |
| **1** | **Extractor** | `Gemini Agent` | None | Copy the `Extractor` sub-agent instructions from Step 2 and append at the end: `Meeting transcript: ${trigger.transcript}` |
| **2** | **Verifier** | `Gemini Agent` | Bucket (`participants.md`) | Copy the `Verifier` sub-agent instructions from Step 2 and append at the end: `Extracted actions to verify: ${step1.output}` |
| **3** | **Copywriter** | `Gemini Agent` | None | Copy the `Copywriter` sub-agent instructions from Step 2 and append at the end: `Decisions and open items: ${step1.output} | Verified actions table: ${step2.output}` |
| **4** | **Organizer Approval** | `Human in the loop (Approval)` | — | The meeting organizer reviews the draft and the "To Clarify" section (`${step3.output}`) before sending |
| **5** | **Send Follow-up** | `Connector Action` | — | Send email to participants via Gmail *(or finish with output)* |

### 🧪 Final Test
- Run the workflow with [`meeting-transcript-2.txt`](./data-kit/meeting-transcript-2.txt), open the **Runs** tab on the *Needs Review* status, and **Reject** the approval: verify that the flow terminates immediately without sending any email.
