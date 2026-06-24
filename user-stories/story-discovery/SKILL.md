---
name: story-discovery
description: Pressure-test a fuzzy feature idea before any stories get written — audit it for vagueness, grill one question at a time, and produce a Story Brief. Say "run story discovery", "explore this feature idea", "challenge my assumptions on this", "is this ready for user stories", or "audit this idea for gaps".
user-invocable: true
---
 
# Story Discovery
 
Vagueness is the number-one defect in user stories. This skill kills it before drafting starts. It audits a rough idea, interrogates it relentlessly (one question at a time), and hands off a Story Brief the drafter can build from without guessing.
 
## How to Run
- "Run story discovery on [feature idea]"
- "Challenge my assumptions on this feature before I write stories"
- "Is this idea ready for user stories?"
---
 
## Preflight
 
1. Look for project context in this order; load the first that exists: `config.md`, `product-context.md`, or `story-workshop/product-context.md`.
   - If none: tell the user "No product context found — I'll work from what you tell me. Drop a product-context.md anytime to make this sharper." Continue.
2. Read `references/domain.md` (the six readiness fields, vagueness red-flags, grilling method).
3. Read `references/question-bank.md`. Keep `references/brief-template.md` ready for Step 4.
4. Continue silently.
## What the Agent Does
 
### Step 1: Capture the Raw Idea
- If the user gave an idea, use it verbatim. If not, ask ONE question: "What feature or change are you thinking about? A vague sentence is fine — I'll sharpen it."
- Derive a short kebab-case slug for the feature (e.g., `bulk-csv-export`). Confirm it in one line.
### Step 2: Vagueness Audit
Score the idea against the six readiness fields in `domain.md`. Present a compact diagnostic:
- **What's here** — fields adequately covered, named specifically.
- **What's missing** — absent fields, and what the drafter would be forced to guess.
- **What's ambiguous** — weasel words ("better", "seamless", "handle", "etc.") that two people would read differently.
Do not silently fill gaps. Name them.
### Step 3: Grill (One Question at a Time)
Work the gaps from Step 2, ordered by impact and dependency (resolve upstream decisions first — see `domain.md`).
- Ask exactly ONE question per turn. Never batch. Wait for the answer.
- With every question, give your **recommended answer** and a one-line reason, so the user can accept, tweak, or reject.
- If a question is answerable from the loaded product context, answer it yourself and confirm instead of asking.
- Stop when all six fields are story-ready — not when they are exhaustive. Match depth to stakes (`domain.md` "definition of ready").
### Step 4: Assemble the Story Brief
Fill `references/brief-template.md`. Lead with a 2-minute natural-language summary a senior colleague could act on, then the structured fields. Show it in chat for approval.
 
### Step 5: Save and Hand Off
- On approval, save to `story-workshop/<slug>/01-story-brief.md`.
- Say: "Brief saved. Run story-drafter next — it reads this brief and writes the SAFe stories."
## Rules
- One question at a time. Asking several at once is bewildering and non-negotiable to avoid.
- Every question carries a recommended answer with a reason — never ask a bare question.
- Never draft user stories or acceptance criteria here. That is story-drafter's job. Discovery produces a brief, nothing more.
- Name ambiguity out loud; never resolve a weasel word by quietly assuming what it means.
- Prefer answering from product context over asking the user the same thing.
- Don't over-grill a trivial change. If the idea is already story-ready, say so and skip to the brief.
- Show the brief before saving. Never auto-save.
