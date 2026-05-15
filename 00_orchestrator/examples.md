# Examples — 00_orchestrator

The four Handoff Packets in the Anderson `case.md` show what my work looks like at each stage. Examples below show different routing types.

---

## Example 1 — New prospect from website (standard new-lead routing)

**Inbound:**
> Website contact form. Body: "Hi, my wife and I are relocating from Denver for my new job at Indeed in August. Looking to buy in East or Central Austin, ideally close-in. Budget around $700k. Can we set up a call?" Sender: Jamie Anderson, jamie.anderson@example.com, (512) 555-0142.

**My work:**

1. Searched `_cases/` — no match for "Anderson" or this email.
2. New case. Naming: `2026-05-08-anderson-buyer/`.
3. Routing: Step 5 of decision tree → 01_lead_qualifier.
4. Owner rotation: Maria's turn in the rotation. Anderson stated specific area + budget so this fits Maria's specialty (mid-market central).
5. Priority: standard (warm-sounding, but no forced timeline yet — 01 will reassess).

**Created `case.md` with this initial state:**

```yaml
---
case_id: 2026-05-08-anderson-buyer
client_name: Jamie Anderson (spouse name unknown)
primary_contact: jamie.anderson@example.com / (512) 555-0142
intent: buyer
stage: new_lead
current_owner: 01_lead_qualifier
assigned_agent: Maria
opened: 2026-05-08
last_updated: 2026-05-08
priority: standard
---
```

**Handoff Packet appended:** (full version in `_cases/2026-05-08-anderson-buyer/case.md`, top packet)

**Log entry:** `2026-05-08 — 00_orchestrator — Opened case from website contact form. Routed to 01.`

---

## Example 2 — Existing-case inbound (client reply mid-deal)

**Inbound:**
> Email from Pat Anderson to Maria's address: "Thanks Maria. Quick question — do we need to be at the inspection on Friday? Pat"

**My work:**

1. Searched `_cases/` — match on `2026-05-08-anderson-buyer`.
2. Read the case.md. Current state: `stage: under_contract`, `current_owner: 04_transaction_coordinator`. Most recent Handoff Packet is from 03 to 04. There's no open packet for client reply.
3. This is a routine client question, not a transaction milestone. Default for client-facing reply is 03_client_communication.
4. Maria is the assigned agent — she'll review the draft.

**Updated case.md frontmatter:**
- `current_owner` → `03_client_communication`
- `last_updated` → today's date

**Log entry:** `2026-05-14 — 00_orchestrator — Pat asked if they need to attend inspection. Routed to 03 for Maria-voice reply.`

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-14T10:04:00-05:00
- **From:** 00_orchestrator
- **To:** 03_client_communication
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** under_contract → under_contract
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Pat emailed Maria asking if they need to be at Friday's inspection. Quick reply needed in Maria's voice. Per case.md, inspection is booked at Hilltop Home Inspections, Friday 5/16 9am, with Maria attending. Andersons do NOT need to be there.

### What I'm passing forward
- Verbatim message: "Thanks Maria. Quick question — do we need to be at the inspection on Friday? Pat"
- Facts: inspection 5/16 9am, Maria attending, Andersons not required to attend, Maria will walk them through findings after
- Channel: email (Pat's preference, per qualification.md)
- Tone: warm, brief

### What I need back (if anything)
- Sent timestamp after Maria reviews

### Escalate to human if
- If Pat replies asking to attend after all → that's fine, just confirm via 03
```

---

## Example 3 — Disambiguating between multiple existing cases

**Inbound:**
> Text to Maria: "Hi Maria, the inspection is set for 9am Friday, Marcos confirmed. Let me know if you need anything else." Sent from (512) 555-0291 (Marcos Vela, Hilltop Home Inspections).

**My work:**

1. Searched `_cases/` — Marcos's number/email is associated with multiple cases as the inspector contact (Anderson + at least one other in the past).
2. Which case? The message says "the inspection" but doesn't name a property. Maria has multiple deals.
3. **Routing call:** ambiguous. Could be Anderson; could be another case Maria has running.
4. Default: escalate to `human:Maria` with my recommended guess (most likely Anderson, since that's the only Maria-owned case currently in option period).

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-13T15:22:00-05:00
- **From:** 00_orchestrator
- **To:** human:Maria
- **Case ID:** (likely 2026-05-08-anderson-buyer — please confirm)
- **Stage transition:** N/A
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Marcos from Hilltop confirmed an inspection time for Friday 9am, but didn't name the property. Most likely it's Anderson's 1247 Berkman (they're the only active case in option period with you as agent). Confirming with you before routing to 04 to update the tracker.

### What I'm passing forward
- Inbound text verbatim
- Best guess: Anderson case
- Other possibility: a deal I don't have visibility on

### What I need back (if anything)
- Confirmation of which case
- After confirm, I'll route to 04 to update the tracker

### Escalate to human if
- N/A (already at human)
```

---

## Example 4 — Hostile / legal-adjacent message (immediate escalation)

**Inbound:**
> Email from Vanessa (the Travis Heights seller): "If the buyer doesn't accept our pre-list condition, we'll be talking to a lawyer about whether our representation was adequate."

**My work:**

1. Located the case.
2. Step 2 of routing decision tree: "lawyer" keyword present → immediate escalation.
3. No drafts. No routing to 03.

**Updated case.md frontmatter:**
- `current_owner` → `human:Diana`
- `priority` → `urgent`

**Log entry:** `2026-05-25 — 00_orchestrator — Vanessa email contained "lawyer" — escalated to Diana, no drafts produced.`

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-25T14:30:00-05:00
- **From:** 00_orchestrator
- **To:** human:Diana
- **Case ID:** 2026-05-14-castillo-reyes-seller
- **Stage transition:** under_contract → under_contract
- **Human owner:** Diana
- **Priority:** urgent

### Why this handoff
Inbound email from Vanessa mentions "talking to a lawyer." Per system rules, immediate human escalation. No drafts, no further routing. The full inbound text is in this case's communication_log.md (appended by me without a draft, per 03's rule for legal-adjacent messages).

### What I'm passing forward
- Verbatim email from Vanessa
- Current case state (under contract, in negotiation phase per 04's tracker)

### What I need back (if anything)
- Direction on whether a written follow-up should come from this system at all post-Diana-call

### Escalate to human if
- N/A
```

---

## Pattern notes

- **Routing is mostly mechanical.** ~85% of inbound falls into one of the standard decision-tree paths and routes without escalation.
- **The 15% requiring escalation is where this system earns its keep.** Bad routing on a hard case can hand Diana's team a problem. Escalating to a human is always the safe option.
- **A new case file is a commitment.** Once opened, it lives forever (until manually archived). Don't open cases speculatively.
- **The Handoff Packet I produce is just like every other Handoff Packet** — same format, same expectations. I don't get a special pass.
- **My log entries are the system's audit trail.** Diana can read `case.md` files top-to-bottom and reconstruct exactly why every routing happened. This is the system's accountability.
