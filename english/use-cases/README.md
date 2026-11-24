# "Build Your Agent" Workshop: Use Case Construction Guide

Facilitator guide for the **Gemini Enterprise and No-Code Agents** module. It explains how to prepare the data kit and how to build, step by step, the **nine cases** available across three instructional tracks:

### A) Standard / Advanced Track (Cases 1–5)
Progression from a single agent to a multi-agent system and workflow:

| Step | Tool | What You Build |
|---|---|---|
| 1 · Chat agent | Agent Designer | A single agent with instructions and one knowledge source |
| 2 · Root agent | Agent Designer (Flow) | The Step 1 agent becomes a sub-agent; additional sub-agents and a coordinating main agent are added |
| 3 · Workflow | Workflow Builder | The process becomes a flow with triggers, steps, and a human approval point before any write action |

### B) "Simple Mode" Track — Outlook Connector Only (Cases 6–7)
Progression designed for cross-functional business users using **exclusively the Microsoft Outlook connector** (no other connectors, no sub-agents, no workflows):

| Step | Tool | What You Build |
|---|---|---|
| 1 · Prompt | Gemini Enterprise Chat | Direct use in chat (without an agent) for quick summaries or drafts on copied/pasted text |
| 2 · (Simple) Agent without connectors | Agent Designer | Single agent configured with fixed instructions and context documents uploaded to *Knowledge* (FAQs, SLAs, templates, guidelines, directory) |
| 3 · (Simple) Agent with Outlook connector | Agent Designer + Microsoft Outlook | The same single agent connected **only to Microsoft Outlook** to read emails/calendar and save reply or follow-up drafts (*Create message*, without automatic sending) |

### C) 2h Workshop Track — Project + Technical Manual + Outlook Only (Cases 8–9)
Hands-on 2-hour progression calibrated for an industrial machine-manufacturing context, using **only Microsoft Outlook** as a connector (no Teams connector, no sub-agents, no workflows):

| Step | Tool | What You Build |
|---|---|---|
| 1 · Gemini Project | Projects in Gemini Enterprise | Creation of a Project with 3 job-order/fleet documents to pass **cross-document data extraction** tests across multiple documents |
| 2 · (Simple) Agent without connectors | Agent Designer | Single technical agent with fixed instructions and the machine's **Operation and Maintenance Manual** (`Heron-X 400` / `Kestrel-500 Hybrid`) + guidelines uploaded to *Knowledge* |
| 3 · (Simple) Agent with Outlook connector | Agent Designer + Microsoft Outlook | The same technical agent connected **only to Microsoft Outlook** to triage technical emails or prepare/document meetings by saving replies in *Drafts* (*Create message*, without sending) |

> **Advanced challenge for faster groups (2h Workshop):** in addition to Cases 8 and 9, you can assign **[Case 4 · From Minutes to Actions](./04-minutes-to-actions/README.md)** working as always on a **pasted `transcript`** (since the Microsoft Teams connector is not available).

All groups start at Step 1. A group advances to the next step only when it passes the **Gate Test**: the facilitator acts as a "gate" and verifies the test in person before giving the green light.

> **UI Note.** Menu and button names cited here follow Google's documentation for Agent Designer and Workflow Builder, which is in English and changes frequently. Before the first session, do a full walkthrough in the sandbox and align the labels with what participants actually see.

---

## 0. Structure of This Folder (`use-cases/`)

To streamline workshop delivery and preparation, each case has its own subfolder containing:
- **`README.md`**: all ready-to-copy/paste configurations and prompts for the **3 steps** of the case, plus the verification tests ("gates").
- **`data-kit/`**: ready-to-use synthetic files (project dossiers, technical operation and maintenance manuals, emails, calendar invites, FAQs, templates, Markdown tables, datasheets, transcripts) already aligned with the edge cases required by the tests.
- **`*_rev.docx`**: Participant Handout in Word format ready to print or distribute in the classroom.

| Case | Track | Folder & Agent Guide | Data Kit |
|---|---|---|---|
| **Case 1 · Request for Quotation (RFQ)** | Advanced (Multi-Agent + Workflow) | [`01-request-for-quotation/README.md`](./01-request-for-quotation/README.md) | [`01-request-for-quotation/data-kit/`](./01-request-for-quotation/data-kit/) |
| **Case 2 · Technical Support** | Advanced (Multi-Agent + Workflow) | [`02-technical-support/README.md`](./02-technical-support/README.md) | [`02-technical-support/data-kit/`](./02-technical-support/data-kit/) |
| **Case 3 · Supplier Quotes** | Advanced (Multi-Agent + Workflow) | [`03-supplier-quotes/README.md`](./03-supplier-quotes/README.md) | [`03-supplier-quotes/data-kit/`](./03-supplier-quotes/data-kit/) |
| **Case 4 · From Minutes to Actions** | Advanced / 2h Challenge *(with transcript)* | [`04-minutes-to-actions/README.md`](./04-minutes-to-actions/README.md) | [`04-minutes-to-actions/data-kit/`](./04-minutes-to-actions/data-kit/) |
| **Case 5 · Job Order Status** | Advanced (Multi-Agent + Workflow) | [`05-job-order-status/README.md`](./05-job-order-status/README.md) | [`05-job-order-status/data-kit/`](./05-job-order-status/data-kit/) |
| **Case 6 · Inbox Triage and Reply Drafts** | Simple (Prompt + Outlook Only) | [`06-inbox-triage/README.md`](./06-inbox-triage/README.md) | [`06-inbox-triage/data-kit/`](./06-inbox-triage/data-kit/) |
| **Case 7 · Meeting Preparation and Follow-up** | Simple (Prompt + Outlook Only) | [`07-meeting-prep-followup/README.md`](./07-meeting-prep-followup/README.md) | [`07-meeting-prep-followup/data-kit/`](./07-meeting-prep-followup/data-kit/) |
| **Case 8 · Machine Technical Support and Inbox Triage** | **2h Workshop (Project + Manual + Outlook)** | [`08-service-manual-inbox/README.md`](./08-service-manual-inbox/README.md) | [`08-service-manual-inbox/data-kit/`](./08-service-manual-inbox/data-kit/) |
| **Case 9 · Machine Commissioning, Technical Support and Meeting Management** | **2h Workshop (Project + Manual + Outlook)** | [`09-project-manual-meeting/README.md`](./09-project-manual-meeting/README.md) | [`09-project-manual-meeting/data-kit/`](./09-project-manual-meeting/data-kit/) |

---

## 1. Timing and Progression

The agenda slide allocates 40 minutes for building (20–60') and 15 minutes for testing (60–75'). With the stepped approach, building and testing alternate at every stage. A realistic breakdown:

| Time | Average Group | Fast Group |
|---|---|---|
| 20–40' | Step 1 and test | Step 1 and test |
| 40–60' | Step 2 | Step 2 and test |
| 60–75' | Step 2 test | Step 3 and Final Test |

Anyone who does not reach Step 3 has missed nothing: they still have a working agent to showcase during the debrief. In the 3-hour format, the realistic target is Step 2.

**Golden rule to repeat in the classroom:** you do not move to the next step out of boredom — you move because the test has passed. A root agent built on top of a sub-agent that hallucinates data multiplies the error.

---

## 2. Before the Workshop

### 2.1 Sandbox Prerequisites

Verify with IT at least a few days beforehand:

- **Agent Designer enabled** for the sandbox app. This is a feature toggled on by the administrator in the web app's feature settings.
- **Workflow Builder enabled**, required for Step 3. It must be enabled separately and, per Google's documentation, may require the project to be allowlisted. If it is unavailable, Step 3 is run in a scaled-back version (see the variant described in each case).
- **Sandbox connectors**: at minimum, read access to Google Drive for the data kit. Depending on the case, Step 3 requires Gmail (or Outlook), Google Chat, and Google Sheets. Also check which write actions are permitted.
- **Participant accounts**: access to the sandbox app and the kit folder, with connectors already authorized. "First sign-in" and connector authorization are already covered in the demo: have anyone who missed it repeat the step right at the start.

### 2.2 The Data Kit

Create a shared folder, for example `Agent Workshop – Data Kit`, with one subfolder per case:

```
Data Kit/
├── 01-request-for-quotation/
├── 02-technical-support/
├── 03-supplier-quotes/
├── 04-minutes-to-actions/
├── 05-job-order-status/
├── 06-inbox-triage/
├── 07-meeting-prep-followup/
├── 08-service-manual-inbox/
└── 09-project-manual-meeting/
```

Rules for the kit:

- **Synthetic data only.** No real customers, suppliers, personal names, or figures. The sample technical values in this guide are fictional: adapt them so they feel plausible for Caracol, without using real data.
- **Every kit contains at least one edge case** — the document designed to make a poorly written agent fail. That is what makes the test meaningful.
- **Small files**: few documents, kept concise. The goal is to learn how to build, not to stress-test the model.

In the sections for each individual case below, you will find the content to prepare for every file.

### 2.3 Participant Materials

- Slides 21–25 displayed on screen during the build phase.
- A printed sheet or shared document containing the **instructions template** (Section 3.3) and the **test prompts** for their assigned case.

---

## 3. The Tools in Five Minutes

### 3.1 Agent Designer (Steps 1 and 2)

Agent Designer is Gemini Enterprise's no-code tool for creating single agents and multi-step agents — i.e., a main agent coordinating one or more sub-agents.

**Two ways to create an agent** (from the web app, *Create agent* menu item):

1. **From prompt**: describe the agent in the left-hand chat and Agent Designer generates a first draft. It is fast, but the output always needs review.
2. **From the builder** (*Proceed to builder*): opens the canvas directly with a blank agent to configure manually. This is better suited when you want tight control over instructions and sub-agents.

**For the workshop, recommend the builder**, or using the prompt strictly for an initial draft. Writing instructions is the core learning exercise for participants, and letting the tool generate them entirely defeats the purpose.

**The canvas** has three main tabs:

- **Flow**: the visual representation of the agent. Clicking the main agent node lets you configure its name, description, instructions, model, data sources, and tools. Hovering over the node reveals *Add subagent*.
- **Preview**: the interactive testing environment. This is where test prompts are run.
- **Schedule**: scheduled executions (not needed in Steps 1 and 2).

**Main fields of an agent:**

| Field | What to Enter |
|---|---|
| Name | Short, descriptive name with the group prefix to avoid conflicts in the sandbox: `G3 – RFQ Pre-qualification` |
| Description | One sentence explaining what it does. In Step 2 this matters: it helps the main agent decide whom to delegate to |
| Instructions | The complete instructions (template in Section 3.3). *Help me write* is also available — useful for polishing, not for starting from scratch |
| Model | Leave the default model, unless IT specifies otherwise |
| Data sources & tools | Connectors and data buckets that the agent or sub-agents can use |
| Knowledge | *Add files*: kit files to upload for the single agent (Step 1) |

**How to provide data to agents:**

- **Single agent (Step 1)**: upload files directly into *Knowledge*. It is simple and immediate — the agent sees only those files.
- **Sub-agents (Step 2)**: you do not manually upload *Knowledge* to sub-agents; instead, point them directly to a **bucket** where the data is hosted.

### 3.2 Workflow Builder (Step 3)

Workflow Builder creates **workflow agents**: agents that execute a sequence of steps, combining AI automation and human intervention, starting from a trigger.

**Available triggers:**

| Trigger | When It Fires | Use in the Workshop |
|---|---|---|
| Manual | On demand: the user invokes the workflow with `@workflow-name` from chat, optionally filling in input fields | The safest choice in the classroom for all cases |
| Schedule | At a set frequency | Case 5 |
| Event | When data changes in a connected app, with a filter | Cases 1, 2, and 3, if the connector event is available in the sandbox |

**Main step types:**

- **Gemini Agent**: an AI step with its own instructions and data bucket connection. It receives only what is explicitly passed into the step's prompt, referencing trigger fields or outputs from previous steps using the `${step_name.output}` syntax.
  > **Note on existing agents (ADK/A2A) vs. Gemini Agent:** In Gemini Enterprise, the workflow step that invokes an external agent supports only code-registered agents (**ADK** or **A2A** protocol), not no-code agents built in Agent Designer. Therefore, in Step 3 **we rebuild the Step 2 sub-agents as a sequential chain of `Gemini Agent` steps** inside the workflow, copy-pasting the exact same instructions and data bucket connections.
- **Human in the loop**, in two variants:
  - **Request info**: pauses the flow and asks a person one or more questions.
  - **Approval**: pauses the flow and presents the output for approval before proceeding to subsequent steps.
- **Connector actions**: sending emails, posting messages, updating files. Availability and exact names depend on the connectors enabled in the sandbox.

When an execution reaches a human step, it pauses and appears with status *Needs Review* in the workflow's *Runs* tab. Show participants where to find it: that is where runs are approved or rejected.

### 3.3 Instructions Template

Have everyone use the same structure. The instructions provided below for each case follow this template.

```
ROLE
Who you are, in one sentence.

OBJECTIVE
What you produce and for whom.

INPUT
What you receive (pasted text, files, user request).

PROCEDURE
1. ...
2. ...

OUTPUT FORMAT
Exact structure of the response (table, sections, length).

RULES
- Use only the information present in [source]. Do not invent data.
- If information is missing, write "not specified" / ask for it.
- ...

EDGE CASES
- If X happens, do Y.
```

Three principles to emphasize in the classroom:

1. **Anti-hallucination rules must be written explicitly.** Models tend to "fill in" missing data with plausible values, which is precisely what the tests are designed to catch.
2. **The output format must be described accurately**, especially in Step 2, where one sub-agent's output becomes another's input.
3. **Edge cases are written before building**, not patched in after seeing an error.

---

## 4. Common Pattern Across the Three Steps

### Step 1 · Chat agent

1. Create the agent from the builder.
2. Fill in name, description, and instructions.
3. Upload the kit files specified in the case into *Knowledge*.
4. Save and test in *Preview* using all test prompts, **including the edge case**.
5. Refine the instructions until the Gate Test passes, then call the facilitator.

### Step 2 · Root agent

1. **Reopen the same agent** from Step 1, or duplicate it if the UI allows and you want to preserve the previous version.
2. Turn it into a sub-agent: the cleanest approach is to create a new main ("root") agent and move the Step 1 instructions into a sub-agent dedicated to that task. Alternatively, add sub-agents to the existing agent and rewrite its instructions from "executor" to "coordinator". Pick one approach and use it consistently across all groups.
3. Add the remaining sub-agents via *Add subagent*, each with its own name, description, and instructions, pointing them to the bucket where the data is hosted.
4. Write the root agent's instructions: **when** to call each sub-agent and **how** to combine their responses.
5. Test in *Preview* with the test prompts, then call the facilitator.

**Key takeaway at Step 2:** the root agent does not know how to do the work itself — it knows whom to delegate it to. If the root agent answers "on its own" without delegating, either the sub-agent descriptions are too vague or the root instructions fail to specify when to delegate.

### Step 3 · Workflow

1. Create a new workflow in Workflow Builder.
2. Choose the trigger. In the classroom, **Manual with input fields** is the most reliable; Event or Schedule triggers are a bonus.
3. Add the steps: rebuild the Step 2 sub-agents as a **sequential chain of *Gemini Agent* steps** (pasting the instructions already written in Step 2, pointing to the same data in the bucket, and passing outputs via `${step_name.output}`), then add **Approval** (and **Request info**, if applicable), and finally the connector action.
4. Run the workflow, go to *Runs*, open the execution in *Needs Review*, and test both approving and rejecting.

**Key takeaway at Step 3:** whereas in Step 2 the Root Agent dynamically decides in chat which sub-agents to invoke, the workflow turns those sub-agents into a **deterministic step-by-step pipeline** governed by a trigger and gated by a human approval point before any write action.

**Variant without write connectors:** the flow ends with approval and the final output visible in the run log. The instructional value — understanding where and why to keep a human in the loop — remains intact.

---

## 5. Case 1 · Request for Quotation (RFQ)

**Objective:** from a prospective customer's initial email, determine whether the request is feasible, what information is missing, and how to reply.

### 5.1 Data Kit (`01-request-for-quotation/`)

| File | Content to Prepare |
|---|---|
| `machine-capacity-sheet.md` | One page with: maximum build volume (e.g., 4000 × 2000 × 1500 mm, fictional value), supported materials (5–6 entries), typical tolerances, indicative lead times by size bracket, and what is *not* offered (e.g., transparent parts, food-grade certifications) |
| `email-01-complete.txt` | Request with all required details: marine sector, hull mold, dimensions within build volume, material specified, quantity 1, delivery in 8 weeks |
| `email-02-incomplete.txt` | Generic request: "we need a quote for a composite component, can you help us?", with no dimensions or quantity |
| `email-03-out-of-capacity.txt` | Part with one dimension exceeding the maximum build volume, phrased unobtrusively (e.g., in meters, buried inside a paragraph) |
| `materials-datasheet.md` | 3 fictional materials with key properties and typical applications |
| `case-study.md` | 4 fictional application case studies, one per sector: marine, aerospace, architecture, automotive |

The edge case is email 3: the out-of-capacity dimension must be "tucked away" subtly enough to slip past an agent that does not genuinely compare values.

### 5.2 Step 1 · Agent "RFQ Pre-qualification"

**Knowledge:** `machine-capacity-sheet.md`

**Description:** Pre-qualifies customer requests for quotation by comparing them against the machine capacity sheet.

**Instructions:**

```
ROLE
You are a technical pre-sales assistant performing the initial evaluation of requests for quotation.

OBJECTIVE
Given the text of a customer email, determine whether the request is feasible, what is missing to prepare a quote, and what questions to ask the customer.

INPUT
The text of an email pasted by the user.

PROCEDURE
1. Extract from the email: sector, part type, dimensions, material, quantity, requested lead time, special constraints.
2. Compare each requirement against the machine capacity sheet in your knowledge. Convert units of measurement before comparing.
3. Classify the request as: FEASIBLE, NEEDS CLARIFICATION, NOT FEASIBLE.
4. Prepare questions to ask the customer for any missing information.

OUTPUT FORMAT
- Verdict: FEASIBLE / NEEDS CLARIFICATION / NOT FEASIBLE, with a one-sentence justification.
- Requirements table with columns: Requirement | Value in Email | Comparison with Capacity Sheet.
- Missing information (bulleted list).
- Questions for the customer (maximum 5).

RULES
- Use only the machine capacity sheet to evaluate feasibility. Do not use general knowledge.
- If a value is not in the email, write "not specified". Do not estimate it.
- Do not propose alternative solutions (e.g., printing in multiple sections) unless provided for in the capacity sheet.

EDGE CASES
- If even a single requirement exceeds the limits in the sheet, the verdict is NOT FEASIBLE and you must state which requirement exceeds the limit and by how much.
- If the email is not about a request for quotation, state so and do not fill in the table.
```

**Test prompts:**

1. Paste `email-01-complete.txt` → expected: FEASIBLE, complete table.
2. Paste `email-02-incomplete.txt` → expected: NEEDS CLARIFICATION, relevant questions.
3. Paste `email-03-out-of-capacity.txt` → expected: NOT FEASIBLE, citing the dimension that exceeds capacity.

**Gate Test:** prompt 3 returns NOT FEASIBLE, identifies the out-of-bounds requirement, and does not propose invented workarounds.

**Common mistakes:** the agent fails to convert meters to millimeters; the agent suggests "splitting the part into multiple sections". Fix this in the instructions (Step 2 of Procedure and Rule 3), not in the prompt.

### 5.3 Step 2 · Root agent "Pre-Sales Desk"

| Agent | Role | Data Source |
|---|---|---|
| **Pre-Sales Desk** (root) | Understands the request and routes it | None |
| Pre-qualification | The Step 1 agent | Data bucket (`machine-capacity-sheet.md`) |
| Materials | Answers questions on material properties and selection | Data bucket (`materials-datasheet.md`) |
| Case Studies | Finds relevant references by sector | Data bucket (`case-study.md`) |
| Copywriter | Drafts the customer reply based on outputs from the other sub-agents | None |

**Root Instructions:**

```
ROLE
You coordinate the technical pre-sales desk. Do not answer domain questions yourself: delegate to your sub-agents.

PROCEDURE
1. If the user pastes an RFQ email, always call Pre-qualification.
2. If the request includes questions about materials, call Materials.
3. If the request asks for references or examples of similar work, or specifies an industry sector, call Case Studies.
4. At the end, always call Copywriter, passing it all collected outputs, to produce a single unified reply for the customer.

OUTPUT FORMAT
- Internal summary (for sales): pre-qualification verdict and sub-agents consulted.
- Draft customer reply (from Copywriter).

RULES
- Do not add technical information that did not come from the sub-agents.
- If Pre-qualification returns NOT FEASIBLE, the draft must state so politely without promising alternatives.
```

**Sub-agent Instructions (summary to expand):**

- **Materials:** "Answer using only information from the datasheets. For each suggested material, state the property that makes it suitable. If no material is suitable, say so."
- **Case Studies:** "Search the case studies for entries in the same sector or a similar application. Return at most 2 cases with title and a one-sentence summary. If none match, say so."
- **Copywriter:** "Write a reply to the customer in English, professional tone, maximum 150 words. Use only the information received. If there are questions for the customer, list them at the end."

**Test prompts:**

1. `email-01-complete.txt` + "The customer also asks which material we recommend for a marine mold and whether we have examples of similar projects."
2. `email-03-out-of-capacity.txt`

**Gate Test:** prompt 1 engages both Materials and Case Studies and produces **one single** coherent draft; prompt 2 produces a draft that promises no alternatives.

### 5.4 Step 3 · Workflow "RFQ Intake"

Rebuild the Step 2 sub-agents as a chain of `Gemini Agent` blocks:

| # | Step | Configuration |
|---|---|---|
| 0 | Trigger | **Manual** with input field `email_text`. Advanced variant: **Event** on the email connector, filtered by subject (e.g., contains "RFQ") |
| 1 | Gemini Agent (`Pre-qualification`) | Bucket: `machine-capacity-sheet.md`. Same instructions as sub-agent *Pre-qualification*, input: `${trigger.email_text}` |
| 2 | Gemini Agent (`Materials`) | Bucket: `materials-datasheet.md`. Same instructions as sub-agent *Materials*, input: `${trigger.email_text}` |
| 3 | Gemini Agent (`Case Studies`) | Bucket: `case-study.md`. Same instructions as sub-agent *Case Studies*, input: `${trigger.email_text}` |
| 4 | Gemini Agent (`Copywriter`) | No data source. Same instructions as sub-agent *Copywriter*, combines `${step1.output}`, `${step2.output}`, `${step3.output}` |
| 5 | Approval | Shows the approver the draft reply and the pre-qualification verdict |
| 6 | Action | Send the reply via email connector; or, if sending is disabled, create a draft or simply close with output |

**Final Test:** with `email-02-incomplete.txt`, the flow pauses at Approval with the questions for the customer; when rejected, nothing is sent.

---

## 6. Case 2 · Technical Support

**Objective:** help Level 1 support respond to a field issue report and prepare an escalation when needed.

### 6.1 Data Kit (`02-technical-support/`)

| File | Content to Prepare |
|---|---|
| `troubleshooting-manual.md` | 3–4 pages with an alarm table: code (e.g., E101–E110, fictional), description, probable causes, step-by-step verification procedure, when to call a technician. Code **E199** must not appear |
| `ticket-history.md` | 20-row table with columns `ticket_id, date, machine_serial, alarm_code, customer_description, solution, resolution_time_hours`. Include at least 3 tickets on the same alarm (e.g., E104) |
| `service-report-template.md` | Fields: customer, serial number, alarm code, description, checks already performed, priority, suspected spare parts |

There are two edge cases: alarm E199 (absent from the manual) and a report missing the machine serial number (used in Step 3).

### 6.2 Step 1 · Agent "Manual Support"

**Knowledge:** `troubleshooting-manual.md`

**Instructions:**

```
ROLE
You are a Level 1 technical support assistant for industrial machines.

OBJECTIVE
Guide the operator through verifying an alarm using exclusively the troubleshooting manual.

PROCEDURE
1. Identify the alarm code or described symptom.
2. Look up the corresponding entry in the manual.
3. Report the probable causes and verification procedure in the exact order given in the manual.

OUTPUT FORMAT
- Alarm: code and description.
- Probable causes.
- Verification procedure (numbered steps).
- When to call a technician.
- Source: manual section.

RULES
- Always cite the manual section from which you take the procedure.
- Do not suggest interventions that are not in the manual, even if they seem reasonable.

EDGE CASES
- If the code or symptom is not in the manual, state that the procedure is undocumented and recommend escalating to a technician. Do not propose generic checks.
```

**Test prompts:**

1. "The machine reports E104, what should I check?"
2. "The customer says the extruder stops mid-print without an alarm code." (symptom documented in the manual)
3. "Alarm E199, how do I proceed?"

**Gate Test:** prompt 3 states that the procedure is undocumented and recommends escalation, without inventing checks.

### 6.3 Step 2 · Root agent "Support Triage"

| Agent | Role | Data Source |
|---|---|---|
| **Support Triage** (root) | Classifies the ticket and coordinates | None |
| Manual | The Step 1 agent | Data bucket (`troubleshooting-manual.md`) |
| Ticket History | Finds similar past tickets and how they were resolved | Data bucket (`ticket-history.md`) |
| Escalation | Fills out the service report for the technician | Data bucket (`service-report-template.md`) |

**Root Instructions:**

```
ROLE
You triage incoming technical support tickets.

PROCEDURE
1. Always call Manual with the alarm code or symptom.
2. Always call Ticket History to check whether the issue has occurred before.
3. Call Escalation if: the manual does not document the issue, or the manual states to call a technician, or the ticket history shows that the issue has recurred more than twice on the same serial number.

OUTPUT FORMAT
- Priority: HIGH / MEDIUM / LOW, with justification.
- What to do immediately (from Manual).
- Past occurrences (from Ticket History).
- Service report (from Escalation), only if applicable.

RULES
- Do not paraphrase manual procedures: report them verbatim.
- If sub-agents provide conflicting information, flag it.
```

**Sub-agents:**

- **Ticket History:** "Search `ticket-history.md` for tickets with the same alarm code or a similar description. Return at most 3 tickets with ID, date, solution, and resolution time. If there are none, say so."
- **Escalation:** "Fill out the service report using only the data received. Write 'to be completed' in any fields without data. Do not assign spare parts unless indicated by the manual or ticket history."

**Gate Test:** for "E104 on serial number M-0042", the response combines the manual procedure with at least one similar ticket from the history.

### 6.4 Step 3 · Workflow "New Support Ticket"

Rebuild the Step 2 sub-agents as a chain of `Gemini Agent` blocks:

| # | Step | Configuration |
|---|---|---|
| 0 | Trigger | Manual with fields `description`, `alarm_code`, `serial_number` (the last one **optional**) |
| 1 | Request info | If `serial_number` is empty, ask the operator to enter it. If the builder does not support a condition, include the step unconditionally and have the operator reply "already provided" when present |
| 2 | Gemini Agent (`Manual`) | Bucket: `troubleshooting-manual.md`. Same instructions as sub-agent *Manual*, input: `${trigger.alarm_code}` and `${trigger.description}` |
| 3 | Gemini Agent (`Ticket History`) | Bucket: `ticket-history.md`. Same instructions as sub-agent *Ticket History*, input: code, description, and serial number (`${trigger.serial_number} ${step1.output}`) |
| 4 | Gemini Agent (`Escalation and Triage`) | Bucket: `service-report-template.md`. Same instructions as sub-agent *Escalation* + priority assignment, combining `${step2.output}` and `${step3.output}` |
| 5 | Approval | The service manager approves priority and service report |
| 6 | Action | Notify the technician (email or Chat message), or close with output |

**Final Test:** a ticket submitted without a serial number triggers the Request info step before triage begins.

---

## 7. Case 3 · Supplier Quotes

**Objective:** read and compare supplier quotes in a standardized way and prepare for renegotiation.

### 7.1 Data Kit (`03-supplier-quotes/`)

| File | Content to Prepare |
|---|---|
| `supplier-quote-A.md` | Complete quote: unit price, quantity, delivery lead time, payment terms, validity, warranty |
| `supplier-quote-B.md` | Complete quote, but with higher price and shorter lead time |
| `supplier-quote-C.md` | Quote **missing payment terms** and with validity tucked away in an inconspicuous spot |
| `procurement-evaluation-criteria.md` | Weighted criteria: price 40%, lead time 30%, payment terms 20%, warranty 10% (sample weights) |

The edge case is Quote C.

### 7.2 Step 1 · Agent "Quote Extractor"

**Knowledge:** none — the user attaches or pastes one quote at a time. Alternatively, upload all three quotes and ask the user to specify which one to analyze.

**Instructions:**

```
ROLE
You are a procurement assistant who extracts structured data from supplier quotes.

OBJECTIVE
Return the data from a quote in a standardized, consistent table so it can be compared against other quotes.

OUTPUT FORMAT
A two-column table, Field | Value, with these rows in exact order:
Supplier, Unit Price, Quantity, Total Price, Delivery Lead Time, Payment Terms, Quote Validity, Warranty, Notes.

RULES
- Report values exactly as written in the quote, including units of measurement.
- If a field is missing, write "not specified". Never use an estimated or "typical" value.
- Calculate Total Price only if both Unit Price and Quantity are present.
- In Notes, flag any ambiguities or special conditions.
```

**Gate Test:** on Quote C, Payment Terms is reported as "not specified" and Quote Validity is accurately found.

### 7.3 Step 2 · Root agent "Quote Analysis"

| Agent | Role | Data Source |
|---|---|---|
| **Quote Analysis** (root) | Coordinates extraction, comparison, and negotiation | None |
| Extractor | The Step 1 agent | Data bucket (the three quotes) |
| Analyst | Builds the weighted comparison matrix | Data bucket (`procurement-evaluation-criteria.md`) |
| Negotiator | Identifies renegotiation leverage points | None |

**Root Instructions:**

```
PROCEDURE
1. Call Extractor for each available quote.
2. Pass all extracted tables to Analyst.
3. Pass the comparison matrix to Negotiator.

OUTPUT FORMAT
- Comparison matrix (from Analyst).
- Ranking with scores.
- Points to renegotiate per supplier (from Negotiator).

RULES
- Any quote containing "not specified" fields must be marked as INCOMPLETE in the ranking — neither excluded nor filled in.
```

**Sub-agents:**

- **Analyst:** "Build a table with suppliers as columns and criteria as rows. Assign a score from 1 to 5 per criterion according to the evaluation criteria and compute the weighted total. If a criterion is 'not specified', assign 0 and mark the quote INCOMPLETE."
- **Negotiator:** "For each supplier, indicate at most 3 points on which to request an improvement, justifying each by comparison with the other suppliers. Use only values from the matrix."

**Gate Test:** the matrix compares all three quotes and flags Quote C as incomplete.

### 7.4 Step 3 · Workflow "New Supplier Quote"

Rebuild the Step 2 sub-agents as a chain of `Gemini Agent` blocks:

| # | Step | Configuration |
|---|---|---|
| 0 | Trigger | Manual with supplier name (`target_supplier`); advanced variant: Event on new file in the kit folder, if available |
| 1 | Gemini Agent (`Extractor`) | Bucket: the three quotes (`supplier-quote-A.md`, `B`, `C`). Same instructions as sub-agent *Extractor* applied across all quotes |
| 2 | Gemini Agent (`Analyst`) | Bucket: `procurement-evaluation-criteria.md`. Same instructions as sub-agent *Analyst*, input: `${step1.output}` |
| 3 | Gemini Agent (`Negotiator and Draft`) | No data source. Identifies renegotiation points for `${trigger.target_supplier}` from `${step2.output}` and drafts a renegotiation email (max 120 words) |
| 4 | Approval | The buyer approves the draft |
| 5 | Action | Send via email, or close with output |

**Final Test:** the draft cites only points present in the comparison and is never sent without approval.

---

## 8. Case 4 · From Minutes to Actions

**Objective:** turn a meeting transcript into verified decisions and action items, and send the follow-up.

### 8.1 Data Kit (`04-minutes-to-actions/`)

| File | Content to Prepare |
|---|---|
| `meeting-transcript-1.txt` | Status meeting of 20–30 speaking turns, with 3 decisions and 4 action items — all with explicit owner and deadline |
| `meeting-transcript-2.txt` | Meeting with 5 action items: one **without an owner** ("someone should check with the supplier"), one assigned to an owner **not listed** among participants, and one with a vague deadline ("shortly") |
| `participants.md` | Table with `name, role, email` of participants, using fictional names and emails |

### 8.2 Step 1 · Agent "Minutes Extractor"

**Instructions:**

```
OBJECTIVE
From a meeting transcript, extract decisions, action items, and open points.

OUTPUT FORMAT
1. Decisions (bulleted list).
2. Action Items: table Action | Owner | Deadline | Status. Status is either OK or TO VERIFY.
3. Open Points (bulleted list).

RULES
- An action item without an explicitly named owner gets Owner "UNASSIGNED" and Status TO VERIFY.
- A vague deadline ("shortly", "as soon as possible") is quoted verbatim with Status TO VERIFY.
- Do not infer the owner from whoever spoke last or whoever seems responsible for that domain.
```

**Gate Test:** on transcript 2, the ownerless action item is marked UNASSIGNED rather than attributed to a person.

### 8.3 Step 2 · Root agent "Meeting Follow-up"

| Agent | Role | Data Source |
|---|---|---|
| **Meeting Follow-up** (root) | Coordinates | None |
| Extractor | The Step 1 agent | None |
| Verifier | Cross-checks owners against participants and validates deadlines | Data bucket (`participants.md`) |
| Copywriter | Drafts the follow-up email | None |

**Sub-agents:**

- **Verifier:** "For each action item, check that the owner is in the participant list and add their email address. If not listed, flag OWNER NOT IN LIST. If the deadline is not a calendar date, flag DEADLINE TO BE DEFINED. Do not fix the data: flag it."
- **Copywriter:** "Write the follow-up email: decisions, table of verified action items, followed by a 'To Clarify' section listing flagged action items. Maximum 200 words excluding the table."

**Root Instructions:** call in sequence Extractor → Verifier → Copywriter; display the count of action items requiring clarification at the very top.

**Gate Test:** the owner absent from the participant list is flagged before the follow-up is drafted, and appears under the "To Clarify" section.

### 8.4 Step 3 · Workflow "Meeting Follow-up"

Rebuild the Step 2 sub-agents as a chain of `Gemini Agent` blocks:

| # | Step | Configuration |
|---|---|---|
| 0 | Trigger | Manual with input field `transcript` |
| 1 | Gemini Agent (`Extractor`) | No data source. Same instructions as sub-agent *Extractor*, input: `${trigger.transcript}` |
| 2 | Gemini Agent (`Verifier`) | Bucket: `participants.md`. Same instructions as sub-agent *Verifier*, input: `${step1.output}` |
| 3 | Gemini Agent (`Copywriter`) | No data source. Same instructions as sub-agent *Copywriter*, input: `${step1.output}` and `${step2.output}` |
| 4 | Approval | The meeting organizer approves |
| 5 | Action | Send to participants, or close with output |

**Final Test:** when approval is rejected, the flow terminates without sending anything. Have groups explicitly test rejection, not just approval.

---

## 9. Case 5 · Job Order Status

**Objective:** get quick answers on job order status and generate a weekly risk report.

### 9.1 Data Kit (`05-job-order-status/`)

| File | Content to Prepare |
|---|---|
| `job-order-status.md` | 15-row table, columns: `job_order_code, customer, machine, phase, expected_delivery_date, status, progress_%, notes`. Possible phases: design, procurement, assembly, testing, shipping. Include **one job order with a past delivery date and status "in progress"**, plus 2–3 job orders with notes indicating a risk (e.g., "component supplier delay") |
| `thresholds.md` | Sample rules: delayed if the delivery date is past and status is not "delivered"; at risk if fewer than 15 days remain and progress is below 70%, or if notes mention suppliers or spare parts |
| `job-order-status-quiet-week.md` | Table with the same columns, containing zero delayed or at-risk job orders. Used for the Step 3 test |

Note: in Step 1 `job-order-status.md` can be uploaded directly to *Knowledge*, whereas in Step 2 the sub-agents point to the bucket hosting the data.

### 9.2 Step 1 · Agent "Job Order Lookup"

**Instructions:**

```
OBJECTIVE
Answer specific questions about job order status using only data from the job order sheet.

RULES
- Always cite the job order code in your answer.
- If the requested job order is not in the sheet, state so explicitly. Do not look for "similar" job orders.
- If the question asks for a metric not present in the sheet (e.g., margin, cost), state so.
- Use today's date to determine whether a delivery date is already past.
```

**Test prompts:** "Which job orders are in testing?", "When are we delivering C-2026-014?", "What is the status of C-2026-099?" (non-existent).

**Gate Test:** for the non-existent job order, the agent explicitly states that it is not present in the sheet.

### 9.3 Step 2 · Root agent "Job Order Report"

| Agent | Role | Data Source |
|---|---|---|
| **Job Order Report** (root) | Coordinates and determines output format | None |
| Lookup | The Step 1 agent | Data bucket (`job-order-status.md`) |
| Delay Analyst | Applies the delay rule | Data bucket (`job-order-status.md`, `thresholds.md`) |
| Risk Analyst | Applies the risk rules | Data bucket (`job-order-status.md`, `thresholds.md`) |
| Report Writer | Writes the final report | None |

**Root Instructions:**

```
PROCEDURE
- Specific question about a single job order → Lookup only.
- Request for a report or overall status overview → Delay Analyst, Risk Analyst, then Report Writer.

OUTPUT FORMAT
1. Delayed (sorted by days overdue, most severe at the top).
2. At risk (with the reason).
3. On track (count only).

RULES
- A job order with a past delivery date and status other than "delivered" is DELAYED, even if its status says "in progress".
- If there are no delayed or at-risk job orders, state so explicitly. Do not invent critical issues.
```

**Gate Test:** the overdue job order marked "in progress" appears right at the top of the report.

### 9.4 Step 3 · Workflow "Weekly Status Report"

Rebuild the Step 2 sub-agents as a chain of `Gemini Agent` blocks:

| # | Step | Configuration |
|---|---|---|
| 0 | Trigger | Weekly **Schedule** (e.g., Monday at 8:00 AM). In the classroom, to test it right away, add or use a Manual trigger |
| 1 | Gemini Agent (`Delay Analyst`) | Bucket: `job-order-status.md`, `thresholds.md`. Same instructions as sub-agent *Delay Analyst* |
| 2 | Gemini Agent (`Risk Analyst`) | Bucket: `job-order-status.md`, `thresholds.md`. Same instructions as sub-agent *Risk Analyst* |
| 3 | Gemini Agent (`Report Writer`) | No data source. Same instructions as sub-agent *Report Writer*, input: `${step1.output}` and `${step2.output}` |
| 4 | Approval | The OPS manager approves |
| 5 | Action | Send to the team (email or Chat), or close with output |

**Final Test:** on the "quiet week" dataset, the report states that there are no critical issues, without inventing risks.

---

## 10. "Simple Mode" Track — Outlook Connector Only (Cases 6 and 7)

When the workshop is aimed at a broad cross-functional business audience or when you prefer not to introduce sub-agents, data buckets, and Workflow Builder, **Cases 6 and 7** offer a **streamlined 3-step progression** using **exclusively the Microsoft Outlook connector** (no other connectors enabled):

1. **Step 1 · Prompt (direct use in chat):** quick summaries or initial drafts on text copied and pasted into the main Gemini Enterprise chat, letting participants experience firsthand both the speed and the limitations of working without company context.
2. **Step 2 · (Simple) Agent without connectors:** a single agent in *Agent Designer* with fixed instructions and files uploaded directly to *Knowledge* (FAQs, SLAs, templates, guidelines, stakeholder directory), still tested via copy-paste.
3. **Step 3 · (Simple) Agent with Outlook connector:** the exact same single agent with *Knowledge* + **only the Microsoft Outlook connector** enabled under *Data sources & tools*, to read live emails/calendar events and save replies into the Outlook *Drafts* folder (*Create message*, keeping *Send mail* disabled).

> **Prerequisite for Step 3 on Outlook:** each participant emails themselves 2–3 test messages (and for Case 7 creates 1 event on their own Outlook Calendar) keeping the `[WORKSHOP]` subject prefix already provided in the `data-kit/` files, ensuring the agent filters only workshop items without touching real work emails.

---

### 10.1 Case 6 · Inbox Triage and Reply Drafts (`06-inbox-triage/`)

- **Complete guide and prompts:** [`06-inbox-triage/README.md`](./06-inbox-triage/README.md)
- **Objective:** classify incoming emails by department and priority/SLA, check mandatory data fields, and prepare drafts compliant with FAQs, reply templates, and authority limits ("Red Rules"), saving them as drafts in Outlook.
- **Data kit (`06-inbox-triage/data-kit/`):**
  - `triage-guidelines-and-sla.md` and `faq-and-reply-templates.md` *(Knowledge for Steps 2 and 3)*;
  - `email-01-invoice-clarification.txt` *(standard billing inquiry)*, `email-02-incomplete-operational-urgency.txt` *(high-priority outage missing Contract Code `NS-XXXX`)*, `email-03-out-of-authority-refund-request.txt` *(edge case: 25% credit note request + notice period reduction from 60 to 15 days)*, `morning-inbox-batch.txt` *(4 mixed emails including a newsletter to ignore)*.
- **Gate & Final Test:** on email 3, the agent flags `ESCALATE INTERNALLY` (`amministrazione@...` + `ufficio.legale@...`), strictly applies the neutral holding *Template C* without promising discounts/refunds/waivers, and in Step 3 saves **only a draft** in Outlook without sending it.

---

### 10.2 Case 7 · Meeting Preparation and Follow-up (`07-meeting-prep-followup/`)

- **Complete guide and prompts:** [`07-meeting-prep-followup/README.md`](./07-meeting-prep-followup/README.md)
- **Objective:** prepare the *5-Minute Prep Sheet* before the meeting by cross-referencing the Outlook Calendar invite against the email thread in Outlook Mail, and turn post-meeting notes into a verified follow-up email draft saved in Outlook.
- **Data kit (`07-meeting-prep-followup/data-kit/`):**
  - `meeting-guidelines-and-templates.md` and `project-stakeholder-directory.md` *(Knowledge for Steps 2 and 3)*;
  - `calendar-invite-aurora-status-review.txt` + `pre-meeting-email-thread.txt` *(for the Prep phase: contain an unanswered technical question on 4096-bit SAML and out-of-scope requests regarding Go-Live and a free "Tender Management" module)*;
  - `post-meeting-notes-complete.txt` + `post-meeting-notes-edge-case.txt` *(for the Follow-up phase: the edge case includes an action item without an owner, an action item assigned to `Stefano Riva` who is missing from the directory, a vague `"as soon as possible"` deadline, and an out-of-contract request to isolate)*.
- **Gate & Final Test:** in the *Prep* phase, the agent isolates extra-contractual requests under *Out-of-Scope Topics*; in the *Follow-up* phase, it catches all 4 traps without inventing an email address for `Stefano Riva`, and in Step 3 saves **only the follow-up draft** in Outlook without modifying the calendar or sending messages.

---

## 11. 2h Workshop Track — Project + Technical Manual + Outlook Only (Cases 8 and 9)

These two cases fit the **2-hour Workshop** agenda tailored for an industrial/manufacturing setting (robotic LFAM machine builder) using **exclusively the Microsoft Outlook connector** (no Teams connector, no sub-agents, no workflows):

1. **Step 1 · Gemini Project (Cross-document data extraction):** participants create a Project with **3 interconnected fleet or job-order documents** and pass 3 cross-document tests (numerical calculations, warranties/deadlines, *Go/No-Go* readiness status, and anti-hallucination checks on non-existent data).
2. **Step 2 · (Simple) Agent without connectors (Technical Domain — Machine Manual):** in *Agent Designer*, they build a single agent with fixed instructions and a complete 5-chapter **synthetic Operation and Maintenance Manual** (operating limits, PPE and safety prohibitions, scheduled maintenance, alarm codes + undocumented code trap) uploaded to *Knowledge*.
3. **Step 3 · (Simple) Agent with Outlook connector only:** they connect the exact same technical agent **only to Microsoft Outlook** to read emails (plus calendar in Case 9) tagged `[WORKSHOP]` and automatically save reply or follow-up drafts into the *Drafts* folder (*Create message*, never automatic send).

> **Advanced challenge for faster groups:** upon finishing Case 8 or Case 9, faster groups can tackle **[Case 4 · From Minutes to Actions](./04-minutes-to-actions/README.md)** working as always with a **pasted `transcript`** (since the Microsoft Teams connector is not available).

---

### 11.1 Case 8 · Machine Technical Support and Inbox Triage (`08-service-manual-inbox/`)

- **Complete guide and prompts:** [`08-service-manual-inbox/README.md`](./08-service-manual-inbox/README.md) · **Participant Handout:** [`2026-11-20_Case8-Service-Manual-Inbox_rev.docx`](./08-service-manual-inbox/2026-11-20_Case8-Service-Manual-Inbox_rev.docx)
- **Objective:** (1) cross-reference the `Heron-X 400` fleet registry, 2026 service log, and spare parts pricelist inside a **Gemini Project**; (2) build a **technical agent** grounded in the **`Heron-X 400` Operation and Maintenance Manual (Rev. 3.1)**; (3) connect it to **Microsoft Outlook (Mail)** to triage customer emails and save reply drafts without sending them.
- **Data kit (`08-service-manual-inbox/data-kit/`):**
  - `dossier-01-customer-machine-registry.md`, `dossier-02-service-and-fault-log.md`, `dossier-03-spare-parts-pricelist-and-terms.md` *(Step 1 Project — 5 billable interventions out of 10 totaling €3,250; 2 scheduled services < 50 h away with 15% Premium discount; `HX-2025-099` and missing shipping-cost traps)*;
  - `heron-x400-operation-and-maintenance-manual.md` and `service-guidelines-and-templates.md` *(Steps 2 and 3 Knowledge)*;
  - `email-01-1000h-maintenance.txt`, `email-02-incomplete-machine-downtime.txt`, `email-03-unknown-alarm-and-warranty.txt` *(edge case: undocumented `A299` + light-curtain bypass request + free warranty claim + 20% discount)*, `email-04-trade-show-newsletter.txt` *(`INFORMATIONAL ONLY` noise)*.
- **Gate & Final Test:** always refuses bypassing optical safety barriers (Ch. 2), declares `A299` undocumented without inventing troubleshooting steps, escalates to both `ingegneria.l2@lfam-demo.example` and `contratti@lfam-demo.example` using *Template C*, and in Step 3 saves **only a draft** in Outlook.

---

### 11.2 Case 9 · Machine Commissioning, Technical Support and Meeting Management (`09-project-manual-meeting/`)

- **Complete guide and prompts:** [`09-project-manual-meeting/README.md`](./09-project-manual-meeting/README.md) · **Participant Handout:** [`2026-11-20_Case9-Project-Manual-Meeting_rev.docx`](./09-project-manual-meeting/2026-11-20_Case9-Project-Manual-Meeting_rev.docx)
- **Objective:** (1) cross-reference customer order specification `COMM-2026-088`, Pre-FAT test report, and stakeholder directory/milestones inside a **Gemini Project**; (2) build a **technical/PMO agent** grounded in the **`Kestrel-500 Hybrid` Operation and Maintenance Manual (Rev. 2.4)**; (3) connect it to **Microsoft Outlook (Calendar + Mail)** to generate the *5-Minute Prep Sheet* and save the `[FOLLOW-UP]` email in Drafts without sending.
- **Data kit (`09-project-manual-meeting/data-kit/`):**
  - `dossier-01-customer-order-specification.md`, `dossier-02-fat-test-report.md`, `dossier-03-stakeholder-directory-and-plan.md` *(Step 1 Project — 3 tests with deviations out of 6, `NO-GO` status due to 2 open criticalities, `FAT-07`/`PEKK-CF` and missing late-penalty traps)*;
  - `kestrel-500-operation-and-maintenance-manual.md`, `technical-meeting-guidelines-and-templates.md`, and `dossier-03-stakeholder-directory-and-plan.md` *(Steps 2 and 3 Knowledge)*;
  - `calendar-invite-kestrel-status-review.txt`, `pre-meeting-email-thread-kestrel.txt` *(unanswered technical questions resolved via the Manual + aluminum milling prohibition + out-of-contract requests)*, `post-meeting-notes-complete.txt`, and `post-meeting-notes-edge-case.txt` *(4 traps: ownerless action item, `Marco Bellini` not in directory, vague `"as soon as possible"` deadline, out-of-contract/aluminum requests)*.
- **Gate & Final Test:** blocks aluminum milling and compressed air on carbon fiber dust (Ch. 2), declares `K488` undocumented without inventing checks, catches all 4 traps in the post-meeting notes without inventing an email address for `Marco Bellini`, and in Step 3 saves **only the `[FOLLOW-UP]` draft** in Outlook.

---

## 12. Facilitator Checklist

### The Day Before

- [ ] Gemini Projects, Agent Designer (and Workflow Builder for Cases 1–5) visible using a participant test account
- [ ] Complete data kit across all nine subfolders, accessible from participant accounts
- [ ] For Cases 6–9: **Microsoft Outlook** connector authorized and tested for read + draft creation (*Create message*, with *Send mail* disabled)
- [ ] Every selected case built at least once up to the target step, with all tests passing
- [ ] At least one Step 3 workflow (Cases 1–5) or Outlook draft creation (Cases 6–9) tested end-to-end
- [ ] UI labels aligned with this guide

### During the Build

- [ ] Every group uses its group prefix in project and agent names
- [ ] The facilitator verifies each Gate Test in person before allowing a group to advance
- [ ] Anyone stuck for more than 5 minutes gets a hint pointing to their instructions, not the finished answer

### Before the Debrief

- [ ] Every group can clearly state which step they reached and which test they passed
- [ ] Agents remain inside the sandbox: no publishing or sharing outside the intended perimeter

---

## 13. Common Issues

| Symptom | Probable Cause | What to Suggest |
|---|---|---|
| Agent invents missing values | Missing explicit anti-hallucination rule | Add "If a value is missing, write 'not specified'" plus an edge case |
| Agent uses general knowledge instead of kit files | Instructions do not restrict the source | Add "Use only [file]"; verify that the files are uploaded in *Knowledge* |
| Root agent answers without delegating | Vague sub-agent descriptions or root instructions lacking delegation rules | Rewrite descriptions with each sub-agent's exact task; in the root, add a "when → whom" rule for each sub-agent |
| Two sub-agents give conflicting answers | Overlapping data sources | Point each sub-agent strictly to the files in the bucket it actually needs |
| Workflow does not receive trigger data | Missing output reference in the step prompt | Explicitly pass fields using the reference to the trigger or previous step's output |
| Nobody can find the approval prompt | Not looking under *Runs* | Show the *Needs Review* status and where to open the run |
| Outlook connector reads too many personal emails (Cases 6–9) | Search query in prompt is too broad | Always use the `[WORKSHOP]` subject prefix on test emails/events and require it in the prompt |
| Connector cannot write / create the draft | *Create message* action not enabled in sandbox | Check Outlook connector action permissions, or finish with the ready-to-copy draft in chat |
