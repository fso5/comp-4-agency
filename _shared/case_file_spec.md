# Case File Spec

**This file is the contract.** Every specialist in the system reads from and writes to a Case File. If you change this spec, you change the system. Don't change it without Diana.

---

## What a Case File is

A Case File is one folder under `_cases/` that represents a single piece of work moving through the agency. A "piece of work" is usually a person — a buyer, a seller, sometimes both — but it can also be a referral lead that hasn't been qualified yet, or a research request that's not tied to a specific client.

**One person, one Case File.** When a buyer becomes a client and goes under contract, you don't start a new Case File. You keep adding to the existing one. The Case File is the spine of the relationship.

---

## Naming convention

```
_cases/<YYYY-MM-DD>-<lastname>-<intent>/
```

- `YYYY-MM-DD` — the date the case was opened (when the lead first arrived)
- `lastname` — primary contact's last name, lowercase, no spaces (e.g. `anderson`, `garcia-lopez`)
- `intent` — one of `buyer`, `seller`, `both`, `unknown`

Examples:
- `2026-05-08-anderson-buyer/`
- `2026-04-22-okonkwo-seller/`
- `2026-05-12-garcia-lopez-both/`
- `2026-05-14-unknown-unknown/` (cold lead, no name yet)

If a case starts as `unknown` and gets clarified, **rename the folder** and update the `case_id` in `case.md`. Yes, this is a hassle. It's worth it because Diana can scan `_cases/` and immediately see what's going on.

**When you have a first name but not a last name** (common with Instagram DMs and short web inquiries): use the first name in the `lastname` slot rather than `unknown`. So `@sara_mc_austin` becomes `2026-05-14-sara-buyer/`. If a social handle is the only identifier and the first name isn't clear, use a sanitized version of the handle: `2026-05-14-sara-mc-buyer/`. We rename to a real last name as soon as we have one. The goal is scannability of `_cases/`; `unknown-unknown` folders pile up and become indistinguishable.

---

## Folder structure

```
_cases/<case_id>/
├── case.md                # The spine. Header + log. Every specialist updates this.
├── qualification.md       # Produced by 01_lead_qualifier
├── research_brief.md      # Produced by 02_property_research (may have multiple, see below)
├── communication_log.md   # Produced by 03_client_communication (rolling log of all drafts)
└── transaction_tracker.md # Produced by 04_transaction_coordinator (once under contract)
```

Files appear in the folder as the work progresses. A brand-new case may only have `case.md` and `qualification.md`. A deep deal has all five.

**Multiple research briefs:** If a buyer requests research on three different neighborhoods over the course of a search, do not overwrite. Number them: `research_brief.md`, `research_brief_02.md`, `research_brief_03.md`. The most recent one is the latest version of the active question, not the only one.

---

## `case.md` — the spine

Every `case.md` has this exact structure:

```markdown
---
case_id: 2026-05-08-anderson-buyer
client_name: Jamie & Pat Anderson
primary_contact: jamie.anderson@example.com / (512) 555-0142
intent: buyer
stage: under_contract
current_owner: 04_transaction_coordinator
assigned_agent: Maria
opened: 2026-05-08
last_updated: 2026-05-14
priority: standard
---

# Case: Jamie & Pat Anderson — Buyer

## Snapshot
One paragraph, max five sentences. What is this case, who is the client, what stage are we in, what is the most important thing the next person to touch this file needs to know.

## Stage history
- 2026-05-08 → new_lead (opened by orchestrator from website form)
- 2026-05-08 → qualified (01_lead_qualifier)
- 2026-05-09 → researching (02_property_research, neighborhood brief on Mueller)
- 2026-05-10 → showing (03_client_communication drafted showing-confirm emails)
- 2026-05-13 → under_contract (offer accepted on 1247 Berkman)
- 2026-05-13 → coordinating (04_transaction_coordinator took over)

## Log
Reverse-chronological. Every specialist adds an entry when they finish work.
Each entry is one or two lines. Detail lives in the artifact files, not here.

- 2026-05-14 — 04_transaction_coordinator — Day 1 of option period. Inspection scheduled 5/16 9am. Tracker updated.
- 2026-05-13 — 04_transaction_coordinator — Picked up case. Contract executed. Tracker created.
- 2026-05-13 — 03_client_communication — Drafted offer-accepted celebration text (Maria's voice).
- ...

## Open Handoff Packets
The most recent Handoff Packet sits at the bottom. When a specialist finishes,
they append a new packet here. The orchestrator looks here first to see who is up.

(See current packet at bottom of file.)
```

### The header fields, in detail

| Field | Required | Values |
|---|---|---|
| `case_id` | yes | matches folder name exactly |
| `client_name` | yes | human-readable, e.g. "Jamie & Pat Anderson" |
| `primary_contact` | yes | email and/or phone — whatever Diana's team will actually use |
| `intent` | yes | `buyer`, `seller`, `both`, `unknown` |
| `stage` | yes | see Stages below |
| `current_owner` | yes | the folder name of whichever specialist is up, OR `human:<name>` if it's been escalated |
| `assigned_agent` | yes | which human on Diana's team owns the relationship (`Diana`, `Maria`, `Tom`, `Jordan`) |
| `opened` | yes | YYYY-MM-DD the case was first opened |
| `last_updated` | yes | YYYY-MM-DD anyone touched it |
| `priority` | yes | `standard`, `warm`, `urgent` |

### Stages

Use exactly these strings. Specialists check `stage` to decide what's appropriate.

- `new_lead` — just arrived, not yet qualified
- `qualified` — 01 finished, ready for next step
- `researching` — 02 is producing or has produced a research brief
- `showing` — actively scheduling/attending showings, primary owner is the human + 03 for comms
- `offer_pending` — offer drafted/sent, awaiting response
- `under_contract` — fully executed contract, 04 is now primary
- `coordinating` — synonym for under_contract, used while 04 is active
- `closed` — closed and funded
- `lost` — client went with another agent, or buyer fell through (note why in the log)
- `dormant` — client paused (timeline shifted, life event) — keep the file, set a follow-up reminder

---

## When to open a new Case File vs. update an existing one

**Open a new one when:**
- A brand-new person contacts the team
- An existing past client comes back for a new transaction more than 12 months after their last one closed (start fresh; link the old case in the Snapshot)

**Update an existing one when:**
- Anything happens with someone you already have a file on
- A buyer becomes a seller (or vice versa) within the same active relationship — update `intent` to `both`, don't fork

If you're unsure, ask Diana before opening a new file. Duplicate case files are the #1 way this system gets corrupted.

---

## Who can write what

| File | Who writes it |
|---|---|
| `case.md` (header) | Orchestrator owns the header. Specialists update `stage`, `current_owner`, `last_updated`. |
| `case.md` (log) | Every specialist appends one line when they finish. Never delete log entries. |
| `qualification.md` | 01_lead_qualifier only |
| `research_brief*.md` | 02_property_research only |
| `communication_log.md` | 03_client_communication only |
| `transaction_tracker.md` | 04_transaction_coordinator only |

A specialist can **read** any file in the case folder. They can only **write** their own.

The one exception: any specialist can append a Handoff Packet to `case.md` because that's how handoffs work. See `handoff_packet_spec.md`.

---

## What is NOT in the Case File

These belong elsewhere — don't try to cram them in:

- Long-form client preference notes that span deals (those live in Diana's CRM, if/when she adopts one)
- Listing photos, contracts, signed PDFs (those live in shared Drive; the tracker links to them)
- Personal life context the agent picked up from the client (note in the log only if directly relevant to the work)

The Case File is the operational record, not the relationship CRM. Keep it focused on the work.
