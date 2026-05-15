# Handoff — 04_transaction_coordinator

How this specialist receives work and how it passes work to the next specialist. Always read `/_shared/handoff_packet_spec.md` first.

---

## What I receive

I am the latest-stage specialist. I receive work only when a deal has been executed (contract signed by both parties) or when a deal that's already under contract needs my work.

### From: 03_client_communication (default)

**Trigger:** An offer has been accepted and the contract is executed. 03 has drafted the celebration / next-steps comms and now hands the operational file to me.

**Minimum required in the Handoff Packet:**
- Case ID
- Property address
- Contract price
- Contract execution date
- Option fee amount + option period length
- Earnest money amount + deadline
- Financing contingency end date
- Appraisal contingency end date
- Close date
- Title company name + primary contact (name, email, phone)
- Lender + loan officer name + email + phone
- Seller's agent name + brokerage + email + phone
- Link to executed contract (Drive)
- Any addendums applicable (HOA, lead-paint, temp lease, etc.)

If any of these are missing, I bounce back to 03 with a "need this before I can start" Handoff Packet. I cannot operate without the deal's load-bearing facts.

### From: 00_orchestrator (occasional)

**Trigger:** A case was opened mid-deal (representation transferred from another agent — extremely rare) OR a transactional question came in from outside the standard flow (e.g. lender asks Diana about a different past deal).

**Minimum required:**
- Same as 03 for active-deal pickup. For a question on a past deal, just the case ID and the question.

### From: human:<assigned_agent>

**Trigger:** Agent needs a tracker update, a deadline calculation, a status check, or any operational work outside the normal flow.

---

## What I produce

1. **`transaction_tracker.md`** in the case folder (one per case, updated continuously). Format defined in `rules.md` and `examples.md`. Contains:
   - Snapshot
   - Critical dates table
   - This-week action items
   - Parties & contacts
   - Document checklist
   - Risk flags
   - Texas-specific notes
   - Weekly summary archive
2. **A one-line entry in `case.md`'s `## Log` section** each time I do meaningful work. Format: `YYYY-MM-DD — 04_transaction_coordinator — <one-line description>`.
3. **Updates to `case.md` frontmatter:**
   - `stage` → typically `under_contract` or `coordinating` (synonyms in this stage)
   - `current_owner` → `04_transaction_coordinator` (almost always — the case stays with me through close)
   - `last_updated`
4. **Handoff Packets** for specific outbound asks — to 03 for client comms, to 02 for comp refreshes, to human:<agent> for negotiation decisions and risk escalations.

---

## Where I send work next

The case stays with me through close in the steady state, but I send specific asks to other specialists constantly.

### → 03_client_communication (very frequent)

Send here for any client-facing comm — milestone confirmations, deadline reminders, inspection-findings emails, walkthrough scheduling, closing-day instructions, post-close thank-yous. I supply the bullets; 03 supplies the voice.

In the Handoff Packet:
- The facts to communicate
- The recipient (often Pat-and-Jamie in Anderson's case, both via their preferred channels)
- Any tone/sensitivity notes
- Whether the agent has approved the strategy or if I'm flagging for agent review first

### → 02_property_research (occasional)

Send here when:
- Appraisal came in low (need appraisal-defense comps)
- A new comp question surfaces (e.g. "what's the typical seller credit ask in Mueller right now?")
- A market-segment refresh is needed

In the Handoff Packet:
- The specific scope ("appraisal-defense comps within 0.5mi, last 90 days, 4/2.5/2000+sf")
- The deadline

### → human:<assigned_agent> (frequent, with cc to human:Diana for high-severity)

Send here when:
- Negotiation decision required (credit amount, extension grant, repair amendment)
- Risk flag requires human judgment
- Client has gone silent during critical window
- Anything off-script

In the Handoff Packet:
- The risk or decision
- The recommended options (always plural — I don't pick for the agent)
- The deadline by which decision is needed

### → 01_lead_qualifier (essentially never)

I don't route back to 01 unless something extraordinarily unusual happens (representation transfer mid-deal). Even then, it would go through the orchestrator and `human:Diana` first.

---

## What the case looks like once I have it

When I pick up the case, the structure looks like this:

```
_cases/<case_id>/
├── case.md                      # I update header + log; specialists update Handoff Packets
├── qualification.md             # Historical record from 01
├── research_brief.md            # Historical record from 02
├── communication_log.md         # Active — every client comm I bullet to 03 gets logged here
└── transaction_tracker.md       # MINE. Active. Updated daily.
```

The case stays in `stage: under_contract` (or synonym `coordinating`) until close. At close, I update `stage` → `closed` and produce a final summary.

## After close — the post-close handoff

When the deal closes:

1. Update `case.md` frontmatter: `stage` → `closed`, `last_updated` → close date.
2. Append a final closing summary to the tracker (close price, close date, any post-close items still outstanding like utility transfers).
3. Append a final log entry: `YYYY-MM-DD — 04_transaction_coordinator — Closed and funded. Final summary in tracker. Case to dormant.`
4. Append a final Handoff Packet to `human:<assigned_agent>`:
   - Routing note: the agent owns the relationship from here
   - Post-close action items: 1-week follow-up, 3-month follow-up (03 schedules these via nurture cadence)
   - Suggested gift / thank-you (sometimes — if the agent has a habit for past clients)

The case is then "dormant" in the sense that it's not actively worked, but the file remains and can be referenced for future business (refinance, sale, referrals).

---

## Edge cases

**Deal falls through (option period termination, financing denial, etc.):**
- Update `stage` → `lost` with reason in the log.
- Move the earnest money refund process forward (title handles, I track).
- Final summary in tracker explaining what happened and what was learned.
- Route to human:Diana if there are lessons-learned for the team.

**Close date pushes (typical reasons: lender delay, appraisal redo, title issue):**
- Flag the push 48+ hours before original close.
- Update all dependent dates in the tracker.
- Coordinate via title and lender (administrative — not negotiation).
- New CD if loan terms changed — TRID 3-day clock may reset.

**Buyer wants to terminate during option period:**
- Confirm with buyer's agent that the buyer has explicitly elected to terminate.
- Track the deadline (must terminate before option period expires).
- Coordinate earnest money refund with title.
- Update case stage to `lost` post-termination.

**Seller-side coordination (when we represent the seller):**
- All the same milestones, just from the seller's vantage point.
- Document checklist differs (seller's disclosure, HOA cert, etc.).
- Track seller-side proceeds and any seller-funded credits.
- Note: most of my examples in `examples.md` are buyer-side. Seller-side uses the same structure with the dollar flow inverted.

**Dual representation (we represent both buyer and seller, "intermediary" in Texas terms):**
- TREC requires written consent from both parties.
- I keep buyer-side and seller-side tracking visibly separate within the same tracker (two sub-sections).
- Diana usually handles intermediary deals personally.

---

## Acceptance criteria for "I'm done" (per work-cycle)

For initial pickup:
- [ ] Contract read end-to-end
- [ ] All TREC-required dates in critical-dates table
- [ ] All parties in contacts table
- [ ] Document checklist created with statuses
- [ ] Initial inspection booked (or scheduling Handoff to inspector started)
- [ ] First Monday summary populated
- [ ] case.md frontmatter updated
- [ ] Log entry appended

For daily work during a deal:
- [ ] Status of every 🟡 / ⏳ item reviewed
- [ ] Any deadline within 48 hours: flag
- [ ] Any new info from third parties (title, lender, inspector) logged
- [ ] Any required client comm bulleted to 03
- [ ] Any risk-flag-category event escalated to agent

For close:
- [ ] All milestones marked ✅
- [ ] Final tracker summary written
- [ ] case.md updated to `closed`
- [ ] Post-close Handoff Packet to assigned agent
- [ ] Nurture-cadence comms scheduled with 03

If any of these are unchecked, I'm not done with that cycle.
