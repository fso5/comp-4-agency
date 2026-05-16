# Diana Lin Realty — Agency System

**A markdown-only AI operating system for a 4-person boutique real estate team. Five specialists coordinate via a Case File spine. Built so the newest agent is operational in a day.**

> Diana's actual frustration: *"When a lead comes in, who responds first depends on who saw the notification. When a property research request goes out, the agent doing it rebuilds the wheel every time. When a deal moves into contract, my newest agent Slacks me at 11pm asking which document needs to go where."*

This is the system that solves those three problems specifically. Not a generic agency tool. Not another platform. Just folders and markdown.

---

## What most submissions for this brief will build vs. what this is

```
// most entries
Five folders shipped. identity.md, rules.md, examples.md, handoff.md
in each one. The brief described a handoff so the file is named "handoff.md".
The handoff contents describe the handoff in prose. Specialists "pass work
to the next folder." The README explains the architecture.

// this system
Five folders + a shared Case File spine + a structured Handoff Packet spec
that every handoff.md references. Specialists don't pass prose to each
other; they append a typed packet (6 required fields, 4 body sections) to
case.md at the bottom. The README shows the system being used end-to-end
on a real deal (Anderson buyer, Mueller, $712k, executed contract). The
case folder is the receipt that the system works.
```

The folders ARE the system. There is no software to install. You point Claude at one of the specialist folders, give it the request, and it does its job — qualifies a lead, researches a neighborhood, drafts an email in the assigned agent's voice, tracks a TREC transaction. The system runs on the structure, not the tool.

---

## Where this fits in Diana's stack (60/30/10)

Per Jake Van Clief's **Constraint 06: Layer Triage** from the Clief Notes Vault:

> "60% of what a business runs should be traditional tools (spreadsheets, databases, software — they do not hallucinate). 30% should be rule-based automation (Zapier, n8n, email rules). 10% should be AI (judgment, synthesis, creativity)."

This system is **the 10%.** It does NOT replace Diana's existing stack — it sits on top of it.

| Layer | What Diana already has | What this system adds |
|---|---|---|
| **60% — Traditional tools** | ABoR MLS, TCAD, DocuSign, Google Drive, Calendar, Sheets pipeline | (unchanged — this system doesn't touch them) |
| **30% — Automation** | (gap — could add) Zapier from web form → Slack, Calendar deadline reminders, drip nurture sequences | (a Week-5 candidate; out of scope for this submission) |
| **10% — AI judgment layer** | (the gap this fills) | **The five specialists.** Lead qualification, neighborhood research, voice-matched comms, TREC deadline tracking, orchestration routing |

The five specialists are explicitly the **judgment layer**. Each one exists because the work requires synthesis, voice matching, or risk pattern recognition — not because the work is novel. The 60% and 30% layers stay in Diana's existing stack; this system is what gets dropped into a Claude project.

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
                  │ tracks TREC deadlines,  │
                  │ documents, deals        │
                  │ once under contract     │
                  └─────────────────────────┘

  Underneath it all: the CASE FILE — a folder under _cases/ that contains
  case.md (the spine) + artifact files (qualification.md, research_brief.md,
  communication_log.md, transaction_tracker.md). The Case File is what
  every specialist reads from and writes to.

  Handoff Packets — structured markdown blocks appended to case.md —
  are how specialists pass work to each other. The handoff IS a typed
  object, not prose. Every handoff.md references the spec.
```

---

## Receipts — the system in action on a real deal

The Anderson buyer case at `_cases/2026-05-08-anderson-buyer/` is the system's live test. It shows what every artifact looks like at every stage, with realistic Austin specifics:

- A real Mueller neighborhood ($712k home, 4/2.5/2080sf, walkable to Maplewood Elementary)
- Real TREC mechanics (7-day option period, 21-day financing/appraisal contingencies, TRID 3-day CD rule)
- Real Texas vocabulary (TCAD records, ABoR MLS, Travis County tax cadence)
- Real voice matching (Maria's actual phrases, not adjectives — "Want to jump on a 10-minute call?", "Wear shoes you can walk in")
- 4 Handoff Packets visible in `case.md`, each addressing the spec's required fields

Read the case top-to-bottom in 10 minutes. You'll see the whole system run.

---

## How a typical request flows

A walk-through of the Anderson case from website form to under-contract.

### Day 0 — Lead arrives
Pat & Jamie Anderson fill out a website contact form. "Relocating from Denver, looking in East/Central Austin, budget around $700k."

**00_orchestrator** reads the inbound, sees no matching case, opens a new one at `_cases/2026-05-08-anderson-buyer/`. Routes to 01.

### Day 0 — Qualified
**01_lead_qualifier** reads the message, asks for missing info (or flags unknowns), produces `qualification.md`. Score: warm (verified Cadence Bank pre-approval, 3-month timeline, defined geography). Routes to 02.

### Day 1 — Researched
**02_property_research** produces `research_brief.md` covering Mueller, Holly, East Cesar Chavez. 7 active comps in range, sold comps for context, school ratings, walkability. TL;DR + recommended Saturday showing slate. Every fact has a source citation. Routes to 03.

### Day 2 — Showings
**03_client_communication** drafts showing-confirm emails (Pat-preferred channel) and texts (Jamie-preferred) in Maria's voice. Maria reviews one-word edits, sends.

### Day 5 — Offer accepted
After tours, an offer goes in. Counter-offer email drafted by 03 in Maria's voice. Offer accepted at $712k. 03 drafts the celebration text + timeline email (with the wire-fraud warning). **Stage transitions to under_contract.** Routes to 04.

### Days 5–35 — Under contract
**04_transaction_coordinator** picks up. Creates `transaction_tracker.md` with all TREC deadlines (option period 5/20, financing 6/3, appraisal 6/3, close 6/13). Inspection booked at Hilltop. Earnest money tracked to Independence Title. Weekly Monday summaries land in case.md for Maria. Any client comms go from 04 → 03 (for voice) → human:Maria (for review/send).

### Day 35 — Close
Final walkthrough, signing at Independence Title, funding. 04 updates case.md `stage` → `closed`. Schedules 1-week and 3-month nurture follow-ups through 03.

**That's one case, one Case File, four specialists touched, every handoff explicit and logged.**

---

## What's in each folder

Every specialist folder contains the same four files:

| File | What it tells the AI |
|---|---|
| **identity.md** | Who this specialist is, what they own, what they don't |
| **rules.md** | How they operate. Always-dos. Never-dos. With reasoning per rule. |
| **examples.md** | 2-3 example interactions showing the specialist in action |
| **handoff.md** | What this specialist receives, what it produces, where it routes next. References the shared `_shared/handoff_packet_spec.md`. |

Plus:

- **`_shared/`** — the cross-cutting reference shelf (the "factory" layer in ICM terms)
- **`_cases/`** — the actual work product, one folder per case
- **`CLAUDE.md`** — workspace identity / entry point for any AI assistant opening the project

---

## Onboarding a new team member in a day

This is the bar Diana set. Here's how it goes.

### Hour 1 — Read this README + the example case
Read this README front-to-back, then open `_cases/2026-05-08-anderson-buyer/case.md` and read it top-to-bottom. Follow the trail: read `qualification.md`, `research_brief.md`, `communication_log.md`, `transaction_tracker.md`. You'll see the whole system in action against one realistic deal.

### Hour 2 — Read each specialist's identity.md
Open `00_orchestrator/identity.md`. Then `01_lead_qualifier/identity.md`. Then 02, 03, 04. Don't memorize — just understand what each one owns and doesn't own.

### Hour 3 — Read the two contracts
Open `_shared/case_file_spec.md` (the contract for Case Files) and `_shared/handoff_packet_spec.md` (the contract for Handoff Packets). These two files are why the system works. Spend the time.

### Hour 4 — Skim the reference shelf
`_shared/agent_voices.md` (whose voice does what). `_shared/austin_market_reference.md` (the neighborhoods we work). `_shared/tx_transaction_timeline.md` (TREC + TRID + Travis County mechanics). `_shared/glossary.md` (terms you might not know).

### Hours 5–8 — Practice run on a fake lead
Diana hands you a fake inbound. You play orchestrator. Walk through the routing. Open the case file. Read the relevant `rules.md`. Produce the artifact. Append the Handoff Packet. Diana reviews and tells you what you missed.

### Day 2 — Shadow a real case
Diana puts you on an active case at whatever stage it's in. You read what's been done. You produce the next step under supervision. By end of Day 2, you're operational.

If you find yourself confused, the question is almost always answerable by reading one of these files. The order to consult: the specialist's `rules.md` → `examples.md` → `_shared/<relevant>.md` → `_shared/glossary.md` → ask Diana.

---

## Setup — dropping this into a Claude Project

For Diana / Maria / Tom / Jordan to use this system day-to-day:

### Option A — Use as a Claude Project (recommended)

1. Create a new Project in Claude (or your AI tool of choice).
2. Upload the entire folder structure to the project's knowledge base.
3. Set the project's custom instructions:

   > You are part of the Diana Lin Realty agency system. Every request you handle starts at 00_orchestrator. Read 00_orchestrator/identity.md and 00_orchestrator/rules.md to determine routing. After routing, read the destination specialist's identity.md, rules.md, examples.md, and handoff.md. Use the Case File and Handoff Packet conventions defined in _shared/. Always produce: an artifact file (where applicable), an entry in case.md's Log section, and a Handoff Packet at the bottom of case.md.

4. Start a conversation with the inbound (paste the message, the contact, the channel). Claude will identify or open a case and route.

### Option B — Local folder use (Claude Code or similar)

1. Clone the repo locally.
2. When working on a case, open the relevant specialist folder in your editor and the case folder side-by-side.
3. Hand the AI the specialist's files + the case folder + the inbound. Ask it to produce the next step.

Both work. Option A is faster for live work; Option B is better for tinkering with the system itself.

### Day-zero customizations Diana should make

Before the team uses this in production, swap these in:

- **Agent names** — replace Maria / Tom / Jordan in `_shared/agent_voices.md` and any examples with your actual team members
- **Voice cards** — start fresh and observe actual writing patterns for 2-4 weeks before locking down voices (Rule 8 of `03_client_communication/rules.md` says how)
- **Contact info** — update fictional phone numbers and emails to real ones
- **Title / lender / inspector list** — drop in the team's actual go-to relationships
- **Service area** — verify the neighborhoods in `austin_market_reference.md` match the team's actual footprint

The system structure stays the same. The content gets personalized.

---

## Design decisions worth knowing

Eight choices made deliberately. Each one is the thing that separates this submission from filling out the template.

**1. The Case File is a folder, not a file.** Each case is a folder containing `case.md` (the spine) plus per-specialist artifact files. Specialists own their own artifacts; the spine is the shared narrative. Multiple research briefs on the same case can coexist (`research_brief.md`, `research_brief_02.md`). The folder name encodes useful info (`2026-05-08-anderson-buyer`).

**2. The Handoff Packet is a typed object, not prose.** Six required fields (From, To, Case ID, Stage transition, Human owner, Priority) + four required body sections (Why this handoff, What I'm passing forward, What I need back, Escalate to human if). Every `handoff.md` in every specialist folder references the same spec. This is what "actually defined vs. hand-waved" looks like.

**3. The Handoff Packet lives inline in case.md, not as a separate file.** We considered making each Handoff a separate file. Decision: keep them inline so case.md tells a single readable top-to-bottom story. Easier to onboard a new agent on a single file than to chase pointers across many.

**4. 04_transaction_coordinator keeps the case** through close. Other specialists are called in for specific asks (03 for client comms, 02 for appraisal-defense comps) but the case stays with 04. Under-contract deals have one operational owner; the system reflects that.

**5. Voice cards have phrases, not adjectives.** A card that says "Maria is warm and professional" doesn't help an AI produce Maria's actual sentences. A card that says "Maria opens emails with '<Name> —' (dash, no greeting); never uses em dashes; offers a phone call in any email that involves a decision" produces Maria's actual sentences on the first try.

**6. One specialist (Jordan) is explicitly "ramping."** Her voice card acknowledges she's still developing. The system assigns her cold-lead nurture cases for practice because the stakes are lower and the feedback loop with Diana is faster. This reflects how real teams work — not everyone is at the same level, and the system should adapt.

**7. Refusal mechanisms are built into the rules.** 01 refuses to score a lead "hot" without verified financing. 02 refuses to publish a fact without a source. 03 refuses to draft when the client uses the word "lawyer" — escalates to Diana. 04 refuses to communicate directly with the client. The system says NO at specific named conditions, not "use judgment."

**8. The methodology gets sharper with use.** Voice cards include a Rule 8 that says "when the agent edits a draft, log the edit. If Maria changes 'Hi Pat,' to 'Pat —' three times in a row, update her voice card." This is the **edit-source principle** from the ICM paper Section 6.3 applied to ongoing operations.

---

## What this system doesn't do

- **No automated sending of any client communication.** Every draft is reviewed by the named agent before send. This is a deliberate design choice — a real estate transaction has too many high-stakes moments to delegate the final send.
- **No replacement of MLS, CRM, or any other software.** Complements them. Diana still pulls comps from ABoR, signs documents in DocuSign, stores PDFs in Drive. The Case File is the operational record on top.
- **No pricing decisions, negotiation, or strategy recommendations.** Specialists supply facts and options; humans decide.
- **No commercial, multi-family >4, or land deals.** Residential only.
- **No real-time multi-agent execution.** Specialists run sequentially. One stage, one job (per ICM Principle 1).

---

## What we'd add with another week

(Honest list, framed as roadmap not regret.)

- **A seller-side worked example case** (the Castillo-Reyes case is referenced in examples but not fully built) — would complement the buyer-side Anderson walkthrough
- **A `_templates/` folder** with common forms (inspection objection skeleton, amendment-request bullet-list templates, cold-lead nurture sequence) — reduces friction further
- **A weekly review skill** — Diana runs it every Friday, sweeps active cases, surfaces anything that's drifted
- **An `_archive/` convention** for closed cases so `_cases/` stays scannable for active work
- **The 30% automation layer** — Zapier flows that move web-form leads into the system without manual paste, deadline reminders that fire from the tracker, drip nurture sequences for cold leads

The system is shippable as-is. These would extend its reach, not patch foundations.

---

## Methodology and attribution

Built on **Interpretable Context Methodology (ICM)** — Jake Van Clief & David McDermott's approach that replaces multi-agent frameworks with filesystem structure. Numbered folders are stages; plain markdown files carry the prompts and context that tell a single agent what role to play at each step.

The structure expresses the full **L0–L4 context hierarchy** from the paper:

- **L0** — `CLAUDE.md` at root (workspace identity)
- **L1** — `README.md` + `00_orchestrator/identity.md` (task routing)
- **L2** — each specialist's `identity.md` + `rules.md` + `examples.md` + `handoff.md` (per-stage contract)
- **L3** — `_shared/*` (reference material — the "factory," stable across runs)
- **L4** — `_cases/<case_id>/*` (working artifacts — per-run)

The Handoff Packet format extends Ari Evergreen's community-shared **ICM Handoff Protocol** to this multi-folder use case.

References:
- Van Clief, J. & McDermott, D. (2026). *Interpretable Context Methodology: Folder Structure as Agentic Architecture.* arXiv:2603.16021.
- ICM Handoff Protocol — `github.com/PUSHINGSQUARES/icm-handoff-protocol`
- 60/30/10 framework — Clief Notes Vault, Constraint 06: Layer Triage

Built for Clief Notes Weekly Competition #4 (2026-05).
