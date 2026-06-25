---
name: newsletter-chain
description: Run the full keynote-to-newsletter chain end to end — from a keynote transcript to a finished newsletter plus hero-image prompts. Conducts all six skills in sequence with review gates. Say "turn this transcript into a newsletter", "run the newsletter chain", "run the whole keynote-to-newsletter chain", "transcript to newsletter", or "build a newsletter from this keynote".
user-invocable: true
---

# Newsletter Chain (Orchestrator)

The front door to the keynote-to-newsletter skills. Takes a keynote/conference transcript and runs the whole pipeline — topic, outline, draft, AI-pattern audit, Hemingway cut, image prompts — by invoking each skill in order and passing each output to the next.

This skill conducts. It does not redo the work. At each step, invoke the named skill and let it do its job.

> Self-contained orchestrator. It assumes the other six skills are available (installed as a plugin, or loaded individually).

## How to Run

- "Turn this transcript into a newsletter"
- "Run the newsletter chain" / "run the whole keynote-to-newsletter chain"
- "Build a newsletter from this keynote"

## Setup

1. Confirm a transcript is provided (file or pasted). If not, ask for it before starting.
2. Pick a mode:
   - **Guided (default):** stop at the review gates below for the user's call.
   - **Express:** run straight through, making sensible default choices, and present everything at the end. Use this only if the user asks for it ("just run it," "express," "don't stop").
   State which mode you're running so the user knows what to expect.

## The Sequence

Run these in order. After each, save its output file so the next skill can read it.

1. **transcript-topic-scanner** → produces `topic-brief-[slug].md`
   🚦 GATE (guided): show the recommended topic + alternates. Ask which to run with. Default = the ★ pick.
2. **outline-builder** → reads the topic brief → produces `outline-[slug].md` (outline + 5 subject lines)
   🚦 GATE (guided): show the outline + subject lines. Get approval or edits before drafting.
3. **content-writer** → reads the outline → produces `draft-[slug].md`
   🚦 GATE (guided): show the draft. Approve or request revisions before editing passes.
4. **writing-auditor** → reads the draft → AI-pattern report → `audited-[slug].md` (if fixes applied)
   🚦 GATE (guided, light): show the report. Ask which fixes to apply (default = apply all criticals).
5. **hemingway** → reads the audited/draft → produces `final-[slug].md`
   🚦 GATE (guided): show the cut report + trimmed draft. Approve, or restore any darlings.
6. **midjourney-prompt-creator** → reads the final → outputs 2–3 hero-image prompts.

At the end, summarize what was produced and where each file was saved.

## Rules

- Conduct, don't duplicate. Invoke each skill; never re-implement its logic here.
- Run the steps in order. Each skill depends on the previous skill's output file — don't skip or reorder.
- In guided mode, never blow past a gate. Wait for the user's call before moving on.
- In express mode, still SAVE every intermediate file, and surface anything the auditor flagged as critical even if you auto-applied fixes.
- If a step produces a weak result (thin topic, weak outline), say so and offer to rerun that step before continuing — don't propagate weakness down the chain.
- Keep one consistent `[slug]` across all files for a given run so the outputs stay grouped.
- The user can also run any skill standalone; this orchestrator is for the full run.
