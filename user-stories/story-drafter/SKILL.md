---
name: story-drafter
description: Turn a Story Brief into SAFe-ready user and enabler stories — user-voice form, Gherkin acceptance criteria, sensible slicing, and tentative story points — then push them to Notion. Say "draft the stories", "run story drafter", "turn this brief into SAFe stories", "write user stories from the brief", or "split this into stories".
user-invocable: true
---

# Story Drafter

Converts a refined Story Brief into a thin, vertical slice of SAFe-ready stories. User stories in user-voice form, enabler stories in technical form, Gherkin acceptance criteria on every one, and a tentative size for estimating poker. Saves a handoff file and pushes to Notion.

> Self-contained edition: all reference material is inlined in this file (see "Reference Material" below). No external files required.

## How to Run
- "Draft the stories for <slug>"
- "Turn this brief into SAFe stories"
- "Split this feature into stories and push to Notion"

---

## Preflight

1. Find the brief: `story-workshop/<slug>/01-story-brief.md`. If no slug given, ask which feature, or accept a pasted brief. If the brief is missing, say so and suggest running story-discovery first.
2. Use the Reference Material at the bottom of this file (Story Formats, Splitting Patterns, Output Template).
3. Check the Notion connector. Read `notion-config.md` if present (database ID + property map). If Notion is unavailable, note it — you'll save markdown only.
4. Continue silently.

## What the Agent Does

### Step 1: Load and Confirm
Read the brief. Restate the NOW slice and the named constraints, edge cases, and enabler signals in two lines. Flag any blank/weasel fields; proceed with explicit assumptions or bounce back to discovery.

### Step 2: Choose a Split
Pick a splitting technique (see Reference: Splitting Patterns) that fits the brief (workflow steps, CRUD, use-case scenarios, etc.). State which and why. Produce a short ordered list of vertical slices — each independently valuable, each fitting one iteration.

### Step 3: Draft User Stories
For each slice, write a user story per Reference: Story Formats:
- User-voice form: "As a <role/persona>, I want <activity> so that <business value>." Use the brief's persona name if it has one. Use the system-as-user form when the actor is a device or system.
- Gherkin acceptance criteria (Given/When/Then) covering the happy path PLUS every edge case named in the brief's quality bar. Express NFRs (perf, permissions, PII) as their own criteria.

### Step 4: Draft Enabler Stories
For the exploration / architecture / infrastructure / compliance work implied by the brief's enabler signals, write enabler stories in technical language. Tag each type (spike, refactor, infrastructure, verification, etc.) and state how it will be demonstrated (knowledge gained, artifact, stub).

### Step 5: Size (tentative)
Give each story a modified-Fibonacci size (1,2,3,5,8,13,20,40,100) with a one-line rationale across volume / complexity / knowledge / uncertainty. Label it "tentative — for the team's estimating poker", never a commitment. Anything ≥13 must be split in Step 2.

### Step 6: Review and Save
Show all stories grouped (user stories, then enablers). On approval, fill the Output Template (see Reference) and save to `story-workshop/<slug>/02-stories.md`.

### Step 7: Push to Notion
If Notion is connected: read the target database schema (from `notion-config.md`, or query the database to discover its properties). Map story fields to properties and SHOW the mapping. On approval, create one page per story. Report created page links. If Notion is unavailable, skip and tell the user the markdown is ready to paste.

## Rules
- Always user-voice form for user stories; persona name when the brief gives one; system-as-user form when no human actor.
- Every story carries Gherkin acceptance criteria. Cover the happy path and each edge case from the brief — never just the happy path.
- Enabler stories use technical language, are type-tagged, and state how they're demoed.
- Every story must fit a single iteration. If a draft can't, split it — never ship an epic disguised as a story.
- Story points are tentative placeholders for estimating poker. Never present them as final or as time.
- Show stories before saving and show the Notion field mapping before creating pages. Never auto-push.
- Don't re-run discovery. If the brief has real gaps, list them and proceed on stated assumptions or send the user back to story-discovery.

---
---

# Reference Material

## Reference: Story Formats (SAFe)

Source of truth: Scaled Agile — Stories. A story is a short, simple description of a small, vertical slice of system behavior, told from the user's perspective. Keep it small enough for an Agile Team to finish in a few days or less.

### User stories — user-voice form

The recommended expression. It forces who / what / why:

```
As a <user role or persona>, I want to <activity> so that <business value>.
```

- **Role:** a specific user role. If the brief names a persona, use the persona name: "As Jane, I want…". Personas embody representative users (e.g., thrill-seeker "Jane" vs. timid rider "Bob").
- **Activity:** what they do with the system.
- **Business value:** why — the outcome. Never omit the "so that"; a story without value is a task.

**System-as-user variant** — when the actor is a device or system (e.g., a printer, a transaction server), keep the same shape with the system as the user:

```
As the <system/device>, I want to <activity> so that <purpose>.
```

### Enabler stories — technical form

Enabler stories support exploration, architecture, infrastructure, and compliance. They may not reach an end user, so they're written in technical (not user-centric) language. Invite a System Architect when useful. Types include:

| Type | Purpose |
|------|---------|
| **Spike** | Time-boxed exploration to reduce uncertainty / answer a question. |
| **Refactoring** | Improve internal structure without changing behavior. |
| **Architecture** | Build the runway needed for upcoming user stories. |
| **Infrastructure** | Build or improve dev/test/deploy infrastructure. |
| **Jobs needing human interaction** | e.g., indexing 1M pages, data backfills. |
| **Configuration** | Create product/component configs for different purposes. |
| **Verification of system qualities** | Performance, vulnerability, compliance testing. |

Enablers are demonstrated like user stories — by showing the knowledge gained, the artifact produced, or a UI/stub/mock.

### The 3Cs

Every story is Card + Conversation + Confirmation.
- **Card** — the statement of intent (the user-voice or enabler line). Small by design; the card size limits premature detail.
- **Conversation** — the just-in-time discussion that uncovers detail, gaps, and NFRs. (The brief captures much of this up front.)
- **Confirmation** — the acceptance criteria. This is where the story becomes specific and testable.

### Acceptance criteria — BDD / Gherkin

Write confirmation as behavior-driven scenarios in the system's domain language:

```
Scenario: <short name>
  Given <precondition / context>
  When <action the user/system takes>
  Then <observable, verifiable outcome>
```

Rules:
- One scenario for the happy path; one scenario for EACH edge case named in the brief's quality bar (empty, error, permission-denied, large volume, concurrency).
- Non-functional requirements become their own scenarios (e.g., performance target, permission enforcement, PII masking).
- "Then" must be observable and verifiable — no "works correctly". State the actual expected result.
- Keep scenarios in business-readable language so they can be automated as executable acceptance tests.

### Born-INVEST checklist (write to pass it)

- **I**ndependent — minimize ordering dependencies on other stories.
- **N**egotiable — a flexible statement of intent, not a spec contract.
- **V**aluable — a vertical slice delivering value to a user or the solution.
- **E**stimable — clear enough that the team could size it.
- **S**mall — fits within one iteration.
- **T**estable — the acceptance criteria make the test obvious.

### Sizing (tentative)

Assign a relative size on the modified Fibonacci sequence: 1, 2, 3, 5, 8, 13, 20, 40, 100. A point blends:
- **Volume** — how much is there?
- **Complexity** — how hard is it?
- **Knowledge** — what's known?
- **Uncertainty** — what's unknown?

Sizes are relative to a team's "one", not time. Anything ≥13 is a smell — split it. Always label the number "tentative — for estimating poker"; the team owns the real estimate. The PO and Scrum Master participate but don't estimate.

---

## Reference: Story Splitting Patterns (SAFe / Agile Software Requirements)

Splitting big stories into small ones is a core skill — small items flow faster, with less variability and risk. Always split into VERTICAL slices: each slice must deliver observable value, not a horizontal layer (no "build the DB" story). Pick the technique that produces the most independent, valuable slices for this brief.

| # | Technique | Split when… | Example |
|---|-----------|-------------|---------|
| 1 | **Workflow steps** | The feature is a multi-step flow | Submit → review → approve as separate stories |
| 2 | **Business rule variations** | One behavior has several rules | Domestic vs. international tax rules |
| 3 | **Major effort** | One part dwarfs the rest | Ship the common case; defer the heavy variant |
| 4 | **Simple / complex** | There's a clean simple core | Single-item first, bulk later |
| 5 | **Variations in data** | Multiple data types/formats | CSV first, then XLSX, then JSON |
| 6 | **Data entry methods** | Several input paths | Manual entry now, import later |
| 7 | **Deferred system qualities** | An NFR can come after function | Make it work, then make it fast/scale |
| 8 | **Operations (CRUD)** | A resource needs full lifecycle | Create + Read now; Update + Delete later |
| 9 | **Use-case scenarios** | Distinct end-to-end scenarios | New customer vs. returning customer path |
| 10 | **Break-out spike** | Too much uncertainty to estimate | Spike to learn, then a sized story |

How to choose:
1. Start from the brief's NOW slice and natural slicing axes.
2. Prefer the technique that isolates the highest-value, lowest-uncertainty slice to do first.
3. If you can't estimate a slice, you have too much uncertainty → break-out spike (#10) as an enabler.
4. Sequence the slices so the first one is independently demoable.

State your choice explicitly:
> Splitting by **workflow steps (#1)**: the export flow is select → generate → download. Slice 1 is "generate + download the current filtered view"; pagination and scheduling become later slices.

Slice quality gate: each slice is vertical (delivers value), fits one iteration (size < 13), is ordered with slice 1 standing alone, and deferred slices land on the brief's LATER list.

---

## Reference: Story Output Template + Notion Mapping

Save to `story-workshop/<slug>/02-stories.md`. This is the handoff to story-evaluator. Keep story IDs stable — the evaluator references them.

```markdown
# Stories: <Feature Title>

slug: <kebab-slug>
source-brief: 01-story-brief.md
split-strategy: <technique # and name + one-line reason>
status: ready-for-evaluation
created: <YYYY-MM-DD>

## User Stories

### US-1 — <short title>
**Story:** As a <role/persona>, I want to <activity> so that <business value>.
**Size (tentative):** <Fibonacci> — <volume/complexity/knowledge/uncertainty note>
**Acceptance criteria:**
    Scenario: Happy path — <name>
      Given <context>
      When <action>
      Then <observable outcome>

    Scenario: <edge case from brief>
      Given <context>
      When <action>
      Then <observable outcome>
**NFRs:** <perf / permissions / PII as Gherkin or noted>
**Notes / dependencies:** <independence flags, links to sources>

## Enabler Stories

### EN-1 — <short title>  ·  type: <spike|refactor|architecture|infrastructure|verification|config>
**Story:** <technical statement of the work>
**Size (tentative):** <Fibonacci> — <rationale>
**Demonstrated by:** <knowledge gained / artifact / stub or mock>
**Acceptance criteria:**
    Scenario: <name>
      Given <context>
      When <action>
      Then <verifiable result>

## Deferred to LATER (not in this slice)
- <slice> — <why deferred>
```

Notion mapping — do NOT assume property names. Resolve the schema first:
1. If `notion-config.md` exists, use its `database_id` and `property_map`.
2. Otherwise query the target database and read its actual properties, then propose a mapping.

Suggested field → property mapping (adapt to the discovered schema, SHOW it before pushing):

| Story field | Typical Notion property | Property type |
|-------------|-------------------------|---------------|
| Story title (US-n / EN-n + title) | Name / Title | title |
| Story statement | Story / Description | rich_text |
| Type (user / enabler + subtype) | Type | select |
| Acceptance criteria (Gherkin block) | Acceptance Criteria | rich_text |
| Size (tentative) | Story Points / Estimate | number or select |
| Status | Status | status / select |
| Source feature/slug | Feature / Epic | relation or rich_text |
| NFRs / notes | Notes | rich_text |

Mapping rules:
- Map only to properties that exist. If a target property is missing, tell the user and either skip it or offer to add it — don't invent properties silently.
- Put Gherkin in a code block within the rich_text so it stays readable.
- Mark Size as tentative in the value or a note — it's pre-estimating-poker.
- One Notion page per story. Report the created page URLs back.
- If the connector errors or is absent, save the markdown and tell the user it's ready to paste.

---

## Reference: Worked Example

Input is the `data-export` Story Brief (filtered CSV export for finance analysts).

**Step 2: Split choice (shown to user)**
> Splitting by **variations in data (#5)** and **deferred system qualities (#7)**: slice 1 is CSV of the current filtered view; XLSX and large-volume performance hardening are later slices.

**Step 3: User story**

### US-1 — Export current filtered view to CSV
**Story:** As a finance analyst, I want to download a CSV of my current filtered transaction view so that I can reconcile in Excel without re-keying.
**Size (tentative):** 5 — moderate volume, low uncertainty; reuses existing filter state.
**Acceptance criteria:**
```
Scenario: Happy path — export filtered view
  Given I have applied filters to the transaction list
  When I click "Export CSV"
  Then a CSV downloads containing only the rows matching my filters
  And the column totals equal the on-screen totals

Scenario: Empty result
  Given my filters match no transactions
  When I click "Export CSV"
  Then a CSV downloads with only the header row
  And no error is shown

Scenario: Permission enforcement
  Given some transactions are outside my row-level permissions
  When I export
  Then those rows are absent from the file
```
**NFRs:**
```
Scenario: PII masking
  Given the export includes a PII column
  When the file is generated
  Then PII values are masked per policy
```

**Step 4: Enabler story**

### EN-1 — Spike: streaming CSV generation for 100k rows  ·  type: spike
**Story:** Investigate streaming vs. in-memory CSV generation to meet the ≤10s / 100k-row target before committing to an approach.
**Size (tentative):** 3 — time-boxed exploration.
**Demonstrated by:** A short recommendation doc + a throughput benchmark on a 100k-row sample.

Why this is good: every story is user-voice with a real "so that"; the enabler is technical and demoable; acceptance criteria cover the brief's exact edge cases and NFRs, not just the happy path; the slice is small, vertical, and shippable; uncertainty got isolated into a spike; sizes are labeled tentative.
