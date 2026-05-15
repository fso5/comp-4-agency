# Examples — 01_lead_qualifier

Three example interactions showing how I handle different incoming leads. The full Anderson qualification.md lives in `/_cases/2026-05-08-anderson-buyer/qualification.md` — read that first for the canonical "warm buyer" pattern. The examples below show variation.

---

## Example 1 — Hot seller lead (referral)

**Input from orchestrator:**
> New case opened. Source: text to Diana's personal phone from her past client (Linda Castillo, sold with us 2019). Linda forwarded a message from her sister: "Hi Diana, Linda said you're the best. My husband and I are listing our house in Travis Heights, 1907 Drake. We want to be on the market by June 1st. He took a new job in Houston. Can we talk this week?"
>
> Sender: Vanessa Castillo-Reyes (Linda's sister)
> Phone: (512) 555-0099
> Email: not provided
> Property mentioned: 1907 Drake Ave, Travis Heights

**My qualification.md (abbreviated):**

```markdown
# Qualification — Vanessa & Marco Castillo-Reyes

## TL;DR
Past-client referral (sister of Linda Castillo, our 2019 client). Sellers in Travis Heights at 1907 Drake. Job-relocation forced timeline — husband Marco starting in Houston, family relocating. Target list by 6/1. Score: hot. Diana should call back today.

## Intent
- Seller. No mention of buying elsewhere through us (likely buying in Houston via different agent).

## Clients & contacts
- Vanessa Castillo-Reyes (primary), (512) 555-0099
- Husband: Marco Reyes
- Source: referral from Linda Castillo (our 2019 client) — tag Linda for thank-you
- Email: unknown — Diana to confirm on first call

## Financial readiness
- Selling, not buying-side — financing not applicable in the traditional sense
- Existing mortgage on 1907 Drake: unknown — Diana to confirm
- Equity position: unknown — needs CMA from 02
- Cash for staging / pre-list repairs: unknown

## Timeline
- Marco's job start: unknown specific date — Diana to confirm
- Stated target: list by 6/1 (about 3 weeks out)
- Hard end date implied: husband relocating, family likely follows by end of summer
- This is a HOT timeline.

## Location & property
- 1907 Drake Ave, Travis Heights, 78704
- Unknown beds/baths/sqft — pull from TCAD
- Travis Heights is a strong neighborhood for our team; we have recent comps

## Motivation
- Marco's new job in Houston
- Family of (unknown) is relocating
- Past-client family — emotional ties, wants someone trusted (specifically asked for Diana)

## Constraints
- 6/1 list target is aggressive — may need to scope pre-list work tightly
- Out-of-state buyer (likely buying in Houston) → may want speed over max price; Diana will probe

## Qualification score: HOT
**Why hot:** referral from past client (highest priority source), specific property identified, forced timeline (job relocation), clear motivation, explicit ask for Diana. Diana should not let this sit.

## Routing recommendation
→ **human:Diana** for the first call. This is too warm and too referral-driven to route to a specialist before Diana has touched it. After Diana's call, route to 02 for CMA on 1907 Drake. (See Handoff Packet.)
```

**My Handoff Packet:**

```markdown
## HANDOFF — 2026-05-14T09:18:00-05:00
- **From:** 01_lead_qualifier
- **To:** human:Diana
- **Case ID:** 2026-05-14-castillo-reyes-seller
- **Stage transition:** new_lead → qualified
- **Human owner:** Diana
- **Priority:** urgent

### Why this handoff
Past-client referral (Linda Castillo). Sister Vanessa needs to list 1907 Drake in Travis Heights by 6/1 due to husband's job relocation to Houston. Specifically asked for Diana. Diana should call back today before another agent gets in. After Diana's first call, I expect this routes to 02 for CMA prep.

### What I'm passing forward
- Property: 1907 Drake Ave, Travis Heights, 78704
- Contact: Vanessa, (512) 555-0099 (no email yet)
- Source: Linda Castillo referral — thank-you note to Linda after the deal
- Target list date: 6/1
- Why: Marco's new Houston job

### What I need back (if anything)
- After Diana's call, route forward (likely 02 for CMA + neighborhood market read)
- Diana to fill in unknowns (email, exact timeline, equity position, pre-list scope)

### Escalate to human if
(N/A — already routed to Diana)
```

---

## Example 2 — Cold web inquiry

**Input from orchestrator:**
> Website contact form, no phone provided. Message body: "Just browsing. Maybe looking in the next year or so. What's the market doing?"
>
> Email: gabe.morris@example.com
> Source: website
> No other context.

**My qualification.md (abbreviated):**

```markdown
# Qualification — Gabe Morris

## TL;DR
Web form inquiry, "just browsing." No financing, no timeline, no specific area, no specific question other than "what's the market doing." Score: cold. Don't burn a research brief on this yet. Route to 03 for a low-touch nurture sequence.

## Intent
- Likely buyer (implied), but not stated explicitly. `intent: unknown` until confirmed.

## Clients & contacts
- Name: Gabe Morris (per email)
- Email: gabe.morris@example.com
- Phone: unknown
- All other details: unknown

## Financial readiness
- Unverified. No mention of pre-approval, budget, or down payment.

## Timeline
- Stated: "next year or so"
- Not actionable for property research; very actionable for nurture comms.

## Location & property
- Not specified.

## Motivation
- Not specified. Possibly tire-kicking; possibly serious but early.

## Qualification score: COLD
**Why cold:** no financing signal, vague timeline (12+ months), no geography, no motivation. Standard "I'm thinking about it" inquiry.

## Routing recommendation
→ **03_client_communication** for a Tuesday-cadence nurture sequence (one helpful market-snapshot email per month, no pressure). If Gabe replies with any specifics, kick back to me for full requalification.
```

**My Handoff Packet:**

```markdown
## HANDOFF — 2026-05-14T11:02:00-05:00
- **From:** 01_lead_qualifier
- **To:** 03_client_communication
- **Case ID:** 2026-05-14-morris-unknown
- **Stage transition:** new_lead → qualified
- **Human owner:** Jordan (newest agent — good practice for her)
- **Priority:** standard

### Why this handoff
Cold web inquiry, 12+ month horizon, no specifics. Not worth research bandwidth. Good fit for a low-touch nurture sequence. Jordan can use this to practice her voice on nurture comms (low stakes).

### What I'm passing forward
- Email only: gabe.morris@example.com
- No phone, no other data
- Suggested nurture cadence: monthly market snapshot, no calls to action
- Tone: friendly, not pushy. We want him to remember us when he's ready.

### What I need back (if anything)
- Bounce back to me if Gabe ever responds with specifics (budget, timeline, area) — that's a requalification trigger.

### Escalate to human if
- Gabe replies with anything urgent or specific (asks to tour something, mentions a specific property, gives a budget)
- Email bounces (then we don't have a path — discard or surface to Jordan)
```

---

## Example 3 — Disqualified (already represented)

**Input from orchestrator:**
> Instagram DM to Diana's team account: "Hey! Saw your post about Mueller. I'm working with @joelblake_realtor on a search but he's not finding what I want in Mueller. Can you send me some listings?"
>
> Sender: @ashtonbuyshouses
> No other info

**My qualification.md (very brief):**

```markdown
# Qualification — @ashtonbuyshouses

## TL;DR
DM inquiry from a buyer who is already represented by another agent (@joelblake_realtor). Standard "shopping around" approach. We do not poach. Score: disqualified.

## Routing recommendation
→ **human:Diana** with a draft polite-decline reply for Diana to review.
```

**My Handoff Packet:**

```markdown
## HANDOFF — 2026-05-14T13:47:00-05:00
- **From:** 01_lead_qualifier
- **To:** human:Diana
- **Case ID:** 2026-05-14-ashtonbuyshouses-disqualified
- **Stage transition:** new_lead → lost
- **Human owner:** Diana
- **Priority:** standard

### Why this handoff
DM inquiry from a buyer who explicitly states they have an existing agent. Per our rules, we don't engage. Drafted a polite decline for your review (below). Logging this case as `lost` with reason "already represented." Quick win for the log.

### What I'm passing forward
- Username: @ashtonbuyshouses
- Existing agent named: @joelblake_realtor
- Suggested reply draft:
  > "Hi Ashton — sounds like you're already in good hands with Joel. Best of luck with the search. If anything ever changes on the representation front, you know where to find us. — Diana Lin Realty"

### What I need back (if anything)
- (none — close the case after Diana sends the reply)

### Escalate to human if
(already at human — N/A)
```

---

## Pattern notes

- **The format flexes to the lead.** Hot referral gets a full breakdown. Cold inquiry gets a short qualification.md. Disqualified gets a near-empty one. Don't bloat the artifact for a lead that doesn't justify it.
- **Routing is the load-bearing decision.** I will be judged on routing accuracy more than on qualification depth. A perfect qualification routed to the wrong specialist wastes the next person's time.
- **The TL;DR is the most-read section.** Treat it as the 3-line summary that Maria reads at a red light. Everything else is for when she has time to dig in.
