# Recording Guide — Option A (Screen recording + ElevenLabs voiceover)

Single source of truth for producing the 3-minute walkthrough video.

**Total time:** ~55 minutes from start to upload.
**Total cost:** $0 (free tiers cover it).

---

## Pre-flight (5 min)

Have these tabs / windows ready BEFORE you start recording:

1. **GitHub repo home:** https://github.com/fso5/comp-4-agency
2. **Anderson case file:** https://github.com/fso5/comp-4-agency/blob/main/_cases/2026-05-08-anderson-buyer/case.md
3. **Handoff packet spec:** https://github.com/fso5/comp-4-agency/blob/main/_shared/handoff_packet_spec.md
4. **Stack mapping (60/30/10):** https://github.com/fso5/comp-4-agency/blob/main/_shared/stack-mapping.md
5. **Voice switcher demo:** https://github.com/fso5/comp-4-agency/blob/main/_shared/voice-switcher.md

Close anything sensitive (Slack DMs, password manager, financial tabs). Hide the macOS menu bar if you want (System Settings → Control Center → Automatically hide and show the menu bar). Use a clean browser profile if your normal one has tabs/extensions visible.

---

## Step 1 — Generate the voiceover (15 min)

### 1a — Sign up for ElevenLabs free tier

Go to **https://elevenlabs.io/sign-up** and create an account. Free tier gives you 10,000 characters/month. Our script is ~2,400 characters. Fits comfortably.

### 1b — Pick a voice

Open **Voices** → **Voice Library**. Recommended for this script:
- **"Brian"** — male, professional, US accent (clean for technical content)
- **"Sarah"** — female, warm, US accent (warmer, slightly more sales-pagey)
- **"Will"** — male, conversational, US accent (sounds most natural, my top pick)

Test 2-3 with a short paste before committing. Pick the one that sounds least synthetic to you.

### 1c — Paste the narration script

Below is the **clean narration text** — stage directions removed, AI-voice-optimized (numbers spelled where ambiguous, em-dashes replaced with commas/periods). **Paste this into the ElevenLabs Text-to-Speech box exactly as written.**

```
This is Diana Lin Realty. A multi-folder AI operating system for a four-person Austin real estate team. Five specialists coordinate via a typed handoff packet appended to a shared case file. Markdown only. No software, no platform. The folders are the system.

The brief said: a system I can teach my whole team to use in one week. This is that system. Let me show you it running on a real deal.

This is the Anderson case. A buyer couple relocating from Denver. Real Mueller pricing, real TREC contract mechanics, real Maria-voice email drafts.

Scroll to the bottom. You'll see four handoff packets. Each one is a typed object. Six required fields. Four body sections. From, To, Case ID, Stage transition, Human owner, Priority. Then Why this handoff, What I'm passing forward, What I need back, Escalate to human if.

No prose. No pass work to the next folder. Mechanical, reviewable, teachable.

Five specialists. Numbered zero through four. Orchestrator routes. Lead qualifier scores. Property researcher produces a sourced brief. Client communication drafts in the agent's voice. Transaction coordinator tracks every TREC deadline once we're under contract.

The shared folder is the reference shelf. Voice cards, Austin market knowledge, Texas transaction mechanics, the sixty thirty ten layer mapping. The cases folder is the working artifacts. One folder per deal.

This system is the ten percent AI judgment layer, per Jake's Constraint Six from the Vault. Diana already has the sixty percent. MLS, TCAD, DocuSign, Drive. The thirty percent, Zapier-style automation, is a separate buildout. This submission is explicitly the judgment layer that sits on top. We don't replace her stack. We add to it.

Final demonstration. The same inspection findings email, written in four different agent voices. Diana, Maria, Tom, Jordan. Same facts. Same situation. Four distinct voices.

This is what Jake praised in Ruben's Maya and Dale identity examples. The methodology preserves voice difference rather than flattening it.

Repo link in the description. Read the README, the pitch doc, or just clone it and drop it in a Claude project. You'll see it work cold in five minutes.
```

### 1d — Generate

Click **Generate**. Listen back. If a word sounds wrong (TCAD, TREC, Mueller, ICM), regenerate or spell it phonetically in the source (e.g., "T-cad" instead of "TCAD"). Common ones to check:
- "TREC" should sound like "treck"
- "TCAD" — either "T-cad" or "tee-cad" works
- "ICM" — should be three letters, "I-C-M"
- "Mueller" — "MYOO-ler" (German pronunciation)

### 1e — Download the MP3

**Download** → save as `voiceover.mp3` in `~/Downloads/`.

Expected length: 2:50 to 3:10.

---

## Step 2 — Record the screen (15 min)

You'll record the screen WITHOUT audio, matching the timing of your voiceover.

### 2a — Open the voiceover in a media player

Open `voiceover.mp3` in QuickTime Player or any media player you can scrub through. This is your timing reference. You'll play it while you record so you know what to show when.

### 2b — Start QuickTime screen recording

**QuickTime Player** → **File** → **New Screen Recording**

Settings:
- **Options** → **Microphone:** None
- **Options** → **Show Mouse Clicks in Recording:** ON (so judges see your clicks)
- **Record entire screen** or **Record selected portion** (your call — full screen looks more pro)

Click **Record** to start.

### 2c — Screen choreography (matched to voiceover timing)

Press play on the voiceover at the same time you start recording. Follow these beats:

| Time | Voiceover says... | What to show on screen |
|---|---|---|
| 0:00–0:15 | "Diana Lin Realty... markdown only..." | GitHub repo home page — slow scroll showing the file tree |
| 0:15–0:30 | "The brief said... let me show you it running on a real deal." | Click into `_cases/2026-05-08-anderson-buyer/` |
| 0:30–0:50 | "This is the Anderson case..." | Open `case.md`. Slow scroll through the frontmatter + Snapshot + Stage history |
| 0:50–1:20 | "Scroll to the bottom. You'll see four handoff packets..." | Scroll fast to the bottom of case.md, slow scroll through the 4 Handoff Packets |
| 1:20–1:30 | "No prose. Mechanical, reviewable, teachable." | Hover/highlight the structured fields (From, To, Case ID, etc.) |
| 1:30–1:55 | "Five specialists. Numbered zero through four..." | Back to repo home. Hover each numbered folder briefly. Click into `01_lead_qualifier/` to show the 4 files |
| 1:55–2:10 | "The shared folder is the reference shelf..." | Click into `_shared/`. Show the list of files in the reference shelf |
| 2:10–2:35 | "This system is the ten percent AI judgment layer..." | Open `_shared/stack-mapping.md`. Slow scroll showing the 60/30/10 table |
| 2:35–3:00 | "Final demonstration. The same inspection findings email..." | Open `_shared/voice-switcher.md`. Scroll through the 4 voice drafts (Diana, Maria, Tom, Jordan) |
| 3:00–end | "Repo link in the description. You'll see it work cold in five minutes." | Hold on the voice-switcher view, or scroll back to repo home for the final beat |

Stop recording when the voiceover ends. Press **Cmd+Shift+5** → **Stop** (or click the menu bar icon).

Save the recording as `screen.mov` in `~/Downloads/`.

### 2d — If you mess up

Just start over. Each take is ~3 minutes. Aim for 2-3 takes max. The screen recording doesn't need to be perfect — the voice is doing the talking. As long as you're roughly in the right place during the right narration, it'll work.

---

## Step 3 — Combine voice + screen in iMovie (10 min)

### 3a — Open iMovie

**iMovie** (free, built-in Mac) → **Create New** → **Movie**. Skip the theme picker.

### 3b — Drag in both files

Drag `screen.mov` and `voiceover.mp3` from Finder into the iMovie media bin.

### 3c — Build the timeline

1. Drag `screen.mov` to the timeline first (the video track)
2. Drag `voiceover.mp3` to the audio track below it
3. Align the start of the voiceover with the start of the screen recording (snap to 0:00)
4. If the screen recording is longer than the voiceover, trim the end of the screen recording to match the voiceover length

### 3d — Mute the screen recording's audio

The screen recording has no audio because you set Microphone to None — but double-check there's no silence track. If there is, right-click the video clip → **Detach Audio** → delete the audio track.

### 3e — Export

**File** → **Share** → **File** → **Resolution: 720p** (smaller file, fine for Loom/YouTube) → **Quality: Medium** → **Compress: Faster** → **Save**

Save as `walkthrough.mp4`. Expected file size: 30-80 MB for a 3-minute 720p clip.

---

## Step 4 — Upload + get a share link (5 min)

### Option 1 — Loom (recommended)
1. Go to **https://www.loom.com/** → sign in (free tier supports 25 videos, 5 min each — we're under both limits)
2. Click **Upload** → drag `walkthrough.mp4`
3. After upload, click **Share** → **Copy link**
4. Make sure the link is set to **Anyone with the link can view** (default for free tier)

### Option 2 — YouTube unlisted
1. Go to **https://studio.youtube.com/** → **Create** → **Upload videos**
2. Set Visibility to **Unlisted**
3. After processing, copy the share link

Either works. Loom is faster to upload and gives a cleaner viewer experience. YouTube is more permanent.

---

## Step 5 — Embed the link + final commit (5 min)

You'll paste your video URL into 3 files. The callout format to paste at the top of README.md and PITCH.md:

```markdown
> 📺 **3-minute walkthrough:** [Watch the video](YOUR_VIDEO_URL)
```

Then in SUBMISSION.md, find the line that says:

```
- **3-minute video walkthrough:** *(record using LOOM-SCRIPT.md, then paste link here before submitting)*
```

And replace it with:

```
- **3-minute video walkthrough:** YOUR_VIDEO_URL
```

Then commit and push:

```bash
cd ~/projects/comp-4-agency
git add -A
git commit -m "Add 3-minute walkthrough video link"
git push origin main
```

Done. The submission is now ready to post on Skool.

---

## Total budget

| Step | Time | Cost |
|---|---|---|
| Pre-flight | 5 min | $0 |
| ElevenLabs voiceover | 15 min | $0 (free tier) |
| Screen recording | 15 min | $0 (QuickTime built-in) |
| iMovie assembly | 10 min | $0 (built-in) |
| Loom upload | 5 min | $0 (free tier) |
| Commit + push | 5 min | $0 |
| **Total** | **~55 min** | **$0** |

---

## Troubleshooting

**ElevenLabs voice sounds robotic.** Try a different voice. "Will" or "Brian" tend to sound most natural. You can also adjust **Stability** down to 30-40% and **Similarity** up to 75% in the settings panel for more expressiveness.

**QuickTime can't record system audio.** That's fine — we're not recording audio in the screen recording. The voiceover gets added in iMovie.

**iMovie audio levels are uneven.** Select the audio clip in iMovie → use the audio waveform handles to bring up/down loudness.

**File size too big to upload.** In iMovie export, drop quality from Medium to Low. Or change resolution to 540p.

**Video looks compressed/pixelated.** That's normal at 720p for a fast upload. Loom and YouTube both re-encode anyway. The CONTENT is the point, not the resolution.

**You hate hearing AI voices.** That's the trade. Recording your own voice over the screen is the alternative — adds ~30 min for retakes but gives you control. For this audience (technical, AI-literate community), AI voice is widely accepted in 2026.

**The voice rushes through a section / hits a beat wrong.** Edit the script in ElevenLabs, add a period or comma to slow the cadence, regenerate. Or split the script into 2-3 paragraphs and generate each separately, then concatenate in iMovie.

---

## Why this is the right move per the cold-agent verdict

> "This submission is technically the best-engineered entry I'd expect to see this week on the architecture+handoff axes. It will probably medal. To win, it needs one external receipt that meets the Ruben bar — a Loom is the cheapest path."

55 minutes between you and that external receipt. Go ship it.
