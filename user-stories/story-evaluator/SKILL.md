---
name: story-evaluator
description: Score drafted user/enabler stories against a quality rubric — INVEST, testability, and ambiguity — and produce a scorecard table with specific fixes. Say "evaluate the stories", "run story evaluator", "score these stories", "check my stories against INVEST", or "are these stories ready".
user-invocable: true
---
 
# Story Evaluator
 
Grades stories before they enter the backlog. Checks each against INVEST, testability, and ambiguity, then produces a scorecard table with a Ready / Revise / Reject verdict and concrete, quoted fixes. It diagnoses — it does not silently rewrite.
 
## How to Run
- "Evaluate the stories for <slug>"
- "Score these stories against INVEST"
- "Are these stories ready for the backlog?"
---
 
## Preflight
 
1. Find the stories: `story-workshop/<slug>/02-stories.md`. If no slug given, ask, or accept pasted stories. If missing, suggest running story-drafter first.
2. Read the matching brief if present (`01-story-brief.md`) — needed to check that edge cases and the quality bar are actually covered.
3. Read `references/rubric.md`. Keep `references/scorecard-template.md` ready.
4. Continue silently.
## What the Agent Does
 
### Step 1: Inventory
List every story by ID (US-n, EN-n). Note its type. If a story has no acceptance criteria at all, mark it immediately as a Testability Fail.
 
### Step 2: Score Each Story
Apply `references/rubric.md`. For every story, rate each check Pass / Partial / Fail:
- **INVEST** — Independent, Negotiable, Valuable, Estimable, Small, Testable.
- **Testability** — AC present; every Then is observable/verifiable (no "works correctly"); brief's edge cases covered; NFRs expressed as criteria.
- **Ambiguity** — quote any weasel word, unowned passive, hidden plural, or solution-stated-as-need. Each instance is a Partial or Fail.
### Step 3: Verdict + Fixes
- Compute the per-story verdict using the thresholds in `rubric.md` (Ready / Revise / Reject).
- For every Partial or Fail, write a specific fix that quotes the offending text and states the change — do not rewrite the whole story for them.
- Roll up a backlog-level summary: counts by verdict, the top systemic issue across stories.
### Step 4: Build the Scorecard
Fill `references/scorecard-template.md` — the per-story table, verdicts, and the fix list. Show it in chat.
 
### Step 5: Save and Route
- On approval, save to `story-workshop/<slug>/03-evaluation-scorecard.md`.
- For any Revise/Reject story, offer: "Want me to send these fixes back to story-drafter?" (Do not auto-edit.)
- If the stories live in Notion, offer to write the verdict/score back to each page (show the mapping first; never auto-write).
## Rules
- Diagnose, don't rewrite. Flag with quoted evidence and a specific fix; leave authoring to story-drafter.
- Every Partial/Fail must quote the exact offending text — no vague "this is unclear".
- A story with no acceptance criteria is an automatic Reject, regardless of other scores.
- Use the brief as ground truth for edge-case coverage. A happy-path-only story with named edge cases in the brief fails Testability.
- "Valuable" fails if the "so that" is missing or restates the activity. "Small" fails if tentative size ≥ 13.
- Be honest but not nitpicky — don't manufacture issues on a story that genuinely passes. Match scrutiny to stakes.
- Show the scorecard before saving and any Notion write-back before doing it. Never auto-modify stories.
