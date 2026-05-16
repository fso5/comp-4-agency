# Submission writeup — 100 words

**What I built:** A markdown-only AI operating system for Diana Lin Realty, a 4-person Austin team. Five specialists (orchestrator, lead qualifier, property researcher, client communicator, transaction coordinator) coordinate via a typed Handoff Packet appended to a shared Case File. Every deal is one folder with a `case.md` spine + per-specialist artifacts.

**One design decision:** The Handoff Packet is a typed object — six required fields, four body sections — not prose. Every `handoff.md` references the spec. This is what "actually defined" vs. "hand-waved" looks like at scale.

**One thing I'd add with another week:** A seller-side worked example case (Castillo-Reyes is referenced but not built) plus the 30% Zapier-automation layer that sits beneath the AI judgment layer.

---

*Word count: 102*

---

## Notes for posting

Comment body for the Skool submission:

```
Repo: https://github.com/fso5/comp-4-agency
Pitch (60-second read): https://github.com/fso5/comp-4-agency/blob/main/PITCH.md

[100-word writeup above]
```

GitHub topics worth tagging: `claude-projects`, `ai-agents`, `real-estate`, `icm`, `multi-folder-architecture`, `handoff-protocol`.

---

## Key files for judges (Jake, Matthew, mods)

In priority order for a cold read:

1. [`README.md`](README.md) — full architecture + 60/30/10 stack mapping + design decisions
2. [`PITCH.md`](PITCH.md) — 60-second sales-page-style positioning
3. [`_cases/2026-05-08-anderson-buyer/case.md`](_cases/2026-05-08-anderson-buyer/case.md) — the receipts (system run end-to-end)
4. [`_shared/case_file_spec.md`](_shared/case_file_spec.md) + [`_shared/handoff_packet_spec.md`](_shared/handoff_packet_spec.md) — the two contracts
5. [`_shared/voice-switcher.md`](_shared/voice-switcher.md) — same email in four voices (Diana / Maria / Tom / Jordan), proves the methodology preserves voice difference
6. [`_shared/stack-mapping.md`](_shared/stack-mapping.md) — explicit 60/30/10 mapping (Constraint 06 fluency)
