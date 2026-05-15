# Examples — 04_transaction_coordinator

The full Anderson `transaction_tracker.md` in `/_cases/2026-05-08-anderson-buyer/` is the canonical example of a tracker at Day 2 of option period. Examples below show different moments in a deal's lifecycle.

---

## Example 1 — Risk flag: low appraisal

**Background:** Anderson deal. Appraisal came back at $698,000 against $712,000 contract price. $14,000 under.

**My response (in three places):**

### 1. Update to the risk flags section of `transaction_tracker.md`:

```markdown
## Risk flags

🔴 **2026-06-02 — Appraisal low**
- Contract price: $712,000
- Appraised value: $698,000
- Gap: $14,000 (~2.0%)
- Comp set the appraiser used: 3 properties (one in Mueller, two in Holly — the Holly inclusions are arguable)
- Lender (Cadence): will only lend up to 80% of appraised value, so buyer needs to either (a) bring an additional $14k cash, (b) negotiate price reduction, (c) negotiate seller credit, or (d) walk per appraisal contingency (expires 6/3)
- **Required decision: by 6/3 EOD.** Appraisal contingency expires.

**Recovery options to discuss with Maria:**
1. Renegotiate to $698-705k. Comp data from 02 needed to support our ask.
2. Buyer absorbs the $14k cash. Pat said reserves are comfortable, but check.
3. Split: buyer brings $7k, seller drops $7k.
4. Walk (last resort — Anderson really wants this house).

**Need from 02:** appraisal-defense comp set within 0.5mi, last 90 days, similar specs. Need by 6/3 10am.
**Need from 03:** drafted email to Pat for Maria's review explaining the situation + the three options.
**Need from human:Maria:** decision on negotiation approach, possible call to listing agent.
```

### 2. Two Handoff Packets — one to 02, one to 03 + Maria:

```markdown
## HANDOFF — 2026-06-02T14:11:00-05:00
- **From:** 04_transaction_coordinator
- **To:** 02_property_research
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** under_contract → under_contract
- **Human owner:** Maria
- **Priority:** urgent

### Why this handoff
Appraisal came in $14k low ($698k vs. $712k contract). Need appraisal-defense comps to push back. Goal is to support either a renegotiation to $705-710k or, if seller doesn't move, a hybrid approach where the Andersons bring some cash. Appraisal contingency expires 6/3 EOD.

### What I'm passing forward
- Property: 1247 Berkman Dr
- Contract price: $712,000
- Appraised: $698,000
- Appraiser used these comps: <list from appraisal report> — note the two Holly comps which are weaker
- Need defense set: within 0.5mi, last 90 days, comparable specs (4/2.5/2000+sf in Mueller)

### What I need back (if anything)
- Refresh brief by 2026-06-03 10am CT — Maria needs it before her call with listing agent
- TL;DR optimized for "what is this property actually worth" — the appraisal-defense angle

### Escalate to human if
- No defensible comp set exists (means we'd need to accept the appraisal or walk)
```

```markdown
## HANDOFF — 2026-06-02T14:14:00-05:00
- **From:** 04_transaction_coordinator
- **To:** human:Maria
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** under_contract → under_contract
- **Human owner:** Maria
- **Priority:** urgent

### Why this handoff
Appraisal came in $14k under contract. Need your decision on negotiation strategy by EOD tomorrow (appraisal contingency expires 6/3). I've also routed 02 for an appraisal-defense comp refresh — they'll have it for you by 6/3 10am. After your decision, I'll route 03 to draft the email to Pat.

### What I'm passing forward
- Risk flag in tracker (see above)
- Four options summarized
- Comp refresh in flight (02 has the request)

### What I need back (if anything)
- Decision on which option (renegotiate, buyer-absorbs, split, walk)
- Negotiation strategy if renegotiating (your call on the listing-agent conversation)

### Escalate to human if
- N/A (already at human)
```

---

## Example 2 — Monday weekly summary (mid-deal, no flags)

**Background:** Anderson deal, Monday 5/19 (week 1 of option period, day before option expires).

```markdown
### Week of 5/19 (week 1 of ~4)

We're in the final 36 hours of the option period (expires 5/20 11:59pm).

- **Key milestone this week:** Option period closes 5/20. After this, if Andersons want to terminate, they lose the earnest money. We're past the "free walk" window.
- **Completed since last summary:**
  - Earnest money received by Independence Title 5/15 (one day ahead of deadline) ✅
  - Inspection completed 5/16. Three minor items flagged (HVAC age, GFCI outlet, fence). Inspection report filed.
  - Inspection negotiation submitted to seller 5/17: $2,500 HVAC credit + GFCI fix. Seller accepted both 5/18 ✅
  - Amendment for $2,500 credit signed and filed (TXR-1903 form).
- **Anything at risk:** No. Clean week.
- **Client action items this week (bulleted to 03 for Maria-voice drafts):**
  - Mid-week check-in call (Tue 5/19 4pm CT) — confirm Andersons are good with everything
  - Heads-up email/text on 5/20 morning that option period ends that night (no action required from them, just awareness)
- **Agent action items:**
  - Confirm Pat is on the 5/19 4pm call
  - Send personal note to seller's agent thanking her for the smooth negotiation (relationship)
```

---

## Example 3 — Picking up a case (the moment of executed contract)

**Incoming Handoff Packet (from 03):**

> Offer accepted at $712k on 1247 Berkman. Contract executed today 5/13. Maria's the agent. Title is Independence (Brittany Wu). Lender is Cadence (Raj Patel). 7-day option period started today. (See full Handoff Packet in case.md.)

**My first 60 minutes of work:**

1. **Read the executed contract.** Confirm price ($712,000), option fee ($250), option period (7 days, ends 5/20 11:59pm), earnest money ($7,120, due to title within 3 days), financing contingency (21 days, ends 6/3), appraisal contingency (21 days, ends 6/3), close date (6/13), possession terms (at funding).
2. **Confirm parties.** Title, lender, seller's agent, buyer's agent all on file. Inspector to be booked.
3. **Create `transaction_tracker.md`** with the standard sections. Populate every known field.
4. **Book the inspection.** Email Hilltop Home Inspections to schedule for Friday 5/16 9am — within option period, leaves buffer for renegotiation if anything comes up.
5. **Send a bullet to 03** asking for a "celebration text + timeline email" in Maria's voice.
6. **Send a bullet to 03** asking for a Monday-summary template email confirming all the dates (Maria approves; goes to client Monday 5/19).
7. **Update `case.md` frontmatter:** `stage` → `under_contract` → `coordinating`, `current_owner` → `04_transaction_coordinator`, `last_updated` → 2026-05-13.
8. **Log entry:** `2026-05-13 — 04_transaction_coordinator — Picked up case. Tracker created. Critical dates locked: option 5/20, financing 6/3, appraisal 6/3, close 6/13.`
9. **Initial Monday summary** (since today is the first day, this seeds the cadence): see the tracker.
10. **No Handoff Packet at this stage** — the case stays with me. The next Handoff Packets will be the ones I produce as comms / risks surface.

**The deliverable for hour-one is the populated `transaction_tracker.md` file**, the case.md updates, and the log entry. Then I email title + lender to confirm I'm the point of contact for ops questions on this file. Then I wait.

---

## Pattern notes

- **The tracker is the single source of truth** for the deal once we're under contract. Every other artifact in the case folder is a historical record at this stage; the tracker is alive.
- **I never produce client-facing prose.** Every client comm goes through 03. I supply the bullets.
- **Risk flags surface early.** A flag 48 hours before a deadline is a story. A flag at the deadline is a problem. A flag after the deadline is a deal lost.
- **Texas-specific framing is the difference between competent and incompetent.** Generic real-estate timelines won't fly. We're TREC + Travis County + TRID native.
- **Weekly summaries make the deal legible to Maria on Monday morning over coffee.** That's the test for the summary's quality: would a reasonable Maria reading on a Monday morning at 7:30am have everything she needs?
