---
name: outline-builder
description: Turn a newsletter topic brief into a structured outline with a real draft hook, section-by-section structure, and 5 subject line options. Second skill in the keynote-to-newsletter chain. Say "build the outline", "outline this newsletter", "structure the newsletter from the topic brief", "outline builder", or "give me subject lines and an outline".
user-invocable: true
---

# Outline Builder

Second skill in the keynote-to-newsletter chain. Takes the topic brief from the Topic Scanner and turns it into a newsletter outline you approve before drafting — a real hook, a clear thesis/promise/stakes, a section-by-section structure carrying the specific evidence from the transcript, and 5 subject line options.

> Self-contained skill. All reference material is inlined in the **Reference** sections at the bottom.

## How to Run

- "Build the outline" (after running the Topic Scanner)
- "Outline this newsletter from the topic brief"
- "Structure the newsletter and give me subject lines"

## What the Agent Does

### 1. Load the Input

Read the topic brief (`topic-brief-[slug].md`) from the Topic Scanner. Use the ★ recommended pick unless the user named an alternate. If no brief exists, ask for the topic + angle (and the transcript/quotes if available) — don't outline without an angle.

### 2. Recommend a Format

This newsletter's structure varies by piece, so pick the format that fits the angle. See **Reference B: Format Options** and recommend one: "I'd go with [format] because [one line]. Good, or want a different shape?" Let the user override.

### 3. Build the Outline

Following **Reference C: Outline Template**, produce: a **real draft hook** (an actual opening line, never "[insert hook]"); **thesis, promise, stakes** meeting **Reference A: Essentials**; **sections** each with a title, the specific points it makes, and the transcript evidence/quotes it uses; a **CTA** and an **estimated word count**.

### 4. Run the Essentials Check

Self-check the outline against **Reference A: Essentials**: does the hook grab in 3 sentences, is the thesis arguable, does the promise pull, do the stakes land early? Fix anything weak before showing it. Flag any element you couldn't make strong.

### 5. Generate 5 Subject Lines

Using **Reference D: Subject Line Patterns**, write 5 subject lines — each a different pattern, each under 60 characters, each specific to this piece. Name a top pick with a real reason, and offer preview text for the winner.

### 6. Show, Approve, Save

Show the full outline + subject lines in chat. Ask: "Does this structure work? Anything to change before drafting?" On approval, save as `outline-[slug].md` for the Content Writer and confirm the path.

## Rules

- Never use a placeholder hook. Write a real opening line, grounded in the transcript.
- All 5 subject lines use different patterns and stay under 60 characters. No two from the same framework, no generic lines that fit any topic.
- Sections must carry specific evidence from the brief/transcript — quotes and points, not vague headers.
- Don't skip approval. Fixing the outline now is cheaper than rewriting the draft.
- Match the writer's voice: practical AI for individuals and small teams, opinionated and independent, optimistic realism — never "conference recap" energy or AI-tell phrasing ("in today's fast-paced world," "let's dive in").
- If the angle is too thin for the chosen format, say so and suggest a tighter shape.

---

## Reference A: Newsletter Essentials — Hook, Thesis, Promise, Stakes

Every outline must have these four bones before drafting. Fix any weak one at the outline stage — it's almost impossible to bolt on later.

**Hook (first 3 sentences).** Grabs the reader before they bounce. Pick a pattern: *The Already-Happened* (past-tense revelation), *The Paradigm Flip* (challenges an assumed truth), *The Visceral Moment* (sensory detail + emotion), *The Contradiction* (two true things that shouldn't both be true), *The Vulnerability Drop* (honest admission of struggle). A hook is a real sentence, never a placeholder.

**Thesis (within first 150 words).** Arguable (someone could disagree), specific, reframes the topic. One sentence, two max.

**Promise (why keep reading).** Include 3+ of: transformation (who the reader becomes), urgency (why now), credibility (why the writer has standing), specificity (a concrete number/framework/outcome), emotional pull (desire, fear, curiosity).

**Stakes (by the 4th paragraph).** Why should the reader care today? Connect the personal to the universal fast.

**Self-check before showing:** Does the hook land in 3 sentences or is there throat-clearing? Is the thesis arguable? Does the promise hit 3+ elements? Are stakes clear by paragraph 4? Is the real insight up front, not buried (buried lede)?

**Red flags:** buried lede, throat-clearing before tension, an abstract headline no one could argue with, missing stakes, writer as distant observer. **AI tells to avoid:** "In today's fast-paced world…", "In this essay, I will…", "Let's dive in", vague dating, "not just X, but Y".

---

## Reference B: Newsletter Format Options

Structure varies by piece. Pick the format that fits the angle — don't force every newsletter into the same mold.

- **Essay (one strong argument)** — when the brief has a single sharp opinion or reframe. Hook → thesis → argument built in 2–4 moves each backed by evidence → counterpoint → what it means → CTA. Best for contrarian takes and reframes.
- **Listicle (several insights, one theme)** — when the talk surfaced multiple quick-hit insights. Hook → theme framing → 3–7 numbered insights each with a quote/example → synthesis → CTA. Best for "N things from [event] that matter."
- **Hybrid (idea + evidence)** — one core idea plus supporting moments. Hook → idea → 2–3 supporting beats from the transcript → implication → CTA.
- **Teaching / Framework** — when a repeatable method surfaced. Hook → the problem it solves → the framework in steps → worked example from the talk → how the reader applies it → CTA. Best for "AI translator" pieces.
- **Q&A / Mailbag** — when the angle answers a question the audience is asking. Hook → the question → answer in 2–3 parts with evidence → CTA.

| Brief signal | Format |
|---|---|
| One contrarian take / reframe | Essay |
| Multiple quick insights, one theme | Listicle |
| One idea + several proof points | Hybrid |
| A repeatable method | Teaching / Framework |
| Answers an audience question | Q&A |

If the angle is thin for the chosen format, recommend a tighter shape rather than padding.

---

## Reference C: Outline Template

The deliverable and handoff to the Content Writer. Output this structure. Show in chat first, then save as `outline-[slug].md`.

```markdown
# Outline — [Working Title]

**Source brief:** [topic-brief file name]
**Format:** [Essay / Listicle / Hybrid / Teaching / Q&A] — [one-line why]
**Estimated length:** [word count target]

## Bones
- **Hook (draft):** [a real opening line, grounded in the transcript]
- **Thesis:** [one arguable, specific sentence that reframes the topic]
- **Promise:** [what the reader gets/becomes — hits 3+ essentials]
- **Stakes:** [why the reader should care today]

## Structure
### Opening
- [How the hook opens into the thesis — 2–3 bullets]
### [Section 1 title]
- Point: [the specific argument]
- Evidence: > "[transcript quote]" — [location]
- Transition: [how it leads to the next section]
### [Section 2 title] … (repeat)
### Close
- Landing: [the line of thinking that resolves the thesis]
- **CTA:** [what the reader should do / think / try]

## Subject Lines (pick one)
1. "[line]" — Pattern: [name] — [why it works]
… (5 total)
**My pick: #[X]** — [one-line reason]
**Preview text for the pick:** [inbox line next to the subject]

## Handoff Notes for Content Writer
- **Format to write:** [restate]
- **Voice:** practical AI for individuals/small teams, opinionated, optimistic realism
- **Must keep:** [any quote or beat that has to survive into the draft]
- **Target length:** [word count]
```

Rules: the hook is a real sentence; every section carries a specific point AND evidence (no empty headers); 5 subject lines from 5 patterns all under 60 chars; keep it scannable (~30-second read); keep the Handoff Notes accurate.

---

## Reference D: Subject Line Patterns

Generate 5 subject lines, each a different pattern, each under 60 characters, each specific to this piece. Then name a top pick and offer preview text.

**Pattern library (pick the 5 most relevant — no two from the same):**
1. **The Number** — "5 things the keynote got right about agents"
2. **The Question** — "Are you automating the wrong work?"
3. **The Curiosity Gap** — "The demo everyone missed"
4. **The Direct Promise** — "Ship AI features without the rework"
5. **The Personal Story** — "I changed my mind about agents this week"
6. **The Contrarian** — "Stop deploying agents"
7. **The News Hook** — "[Event]: what it means for small teams"

**Hard constraints:** under 60 characters (count them); no spam triggers (no ALL CAPS, "free," excessive punctuation, "$$$"); specific to THIS piece (a line that could front any AI newsletter is a fail); 5 different patterns.

**Output:**
```
1. "[line]" — Pattern: [name] — [trigger it pulls]
…
My pick: #[X] — [why strongest for THIS piece]
Preview text for the pick: [a second hook, not a repeat — under ~90 chars]
```

The preview is a second subject line that extends the hook rather than repeating the subject.
