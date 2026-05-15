# Handoff Packet Spec

**The handoff is the whole game.** If specialists pass vague prose to each other, the system collapses into "ask Diana." The Handoff Packet is the structured artifact that makes routing mechanical and review-able.

Every handoff appends one of these blocks to the bottom of `case.md`. The orchestrator scans the bottom of `case.md` first to determine who is up.

---

## The format

```markdown
## HANDOFF — 2026-05-13T14:22:00-05:00
- **From:** 03_client_communication
- **To:** 04_transaction_coordinator
- **Case ID:** 2026-05-08-anderson-buyer
- **Stage transition:** offer_pending → under_contract
- **Human owner:** Maria
- **Priority:** standard

### Why this handoff
Offer on 1247 Berkman was accepted at $712,000. Contract executed today. Option period
runs 7 days. Maria needs the transaction coordinator to take over the deadlines and document
tracking. Maria stays on client comms.

### What I'm passing forward
- Artifact: `/cases/2026-05-08-anderson-buyer/communication_log.md` (see entries 5/12–5/13)
- Property: 1247 Berkman Dr, Mueller, 78723
- Executed contract: shared Drive → `Anderson — 1247 Berkman / Contract Executed 5-13.pdf`
- Option period: 7 days starting 5/13, expires 5/20 11:59pm
- Earnest money: $7,120 due to title within 3 days
- Title company: Independence Title — Brittany Wu, brittany@indeptitle.com
- Lender: Cadence Bank — Raj Patel, raj.patel@cadence.example, pre-approved $750k

### What I need back (if anything)
- Weekly deadline summary in case.md log every Monday morning
- Immediate flag if option period or financing contingency is at risk
- All client-facing comms (deadline reminders, scheduling) come back to 03 — 04 drafts the bullet, 03 puts it in voice

### Escalate to human if
- Lender becomes unreachable >24hrs
- Inspector flags structural / foundation issues
- Title issue surfaces (lien, easement dispute)
- Seller requests extension or amendment of any kind
```

---

## The fields, in detail

### Header line: `## HANDOFF — <ISO 8601 timestamp>`

ISO format with timezone offset. Austin is Central Time (`-05:00` in DST, `-06:00` otherwise). Timestamps let Diana sort by chronology and prove what happened when.

### `From` and `To`

The folder name of the originating specialist and the receiving specialist. Use the full prefixed folder name (`01_lead_qualifier`, not "lead qualifier"). The `To` value can also be `human:<name>` when escalating (e.g. `human:Maria`).

Valid `From` / `To` values:
- `00_orchestrator`
- `01_lead_qualifier`
- `02_property_research`
- `03_client_communication`
- `04_transaction_coordinator`
- `human:Diana` / `human:Maria` / `human:Tom` / `human:Jordan`

### `Case ID`

Must match the folder name exactly. Belt and suspenders — the packet is also inside the case folder, but having the ID inline makes packets copy-paste-safe if Diana ever wants to review them outside the folder.

### `Stage transition`

Two stage names from `case_file_spec.md`, separated by an arrow: `qualified → researching`. If the stage isn't changing (e.g. 03 hands back to 04 within the same `under_contract` stage), use the same stage on both sides: `under_contract → under_contract`. Always include it — it forces the writer to think about whether a stage change is implied.

### `Human owner`

Which member of Diana's team is the human accountable for this case. Always one of `Diana`, `Maria`, `Tom`, `Jordan`. Even if the AI specialist is doing the work, a human owns the relationship.

### `Priority`

- `standard` — default. Handle in normal work order.
- `warm` — qualified lead, time-sensitive but not on fire. Address within 1 business day.
- `urgent` — option period at risk, financing falling through, client threatening to walk, missed showing the client is mad about. Address immediately, page the human owner.

If you're tempted to invent a fourth priority level, don't. Three is enough. More gradations create noise.

---

## The four body sections

These are not optional. Empty sections are filled with `(none)`, not removed.

### `### Why this handoff`

One paragraph. Two key questions:

1. What did the previous specialist conclude?
2. What is the next specialist being asked to do?

If you can't summarize this in three to five sentences, the handoff isn't crisp enough — go back and tighten the artifact first.

### `### What I'm passing forward`

A list. Include every input the receiving specialist needs to do their job. Be concrete:

- **Always:** link to the artifact file the receiver should read first
- **Almost always:** the specific question or scope of work (don't make the receiver guess)
- **Frequently:** key facts the receiver shouldn't have to re-extract (budget, timeline, address, contract dates)
- **When relevant:** third-party contacts (lender, title, inspector) with name + email + phone
- **When relevant:** links to external docs in shared Drive

If a fact lives in the artifact file the receiver is going to read anyway, you can skip restating it — but err toward restating the load-bearing ones.

### `### What I need back (if anything)`

Most handoffs are one-way. Some aren't.

- 04 hands work to 03 to draft client comms, then needs the drafts back.
- 02 sometimes needs the human to verify a fact before producing the brief.
- 03 may hand back to 01 if a "new lead" turns out to be a renewal of an existing client and qualification needs to be re-run.

If the answer is genuinely "nothing back," write `(none)`. Don't leave it blank.

When return is needed, specify:
- The format expected back (a draft, a verified fact, a yes/no, a confirmed showing time)
- The deadline (e.g. "before Thursday 4pm client call")

### `### Escalate to human if`

This is the safety valve. Every handoff includes the conditions under which the receiving specialist should *stop* and bounce the case back to a human instead of completing.

Be specific. Generic "if anything seems wrong" doesn't help. Write conditions a specialist can mechanically check:

- "Buyer says they're unrepresented and asks for our help with the seller's paperwork — escalate to Diana."
- "Inspector report references foundation, roof structural, or sewer line — escalate to Maria."
- "Client uses the word 'lawyer' — escalate to Diana within 1 hour."

If there's truly nothing the specialist needs to escalate on (rare — there's almost always *something*), write `(none — handle to completion)`.

---

## How the orchestrator uses this

When the orchestrator receives a new message or check-in, it reads `case.md` and looks at the bottom. The most recent Handoff Packet tells it:

- Whose work is open right now (`To:` field)
- Why (`Why this handoff`)
- What the priority is

If the `To` is a specialist folder, the orchestrator routes the request there with the packet as context. If the `To` is `human:<name>`, the orchestrator does not route to a specialist — it surfaces the case to that human and stops.

When a specialist finishes work, they:
1. Append/update their artifact file (`qualification.md`, `research_brief.md`, etc.)
2. Append a one-line entry to the `## Log` section in `case.md`
3. Update `stage`, `current_owner`, `last_updated` in the `case.md` frontmatter
4. Append a new Handoff Packet at the bottom of `case.md`

That's the loop. Same four steps every time. New agents learn it in under an hour.

---

## What "good" looks like

A good Handoff Packet:

- Could be reviewed by Diana on her phone at a red light and she'd know exactly what's going on
- Names specific files, addresses, numbers, names — not "the buyer" or "the property"
- Sets the receiver up to start working immediately without asking clarifying questions
- States escalation conditions in a way a specialist can mechanically check

A bad Handoff Packet:

- "Tom, take a look at this when you get a chance."
- "Continue working on the Anderson case."
- "Need research on the neighborhood."
- "Escalate if anything weird."

If you catch yourself writing a bad one, stop and rewrite. The whole system depends on this.
