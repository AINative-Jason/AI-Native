---
name: story-drafter
description: Turn a Story Brief into SAFe-ready user and enabler stories — user-voice form, Gherkin acceptance criteria, sensible slicing, and tentative story points — then push them to Notion. Say "draft the stories", "run story drafter", "turn this brief into SAFe stories", "write user stories from the brief", or "split this into stories".
user-invocable: true
---
 
# Story Drafter
 
Converts a refined Story Brief into a thin, vertical slice of SAFe-ready stories. User stories in user-voice form, enabler stories in technical form, Gherkin acceptance criteria on every one, and a tentative size for estimating poker. Saves a handoff file and pushes to Notion.
 
## How to Run
- "Draft the stories for <slug>"
- "Turn this brief into SAFe stories"
- "Split this feature into stories and push to Notion"
---
 
## Preflight
 
1. Find the brief: `story-workshop/<slug>/01-story-brief.md`. If no slug given, ask which feature, or accept a pasted brief. If the brief is missing, say so and suggest running story-discovery first.
2. Read `references/story-formats.md`, `references/splitting-patterns.md`. Keep `references/output-template.md` ready.
3. Check the Notion connector. Read `notion-config.md` if present (database ID + property map). If Notion is unavailable, note it — you'll save markdown only.
4. Continue silently.
## What the Agent Does
 
### Step 1: Load and Confirm
Read the brief. Restate the NOW slice and the named constraints, edge cases, and enabler signals in two lines. Flag any blank/weasel fields; proceed with explicit assumptions or bounce back to discovery.
 
### Step 2: Choose a Split
Pick a splitting technique from `splitting-patterns.md` that fits the brief (workflow steps, CRUD, use-case scenarios, etc.). State which and why. Produce a short ordered list of vertical slices — each independently valuable, each fitting one iteration.
 
### Step 3: Draft User Stories
For each slice, write a user story per `story-formats.md`:
- User-voice form: "As a <role/persona>, I want <activity> so that <business value>." Use the brief's persona name if it has one. Use the system-as-user form when the actor is a device or system.
- Gherkin acceptance criteria (Given/When/Then) covering the happy path PLUS every edge case named in the brief's quality bar. Express NFRs (perf, permissions, PII) as their own criteria.
### Step 4: Draft Enabler Stories
For the exploration / architecture / infrastructure / compliance work implied by the brief's enabler signals, write enabler stories in technical language. Tag each type (spike, refactor, infrastructure, verification, etc.) and state how it will be demonstrated (knowledge gained, artifact, stub).
 
### Step 5: Size (tentative)
Give each story a modified-Fibonacci size (1,2,3,5,8,13,20,40,100) with a one-line rationale across volume / complexity / knowledge / uncertainty. Label it "tentative — for the team's estimating poker", never a commitment. Anything ≥13 must be split in Step 2.
 
### Step 6: Review and Save
Show all stories grouped (user stories, then enablers). On approval, fill `references/output-template.md` and save to `story-workshop/<slug>/02-stories.md`.
 
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
