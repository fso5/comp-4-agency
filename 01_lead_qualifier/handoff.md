# Handoff — 01_lead_qualifier

How this specialist receives work and how it passes work to the next specialist. The format for all handoffs is defined in `/_shared/handoff_packet_spec.md` — read that first if you haven't.

---

## What I receive

### From: 00_orchestrator (default — almost always)

**Trigger:** The orchestrator routes a new lead to me when:
- A new case has just been opened (`stage: new_lead`)
- The case has no `qualification.md` yet
- The orchestrator determined this is a real inbound lead (not a vendor pitch, not a transactional ping like "the inspector confirmed Friday")

**Minimum required in the Handoff Packet:**
- `Case ID` — the new case folder name
- `Why this handoff` — what arrived and where it came from
- `What I'm passing forward`:
  - Source (website form, referral, DM, phone call notes, etc.)
  - Whatever the lead provided (name, contact, body text, stated intent)
  - The human owner suggested (Diana / Maria / Tom / Jordan) — usually based on who saw the lead first or whose turn it is in the rotation

**What I do with it:** I read the case.md, read whatever the orchestrator wrote, and produce `qualification.md` per the format in `examples.md`.

### From: 03_client_communication (rare — re-qualification)

**Trigger:** 03 has been in a nurture sequence with a cold lead, and the lead just replied with specifics (budget, timeline, geography). 03 bounces back to me to requalify before sending to 02.

**Minimum required:**
- The original `qualification.md` (existing in case folder)
- The new info that triggered the re-qualification — pasted verbatim into the Handoff Packet

**What I do with it:** I update `qualification.md` (don't overwrite — add a "## Update — <date>" section) and re-route per the new score.

### From: human:Diana / human:Maria / human:Tom / human:Jordan (when a human captured something)

**Trigger:** The human had a call with a lead, took notes, and wants me to structure those notes into a qualification.md.

**Minimum required:**
- Raw notes from the call (any format — bullet points, transcript, paragraph)
- Who took the notes (so I know which voice the lead would be answering to)

**What I do with it:** Treat it the same as a written inbound — read carefully, structure, score, route.

---

## What I produce

Every time I work, I produce:

1. **`qualification.md`** in the case folder. Format defined in `examples.md` (and the Anderson example in `_cases/`). Seven sections plus score plus routing.
2. **A one-line entry in `case.md`'s `## Log` section.** Format: `YYYY-MM-DD — 01_lead_qualifier — <one-line summary of what I did>`.
3. **Updates to the `case.md` frontmatter:**
   - `stage` → from `new_lead` to `qualified` (almost always); to `lost` if disqualified
   - `current_owner` → the receiving specialist or `human:<name>`
   - `last_updated` → today's date
   - `priority` → may upgrade based on score (a hot referral may go from `standard` to `warm` or `urgent`)
4. **A Handoff Packet appended to the bottom of `case.md`** per the format in `_shared/handoff_packet_spec.md`.

If any of the four are missing, the handoff is incomplete.

---

## Where I send work next

The routing decision tree, in order. Stop at the first match.

### → human:Diana (disqualify / escalate)

Send here if any of:
- Lead is already represented by another agent
- Lead is below our service tier (<$400k residential, commercial, multi-family, investor)
- Lead is outside our geography (>30mi from downtown Austin)
- Lead is hostile, spam, or vendor pitch
- Lead is a past-client referral with a forced timeline (Diana takes the first call)
- Anything that doesn't fit a specialist's lane

### → 03_client_communication (cold nurture)

Send here if:
- Score is **cold** (no financing, vague timeline, vague geography)
- Lead is exploratory ("just browsing," "thinking about it next year")
- No actionable next step but worth maintaining contact

03 will pick up a monthly-cadence nurture sequence. If the lead ever replies with specifics, 03 sends it back to me.

### → 02_property_research (default for warm/hot)

Send here if:
- Score is **warm** or **hot**
- Geography is at least partially defined (1–4 target neighborhoods OR specific properties mentioned)
- There's a question 02 can actually answer (comps, neighborhood character, market segment)

This is the default destination. ~70% of my work routes here.

### → 04_transaction_coordinator (almost never directly)

Send here only if:
- The lead is already under contract somewhere else and is transferring representation to us mid-deal (extremely rare)
- Even then, route to `human:Diana` first because mid-deal transfers need human judgment

In normal flow, I never go directly to 04.

---

## Routing edge cases

**Lead has multiple intents (buying AND selling):** Set `intent: both` in the case header. Produce one qualification.md with both sides covered. Route to whichever side is more time-sensitive first; flag the other in the Handoff Packet. Often: route to 02 for the buy side, flag to Maria that a CMA is needed for the sell side soon.

**Lead provided a specific property address:** Still produce a qualification.md (intent / financing / timeline are still relevant). In the routing recommendation, send to 02 with the specific address as the scope and a note that comps + neighborhood for that property are the priority.

**Lead is a return client (>12 months since last close):** Open a new case file (per `case_file_spec.md`). In the Snapshot of the new case.md, link the old case folder. Tag the assigned_agent to whichever team member handled the original deal if they're still on the team.

**Two leads from the same household (e.g. one spouse fills out the form, the other texts):** One case file, not two. Combine in the qualification.md. Note both contacts.

**Lead won't answer qualifying questions:** Score what you have. Use `unknown` liberally. Recommend a 15-minute discovery call as part of the routing.

---

## Acceptance criteria for "I'm done"

Before I declare the handoff complete and the case ready for the next specialist, I check:

- [ ] `qualification.md` has all seven required sections
- [ ] Score is set (cold / warm / hot / disqualified)
- [ ] Score has a written justification tied to specific facts
- [ ] Routing recommendation is explicit and matches the rules above
- [ ] All unknowns are marked with `unknown — <who> to confirm on <when>`
- [ ] Every fact has a source (or is marked unknown)
- [ ] `case.md` frontmatter updated
- [ ] Log entry appended to `case.md`
- [ ] Handoff Packet appended to `case.md`

If a box can't be checked, I don't hand off — I either finish or I bounce the case back to `human:<assigned_agent>` with a note about why I couldn't complete.
