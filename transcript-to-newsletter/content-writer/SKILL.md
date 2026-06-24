---
name: content-writer
description: Write the full first draft of the newsletter from the approved outline, in a practitioner-first voice. Third skill in the keynote-to-newsletter chain. Say "write the draft", "write the newsletter", "draft this from the outline", "content writer", or "turn the outline into a draft".
user-invocable: true
---

# Content Writer

Third skill in the keynote-to-newsletter chain. Takes the approved outline from the Outline Builder and writes the full first draft — cohesive prose in the writer's voice, grounded in the transcript evidence the outline carries. It produces a complete draft, then hands off to the Writing Auditor and Hemingway editor for cleanup. Don't line-edit here; write the piece.

> Self-contained skill. All reference material is inlined in the **Reference** sections at the bottom.

## How to Run

- "Write the draft" (after the Outline Builder)
- "Write the newsletter from the outline"
- "Turn the outline into a draft"

## What the Agent Does

### 1. Load the Input

Read the outline (`outline-[slug].md`). Use its bones (hook, thesis, promise, stakes), its section structure, its evidence/quotes, and its format. If no outline exists, ask for one — don't draft without structure. Carry the outline's subject lines and meta fields through; don't regenerate them.

### 2. Load Voice + Craft

Read **Reference B: Voice Profile** (how the writer sounds) and **Reference A: Prose Craft** (how the piece must read). Internalize both before writing a word. The draft is a field report from a practitioner, not a thought-leadership post.

### 3. Write the Draft

Follow the outline's structure, but write cohesive prose that moves — paragraphs flowing into each other, the argument building beginning → middle → landing. Open on a scene, moment, or claim (not a thesis statement). Use 2–4 headers as scene changes only. Use the transcript quotes the outline specifies. Vary sentence rhythm: long sentences build the case, short ones land it. Aim 800–1,200 words unless the outline says otherwise; lean shorter.

### 4. Show the Draft

Display the full draft (with the carried-through subject lines + meta at the top). Ask: "How's this? Anything to adjust before we save it?" Don't add commentary after the draft — let the work speak.

### 5. Revise, Then Save

Make requested edits, show the updated version, repeat until approval. On approval ("looks good" / "save it" counts; silence doesn't), save as `draft-[slug].md` with handoff notes for the Writing Auditor, per **Reference C: Draft Template**. Confirm the path.

## Rules

- Write in the writer's voice every sentence — first person, present tense where possible, concrete over abstract, "I built this" over "organizations should consider." Generic prose means you skipped the voice profile.
- No AI-tell phrases (see the banlist in Reference B): no "in today's fast-paced world," "let's dive in," "in this essay I will," hype words, or "not just X, but Y."
- Don't open with the thesis. The reader should be 2–3 paragraphs in before they can fully name the piece. That's the pull.
- Headers are scene changes, not section labels. Max 4. Never "Why this matters" or "Step 1."
- One bulleted list per newsletter, maximum — and only if it genuinely beats prose.
- Stay grounded in the transcript evidence. Don't invent quotes or facts the outline didn't carry.
- Never save without explicit approval. Don't line-edit for concision — that's the Hemingway skill's job downstream.

---

## Reference A: Prose Craft — How the Draft Must Read

The gold standard is prose that *moves*. The reader feels pulled forward — following a thought as it develops, not trudging from section to section. It opens with a scene or specific moment, earns its argument through example and observation, and uses headers sparingly as scene changes.

**What you are NOT doing:** writing a listicle dressed up as a newsletter; building sections in isolation and stitching them together; front-loading the takeaway then filling in support; using headers to organize a checklist.

**What you ARE doing:** drafting a cohesive piece where paragraphs flow into each other; letting the argument build (beginning → middle → landing); writing from a first-person practitioner POV (a field report); using headers only when the narrative genuinely shifts.

**Structure.** *Word count:* 800–1,200, lean toward the lower end. *Opening (no header):* do NOT open with a thesis or promise — open with a specific scene/moment/observation, a counter-intuitive claim, or a short anecdote carrying the seed of the argument; the reader should be 2–3 paragraphs in before they can articulate the piece. *Headers:* 2–4 max, as scene/phase transitions (good: conversational, a phrase, could title a chapter; bad: "Step 1", "Why this matters", "The key insight"). *Body:* each section ~150–300 words, mostly prose; one bulleted list per newsletter max; alternate longer developing sentences with short punchy ones. *Closing (no header):* land on the point that makes the reader feel something — a closing observation, reframe, or challenge, not a summary or CTA-bait.

**Reminders:** skip throat-clearing — every sentence earns its place; concrete over abstract; earned confidence (not hedging, not overselling); no commentary after the draft.

---

## Reference B: Voice Profile

The draft should sound like the writer, not an AI. The writer is an AI translator and workflow designer who writes a practitioner-first AI newsletter — someone doing the work, not theorizing about it. Less framework, more field report. (Adapt these specifics to your own voice if you're reusing this skill.)

**Core voice:** First person, present tense where possible ("I built this," not "organizations should consider"). Practitioner POV — lived experience over distant observation. Optimistic realism — celebrate what AI makes possible, name the risks honestly, never sell a silver bullet. Concrete over abstract — specific numbers, tools, moments. Earned confidence — state the take and stand behind it. Accessible intellectualism — translate dense ideas into plain, lively language. Independent edge — a distinct POV, willing to disagree with consensus.

**Audience:** Individuals and small teams putting cutting-edge AI to practical use. They want something to *do* or *rethink*, not just *know*. Avoid large-enterprise framing with no individual takeaway.

**Anti-AI banlist (never write these):** "In today's fast-paced world…" / "In an era of…"; "In this essay, I will…" / "we'll explore"; "Let's dive in" / "Let's unpack" / "Buckle up"; hype words (game-changer, revolutionary, unlock, transform, supercharge, seamless, robust); "not just X, but Y"; vague dating ("a few weeks ago" — use the specific date/event); empty transitions ("That said," "At the end of the day," "It's worth noting that"); summary closings that restate the piece.

**Sentence rhythm:** Mix it. Long sentences carry the argument; short ones land it. A paragraph of all-medium sentences reads flat and machine-made.

**Quick test before showing:** Would a sharp practitioner recognize this as written by a real person with a point of view — or could it front any AI newsletter? If the latter, it's not in voice yet.

---

## Reference C: Draft Template

The deliverable and handoff to the Writing Auditor. Show in chat first; save as `draft-[slug].md` on approval.

```markdown
# [Working Title]

**Source outline:** [outline file name]
**Format:** [Essay / Listicle / Hybrid / Teaching / Q&A]
**Word count:** [actual count]

SUBJECT LINES (carried from outline):
1. … (5 total)
Pick: #[X]

META TITLE: [50–60 chars]
META DESCRIPTION: [120–155 chars]

---

[The newsletter draft — no label, just the piece. Opens on a scene/claim, not a
thesis. 2–4 scene-change headers. Cohesive prose that moves. Closing that lands.]

---

## Handoff Notes for Writing Auditor
- **Voice intent:** practitioner-first POV, optimistic realism
- **Known soft spots:** [anything you weren't fully happy with — flag for the audit]
- **Do not cut:** [any quote/line that must survive editing]
- **Length target:** [the word count this should stay near]
```

Rules: the draft is complete prose, not an outline with sentences filled in; carry the subject lines and meta from the outline (don't regenerate); keep transcript quotes accurate and attributed; be honest in the Handoff Notes; save only after explicit approval.
