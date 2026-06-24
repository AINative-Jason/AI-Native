---
name: story-evaluator
description: Score drafted user/enabler stories against a quality rubric — INVEST, testability, and ambiguity — and produce a scorecard table with specific fixes. Say "evaluate the stories", "run story evaluator", "score these stories", "check my stories against INVEST", or "are these stories ready".
user-invocable: true
---

# Story Evaluator

Grades stories before they enter the backlog. Checks each against INVEST, testability, and ambiguity, then produces a scorecard table with a Ready / Revise / Reject verdict and concrete, quoted fixes. It diagnoses — it does not silently rewrite.

> Self-contained edition: all reference material is inlined in this file (see "Reference Material" below). No external files required.

## How to Run
- "Evaluate the stories for <slug>"
- "Score these stories against INVEST"
- "Are these stories ready for the backlog?"

---

## Preflight

1. Find the stories: `story-workshop/<slug>/02-stories.md`. If no slug given, ask, or accept pasted stories. If missing, suggest running story-drafter first.
2. Read the matching brief if present (`01-story-brief.md`) — needed to check that edge cases and the quality bar are actually covered.
3. Use the Reference Material at the bottom of this file (Rubric, Scorecard Template).
4. Continue silently.

## What the Agent Does

### Step 1: Inventory
List every story by ID (US-n, EN-n). Note its type. If a story has no acceptance criteria at all, mark it immediately as a Testability Fail.

### Step 2: Score Each Story
Apply the Rubric (see Reference). For every story, rate each check Pass / Partial / Fail:
- **INVEST** — Independent, Negotiable, Valuable, Estimable, Small, Testable.
- **Testability** — AC present; every Then is observable/verifiable (no "works correctly"); brief's edge cases covered; NFRs expressed as criteria.
- **Ambiguity** — quote any weasel word, unowned passive, hidden plural, or solution-stated-as-need. Each instance is a Partial or Fail.

### Step 3: Verdict + Fixes
- Compute the per-story verdict using the thresholds in the Rubric (Ready / Revise / Reject).
- For every Partial or Fail, write a specific fix that quotes the offending text and states the change — do not rewrite the whole story for them.
- Roll up a backlog-level summary: counts by verdict, the top systemic issue across stories.

### Step 4: Build the Scorecard
Fill the Scorecard Template (see Reference) — the per-story table, verdicts, and the fix list. Show it in chat.

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

---
---

# Reference Material

## Reference: Story Evaluation Rubric

Three lenses: INVEST, testability, ambiguity. Each check scores Pass / Partial / Fail. Ambiguity reuses the same weasel-word list as story-discovery so the whole chain judges vagueness identically.

Scale: **Pass** = meets the bar, no action. **Partial** = works but weak; fix recommended. **Fail** = blocks the story; fix required.

### Lens 1 — INVEST

| Letter | Check | Pass | Fail |
|--------|-------|------|------|
| **I** Independent | Can it be built without waiting on another story? | No hard ordering dependency, or dependency noted and acceptable | Silently depends on an unbuilt story |
| **N** Negotiable | Is it intent, not a frozen spec? | Leaves room for the conversation | Over-specifies implementation, reads like a contract |
| **V** Valuable | Is there a real "so that" delivering user/solution value? | Clear value distinct from the activity | "so that" missing, or just restates the activity |
| **E** Estimable | Could the team size it? | Enough clarity to estimate | Too vague or too unknown to size (→ needs a spike) |
| **S** Small | Fits one iteration? | Tentative size < 13 | Size ≥ 13, or scope obviously multi-iteration |
| **T** Testable | Do the AC make the test obvious? | Gherkin AC with verifiable outcomes | No AC, or outcomes not verifiable (see Lens 2) |

### Lens 2 — Testability (deep)

| Check | Pass | Partial | Fail |
|-------|------|---------|------|
| AC present | Gherkin scenarios exist | — | No acceptance criteria → **auto-Reject** |
| Observable outcomes | Every `Then` states a verifiable result | Some vague Thens | "works correctly", "as expected", "handled properly" |
| Edge-case coverage | Covers every edge case named in the brief | Covers some | Happy-path only when brief named edge cases |
| NFRs as criteria | Perf / permissions / PII expressed as scenarios | NFRs mentioned but not as AC | NFRs from brief absent |

### Lens 3 — Ambiguity (quote every instance)

Flag and quote each occurrence. One instance → Partial; pervasive or load-bearing → Fail.

- **Weasel verbs:** handle, manage, support, process, deal with, improve, optimize, streamline, leverage.
- **Weasel adjectives:** better, cleaner, seamless, robust, scalable, intuitive, simple, modern, flexible.
- **Unowned passives:** "data is validated", "it gets approved" — by whom, against what rule?
- **Hidden plurals / "etc.":** "users", "various reports", "and so on".
- **Missing/weak actor or value:** generic "user" where a persona exists; vague "so that".
- **Solution stated as need:** UI/tech prescribed instead of the outcome.

### Per-story verdict

- **Ready** — all INVEST Pass, Testability all Pass, no ambiguity Fail. (Minor Partials allowed if noted.)
- **Revise** — no hard Fail, but one or more Partials (weak value, thin AC, a weasel word or two).
- **Reject** — any of: no AC; Valuable Fail; Small Fail; Testable Fail; or pervasive ambiguity.

### Backlog roll-up
Report counts (Ready / Revise / Reject) and name the single most common issue across stories (e.g., "4 of 6 stories cover only the happy path"). That systemic note is the highest-leverage fix.

---

## Reference: Scorecard Template

Save to `story-workshop/<slug>/03-evaluation-scorecard.md`. Lead with the roll-up so a PO sees the verdict first, then the per-story tables, then the fix list.

```markdown
# Evaluation Scorecard: <Feature Title>

slug: <kebab-slug>
source-stories: 02-stories.md
evaluated: <YYYY-MM-DD>

## Roll-up
| Verdict | Count | Stories |
|---------|-------|---------|
| Ready   | <n>   | <IDs>   |
| Revise  | <n>   | <IDs>   |
| Reject  | <n>   | <IDs>   |

Top systemic issue: <one sentence — the highest-leverage fix across the set>

## Scorecard

| Story | I | N | V | E | S | T | Testability | Ambiguity | Verdict |
|-------|---|---|---|---|---|---|-------------|-----------|---------|
| US-1  | ✓ | ✓ | ✓ | ✓ | ✓ | ◐ | ◐ | ✓ | Revise |
| US-2  | ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ | ◐ | Reject |
| EN-1  | ✓ | ✓ | n/a | ✓ | ✓ | ✓ | ✓ | ✓ | Ready |

Legend: ✓ Pass · ◐ Partial · ✗ Fail · n/a not applicable (e.g., Valuable on a pure spike)

## Fixes (by story)

### US-2 — Reject
- **Valuable (✗):** "...so that it works better." → restate the actual outcome, e.g. "so that analysts reconcile without re-keying."
- **Testability (✗):** Then-clause "Then the data is handled properly" is not verifiable → state the observable result and add the empty-result + permission-denied scenarios named in the brief.
- **Ambiguity (◐):** "handle large accounts" — quote it, then quantify (the brief says ≤10s / 100k rows).

### US-1 — Revise
- **Testable (◐):** missing the concurrency edge case from the brief → add a scenario.
```

Fill rules:
- The scorecard row order matches the stories' order in 02-stories.md; keep IDs identical.
- Every ✗ and ◐ in a row must have a matching bullet in the Fixes section, with quoted text.
- Use n/a (not a blank) where a check doesn't apply — e.g., Valuable on a pure exploration spike.
- Keep fixes as direction, not full rewrites; the user routes them back to story-drafter if they want them applied.
- If writing the verdict back to Notion, map: Verdict → a select/status property; optionally the roll-up note → a rich_text property. Show the mapping first.

---

## Reference: Worked Example

Evaluates two stories from the `data-export` set: one strong (US-1), one weak (US-2 deliberately degraded to show Reject).

**Input stories**

### US-1 — Export current filtered view to CSV
> As a finance analyst, I want to download a CSV of my current filtered transaction view so that I can reconcile in Excel without re-keying.
> AC: happy path + empty result + permission enforcement + PII masking. Size: 5.

### US-2 — Improve exports
> As a user, I want better exports so that it works well for large accounts.
> AC: "Given an export, When it runs, Then the data is handled properly." Size: 13.

**Scorecard**

| Story | I | N | V | E | S | T | Testability | Ambiguity | Verdict |
|-------|---|---|---|---|---|---|-------------|-----------|---------|
| US-1  | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | Ready |
| US-2  | ✓ | ✓ | ✗ | ◐ | ✗ | ✗ | ✗ | ✗ | Reject |

**Fixes**

US-2 — Reject
- **Valuable (✗):** "so that it works well" restates the activity. Name the outcome: "so that I can reconcile a large account in Excel without timeouts."
- **Small (✗):** size 13 → split (e.g., by data volume: standard accounts now, 100k-row accounts as a separate slice).
- **Testable / Testability (✗):** "Then the data is handled properly" is not observable. Replace with a verifiable result and add the empty-result and permission-denied scenarios the brief requires.
- **Ambiguity (✗):** quote "better exports", "large accounts", "works well" — each is a weasel phrase; quantify against the brief.

US-1 — Ready: no action. Value is explicit, AC cover the brief's edge cases and NFRs, size fits an iteration.

Why this is good: every ✗ is backed by quoted text and a specific, bounded fix — not "make it clearer"; the evaluator checks US-1's AC against the brief's edge cases, so coverage is judged against ground truth; it diagnoses and routes rather than quietly rewriting, keeping the chain's separation of concerns intact.
d
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
