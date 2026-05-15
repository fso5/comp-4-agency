# Submission writeup — 100 words

**What I built:** A multi-folder AI operating system for Diana Lin Realty, a 4-person Austin team. Five specialists (orchestrator, lead qualifier, property researcher, client communicator, transaction coordinator) coordinate via structured Handoff Packets appended to a shared Case File. Every deal is one folder with a markdown spine and per-specialist artifacts.

**One design decision:** The Case File is a folder of artifacts, not a single document. Each specialist owns one file; handoffs are markdown blocks inside `case.md`. This makes the system's history readable top-to-bottom and gives specialists a clean lane.

**One thing I'd add with another week:** A seller-side worked example case to complement the buyer-side Anderson walkthrough.

---

*Word count: ~100*

---

## Notes for posting

When dropping the repo link in the comp comments, the post text could be the three sections above. Tweak as feels right.

GitHub topics worth tagging: `claude-projects`, `ai-agents`, `real-estate`, `icm`, `multi-folder-architecture`.
