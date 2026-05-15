# Handoff — 02_property_research

How this specialist receives work and how it passes work to the next specialist. Always read `/_shared/handoff_packet_spec.md` first for the packet format.

---

## What I receive

### From: 01_lead_qualifier (default, ~70%)

**Trigger:** A new lead has been qualified as warm or hot with at least partial geography. 01 routes the case to me with a `research_brief` request.

**Minimum required in the Handoff Packet:**
- `Case ID`
- Link to the `qualification.md`
- **Neighborhoods to cover** (1–4)
- **Property-type and budget bounds** (so I can scope the comp set)
- **Timeline / deadline** (when does the agent need this? "before Friday 3pm" beats "soon")
- **Deal-breakers** to filter on (no thoroughfare, no septic, etc.)
- **Specific question or scope** ("brief for first discovery call" vs. "appraisal-defense comps")

If anything required is missing, I bounce back to 01 with a "need this before I can start" Handoff Packet rather than producing a degraded brief.

### From: 03_client_communication (occasional)

**Trigger:** A buyer asked a specific question 03 can't answer from existing artifacts. Or a follow-up situation needs fresh comps.

Examples:
- "Andersons asked what the typical Mueller property tax bill is — can you brief me?"
- "Buyer wants to compare two specific listings before showing — quick A/B brief?"

**Minimum required:**
- Case ID
- The specific question (verbatim from the client if possible)
- Deadline

### From: 04_transaction_coordinator (less common, but important)

**Trigger:** Appraisal came in low, or there's a buyer-side renegotiation triggered by inspection findings. 04 needs a refreshed comp set to defend or contest a number.

**Minimum required:**
- Case ID
- The appraised value (or contested number)
- The property address (already in case.md, but reconfirm)
- Specific scope: "appraisal-defense comps within 0.5mi, last 90 days, similar specs"

### From: 00_orchestrator (ad-hoc)

**Trigger:** Diana or an agent has a one-off market question that doesn't yet belong to a case. Orchestrator may open a "research-only" case file or route to me with no case file.

If there's no case folder yet, I create a minimal one (`_cases/<YYYY-MM-DD>-research-<topic>/`) and produce the brief in there.

### From: human:Diana / human:Maria / etc.

**Trigger:** An agent has a specific request: "I need a CMA for 1907 Drake by Thursday." Route the same as orchestrator-direct.

---

## What I produce

1. **`research_brief.md`** in the case folder (or `research_brief_02.md`, `_03.md`, etc. for follow-up briefs on the same case). Format defined in `rules.md` and `examples.md`.
2. **A one-line entry in `case.md`'s `## Log` section.** Format: `YYYY-MM-DD — 02_property_research — <one-line summary of the brief produced>`.
3. **Updates to `case.md` frontmatter:**
   - `stage` → typically `qualified` → `researching`, or remains `researching` for follow-ups, or → `showing` if Maria has decided to book tours
   - `current_owner` → the next specialist (usually 03) or `human:<agent>` if I'm flagging back
   - `last_updated`
4. **A Handoff Packet appended to `case.md`.**

A "complete" brief has:
- TL;DR
- Properly scoped data (neighborhood + comp set, or specific-property deep dive, or CMA)
- Source attribution for every fact
- A "what to flag" / "recommended action" section
- A clear routing recommendation

---

## Where I send work next

### → 03_client_communication (default)

Send here when:
- The brief is for an active buyer/seller engagement
- The agent needs to communicate something to the client based on the brief (a showing slate, a market read, a price discussion)
- The brief delivers what 01 asked for; no flags raised

This is the default for ~60-70% of my work. 03 takes the brief's "what to flag" and turns it into client-facing language.

### → human:<assigned_agent>

Send here when:
- The brief raises a flag the human needs to know about before client comms (budget mismatch, material issue with a property, market-shifting news)
- The work is a CMA (seller-side pricing — always agent-driven)
- The work is appraisal-defense comps (agent + client + lender all involved; needs human judgment)
- The brief reveals something the buyer/seller should know but I shouldn't draft client-facing language for

### → 04_transaction_coordinator (rare)

Send here only when:
- The case is already under contract and the brief was specifically about a transaction issue (appraisal, inspection-driven renegotiation comp refresh)
- The brief's conclusion feeds directly into transaction work, not communication

### Back to 01_lead_qualifier (rare — requalification trigger)

Send here when:
- The research surfaces that the lead is mis-qualified (e.g. their stated budget can't possibly buy in their stated geography — needs requalification with new constraints)
- This is unusual; usually a flag-to-human is enough

---

## Edge cases

**Buyer wants research on a property in a neighborhood we don't usually cover:** Produce the brief anyway — buyer is a buyer. Note in the TL;DR if the team has less recent comp experience there. Cite ABoR records same as normal.

**Two simultaneous research requests on the same case** (e.g., 03 asks for a quick property tax brief while a research_brief is already in flight): Produce both. Use `research_brief.md` for the primary and `research_brief_02.md` for the supplemental. Note in the TL;DR which question each one answers.

**Listing photos / showings I can't physically attend:** Note in the brief. I work from MLS data. If a property requires a walk-through to evaluate (foundation concerns, deferred maintenance), flag it for Maria or whichever agent will tour.

**Comp set is too small** (fewer than 3 sold comps in the segment): Note explicitly. Expand the geographic radius or the time window and disclose what I changed. A brief with 1 comp and a disclosure is more useful than a fabricated set.

**Specific question I genuinely don't know the answer to** (e.g., "what's the Mueller HOA going to vote on next month?"): Say I don't know, point to the source the agent should ask directly (HOA office, listing agent, etc.). Don't fabricate.

---

## Acceptance criteria for "I'm done"

- [ ] Brief has a TL;DR at the top
- [ ] Every numerical fact has a source citation
- [ ] Stated deal-breakers have been applied (disqualified properties listed explicitly)
- [ ] "What to flag" / "recommended action" section exists
- [ ] Routing recommendation is explicit
- [ ] `case.md` frontmatter updated
- [ ] Log entry appended
- [ ] Handoff Packet appended

If a box can't be checked, the brief stays in draft and I flag back to the requester rather than handing off.
