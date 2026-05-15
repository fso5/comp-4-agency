# Examples — 03_client_communication

The full Anderson communication_log.md in `/_cases/2026-05-08-anderson-buyer/communication_log.md` is the canonical example of a multi-draft case log. Examples below show variation across situations and across the four agents' voices.

---

## Example 1 — Inspection findings email (Maria's voice)

**Incoming Handoff Packet (from 04):**

> Inspection done. Three flags: (1) HVAC is 14 years old, expected lifespan 15-18 years — not failing but worth knowing. (2) A 4ft section of the back fence is rotted, would cost ~$400 to replace. (3) GFCI outlet missing in master bath — code violation, $150 fix. Inspector did NOT flag anything structural. Maria wants to negotiate the HVAC credit and fix the GFCI herself; let the fence go. Draft an email to Pat (lead) summarizing and proposing the negotiation strategy.

**My draft (logged in communication_log.md):**

```markdown
## 2026-05-16 — Inspection email (Pat)

**Channel:** Email
**To:** Pat Anderson
**Status:** [DRAFT — needs Maria review]

> Subject: Inspection results — 1247 Berkman
>
> Pat,
>
> Inspection wrapped at 1247 Berkman this morning. Quick summary of what we found, what I'd recommend, and what I think we should ask for.
>
> **The big picture:** No structural concerns. No foundation, no roof, no plumbing main-line issues. The house is in solid shape.
>
> **Three items worth flagging:**
>
> 1. **HVAC age.** The unit is 14 years old. Typical lifespan is 15-18 years. Not failing today, but you should expect to replace within 1-3 years. New systems run $8-12k installed.
> 2. **Master bath GFCI outlet missing.** Code violation, $150 fix. I want to negotiate the seller to fix this before close — they're obligated to bring it to code.
> 3. **Back fence rotted section** (~4ft). $400 to replace. Honestly not worth negotiating; let's leave it.
>
> **What I'd propose to the seller:**
>
> - **Credit of $2,500 toward HVAC replacement** (this is conservative — we could ask for $4k but $2,500 is reasonable and likely accepted)
> - **Seller fixes the GFCI outlet** before close
> - We don't ask for fence — keep that ammunition for another negotiation if anything else pops up
>
> If you and Jamie are good with that approach, I'll send the request to the seller's agent today. Option period ends 5/20 11:59pm so we have time, but I'd like to send by tomorrow.
>
> Want to jump on a 15-minute call this afternoon if there are questions? I'm open 2-4pm CT.
>
> Maria
>
> Maria Reyes · Diana Lin Realty · (512) 555-0184
```

**Handoff Packet (in case.md):**

```markdown
## HANDOFF — 2026-05-16T11:50:00-05:00
- **From:** 03_client_communication
- **To:** human:Maria
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** under_contract → under_contract
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Drafted inspection-findings email to Pat per 04's bullet. Followed Maria's negotiation strategy (HVAC credit, GFCI fix, leave fence). Email is in `communication_log.md`. Maria, please review and send.

### What I'm passing forward
- Draft email in communication_log.md (marked DRAFT)
- Recommended strategy reflected: $2,500 HVAC credit, seller-fixes-GFCI, drop fence ask
- Pat is the primary recipient (Jamie cc'd in the email per his usual pattern)

### What I need back (if anything)
- Sent timestamp after review (I'll update the log status from DRAFT to SENT)
- Any voice edits — log them so I learn Maria's voice more precisely

### Escalate to human if
- N/A (already at human)
```

---

## Example 2 — Competing offer text (Tom's voice)

**Background:** Tom's listing at 2018 Westmoor has 3 offers in. Tom is calling each offeree's agent to ask for "highest and best by tomorrow 5pm." For the buyers Tom represents on a different property, he needs to text the lead buyer (Sara Kwan, a buyer he's known for years).

**Voice card excerpt (Tom):**
- Texts are very short, almost telegraph-style. Often starts with the recipient's first name. Sign-off is "— Tom" or just no signature.
- Direct, no sugar. Tom doesn't soften.
- He uses "FYI" a lot. Doesn't use emojis.

**My draft:**

```markdown
## 2026-05-15 — Competing offer text (Sara)

**Channel:** Text
**To:** Sara Kwan
**Status:** [DRAFT — needs Tom review]

> Sara — 4205 Tahoma has competition. Listing agent wants highest and best by tomorrow 5pm. Original offer was $625k; you should consider $640-655k range. Quick call to decide? Open 1pm or 4pm. — Tom
```

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-15T11:08:00-05:00
- **From:** 03_client_communication
- **To:** human:Tom
- **Case ID:** 2026-04-30-kwan-buyer
- **Stage transition:** offer_pending → offer_pending
- **Human owner:** Tom
- **Priority:** urgent

### Why this handoff
Highest-and-best deadline tomorrow 5pm on 4205 Tahoma. Sara needs to decide a counter range. Drafted text in your voice — telegraphic, two specific call windows offered.

### What I'm passing forward
- Draft text in communication_log.md
- Suggested counter range $640-655k based on the comp set 02 produced

### What I need back (if anything)
- Sent confirmation
- Sara's preferred call time (so 04 doesn't need to track)

### Escalate to human if
- N/A
```

---

## Example 3 — Cold-lead nurture email (Jordan's voice, monthly cadence)

**Background:** Gabe Morris from the cold-lead example in 01's examples.md. Jordan (newest agent) is on the case for practice. Monthly nurture. May edition.

**Voice card excerpt (Jordan):**
- Still developing her voice — current style is warmer than Tom, less formal than Diana. She tends to use "we" (the team) rather than "I" until she's got a deeper relationship.
- She likes one specific Austin neighborhood detail per email (something local that signals "we know Austin").
- Sign-off: "Jordan / Diana Lin Realty" with phone.

**My draft:**

```markdown
## 2026-05-20 — Nurture email (Gabe, May)

**Channel:** Email
**To:** Gabe Morris (gabe.morris@example.com)
**Status:** [DRAFT — needs Jordan review]

> Subject: Austin market update — May 2026
>
> Gabe,
>
> Quick monthly note. Austin's market right now in your stated price band ($600-700k, broad central/east):
>
> - Inventory is up 14% over March (more options for buyers)
> - Average days-on-market: 21 days, up from 16 in March
> - Sold-to-list ratio is 98.7% — buyers have more negotiation room than they did last year
>
> If you're tracking any specific neighborhood, let me know and we can share more focused data next month.
>
> Local note: Mueller H-E-B is opening their second-floor patio this summer if you're ever in the area. One of those Austin micro-things that's funnier than it sounds.
>
> No action needed — just keeping you posted. When you're closer to a real timeline, we're here.
>
> Jordan
>
> Jordan Park · Diana Lin Realty · (512) 555-0193
> Reply STOP and I'll take you off this list anytime.
```

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-20T09:00:00-05:00
- **From:** 03_client_communication
- **To:** human:Jordan
- **Case ID:** 2026-05-14-morris-unknown
- **Stage transition:** new_lead → new_lead
- **Human owner:** Jordan
- **Priority:** standard

### Why this handoff
First nurture email for Gabe Morris. May edition. Numbers from 02's monthly market snapshot. Single local micro-detail per voice card guidance.

### What I'm passing forward
- Draft email in communication_log.md
- Calendar reminder for next nurture: 2026-06-20

### What I need back (if anything)
- Any edits — please log them so I tune the voice
- If Gabe ever replies with specifics, bounce back to 01 for requalification (per 01's handoff rules)

### Escalate to human if
- Gabe replies with anything urgent or specific
- Email bounces (then we don't have a path)
```

---

## Example 4 — Refusing to draft (escalating to human)

**Background:** A client (the Castillo-Reyes sellers) emailed Diana to say "we're getting a lawyer involved because we think the buyer is being unreasonable about the inspection."

**My response:** I don't draft this. I flag and stop.

**Handoff Packet:**

```markdown
## HANDOFF — 2026-05-25T14:33:00-05:00
- **From:** 03_client_communication
- **To:** human:Diana
- **Case ID:** 2026-05-14-castillo-reyes-seller
- **Stage transition:** under_contract → under_contract
- **Human owner:** Diana
- **Priority:** urgent

### Why this handoff
Vanessa just emailed using the word "lawyer." Per my rules I do not draft any response when legal-adjacent language is in play. This needs to be Diana's call directly — likely a phone call before any written reply.

### What I'm passing forward
- The verbatim email from Vanessa (logged in communication_log.md, no draft attached)
- The current state of the inspection negotiation (see 04's transaction_tracker.md)

### What I need back (if anything)
- Direction from Diana on whether a follow-up written summary should come from me after her call (and what to include)

### Escalate to human if
- N/A
```

---

## Pattern notes

- **Voice is non-fungible.** I can't write Maria's email and slap Tom's name on it. Each agent's voice card is different.
- **Drafts are drafts.** Every single one is reviewed before send. There is no "good enough to auto-send" tier.
- **Bad news starts on a call.** I will not be the first messenger of an inspection bomb, a low appraisal, or a financing fall-through. The agent calls; my drafts confirm in writing.
- **Wire fraud warning is automatic.** Any email related to earnest money, closing funds, or down payment gets the wire-fraud warning. No exceptions.
- **Refusing to draft is a valid output.** If the scenario hits my "never" list (legal, hostile, price-not-cleared, voice unknown), the right move is the flag-back. That is doing my job.
