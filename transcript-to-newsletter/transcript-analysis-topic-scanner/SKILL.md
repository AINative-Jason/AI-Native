---
name: transcript-topic-scanner
description: Analyze an event or conference keynote transcript and recommend the best newsletter topic. Scans the transcript for the strongest material, then outputs one recommended angle plus a couple of alternates as a topic brief. Say "scan this transcript for a newsletter topic", "analyze this keynote transcript", "what should I write about from this talk", "find the newsletter angle in this transcript", or "run the topic scanner".
user-invocable: true
---

# Transcript Analysis + Topic Scanner

First skill in the keynote-to-newsletter chain. Reads a keynote/conference transcript, mines it for the most newsletter-worthy material, and recommends one topic plus a couple of alternates — written up as a **topic brief** that the Outline Builder reads next.

> This is a self-contained skill. All reference material is inlined in the **Reference** sections at the bottom of this file.

## How to Run

- "Scan this transcript for a newsletter topic"
- "Analyze this keynote transcript"
- "What should I write about from this talk?"
- "Find the newsletter angle in this transcript"

## What the Agent Does

### 1. Get the Transcript

The input is a transcript file or pasted text. If none is provided, ask the user to drop the file or paste it. Don't proceed without a transcript — this skill analyzes a specific talk, it does not invent one.

### 2. Analyze the Transcript

Follow **Reference A: Analysis Template** below. Produce, internally:
- A general summary of the talk (what it was, who spoke, the through-line)
- The main talking points in order
- The key insights and conclusions — the ideas worth keeping

This analysis is working material. Keep it tight; it feeds the scan, it is not the final output.

### 3. Scan for Newsletter Angles

Apply **Reference B: Signal Patterns** below to find where the transcript holds a real newsletter — not just a recap. Look for contrarian takes, "aha" reframes, teachable frameworks, surprising data, and tension the speaker named. A topic without a POINT is not a topic.

### 4. Output the Topic Brief

Use **Reference C: Topic Brief Template** below. Present **one recommended topic + two alternates**. For each: the angle (the argument, not the subject), why it's strong, supporting evidence pulled straight from the transcript (quotes + rough location), and a draft hook.

### 5. Save and Hand Off

Show the brief in chat first. Once the user reacts, save it as a markdown file (e.g. `topic-brief-[slug].md`) so the Outline Builder can pick it up. Confirm the save path.

## Rules

- Every angle needs a POINT. "AI agents" is a subject. "Most teams are deploying AI agents before they've fixed the workflow underneath" is a topic.
- Evidence must come from the transcript. Quote it and cite roughly where it appears. Never fabricate quotes.
- Recommend a clear #1. Don't hedge across three equal options — the user asked for a pick.
- At least one option should carry a strong opinion or contrarian edge. Safe recaps get no opens.
- Match the writer's POV: practical AI translated for individuals and small teams, with a distinct independent take. Avoid generic "here's what happened at the conference" framing.
- If the transcript is thin or off-topic, say so plainly rather than inflating a weak angle.

---

## Reference A: Analysis Template

Working analysis you run on the transcript before scanning for angles. Internal scaffolding — keep it tight, it feeds Step 3, it is not the deliverable.

**1. General Summary (3–5 sentences)** — What was this talk (keynote, panel, fireside)? Who spoke, and what's their credibility/angle? What was the central through-line — the one thing the speaker was really arguing? What was the context (event, audience, moment in the industry)?

**2. Main Talking Points (in order)** — The talk's spine, the 4–8 beats it moved through. For each: the point (one line), what was said (a sentence of substance, not just a label), and the evidence given (data, story, demo, example). Capture them in the speaker's order so you can locate quotes later.

**3. Key Insights & Conclusions** — The ideas worth keeping, separate from the recap. For each: the insight stated as a claim (not a topic), why it matters (what changes if it's true), and the strength of support (did the speaker back it with data/example, or assert it?).

**4. Raw Quote Bank** — Pull 6–12 verbatim lines that are quotable, surprising, or load-bearing. Tag each with a rough location (timestamp if present, otherwise "early / mid / late" or section name). These become the evidence in the brief — having them ready prevents fabrication.
```
> "exact quote"  — [location]
```

Notes: Don't editorialize in this pass — capture what's there; the opinion comes in the scan. Preserve who said what if there are speaker labels. Keep timestamps if they exist; otherwise note approximate position.

---

## Reference B: Signal Patterns — Finding the Newsletter Inside a Transcript

A transcript holds dozens of facts but usually only a few real newsletter angles. Score candidate angles against these signals, strongest first. A good topic usually hits two or more.

1. **Contrarian / against-the-grain take** — The speaker cut against common wisdom, or implied a take they didn't fully say. Highest engagement.
2. **The reframe / "aha"** — A moment that makes the reader see a familiar thing differently. A new mental model, a renamed problem, an analogy that clicks.
3. **Teachable framework** — A repeatable method, checklist, or sequence the speaker laid out (or that you can extract). Translates a talk into something usable.
4. **Surprising data or claim** — A stat, benchmark, or assertion that raises eyebrows. Must be quoted accurately and attributed.
5. **Named tension** — A real tradeoff, conflict, or unresolved problem the speaker surfaced. "X vs Y and why it's not obvious."
6. **Pattern across the talk** — A theme the speaker returned to 3+ times, even without flagging it.

**Turning a signal into an angle.** A subject is not an angle. Force every candidate through this: Subject (what it's about) → Angle (the argument / POV, a sentence with a verb and a stance) → So what (why the reader should care this week). If you can't write the angle as a sentence with a verb and a stance, it's not ready.

**Fit check.** Favor angles that translate cutting-edge AI into practical use for individuals and small teams, carry a distinct independent POV (not "conference recap" energy), and give the reader something to *do* or *rethink*. Down-rank pure event coverage, vendor-flavored angles, or large-enterprise-only takes with no individual takeaway.

**Anti-patterns (don't recommend):** "Here's everything that happened at [event]" (recap, not a take); topics with no verb and no stance; angles whose only evidence is your own speculation; five equally-weighted options with no clear #1.

---

## Reference C: Topic Brief Template

The deliverable and the handoff contract to the Outline Builder. Output exactly this structure. Show it in chat first, then save as `topic-brief-[slug].md`.

```markdown
# Topic Brief — [Talk / Event Name]

**Source:** [transcript file name or event + speaker]
**Date analyzed:** [date]
**Talk in one line:** [the through-line of the keynote]

---

## Recommended Topic ★

**Working title:** [a real, specific title — not a label]
**Angle:** [The argument as a full sentence with a stance. The POINT, not the subject.]
**Why this one:** [Which signal(s) it hit and why it lands for the audience right now.]
**Supporting evidence (from the transcript):**
> "[exact quote]" — [speaker, location]
> "[exact quote]" — [speaker, location]
**Draft hook:** [One opening line showing the tone and entry point.]
**Reader takeaway:** [What the reader can do or rethink after reading.]

---

## Alternate 1
**Working title:** [title]
**Angle:** [sentence with a stance]
**Why it's strong:** [signal + fit, 1–2 lines]
**Key evidence:** > "[quote]" — [location]
**Draft hook:** [one line]

---

## Alternate 2
**Working title:** [title]
**Angle:** [sentence with a stance]
**Why it's strong:** [signal + fit, 1–2 lines]
**Key evidence:** > "[quote]" — [location]
**Draft hook:** [one line]

---

## Handoff Notes for Outline Builder
- **Recommended pick:** [restate the ★ working title]
- **Intended audience:** [individuals / small teams building with AI, unless specified otherwise]
- **Desired feel:** [e.g. sharp, practical, opinionated]
- **Quote bank available:** [yes — N quotes captured; or where the full transcript lives]
```

Rules for filling it: the ★ pick is a real recommendation stated with confidence; every quote is verbatim and attributed; angles are sentences with verbs and stances; alternates are genuinely different from the pick and each other; keep the Handoff Notes accurate so the chain runs clean.
