---
name: story-discovery
description: Pressure-test a fuzzy feature idea before any stories get written — audit it for vagueness, grill one question at a time, and produce a Story Brief. Say "run story discovery", "explore this feature idea", "challenge my assumptions on this", "is this ready for user stories", or "audit this idea for gaps".
user-invocable: true
---

# Story Discovery

Vagueness is the number-one defect in user stories. This skill kills it before drafting starts. It audits a rough idea, interrogates it relentlessly (one question at a time), and hands off a Story Brief the drafter can build from without guessing.

> Self-contained edition: all reference material is inlined in this file (see "Reference Material" below). No external files required.

## How to Run
- "Run story discovery on [feature idea]"
- "Challenge my assumptions on this feature before I write stories"
- "Is this idea ready for user stories?"

---

## Preflight

1. Look for project context in this order; load the first that exists: `config.md`, `product-context.md`, or `story-workshop/product-context.md`.
   - If none: tell the user "No product context found — I'll work from what you tell me. Drop a product-context.md anytime to make this sharper." Continue.
2. Use the Reference Material at the bottom of this file (Domain Rules, Question Bank, Brief Template, Worked Example).
3. Continue silently.

## What the Agent Does

### Step 1: Capture the Raw Idea
- If the user gave an idea, use it verbatim. If not, ask ONE question: "What feature or change are you thinking about? A vague sentence is fine — I'll sharpen it."
- Derive a short kebab-case slug for the feature (e.g., `bulk-csv-export`). Confirm it in one line.

### Step 2: Vagueness Audit
Score the idea against the six readiness fields (see Reference: Domain Rules). Present a compact diagnostic:
- **What's here** — fields adequately covered, named specifically.
- **What's missing** — absent fields, and what the drafter would be forced to guess.
- **What's ambiguous** — weasel words ("better", "seamless", "handle", "etc.") that two people would read differently.
Do not silently fill gaps. Name them.

### Step 3: Grill (One Question at a Time)
Work the gaps from Step 2, ordered by impact and dependency (resolve upstream decisions first — see Reference: Domain Rules).
- Ask exactly ONE question per turn. Never batch. Wait for the answer.
- With every question, give your **recommended answer** and a one-line reason, so the user can accept, tweak, or reject.
- If a question is answerable from the loaded product context, answer it yourself and confirm instead of asking.
- Stop when all six fields are story-ready — not when they are exhaustive. Match depth to stakes (see Definition of Ready).

### Step 4: Assemble the Story Brief
Fill the Brief Template (see Reference). Lead with a 2-minute natural-language summary a senior colleague could act on, then the structured fields. Show it in chat for approval.

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

---
---

# Reference Material

## Reference: Domain Rules

Discovery exists to remove ambiguity before a single story is written. Treat every vague phrase as a defect that will multiply downstream.

### The Six Readiness Fields

A feature idea is "ready for stories" when all six are specific enough that a competent drafter would produce the same stories you would. These are the audit dimensions AND the grilling agenda.

| Field | The real question | Vague | Ready |
|-------|-------------------|-------|-------|
| **1. User & value** | Who specifically benefits, and what outcome do they get — not what the system does? | "Users want exports." | "A finance analyst needs a CSV of filtered transactions so they can reconcile in Excel without re-keying." |
| **2. Context** | What would a colleague joining cold need to know — current state, why now, what exists today? | "We should improve this." | "Today export is PDF-only; 3 enterprise accounts churned citing manual re-entry; Q3 commitment." |
| **3. Sources** | What evidence/material drives this — tickets, designs, research, data, prior art? Primary vs. background? | "Some customer feedback." | "Primary: support tickets #1182/#1190 and the Figma flow. Background: competitor X's export." |
| **4. Constraints** | What boundaries keep this from being technically correct but practically wrong — scope, non-functionals, compliance, dependencies? | "Make it fast and secure." | "Out of scope: scheduled exports. Must honor row-level permissions. ≤10s for 100k rows. PII columns masked." |
| **5. Quality bar** | What separates useful from polished-garbage — edge cases, the toughest reviewer, the failure that matters? | "It should just work." | "Good = correct totals on filtered + paginated data; toughest reviewer is the data team; empty-result export must not error." |
| **6. Scope boundary** | Where does THIS effort stop — the thin slice now vs. later? What's the smallest valuable cut? | "The export feature." | "Now: manual CSV of the current filtered view. Later: XLSX, scheduling, column picker." |

### Vagueness Red-Flags (audit triggers)

Flag and challenge every one of these. They are where stories go wrong.

- **Weasel verbs:** handle, manage, support, process, deal with, improve, optimize, streamline, leverage.
- **Weasel adjectives:** better, cleaner, seamless, robust, scalable, intuitive, simple, modern, flexible.
- **Hidden plurals / "etc.":** "users", "various reports", "and so on" — which users? which reports? what else?
- **Unowned passives:** "data is validated", "it gets approved" — by whom, when, against what rule?
- **Conflated needs:** one idea that is secretly 3 features. Split it.
- **Solution stated as need:** "add a dropdown" — what is the user actually trying to achieve? Recover the why.
- **Missing non-happy-paths:** no mention of empty, error, permission-denied, large-volume, or concurrent cases.

### Grilling Method

Adapted from relentless one-at-a-time interviewing.

1. **One question per turn.** Wait for the answer. Batching questions destroys focus.
2. **Walk the dependency tree.** Resolve upstream decisions first — user & value before scope, scope before constraints, constraints before quality bar. A later answer often depends on an earlier one.
3. **Always recommend.** Every question includes your best-guess answer + a one-line reason. The user accepts, edits, or rejects — far faster than answering cold.
4. **Answer from context when you can.** If product-context.md or prior answers settle a question, state the answer and confirm rather than asking.
5. **Name ambiguity; never silently fill.** "You said 'fast' — I read that as ≤10s for a typical export. Right, or is there a hard SLA?"
6. **Recover the need behind the solution.** When the user proposes UI/tech, ask what outcome it serves before accepting it.

### Definition of Ready (when to stop)

Stop grilling when:
- [ ] Each of the six fields has a specific, non-weasel answer.
- [ ] At least the empty / error / permission / large-volume edge cases are named or explicitly deferred.
- [ ] The thin slice for "now" is agreed and smaller than the original idea.
- [ ] No remaining phrase in the brief would be read two ways by two reviewers.

Match depth to stakes: a copy tweak needs two minutes; a new permissions model needs the full walk. If the idea is already ready, say so and go straight to the brief — don't manufacture questions.

---

## Reference: Question Bank

Concrete grilling questions per field. Ask ONE at a time, ordered top-to-bottom (dependencies flow downward). Every question gets a recommended answer when you pose it. Skip any the product context or a prior answer already settles.

### 1. User & value (resolve first)
- Who is the *specific* role or persona that benefits? (Not "users.")
- What outcome do they get — what can they now do, or stop doing?
- What is the cost of them not having this today?
- Is there more than one user type here? If so, which one is this slice for?
- Why would they choose this over their current workaround?

### 2. Context
- What exists today for this need — nothing, a manual process, a worse version?
- Why now? What changed (deal, churn, regulation, commitment, incident)?
- What part of the system/codebase does this touch?
- Who else is affected downstream (support, ops, billing, another team)?

### 3. Sources
- What should the drafter treat as primary truth — tickets, a design, research, a spec?
- Anything that is background only, or explicitly out of date / must NOT be used?
- Is there a prior or competitor implementation to mirror or deliberately avoid?

### 4. Constraints
- What is explicitly OUT of scope for this effort?
- Non-functionals: performance target, volume, concurrency, uptime?
- Security / compliance: permissions, PII, audit, data residency?
- Hard dependencies — another team, an API, a migration, a feature flag?
- Platform limits the drafter should not assume away?

### 5. Quality bar
- What does "good" look like beyond "it works"? Name the success signal.
- Who is the toughest reviewer, and what would make them sign off?
- Which edge cases matter: empty result, error, permission-denied, huge volume, concurrent edits?
- What is the failure that would actually hurt (wrong totals, data leak, silent drop)?

### 6. Scope boundary (resolve last)
- What is the smallest version that still delivers real value now?
- What can be explicitly deferred to a "later" list?
- Are there natural slices (by user type, by data type, by workflow step, by happy-path-first)?
- Where should this effort STOP so it doesn't sprawl?

### Recommended-answer pattern

Pose each question like this:

> **Q:** Who specifically is this for?
> **My recommendation:** The finance analyst persona — they're the ones hitting the manual re-keying pain in tickets #1182/#1190.
> **Why:** The churn signal all traces to that role; building for "all users" would over-scope.
> Accept, narrow, or tell me I've got the wrong persona?

If product context already answers it, replace the question with a confirmation:

> Product context says exports must honor row-level permissions, so I'll treat that as a hard constraint — flag me if that's changed.

---

## Reference: Story Brief Template

This is the output of story-discovery and the input to story-drafter. Save to `story-workshop/<slug>/01-story-brief.md`. Lead with the natural-language summary; the structured fields below it carry the detail the drafter needs.

```markdown
# Story Brief: <Feature Title>

slug: <kebab-slug>
status: ready-for-drafting
created: <YYYY-MM-DD>
author: <name>

## Summary (read this first)
<2–4 sentence natural-language brief a senior colleague could act on in two minutes.
What needs to become true, for whom, why now, and where this effort stops. No weasel words.>

## 1. User & value
- Primary user/persona: <specific role>
- Outcome they get: <what they can now do / stop doing>
- Cost of status quo: <pain today>

## 2. Context
- Today: <current state / workaround>
- Why now: <trigger>
- System area touched: <component / surface>
- Downstream impact: <teams / systems affected>

## 3. Sources
- Primary: <tickets, designs, specs to treat as truth>
- Background: <supporting material>
- Do NOT use: <stale / out-of-scope material>

## 4. Constraints
- Out of scope: <explicitly excluded>
- Non-functional: <perf / volume / concurrency targets>
- Security & compliance: <permissions, PII, audit>
- Dependencies: <teams, APIs, flags, migrations>

## 5. Quality bar
- "Good" means: <success signal beyond "works">
- Toughest reviewer: <who> — satisfied by <what>
- Edge cases that matter: <empty / error / permission / volume / concurrency>
- Failure that would hurt: <the costly defect>

## 6. Scope boundary
- Slice for NOW: <smallest valuable cut>
- Deferred to LATER: <explicit backlog of next cuts>
- Natural slicing axes: <by user / data / step / happy-path-first>

## Enabler signals (hints for the drafter)
- Technical/architectural work implied: <spikes, infra, refactors, APIs>
- Open questions still unresolved: <anything parked, with owner>

## Open assumptions to confirm
- <assumption 1 — who confirms>
```

Fill rules:
- Every field gets a concrete answer or an explicit "N/A — deferred". No blanks, no weasel words.
- `status: ready-for-drafting` only when the Definition of Ready passes. Otherwise `status: needs-input` and list what's blocking under "Open assumptions".
- "Enabler signals" is a hint section, not a commitment — the drafter decides actual enabler stories.
- Keep the Summary tight enough to paste into a kickoff message unedited.

---

## Reference: Worked Example

**Raw idea (what the user typed):**
> "We need a better export so users can get their data out. Should handle big accounts and be secure."

Slug: `data-export`

**Step 2: Vagueness Audit (what the agent shows)**

*What's here* — A direction: users want to extract their own data.

*What's missing*
- User & value: "users" is unowned — which role, for what task? Drafter would guess.
- Sources: no tickets, designs, or evidence named.
- Scope boundary: "export" could be CSV, XLSX, PDF, API, scheduled — unbounded.

*What's ambiguous*
- "better" — better than what, on which axis?
- "handle big accounts" — what volume, what target?
- "secure" — permissions? PII masking? audit log? All three?

**Step 3: Grilling (one question at a time — abridged)**

> **Q:** Who specifically is this for?
> **Recommendation:** The finance analyst persona reconciling in Excel.
> **Why:** That's the role that re-keys data today; "all users" over-scopes.
> Accept / narrow / wrong persona?

— user: "Yes, finance analysts."

> **Q:** What's the smallest valuable slice for now?
> **Recommendation:** Manual CSV of the *current filtered view*. Defer XLSX, scheduling, column picker.
> **Why:** Covers the reconciliation pain with one screen's worth of build.

— user: "CSV of filtered view is fine for v1."

> **Q:** You said "secure" — I read that as: honor row-level permissions + mask PII columns + write an audit entry. Which are in for v1?
> **Recommendation:** Permissions + PII masking in; audit log deferred.
> **Why:** Permission leak is the costly failure; audit is nice-to-have.

— user: "Agreed, audit later."

**Step 4: Resulting Story Brief (excerpt)**

```markdown
# Story Brief: Filtered CSV Export
slug: data-export
status: ready-for-drafting

## Summary (read this first)
Finance analysts currently re-key transaction data into Excel because export is PDF-only,
and two enterprise accounts cited this in churn. For v1 they need to download a CSV of the
exact filtered view they're looking at, honoring their row-level permissions with PII columns
masked. XLSX, scheduling, and a column picker are explicitly deferred.

## 4. Constraints
- Out of scope: scheduled exports, XLSX, column picker, audit log (deferred)
- Non-functional: ≤10s for 100k rows
- Security & compliance: row-level permissions enforced; PII columns masked

## 5. Quality bar
- "Good" means: totals reconcile against the on-screen filtered + paginated data
- Toughest reviewer: data team
- Edge cases that matter: empty result exports a header-only file (no error); permission-denied rows never appear
```

What makes this good: the audit named ambiguity instead of guessing; every grill turn carried a recommendation; the slice shrank from "an export feature" to "filtered CSV view"; edge cases were captured before drafting, so they become acceptance criteria rather than bugs.

