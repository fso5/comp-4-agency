# Stack Mapping — Where this system fits (Constraint 06: Layer Triage)

The 60/30/10 framework from Jake Van Clief's Clief Notes Vault (Constraint 06: Layer Triage):

> "60% of what a business runs should be traditional tools (spreadsheets, databases, software — they do not hallucinate). 30% should be rule-based automation (Zapier, n8n, email rules). 10% should be AI (judgment, synthesis, creativity)."

> "The question is not 'can AI do this?' It almost always can. The question is 'should AI do this, or is there a layer beneath AI that handles it better, faster, and cheaper?'"

This system is the 10%. Below is the full stack map for a 4-person boutique real estate team like Diana's.

---

## The 60% — Traditional tools (Diana already has these — DO NOT REPLACE)

| Function | Tool | Why it stays at the 60% layer |
|---|---|---|
| MLS access | **ABoR (Austin Board of Realtors) MLS** | Authoritative for active/sold listings. Deterministic queries. Cannot hallucinate prices. |
| Tax records | **TCAD (Travis County Appraisal District)** | Authoritative for sqft, lot size, year built, tax assessed value. Public records, single source of truth. |
| Document signing | **DocuSign** | Legal binding requires deterministic signature workflows. AI cannot replace. |
| File storage | **Google Drive** | Shared docs, executed contracts, photos. Deterministic file paths. |
| Calendar | **Google Calendar** | Showings, deadlines, closings. Deterministic time slots. |
| Deal pipeline | **Google Sheets** (or similar) | Commission tracking, transaction count by month, pipeline aggregates. Deterministic math. |
| Communication archive | **Email + Slack** | Historical record. Searchable. Time-stamped. |
| Title coordination | **Title company portal** (Independence, etc.) | Title-side state of truth. Cannot duplicate. |
| Lender coordination | **Lender portal / email** | Loan-side state of truth. |

**Implication:** This system does NOT replace any of these. It doesn't replicate MLS data, doesn't sign documents, doesn't host PDFs. The Case File POINTS to these systems (e.g. "Executed contract: shared Drive → `Anderson — 1247 Berkman / Contract Executed 5-13.pdf`").

---

## The 30% — Rule-based automation (gap; could be added separately)

Diana currently doesn't have this layer. It's a Week-5-ish addition, not part of this submission. But here's what would go here:

| Trigger | Action | Tool |
|---|---|---|
| Website contact form submitted | Slack message to whoever's up in rotation + email to leadflow@dianalinrealty.com + create case folder | Zapier or Make |
| Lead form contains phone | SMS auto-acknowledgement: "Got your message, Maria will be in touch within 2 hours" | Zapier + Twilio |
| Stage in case.md changes to `under_contract` | Pre-populate transaction_tracker.md skeleton + email title company intro | Custom script + Zapier |
| 48 hours before any tracker deadline | SMS to assigned agent | Zapier + Twilio |
| 7 days post-close | Drip nurture email #1 to client | Mailchimp/Klaviyo |
| 30 days post-close | Drip nurture email #2 | Same |
| 365 days post-close | "Happy anniversary in your new home" check-in to assigned agent | Same |

The shape of the rule is `IF condition X THEN action Y`. None of these require judgment. All can be expressed in Zapier/n8n's UI without writing code.

**Why this isn't in the submission:** The brief was "build the AI operating system." That's the 10% layer specifically. The 30% layer is a separate buildout (and Diana said she doesn't want another platform — so this would be a thin Zapier integration, not new software).

---

## The 10% — AI judgment layer (THIS SYSTEM)

Each of the five specialists exists because the work requires JUDGMENT (Test 3 of the Decision Test) — not deterministic lookup, not if/then rules.

| Specialist | The judgment required |
|---|---|
| **00_orchestrator** | Reading an inbound message and deciding which specialist's lane it falls in. Disambiguating multi-intent inbound. Recognizing past-client referrals vs. cold leads. |
| **01_lead_qualifier** | Reading free-text from a prospect and synthesizing intent, urgency, fit. Scoring (cold/warm/hot) based on factors that aren't reducible to a checklist. Recognizing when to ask for a discovery call vs. proceeding to research. |
| **02_property_research** | Synthesizing comps + neighborhood character + school ratings + walkability into a brief the agent can carry into a meeting. Knowing what to flag vs. what to leave out. |
| **03_client_communication** | Matching the assigned agent's voice — Maria's "Pat —" vs. Tom's "Pat," vs. Jordan's "Hi Pat,". Reading the situation (celebration text vs. inspection-findings email vs. financing-delay call). |
| **04_transaction_coordinator** | Pattern recognition for risk flags (inspector language that implies foundation, lender chatter that signals trouble, title commitment surprises). Knowing what's normal vs. what's signal. |

These are all Test 3 work: synthesis, judgment, voice matching, pattern recognition across unstructured text. They earn the AI layer.

**What's NOT in this system that you might think should be (but doesn't pass Test 3):**

| Function | Why it's not in the AI layer |
|---|---|
| Showing scheduling | Calendar + availability is deterministic. 60% layer. |
| Commission calculation | Math. 60% layer. |
| Sending a reminder 48 hours before a deadline | Rule. 30% layer. |
| Looking up a tax assessment | Lookup. 60% layer. (Though 02 might synthesize across many tax records.) |
| Sending the contract for signature | DocuSign workflow. 60% layer. |
| Recording a deed | Travis County Clerk. External to all three layers. |

---

## How to recognize a future task that wants this system

Run any candidate workflow through the Decision Test (per Constraint 06):

1. **Is the answer deterministic?** If yes → 60% layer. Stop. Don't add to this system.
2. **Can it be expressed as if/then?** If yes → 30% layer. Add to Zapier/n8n. Don't add to this system.
3. **Does it require judgment across unstructured info?** If yes → AI layer. Could fit this system.
4. **If none of the above are yes** → it's manual work that should stay manual.

When in doubt: simpler layer wins.

---

## Roadmap implication

If Diana wants to extend the operational coverage of her team's automation, the highest-leverage NEXT investment is **the 30% layer** (Zapier flows), not more AI specialists. The AI specialists in this submission are already addressing the work that requires judgment. Adding a sixth or seventh specialist won't reduce the 11pm Slacks if the underlying problem is "the email about earnest money didn't get forwarded at the right time."

The 30% layer is where the next reduction in operational friction lives.
