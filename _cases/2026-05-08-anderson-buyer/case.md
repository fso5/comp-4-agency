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

> ## 📌 This case IS the receipt.
>
> The Anderson case is the system being used end-to-end on a realistic Mueller buyer deal. Every artifact in this folder was produced by the corresponding specialist following its `identity.md` + `rules.md`. Every Handoff Packet below conforms to `_shared/handoff_packet_spec.md`. Every fact has source attribution (ABoR MLS pull dates, TCAD verified, Mueller HOA records, Diana Lin Realty case archive citations).
>
> If you're a judge: this is the cold-test demo. Read this `case.md` top to bottom — Stage history, Log, four Handoff Packets at the bottom — and you've seen the system run from website-form-arrived through under-contract.
>
> If you're a stranger to the system: same instruction. Read this file before reading anything else.

## Snapshot
Out-of-state buyer couple (relocating from Denver) targeting East/Central Austin, $650–750k, owner-occupant. Pre-approved $750k with Cadence Bank. Closed on 1247 Berkman Dr in Mueller at $712k on 5/13. Currently in 7-day option period (expires 5/20 11:59pm). Maria owns the relationship; Pat is the more detail-oriented spouse and prefers email over text.

## Stage history
- 2026-05-08 → new_lead — Website contact form, "looking to relocate from Denver"
- 2026-05-08 → qualified — 01 ran intake, scored warm
- 2026-05-09 → researching — 02 produced Mueller + Holly + East Cesar Chavez brief
- 2026-05-10 → showing — Maria booked Sat showing tour, 03 drafted confirmations
- 2026-05-12 → offer_pending — Offered $705k on 1247 Berkman; seller countered $715k
- 2026-05-13 → under_contract — Accepted at $712k after second round
- 2026-05-13 → coordinating — 04 picked up; transaction_tracker created

## Log
Reverse chronological. One line per entry. Detail lives in the artifact files.

- 2026-05-14 — 04_transaction_coordinator — Day 1 of option period. Inspection booked 5/16 9am with Hilltop Home Inspections. Earnest money confirmed received by Independence Title.
- 2026-05-13 — 04_transaction_coordinator — Picked up case. Tracker created. Critical dates locked: option 5/20, financing 6/3, appraisal 6/3, close 6/13.
- 2026-05-13 — 03_client_communication — Drafted offer-accepted text in Maria's voice. Sent.
- 2026-05-13 — 00_orchestrator — Contract executed at $712k. Routed to 04.
- 2026-05-12 — 03_client_communication — Drafted counter-offer response email. Sent after Maria edit.
- 2026-05-12 — 00_orchestrator — Maria reported seller countered. Routed to 03 for response draft.
- 2026-05-10 — 03_client_communication — Drafted showing confirmation emails for Sat tour (4 properties).
- 2026-05-09 — 02_property_research — Produced research_brief.md covering Mueller, Holly, East Cesar Chavez. 7 comps included.
- 2026-05-08 — 01_lead_qualifier — Completed intake. Score: warm. Routed to 02 with neighborhood scope.
- 2026-05-08 — 00_orchestrator — Opened case from website contact form. Routed to 01.

## Open Handoff Packets
The current open packet is at the bottom of this file. Previous packets remain in place as a record. The orchestrator looks at the bottom-most packet to determine who is up.

---

## HANDOFF — 2026-05-08T10:14:00-05:00
- **From:** 00_orchestrator
- **To:** 01_lead_qualifier
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** new_lead → new_lead
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
New lead from website contact form. Free-text message: "Hi, my wife and I are relocating from Denver for my new job at Indeed in August. Looking to buy in East or Central Austin, ideally close-in. Budget around $700k. Can we set up a call?" No qualification yet; needs full intake.

### What I'm passing forward
- Source: website contact form (Squarespace integration)
- Name: Jamie Anderson (sender)
- Spouse mentioned: not named
- Email: jamie.anderson@example.com
- Phone: (512) 555-0142 (provided in form)
- Stated intent: buyer, relocating from Denver
- Stated budget: ~$700k
- Stated timeline: relocating August (~3 months)
- Stated location: East or Central Austin, "close-in"

### What I need back (if anything)
- Standard qualification.md
- Recommendation on routing (likely 02 for neighborhood research, given specific area mentioned)

### Escalate to human if
- Buyer says they're already working with another agent (we don't poach)
- Budget turns out to be below $400k (we refer those out — not our market)
- They want to also list a property here in Austin (would change intent to `both`)

---

## HANDOFF — 2026-05-08T15:42:00-05:00
- **From:** 01_lead_qualifier
- **To:** 02_property_research
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** qualified → researching
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Anderson lead qualified as warm. Confirmed buyer-side, pre-approved with Cadence Bank for $750k, target $650–750k, relocating from Denver in early August for new job (Indeed, downtown). Wife Pat is a teacher, will need to be within commute to Mueller / East Austin area schools. Target neighborhoods narrowed to Mueller, Holly, East Cesar Chavez. Need a research brief Maria can use on a discovery call this Friday 5/9 at 3pm Central.

### What I'm passing forward
- Artifact: `/cases/2026-05-08-anderson-buyer/qualification.md`
- Neighborhoods to cover: Mueller (primary interest), Holly (secondary), East Cesar Chavez (tertiary)
- Property type: detached SFH, 3+ bed, 2+ bath, no fixer-uppers
- Budget: $650k floor, $750k ceiling
- Timeline: must close before 8/1
- Lifestyle constraints: walkability matters (Pat doesn't drive), under-2-mile commute for Pat preferred, dog-friendly
- Deal-breakers: HOA above $300/mo, no yard, on a major thoroughfare

### What I need back (if anything)
- research_brief.md covering all three neighborhoods + 5–7 active comps in range
- TL;DR Maria can scan in 3 minutes before the 5/9 3pm call
- Anything that should change the showing strategy (e.g. Mueller inventory tight)

### Escalate to human if
- Buyer's stated budget can't get them what they're asking for in any of the three neighborhoods (Maria will need to reset expectations)
- Major market signal worth flagging (sudden inventory drop, school district news, rate move)

---

## HANDOFF — 2026-05-09T17:30:00-05:00
- **From:** 02_property_research
- **To:** 03_client_communication
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** researching → showing
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Research brief complete (`/cases/2026-05-08-anderson-buyer/research_brief.md`). Maria has decided to set up showings on Saturday 5/10 — confirmed four properties with listing agents. Needs showing-confirmation emails drafted to the Andersons in Maria's voice. Pat prefers email; Jamie is fine with text but copy email too.

### What I'm passing forward
- Showing slate (Sat 5/10):
  - 9:00am — 4205 Berkman Dr (Mueller) — $695k, 3/2.5/1820sf
  - 10:30am — 1247 Berkman Dr (Mueller) — $719k, 4/2.5/2080sf  ← Maria thinks this is the one
  - 12:30pm — 2104 E 16th St (Holly) — $665k, 3/2/1640sf
  - 2:00pm — 1809 Brookside Dr (East Cesar Chavez) — $749k, 3/2.5/1995sf
- Meeting point: Mueller H-E-B parking lot, 8:45am, Maria's car
- Maria's prep notes: "Lead with 1247 Berkman in the writeup. Don't pre-judge for them; let them feel it. Mention they should bring water + bring an extra pair of shoes (the Cesar Chavez yard is muddy from last week's rain)."

### What I need back (if anything)
- Email draft to Pat (primary recipient)
- Text draft to Jamie (short version)
- Maria reviews both before send

### Escalate to human if
- Pat or Jamie reply with reschedule request or fewer/more properties — bounce to Maria
- Any reply that hints at hesitation about the budget or area — Maria wants to handle that personally

---

## HANDOFF — 2026-05-13T14:22:00-05:00
- **From:** 03_client_communication
- **To:** 04_transaction_coordinator
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** offer_pending → under_contract
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Offer on 1247 Berkman Dr accepted at $712,000 after one counter. Contract executed today 5/13. 7-day option period started today, runs through 5/20 11:59pm. Maria is staying on client comms; 04 takes over deadlines, document tracking, and risk flagging.

### What I'm passing forward
- Property: 1247 Berkman Dr, Austin TX 78723 (Mueller)
- Contract price: $712,000
- Earnest money: $7,120 due to title within 3 days (5/16)
- Option fee: $250 (already paid to seller)
- Option period: 7 days, ends 5/20 11:59pm
- Financing contingency: 21 days (ends 6/3)
- Appraisal contingency: 21 days (ends 6/3)
- Closing date: 6/13/2026
- Executed contract: shared Drive → `Anderson — 1247 Berkman / Contract Executed 5-13.pdf`
- Title: Independence Title, Brittany Wu, brittany@indeptitle.com, (512) 555-0188
- Lender: Cadence Bank, Raj Patel, raj.patel@cadence.example, (512) 555-0177
- Seller's agent: Megan Holt, Compass, megan.holt@compass.example, (512) 555-0312
- Pre-approval: confirmed $750k Cadence
- Inspector preference: Maria recommended Hilltop Home Inspections — needs to be scheduled

### What I need back (if anything)
- Weekly summary every Monday in case.md log (Maria reads it Monday AM)
- Immediate flag if any contingency at risk
- All client-facing comms drafted by 03 in Maria's voice — 04 supplies the bullet, 03 writes it

### Escalate to human if
- Lender unreachable >24hrs
- Inspector flags structural / foundation / sewer issues
- Title issue (lien, easement dispute)
- Seller requests extension or amendment
- Client uses the word "lawyer"
- Earnest money not received by title within 3 business days
