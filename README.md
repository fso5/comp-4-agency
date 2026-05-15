# Diana Lin Realty — Agency System

A multi-folder AI operating system for a boutique real estate team. Five specialists with explicit handoffs. Built so a new agent can be operational in a day.

> **Built for:** Diana Lin, owner of Diana Lin Realty, Austin TX. 4-person team. 60-80 transactions/year. Residential, mostly central Austin.

---

## What this is

Five specialists, organized into folders. Each specialist owns one part of the workflow. Specialists hand work to each other through a structured **Handoff Packet** appended to a shared **Case File**.

The folders ARE the system. There is no software to install. You point an AI (Claude, ChatGPT, or another assistant) at one of the specialist folders, give it the request, and it does its job — qualifies a lead, researches a neighborhood, drafts an email, tracks a transaction. The system runs on the structure, not the tool.

---

## The architecture in one diagram

```
                  ┌─────────────────────────┐
   INBOUND ─────► │  00_orchestrator        │  routes every request
   (any channel)  │  the front door         │  to the right specialist
                  └────────┬────────────────┘
                           │
        ┌──────────────────┼──────────────────────┐
        ▼                  ▼                      ▼
  ┌───────────┐    ┌───────────────┐    ┌─────────────────┐
  │ 01_lead_  │    │ 02_property_  │    │ 03_client_      │
  │ qualifier │    │ research      │    │ communication   │
  │           │    │               │    │                 │
  │ qualifies │    │ produces      │    │ drafts emails,  │
  │ new leads │    │ research      │    │ texts in the    │
  │ scores    │    │ briefs, CMAs  │    │ agent's voice   │
  └────┬──────┘    └───────┬───────┘    └────────┬────────┘
       │                   │                     │
       └───────────────────┼─────────────────────┘
                           ▼
                  ┌─────────────────────────┐
                  │ 04_transaction_         │
                  │ coordinator             │
                  │ tracks deadlines,       │
                  │ documents, deals        │
                  │ once under contract     │
                  └─────────────────────────┘

  Underneath it all: the CASE FILE — a folder under _cases/ that contains
  case.md (the spine) + artifact files (qualification.md, research_brief.md,
  communication_log.md, transaction_tracker.md). The Case File is what
  every specialist reads from and writes to.

  Handoff Packets — structured markdown blocks appended to case.md —
  are how specialists pass work to each other.
```

---

## How a typical request flows

Here's a real walk-through of a lead going from website form to closing. (The full version lives in `_cases/2026-05-08-anderson-buyer/` — read it end-to-end to see the system in action.)

### Day 0 — Lead arrives
Pat & Jamie Anderson fill out a website contact form. "Relocating from Denver, looking in East/Central Austin, budget around $700k."

**00_orchestrator** reads the inbound, sees no matching case, opens a new one at `_cases/2026-05-08-anderson-buyer/`. Routes to 01.

### Day 0 — Qualified
**01_lead_qualifier** reads the message, asks for missing info (or flags unknowns), produces `qualification.md`. Score: warm. Routes to 02 with a request for neighborhood research.

### Day 1 — Researched
**02_property_research** produces `research_brief.md` covering Mueller, Holly, East Cesar Chavez. 7 active comps in range, sold comps for context, school ratings, walkability. TL;DR + recommended Saturday showing slate. Routes to 03.

### Day 2 — Showings
**03_client_communication** drafts showing-confirm emails (Pat-preferred channel) and texts (Jamie-preferred) in Maria's voice. Maria reviews, sends.

### Day 5 — Offer accepted
After tours, an offer goes in. Counter-offer email drafted by 03 in Maria's voice. Offer accepted at $712k. 03 drafts the celebration text + timeline email. **Stage transitions to under_contract.** Routes to 04.

### Days 5–35 — Under contract
**04_transaction_coordinator** picks up. Creates `transaction_tracker.md` with all TREC deadlines (option period, financing, appraisal, close). Inspection booked. Earnest money tracked. Weekly Monday summaries land in case.md for Maria. Any client comms go from 04 → 03 (for voice) → human:Maria (for review/send).

### Day 35 — Close
Final walkthrough, signing at Independence Title, funding. 04 updates case.md `stage` → `closed`. Schedules 1-week and 3-month nurture follow-ups through 03.

That's one case, one Case File, four specialists touched, every handoff explicit and logged.

---

## What's in each folder

Every specialist folder contains the same four files:

| File | What it tells the AI |
|---|---|
| **identity.md** | Who this specialist is, what they own, what they don't |
| **rules.md** | How they operate. Always-dos. Never-dos. |
| **examples.md** | Two to three example interactions showing the specialist in action |
| **handoff.md** | What this specialist receives, what it produces, and where it routes next |

Plus:

- **`_shared/`** — the cross-cutting reference files every specialist uses
- **`_cases/`** — the actual work product, one folder per case

---

## How to onboard a new team member in a day

This is the bar. Here's how it goes.

### Hour 1 — Read this README + the example case
Read this README front-to-back, then open `_cases/2026-05-08-anderson-buyer/case.md` and read it top-to-bottom. Follow the trail: read `qualification.md`, `research_brief.md`, `communication_log.md`, `transaction_tracker.md`. You'll see the whole system in action against one realistic deal.

### Hour 2 — Read each specialist's identity.md
Open `00_orchestrator/identity.md`. Then `01_lead_qualifier/identity.md`. Then 02, 03, 04. Don't memorize — just understand what each one owns and doesn't own.

### Hour 3 — Read the two specs
Open `_shared/case_file_spec.md` (the contract for Case Files) and `_shared/handoff_packet_spec.md` (the contract for Handoff Packets). These two files are why the system works. Spend the time.

### Hour 4 — Read the reference files
Skim `_shared/agent_voices.md` (whose voice does what). `_shared/austin_market_reference.md` (the neighborhoods we work). `_shared/tx_transaction_timeline.md` (Texas transaction mechanics). `_shared/glossary.md` (if you don't know a term, look here first).

### Hours 5–8 — Practice run on a fake lead
Diana hands you a fake inbound (e.g. "This couple just filled out the form, see what comes back"). You play orchestrator. Walk through the routing. Open the case file. Read the relevant `rules.md`. Produce the artifact. Append the Handoff Packet. Diana reviews and tells you what you missed.

### Day 2 — Shadow a real case
Diana puts you on an active case at whatever stage it's in. You read what's been done. You produce the next step under supervision. By end of Day 2, you're operational.

If you find yourself confused, the question is almost always answerable by reading one of these files. The order to consult: the specialist's `rules.md` → `examples.md` → `/_shared/<relevant>.md` → `/_shared/glossary.md` → ask Diana.

---

## Setup — dropping this into a Claude project

For Diana / Maria / Tom / Jordan to use this system day-to-day:

### Option A — Use as a Claude Project (recommended)

1. Create a new Project in Claude (or your AI tool of choice).
2. Upload the entire `agency-system/` folder structure to the project's knowledge base.
3. Set the project's custom instructions:

   > You are part of the Diana Lin Realty agency system. Every request you handle starts at 00_orchestrator. Read 00_orchestrator/identity.md and 00_orchestrator/rules.md to determine routing. After routing, read the destination specialist's identity.md, rules.md, examples.md, and handoff.md. Use the Case File and Handoff Packet conventions defined in _shared/. Always produce: an artifact file (where applicable), an entry in case.md's Log section, and a Handoff Packet at the bottom of case.md.

4. Start a conversation with the inbound (paste the message, the contact, the channel). Claude will identify or open a case and route.

### Option B — Local folder use

If you prefer to keep everything on your own computer:
1. Clone the repo locally.
2. When working on a case, open the relevant specialist folder in your editor and the case folder side-by-side.
3. Hand the AI the specialist's files + the case folder + the inbound. Ask it to produce the next step.

Both work. Option A is faster for live work; Option B is better for tinkering with the system itself.

### Day-zero customizations Diana should make

Before the team uses this in production, swap these in:

- **Agent names** — replace Maria / Tom / Jordan in `_shared/agent_voices.md` and any examples with your actual team members
- **Voice cards** — start fresh and observe actual writing patterns for 2–4 weeks before locking down voices
- **Contact info** — update fictional phone numbers and emails to real ones
- **Title / lender / inspector list** — drop in the team's actual go-to relationships
- **Service area** — verify the neighborhoods in `austin_market_reference.md` match the team's actual footprint

The system structure stays the same. The content gets personalized.

---

## Key files (quick links)

- The two contracts that make everything work:
  - `_shared/case_file_spec.md` — what a Case File is and how it's structured
  - `_shared/handoff_packet_spec.md` — the format for handoffs between specialists
- The worked example showing the whole system in motion:
  - `_cases/2026-05-08-anderson-buyer/` — one deal, end to end, every artifact
- The reference shelf:
  - `_shared/agent_voices.md` — whose voice for which agent
  - `_shared/austin_market_reference.md` — neighborhoods we cover
  - `_shared/tx_transaction_timeline.md` — Texas transaction mechanics
  - `_shared/glossary.md` — terms a new agent might not know

---

## Design decisions worth knowing

A few choices we made deliberately, in case you want to extend or modify:

**Numbered folder prefixes (00–04).** The numbers reflect typical lifecycle order, not a strict sequence. The orchestrator can route to any specialist at any time. The numbers just make the folder list scannable.

**The Case File is one folder, not one file.** Each Case File is a folder containing `case.md` (the spine) plus artifact files. We chose folders over a single big file because:
- Specialists can own their own artifacts cleanly
- Multiple research briefs on the same case can coexist (`research_brief.md`, `research_brief_02.md`)
- The folder name encodes useful info (`2026-05-08-anderson-buyer`)

**The Handoff Packet is markdown inside case.md, not a separate file.** We considered making each Handoff a separate file. Decision: keep them inline in case.md because then case.md is a single, readable, top-to-bottom story of the deal. Easier to onboard a new agent on a single file than to chase pointers across many.

**04_transaction_coordinator keeps the case** through close. Other specialists are called in for specific asks (03 for client comms, 02 for appraisal-defense comps) but the case stays with 04. We considered routing the case to whoever's "up" at any moment; rejected because under-contract deals have one operational owner.

**Voice cards are real and detailed.** It would be easy to write generic voice cards ("Maria is professional and warm"). We chose to write detailed ones with phrases the agent actually uses and phrases they never use. This is what makes voice-matching produce drafts the agent only needs to lightly edit.

**One specialist (Jordan) is explicitly "ramping."** Her voice card acknowledges she's still developing. The system assigns her cold-lead nurture cases for practice because the stakes are lower and the feedback loop with Diana is faster. This reflects how real teams work — not everyone is at the same level, and the system should adapt.

---

## What this system doesn't do

- **It doesn't automate the sending of any client communication.** Every draft is reviewed by the named agent before send. This is a deliberate design choice — a real estate transaction has too many high-stakes moments to delegate the final send.
- **It doesn't replace MLS, your CRM, or any other software.** It complements them. The Case File is the operational record; the team still pulls comps from ABoR, signs documents in DocuSign, stores PDFs in Drive, etc.
- **It doesn't make pricing decisions, negotiate, or recommend strategy.** Specialists supply facts and options; humans decide.
- **It doesn't handle commercial, multi-family >4, or land deals.** Residential only.

---

## What we'd add with another week

(Honest list, in case Diana wants to extend.)

- A `_templates/` folder with common forms (inspection objection skeleton, amendment-request bullet-list templates, cold-lead nurture sequence)
- A second worked example case showing a seller-side flow (the Castillo-Reyes case is referenced in examples but not fully built)
- A `_archive/` convention for completed cases (so `_cases/` stays scannable for active work)
- A weekly review skill — Diana runs this every Friday, sweeps active cases, surfaces anything that's drifted
- A new-hire skill — automates the Day 1 onboarding walkthrough

The system is shippable as-is. These would add polish, not load-bearing structure.

---

## Methodology and attribution

This system is built on **Interpretable Context Methodology (ICM)** — the approach that replaces multi-agent frameworks with filesystem structure. Numbered folders are stages; plain markdown files carry the prompts and context that tell a single agent what role to play at each step. The Case File pattern (one shared object flowing through specialists) and the structured Handoff Packet format are this build's specific implementation of ICM at scale.

References:
- **Van Clief, J. & McDermott, D. (2026).** *Interpretable Context Methodology: Folder Structure as Agentic Architecture.* arXiv:2603.16021.
- **ICM Handoff Protocol** — community-shared pattern layer for chaining stateless worker sessions: `github.com/PUSHINGSQUARES/icm-handoff-protocol`.

This workspace expresses the full L0–L4 context hierarchy from the paper:
- **L0** — `CLAUDE.md` (workspace identity)
- **L1** — `README.md` + `00_orchestrator/identity.md` (task routing)
- **L2** — each specialist's `identity.md` + `rules.md` + `examples.md` + `handoff.md` (per-stage contract)
- **L3** — `_shared/*` (reference material; stable across runs — the "factory")
- **L4** — `_cases/<case_id>/*` (working artifacts; per-run)

Built for the Clief Notes Weekly Competition #4 (May 2026).
