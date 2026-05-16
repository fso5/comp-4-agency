# Diana Lin Realty — Agency System (L0 identity)

This file is the entry point when an AI assistant (Claude or otherwise) opens this workspace. Read this first, then read what it points to.

---

## What this workspace is

A multi-folder **Interpretable Context Methodology (ICM)** system for Diana Lin Realty, a 4-person boutique real estate team in Austin, TX. Five specialists (00–04) coordinate via structured Handoff Packets appended to a shared Case File. The folders are the system — there's no code to run, just markdown to read and write.

## Where things live

```
agency-system/
├── README.md                          ← Human onboarding. Read this if you are a new team member.
├── CLAUDE.md                          ← (this file) Read this if you are an AI assistant.
├── 00_orchestrator/                   ← Entry point for every request. Routes to specialists.
├── 01_lead_qualifier/                 ← Qualifies new prospects.
├── 02_property_research/              ← Produces research briefs and CMAs.
├── 03_client_communication/           ← Drafts emails/texts in the agent's voice.
├── 04_transaction_coordinator/        ← Tracks deals once under contract.
├── _shared/                           ← Reference shelf (the "factory" — stable across runs)
│   ├── case_file_spec.md
│   ├── handoff_packet_spec.md
│   ├── agent_voices.md
│   ├── austin_market_reference.md
│   ├── tx_transaction_timeline.md
│   └── glossary.md
└── _cases/                            ← One folder per active case (the "working artifacts" — per-run)
    └── 2026-05-08-anderson-buyer/     ← Worked example showing the system end-to-end
```

## How to handle a request (in order)

1. **Read `00_orchestrator/identity.md` and `00_orchestrator/rules.md`** to understand routing.
2. **Search `_cases/` for an existing case match** by name, email, or property address.
3. **If matched:** read that case's `case.md` (frontmatter + log + most recent Handoff Packet).
4. **If not matched:** open a new case file per the naming convention in `_shared/case_file_spec.md`.
5. **Route to the right specialist** by reading their `identity.md`, `rules.md`, `examples.md`, `handoff.md`.
6. **Produce the artifact** the specialist owns (`qualification.md`, `research_brief.md`, `communication_log.md`, `transaction_tracker.md`, etc.).
7. **Append to `case.md`:** a one-line Log entry, an updated frontmatter (`current_owner`, `last_updated`, `stage`), and a Handoff Packet at the bottom routing to whoever's up next.

## The two contracts that make the system work

Read these once and refer back when in doubt:

- **`_shared/case_file_spec.md`** — what a Case File is, naming, structure, who can write what
- **`_shared/handoff_packet_spec.md`** — the exact format for handoffs between specialists

If you change either contract, you change the system. Don't change them without Diana.

## Context loading (L0–L4 per ICM)

This workspace is structured as a 5-layer context hierarchy:

| Layer | Files | When to load |
|---|---|---|
| **L0** | This file (`CLAUDE.md`) | First thing. Always. |
| **L1** | `README.md` + `00_orchestrator/identity.md` | When deciding where to route a request |
| **L2** | A specialist's `identity.md`, `rules.md`, `examples.md`, `handoff.md` | When executing as that specialist |
| **L3** | `_shared/*` reference files | When you need stable reference info (voice cards, market data, glossary) |
| **L4** | `_cases/<case_id>/*` | When working a specific case — and only the case in question, not all of them |

Don't load every file every time. Each specialist loads only what its rules say to load. This keeps context tight and the work fast.

## What this workspace is NOT

- **Not a real-time multi-agent system.** Specialists run sequentially. One worker, one phase.
- **Not a piece of software.** Markdown + a convention. Drop into a Claude Project or use locally.
- **Not a replacement for ABoR MLS, DocuSign, Drive, or any other software.** Complements them.
- **Not for non-residential, non-Austin work.** Diana refers those out.

## Standards every artifact must meet

When you produce ANY artifact in this workspace:

1. **Cite sources** for facts (e.g., "ABoR MLS pull 5/9 7am" not "comps say"). 02 explicitly enforces this.
2. **Mark drafts** as `[DRAFT — needs <agent> review]`. Every client-facing comm is human-reviewed.
3. **No invented numbers, prices, dates, or wire instructions.** If you don't know it, the field is `unknown — <who> to confirm on <when>`.
4. **No wire fraud risk.** Never embed wire details in any client comm. Title sends those through verified channels only.
5. **Append, don't overwrite.** Logs grow. Multiple research briefs are numbered (`research_brief_02.md`).
6. **Every handoff updates `case.md`** (frontmatter + log + Handoff Packet). Three updates, every time.

## Who's on the team

- **Diana Lin** — owner. Past-client referrals, sellers >$1.2M, anything legal-adjacent.
- **Maria Reyes** — senior, 5yrs. Mid-market central Austin ($500k–$1.2M).
- **Tom Buchanan** — senior, 5yrs. Condos, townhomes, East Austin.
- **Jordan Park** — ramping, 6 months. First-time buyers, nurture sequences.

Voice cards for each are in `_shared/agent_voices.md`. When 03_client_communication drafts a message, it matches the assigned agent's voice. Read the card first.

## Attribution

This system is built on the **Interpretable Context Methodology** (Van Clief & McDermott, arXiv:2603.16021) and adopts conventions from the community-shared **ICM Handoff Protocol** at github.com/PUSHINGSQUARES/icm-handoff-protocol. The Case File pattern + structured Handoff Packets are this build's specific implementation of those ideas.

Per Jake Van Clief's **Constraint 06 (Layer Triage) — the 60/30/10 framework**, this system is the **10% layer** (AI judgment). The 60% (MLS, TCAD, DocuSign, Drive) and 30% (Zapier automation — gap, not in this submission) stay in Diana's existing stack. See `_shared/stack-mapping.md` for the full mapping.
