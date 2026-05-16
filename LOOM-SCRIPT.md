# Loom recording script — 3-minute walkthrough

Use this as a teleprompter / structure for a Loom or QuickTime screen recording. Reading verbatim is fine. Aim for 2:45 – 3:15 total.

Why this exists: the cold-agent shakedown surfaced that "no video" is the biggest remaining gap vs. the Ruben/Voiceprint bar. A 3-minute Loom converts the 19KB of markdown into something a Sunday-morning judge will actually consume.

Record once. Embed the link at the top of README.md, PITCH.md, and SUBMISSION.md.

---

## Setup before pressing record

1. Open the GitHub repo in one tab: https://github.com/fso5/comp-4-agency
2. Open the Anderson case.md file in another: https://github.com/fso5/comp-4-agency/blob/main/_cases/2026-05-08-anderson-buyer/case.md
3. Have a Claude project open with the folder uploaded (for the 5-minute test demo, optional but powerful)
4. Loom or QuickTime ready. Mic on. Webcam optional (your call).

## The script (read at conversational pace)

**[0:00 — 0:30] Hook + what this is**

> "This is Diana Lin Realty — a multi-folder AI operating system for a 4-person Austin real estate team. Five specialists coordinate via a typed Handoff Packet appended to a shared Case File. Markdown only — no software, no platform. The folders ARE the system.
>
> The brief said: 'a system I can teach my whole team to use in one week.' This is that system. Let me show you it running on a real deal."

**[0:30 — 1:15] The Anderson case as receipts**

(Open `_cases/2026-05-08-anderson-buyer/case.md`)

> "This is the Anderson case — a buyer couple relocating from Denver. Real Mueller pricing. Real TREC contract mechanics. Real Maria-voice email drafts.
>
> Scroll to the bottom. You'll see four Handoff Packets. Each one is a typed object — six required fields, four body sections. From, To, Case ID, Stage transition, Human owner, Priority. Then Why this handoff, What I'm passing forward, What I need back, Escalate to human if.
>
> No prose. No 'pass work to the next folder.' Mechanical, reviewable, teachable."

**[1:15 — 2:00] The folder structure**

(Switch to the repo home view)

> "Five specialists. Numbered 00 through 04. Orchestrator routes; lead qualifier scores; property researcher produces a sourced brief; client communication drafts in the agent's voice; transaction coordinator tracks every TREC deadline once we're under contract.
>
> Underneath: the underscore-shared folder is the reference shelf — voice cards, Austin market knowledge, Texas transaction mechanics, the 60/30/10 layer mapping. The underscore-cases folder is the working artifacts — one folder per deal."

**[2:00 — 2:30] The 60/30/10 framing (Vault fluency)**

(Open _shared/stack-mapping.md briefly)

> "This system is the 10% AI layer per Jake's Constraint 06 from the Vault. Diana already has the 60% — MLS, TCAD, DocuSign, Drive. The 30% — Zapier-style automation — is a separate buildout. This submission is explicitly the judgment layer that sits on top. We don't replace her stack. We add to it."

**[2:30 — 3:00] The voice switcher demo + close**

(Open _shared/voice-switcher.md)

> "Final demonstration: the same inspection-findings email, written in four different agent voices — Diana, Maria, Tom, Jordan. Same facts. Same situation. Four distinct voices.
>
> This is what Jake praised in Ruben's Maya-and-Dale identity examples: the methodology preserves voice difference rather than flattening it.
>
> Repo link in the description. Read the README, the pitch doc, or just clone it and drop it in a Claude project. You'll see it work cold in five minutes."

**[3:00] End.**

---

## Recording tips

- Speak slightly faster than feels natural — natural pacing reads as slow on Loom
- Don't say "umm" — re-record if you do
- The video is a SCAN AID, not a substitute for the repo. Don't try to cover everything. The four files in the README's scan-path are the points to hit.
- Keep the cursor visible and moving — judges will follow it
- If the recording goes over 3:30, cut the 60/30/10 section (2:00-2:30); it's the most expendable part

## After recording

1. Upload to Loom (or YouTube unlisted)
2. Grab the share URL
3. Add to top of README.md as a callout:

```markdown
> 📺 **3-minute walkthrough:** [Loom video](YOUR_URL_HERE)
```

4. Add same link to top of PITCH.md
5. Add link to SUBMISSION.md (replace any "no video" note)
6. Commit + push

## Why this is the highest-leverage final move

Per the cold-agent shakedown verdict: "This submission is technically the best-engineered entry I'd expect to see this week on the architecture+handoff axes. It will probably medal. To win, it needs one external receipt that meets the Ruben bar — a Loom is the cheapest path."
