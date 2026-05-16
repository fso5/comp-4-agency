# Diana Lin Realty — Agency System (the 60-second pitch)

**For:** Boutique residential real estate teams of 3–6 agents doing 50–100 transactions/year. Currently running on duct tape (Google Docs + Slack + Diana's head). Tried generic AI tools, didn't stick.

**What it is:** Five markdown folders that drop into a Claude project. Specialists for lead qualification, property research, voice-matched client comms, TREC transaction tracking, and an orchestrator that routes incoming requests. They coordinate via a typed Handoff Packet appended to a shared Case File.

**The first 5 minutes:** Open `_cases/2026-05-08-anderson-buyer/case.md`. Read the four Handoff Packets at the bottom. That's the system running on a real Mueller buyer deal, end to end, from website form to under-contract at $712k.

---

## The 5-minute test (cold-stranger demo)

> ☑ Open the Claude project. Paste this:
>
> *"Hi, my wife and I are relocating from Denver for my new job at Indeed in August. Looking to buy in East or Central Austin, ideally close-in. Budget around $700k. Can we set up a call? — Jamie Anderson, (512) 555-0142"*
>
> ☑ The system routes to 01_lead_qualifier
> ☑ Produces a qualification.md (warm score, three target neighborhoods, pre-call action items)
> ☑ Appends a Handoff Packet to case.md routing to 02_property_research
> ☑ All in one Claude response

If it doesn't, the folder isn't loaded correctly. (Most common: Claude Project didn't ingest the `_shared/` files — re-upload.)

---

## Where this sits in your stack

You already have:
- **60%** — MLS, TCAD, DocuSign, Drive, Calendar (your traditional tools, can't be replaced)
- **30%** — automation gap that Zapier or similar fills (lead routing, deadline reminders)
- **10%** — the AI judgment layer (THIS — qualification, research, voice matching, risk flagging)

This system is the 10%. It doesn't try to be your CRM. It sits on top.

(Per Jake Van Clief's Constraint 06: Layer Triage — "The question is not 'can AI do this?' It almost always can. The question is 'should AI do this, or is there a layer beneath AI that handles it better, faster, and cheaper?'")

---

## Pricing tiers (illustrative)

| Tier | What you get | Investment |
|---|---|---|
| **Open source (this repo)** | The full folder system, MIT licensed. Drop into your Claude project. Customize over a weekend. | Free |
| **Done-with-You** | We adapt the folders to your team's actual agents, your service area's specific neighborhoods, your local TREC/title relationships. 1-week engagement. | $2,500 |
| **Custom build** | Multi-team rollout. Voice cards built from your team's actual transcripts. Integration into your existing CRM/calendar stack. Ongoing tuning. | Custom |

(Illustrative tier framing — the open-source tier is shipped here. Done-with-You and custom build are stubs to show the productization angle.)

---

## What other systems will do for Diana that this won't

- **Send emails for Diana.** Every draft goes through human review. Real estate has too many high-stakes moments to delegate.
- **Replace her CRM, MLS access, or DocuSign.** These stay. This is the layer on top.
- **Negotiate or price for her.** Specialists supply facts; humans decide.
- **Handle commercial, land, or multi-family >4 units.** Residential only.

---

## The proof

This repo. Specifically `_cases/2026-05-08-anderson-buyer/` — a fully populated buyer case showing every artifact every specialist produces, including 4 Handoff Packets visible in case.md. Real Mueller pricing. Real TREC mechanics. Real voice patterns for Maria (mid-market central agent).

Clone it. Drop it in a Claude project. Get value in five minutes.

If that doesn't happen, message the maintainer.

---

→ Full architecture: [README.md](README.md)
→ AI assistant entry point: [CLAUDE.md](CLAUDE.md)
→ Worked example: [`_cases/2026-05-08-anderson-buyer/`](_cases/2026-05-08-anderson-buyer/)
