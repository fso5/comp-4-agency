# Voice Switcher — the same email in 4 voices

This file demonstrates that the voice cards (`agent_voices.md`) produce genuinely different output for the same situation. Same client, same facts, same goal — four different agents, four distinct voices.

**The situation:** Inspection on a buyer's property revealed three minor items (HVAC age, missing GFCI outlet, rotted fence section). Agent needs to email the buyer (Pat Anderson) summarizing findings and proposing a negotiation strategy.

The facts (constant across all four drafts):
- HVAC is 14 years old (functional, no immediate replacement needed but worth knowing — typical lifespan 15-18 years)
- Master bath GFCI outlet missing (code violation, $150 fix)
- 4ft section of back fence rotted ($400 to replace)
- Negotiation strategy: ask seller for $2,500 HVAC credit + GFCI fix, drop the fence ask
- Option period ends Tuesday

---

## Diana's voice

Diana sounds like a friend who happens to be very good at her job. Warm opening line. Medium-length sentences. Long-relationship references when applicable. No emojis.

> Subject: Inspection results — quick read before tomorrow's call
>
> Pat,
>
> Hope the move-out planning is going smoothly. The Berkman inspection wrapped this morning. The house is solid. Three small items came up worth flagging:
>
> The HVAC unit is 14 years old. Functional today, but you should expect to replace it in the next one to three years (typical $8-12k installed). The GFCI outlet in the master bath is missing — code violation, the seller should fix that one before close. And there's a small rotted section of the back fence, about four feet, that would cost roughly $400 to repair.
>
> What I'd recommend asking the sellers for: a $2,500 credit toward the eventual HVAC replacement, plus they handle the GFCI fix themselves. I'd leave the fence — small enough that it's not worth burning negotiating capital on.
>
> Glad to talk it through if you want, otherwise I'll send the request to their agent in the morning.
>
> Best, Diana

---

## Maria's voice

Maria opens without a greeting. Gets to the point. Uses structured lists for options. Always offers a phone call. One emoji max, only when natural.

> Subject: Inspection results — 1247 Berkman
>
> Pat —
>
> Inspection wrapped at 1247 Berkman this morning. Quick summary of what we found, what I'd recommend, and what I think we should ask for.
>
> **The big picture:** No structural concerns. No foundation, no roof, no plumbing main-line issues. The house is in solid shape.
>
> **Three items worth flagging:**
>
> 1. **HVAC age.** Unit is 14 years old. Typical lifespan 15-18 years. Not failing today, but expect to replace within 1-3 years. New systems run $8-12k installed.
> 2. **Master bath GFCI outlet missing.** Code violation, $150 fix. Negotiable.
> 3. **Back fence rotted section** (~4ft). $400 to replace. Honestly not worth negotiating.
>
> **What I'd propose to the seller:**
>
> - Credit of $2,500 toward HVAC replacement
> - Seller fixes the GFCI outlet before close
> - Leave the fence — keep that ammunition for another negotiation if anything else pops up
>
> Want to jump on a 15-minute call this afternoon if there are questions? I'm open 2-4pm CT.
>
> Maria
>
> Maria Reyes · Diana Lin Realty · (512) 555-0184

---

## Tom's voice

Tom is telegraphic. Short, direct, no softening. No emojis. "FYI" frequent. Texts for almost everything, but this needs to be in writing.

> Subject: Berkman inspection — items + ask
>
> Pat,
>
> Three items from the Berkman inspection. None deal-breaking.
>
> HVAC 14yrs old. Works fine. Expect to replace 1-3yrs. New unit $8-12k.
> GFCI outlet missing master bath. Code violation. $150 fix. Negotiable.
> Fence rotted 4ft section. $400. Not worth fighting for.
>
> Ask: $2500 HVAC credit + seller fixes GFCI. Drop the fence.
>
> Need decision by EOD tomorrow to submit to seller's agent. Quick call works.
>
> T.B.
>
> Tom Buchanan
> Diana Lin Realty · (512) 555-0177

---

## Jordan's voice

Jordan is still developing her voice. Uses "we" more than "I" until relationship is established. Friendly opening, fuller explanations. One Austin micro-detail when it fits. Sign-off includes the team name.

> Subject: Inspection update from this morning — three small items
>
> Hi Pat,
>
> The inspection at 1247 Berkman wrapped up this morning. Marcos from Hilltop Home Inspections did a thorough walkthrough (he's one of the best in Austin — Mueller agents almost always call him first). Three small items came up, and I want to walk you through them and what we'd recommend.
>
> First, the HVAC unit. It's 14 years old, which puts it in the back half of its expected 15-18 year lifespan. It's working fine right now, but planning on replacement within the next one to three years is realistic. A new system runs $8,000 to $12,000 installed.
>
> Second, the master bathroom is missing a GFCI outlet. That's a code violation and a quick fix (about $150). The seller should handle this before close.
>
> Third, there's a four-foot section of rotted fence in the back yard. About $400 to replace. Minor.
>
> What we'd recommend asking the seller for: a $2,500 credit toward the HVAC replacement and that they fix the GFCI outlet themselves. We'd leave the fence — small enough that it's better to keep that as a future bargaining chip if anything else comes up.
>
> Let me know if any of this needs clarification, or if you'd prefer to discuss on a call. I'm available this afternoon.
>
> Jordan
> Diana Lin Realty · (512) 555-0193

---

## What this demonstrates

Four agents. Same facts. Four genuinely distinct voices.

This is the methodology preserving voice difference, not flattening it (same principle Jake highlighted in Ruben's Week 3 winning submission: "Maya and Dale identity examples — same niche, completely different voices — demonstrate the methodology preserves voice difference rather than flattening it").

The voice cards in `agent_voices.md` are what make this work. They're not adjectives ("warm and professional"). They're specific phrases, opening patterns, emoji rules, sample sentences, and explicit do-not-use lists.

When 03_client_communication drafts a message:
1. It reads the `assigned_agent` field in the case's `case.md` frontmatter
2. It opens `agent_voices.md` to that agent's voice card
3. It reads the prior 3 entries in the case's `communication_log.md` for voice continuity
4. It drafts in that agent's voice
5. It marks the draft `[DRAFT — needs <agent> review]`

The voice gets sharper over time through Rule 8 (Communication): "When the agent edits a draft, log the edit. If Maria changes 'Hi Pat,' to 'Pat —' three times in a row, update her voice card."

That's the edit-source principle (ICM Section 6.3) applied to voice tuning in production.
