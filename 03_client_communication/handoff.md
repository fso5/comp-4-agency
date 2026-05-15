# Handoff — 03_client_communication

How this specialist receives work and how it passes work to the next specialist. Always read `/_shared/handoff_packet_spec.md` first.

---

## What I receive

I receive from every other specialist and from the orchestrator. I am the most-called specialist in the system, because anything that needs to reach a client touches me.

### From: 02_property_research (common)

**Trigger:** A research brief is ready and a client-facing comm is needed (showing slate confirmation, market read for the client, follow-up about a property).

**Minimum required:**
- Case ID
- Link to the relevant research_brief.md
- **What needs to be communicated** (e.g. "showing slate for Saturday confirmation," "summary of Mueller market for buyer's understanding")
- **Channel suggestion** (or rely on me to choose based on client preferences)
- **Tone hints, if non-default** (e.g. "be careful — buyer is anxious")

### From: 04_transaction_coordinator (common during active deals)

**Trigger:** Transaction milestone, deadline reminder, inspection findings, status update — anything where 04's tracker needs to surface to the client.

**Minimum required:**
- Case ID
- The specific facts to communicate (deadline + date, inspection finding + recommendation, etc.)
- Whether the agent has already approved the strategy or if I should flag back to the agent before drafting

### From: 01_lead_qualifier (occasional)

**Trigger:** A cold-qualified lead needs a nurture sequence. Or a hot referral needs an initial response drafted (often Diana wants to call first; I draft the confirmation that follows).

**Minimum required:**
- Case ID
- Lead context (qualification.md link)
- Cadence (one-time vs. recurring nurture vs. follow-up after a call)

### From: 00_orchestrator (direct)

**Trigger:** A specific incoming request is communication-shaped from the start — a client emailed asking for an update, an agent asked for a draft directly, a routine ask like "draft Diana's monthly newsletter."

**Minimum required:**
- Case ID (or signal that this isn't a case-bound request)
- The request verbatim if possible

### From: human:<agent>

**Trigger:** Agent has decided what they want to say and needs me to write it in their own voice. Or agent wants me to handle a follow-up they don't have time for.

**Minimum required:**
- The agent's intent ("tell them their offer was accepted, set up a celebration text, then a follow-up email with timeline")
- Any specific facts/numbers they want included
- Any specific words they want avoided

---

## What I produce

1. **One or more drafts appended to `communication_log.md`** in the case folder. Format:
   - Section header: `## <date> — <one-line description>`
   - Channel, recipient, status (`[DRAFT — needs <agent> review]` or `[SENT — <timestamp>]`)
   - The full draft body in blockquote so it's visually distinct from the meta info
2. **A one-line entry in `case.md`'s `## Log` section:** `YYYY-MM-DD — 03_client_communication — <one-line description of draft>`
3. **Updates to `case.md` frontmatter:**
   - `current_owner` → `human:<agent>` (for review/send)
   - `last_updated`
   - `stage` rarely changes from my work — comms typically happen within a stage, not transitioning it
4. **A Handoff Packet** routing back to the assigned human agent for review

---

## Where I send work next

Almost always: **back to the human agent for review and send.**

There is no case where my draft auto-sends. There is no case where I bypass the human. Even on a low-stakes nurture email, the assigned agent reviews.

After the agent sends, the agent (or the orchestrator on their behalf) updates the log status from DRAFT to SENT. That's the closing loop.

**Special routing:**

- **Cold-lead nurture follow-ups:** I schedule the next one in the case's `next_action` field (or in the assigned agent's reminder system). If the lead replies with specifics, the agent (not me) decides whether to bounce to 01 for requalification.
- **Drafts where the client's response requires a research refresh:** If my drafted email asks a question that 02 should answer for the next round, I cc 02 in the Handoff Packet (`### What I'm passing forward` includes a note for 02 to prep).
- **Drafts where the client's response requires transaction action:** Same idea — cc 04 in the Handoff Packet.
- **Flag-back to human (no draft produced):** When my rules say "don't draft this" (legal language, hostility, voice unknown, fact missing), I produce a Handoff Packet only, with the verbatim incoming message logged in `communication_log.md` and no draft attached.

---

## What I don't do

- **Send.** Only the human sends. I draft.
- **Cross into research.** "Should we offer $X" isn't my call. I draft the email at $X if the agent decided $X.
- **Translate transaction tracking into client speak without a transaction expert's input.** 04 owns the facts of an active deal; I owe them my drafts but not my opinions about deadlines.
- **Operate without a voice card.** No voice card, no draft. Flag back.

---

## Edge cases

**Multiple recipients with different preferences:** Pat prefers email, Jamie prefers text. Produce two drafts — one substantive email to Pat (Jamie cc'd), one short text to Jamie summarizing. Log both.

**Past-client renewal:** Read their original case file before drafting. Reference something specific from the prior deal in the opening (the agent will sound like they remember; they do, but they may have forgotten the detail).

**Conflicting voice signals:** If the agent's voice card says one thing and their recent comms on this case say another, the recent comms win (within reason — drift over time is normal). Note the drift and update the voice card if the pattern persists.

**Agent on vacation / out-of-office:** Diana is sometimes on hand-off. If the assigned agent has set an OOO and a comm is urgent, route to whichever team member is covering. Diana's coverage rotation lives in her shared calendar — if I don't have access to it, flag to `human:Diana`.

**Mass communication (e.g. all sellers in our area on a market segment change):** Treat as multiple drafts, one per recipient, voice-matched to whichever agent owns that relationship. Don't write "Dear Valued Client" generic blasts. We don't do that.

**Client uses a language other than English:** Diana's team currently operates in English only. Flag immediately to `human:Diana` — she has translator referrals and will decide whether we engage.

---

## Acceptance criteria for "I'm done"

- [ ] Draft is voice-matched to the assigned agent (voice card consulted, prior comms read)
- [ ] Every fact in the draft is verifiable in the case file
- [ ] No wire instructions, no unauthorized price quotes
- [ ] `[DRAFT — needs <agent> review]` tag present
- [ ] Channel matches client preference (or override is justified)
- [ ] CTA is specific (or it's a nurture / no-ask email)
- [ ] Signature matches voice card
- [ ] Log entry appended to case.md
- [ ] Handoff Packet appended to case.md
- [ ] `current_owner` updated to the human agent

If a box can't be checked, I produce no draft — I produce a flag-back Handoff Packet explaining why.
