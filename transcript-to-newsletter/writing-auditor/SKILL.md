---
name: writing-auditor
description: Audit the newsletter draft for AI writing patterns — the tells that make writing read machine-made. Flags each issue with the exact text and a concrete fix; does not rewrite. Fourth skill in the keynote-to-newsletter chain. Say "audit this", "audit the draft", "check for AI patterns", "scan for AI tells", or "run the writing auditor".
user-invocable: true
---

# Writing Auditor

Fourth skill in the keynote-to-newsletter chain. A focused AI-pattern audit of the draft — it catches the tells that make writing read machine-made (direct contrast, puffery, rule-of-three, em-dash drama, throat-clearing, performed empathy, and more) and reports each one with the exact text and a concrete fix. It does NOT tighten for length — the Hemingway editor does that next. It does NOT rewrite — it flags so the writer decides.

> Self-contained skill. The full pattern library and report format are inlined below.

## How to Run

- "Audit the draft" (after the Content Writer)
- "Check for AI patterns"
- "Scan for AI tells"

## What the Agent Does

### 1. Load the Input

Read the draft (`draft-[slug].md`) from the Content Writer. If the user pasted text instead, audit that. Don't ask permission to start — run the audit.

### 2. Run the AI-Pattern Audit

Read the full **Pattern Library** below first. Work through every category against the draft. For each violation, capture the exact offending text, name the pattern, and write a concrete fix that preserves the writer's voice and register. Prioritize the deepest tells: direct/negative contrast, puffery, performed-empathy "cringe questions," throat-clearing, and rule-of-three.

### 3. Report (don't rewrite)

Present a structured report using the **Report Format** below. Quote each issue verbatim so it's locatable, state the problem in one sentence, and give the actual replacement text. Group by category, criticals first. End with a pattern summary count and an overall rating.

### 4. Offer the Handoff

After the report, ask: "Want me to apply any of these fixes, or send it straight to the Hemingway pass for tightening?" Apply only the fixes the writer approves. Save the cleaned draft as `audited-[slug].md` when fixes are applied; otherwise the original draft moves forward.

## Rules

- Report issues, don't silently rewrite the draft. The writer decides which fixes land.
- Always quote the exact offending text and always provide a concrete replacement. Never flag without a fix.
- Preserve voice in every suggested fix — match the writer's practitioner-first, optimistic-realism register.
- Do NOT tighten for concision or cut words for length — that's the Hemingway skill's job. Stay in your lane: AI patterns only.
- Don't flag intentional rhetorical repetition (anaphora) or a contrast that has a 2–3 sentence expansion buffer.
- If the draft is clean, say so plainly — don't invent issues to look thorough.

---

## Pattern Library

Work through all sections, then report using the Report Format. Flag and fix — never rewrite the whole draft.

1. **Puffery / promotional (CRITICAL).** "stands as / serves as / is a testament," "plays a vital role," "leaves a lasting impact," "rich tapestry / rich heritage," "nestled in the heart of," "breathtaking / stunning," "seamlessly" (describing how something works), "vibrant community." *Fix:* a specific, measurable fact.

2. **Direct / negative contrast (CRITICAL — the deepest tell).** Defining things by what they aren't. "This isn't about X — it's about Y," "It's not X, it's Y," "The problem isn't X, it's Y." Masked: "Rather than X, Y," "Instead of X, Y," "but rather," "as opposed to" (as a definition). *Fix:* state the positive directly. ❌ "Success isn't about working harder but smarter." ✅ "Success comes from working smarter and more strategically." Acceptable only if the negative and positive are separated by 2–3 sentences of expansion.

3. **Performed empathy / cringe questions (CRITICAL).** Faking connection. "Sound familiar?", "And the wildest part?", "Here's the thing," "That's real. Take a second," "We've all been there," rhetorical questions inserted for fake intimacy. *Fix:* delete the performed beat; state the point.

4. **Throat-clearing (CRITICAL).** Opening filler that delays the point. "Here's what's interesting," "Here's why this matters," "The truth is," "Let's be honest," any "Here's [what/why/how]" opener. *Fix:* open on the point itself.

5. **Editorializing.** "it's important to note/remember," "it is worth noting," "notably" (filler), "interestingly" (opener). *Fix:* state the fact directly.

6. **Overused conjunctions / AI transitions.** "moreover," "furthermore," "in addition," "additionally," "consequently," "on the other hand." *Fix:* combine or start fresh.

7. **Section summary statements.** "In summary," "In conclusion," "Overall," "To summarize," "Ultimately" (as restatement), "In short." *Fix:* end on the most important or forward-looking point.

8. **Formulaic challenge sections.** "Despite its [positives], [subject] faces challenges… but with continued innovation, the future looks promising." *Fix:* integrate challenges as concrete facts throughout.

9. **Title case in headings.** "Early Life and Educational Background" → "Early life and education." Sentence case only.

10. **Excessive boldface.** Bold only for true one-time emphasis or first introduction of a term. Never bold the same term twice.

11. **Formulaic lists / rule-of-three (HIGH).** Bullets where prose works; "The benefits include:"; "fast, reliable, and secure." *Fix:* prose; replace three abstract adjectives with three specific facts. ❌ "fast, reliable, and secure" ✅ "processes requests in under 200ms with 99.9% uptime and bank-level encryption."

12. **Em-dash overuse (HIGH).** "[claim] — [amplifier] — [restatement]." One em-dash per paragraph max. ❌ "elegant — simple, effective, affordable — exactly what we need." ✅ "combines simplicity with effectiveness at an affordable price."

13. **Superficial -ing analysis.** "[fact], highlighting the importance of [abstract noun]." *Fix:* replace with the specific implication as a fact.

14. **Vague attributions.** "industry experts believe," "observers note," "critics argue," "research suggests" (no real source). *Fix:* a specific source or state the claim directly.

15. **False ranges.** "from X to Y" when not an actual range. ❌ "dishes from pasta to grilled meats" ✅ "pasta dishes, grilled meats, and seasonal vegetables."

16. **Essay-like organization.** Explicit thesis at paragraph 1, "In this article we will explore," conclusion that restates the intro. *Fix:* inverted pyramid or natural flow. (This chain's drafts should open on a scene — flag if they don't.)

17. **Knowledge disclaimers.** "as of [date]," "based on available information," "to the best of my knowledge," "I should note that." *Fix:* state confidently or omit.

18. **Collaborative / chatbot language & hedging.** "I hope this helps," "let me know if," "certainly!/absolutely!" openers, "Great question!"; hedging "tends to / appears to / seems to" when clear info exists. ❌ "The data appears to suggest users tend to prefer the new interface." ✅ "Users prefer the new interface by a 3:1 margin in testing."

19. **Dramatic section headers.** "THE X:," "HERE'S THE Y:," "THE BOTTOM LINE:," all-caps openers, headers that read like tweet hooks.

20. **Word substitution.** leverages→uses · encompasses→includes · facilitates→enables · utilized→used · commenced→began · prior to→before · in order to→to · delve into→explore · underscore→show · robust→strong · holistic→complete · game-changing/innovative/cutting-edge/transformative→[a specific claim] · synergy/paradigm→[be specific].

21. **Flat rhythm (LOW).** Three+ consecutive sentences of similar length read machine-made. *Fix:* vary length; let a short sentence land after a long one.

---

## Report Format

Run the full audit internally, then present ONLY this report (do not output an annotated copy of the draft):

```
## AI Writing Audit
**Overall:** [X issue(s) across Y categories] | [CLEAN ✓ / NEEDS WORK ⚠️ / MAJOR ISSUES 🚨]

(CLEAN ✓ = 0–2 minor. NEEDS WORK ⚠️ = 3–9 or any moderate pattern. MAJOR 🚨 = 10+ or criticals present.)

---

### 🚨 Critical (fix first)
Include only if contrast, puffery, performed empathy, or throat-clearing are present.
**[Pattern name]:**
> "[exact offending text]"
↳ Problem: [one sentence]
↳ Fix: "[concrete replacement that keeps the writer's voice]"

---

### Issues by category
**[Category]** — [N] issue(s)
> "[exact offending passage]"
↳ Problem: [one sentence, specific]
↳ Fix: "[the actual rewritten text]"
[repeat per issue, per category]

---

### Pattern summary
- [Category]: N
Total flags: N
```

**Key principles:** Quote exactly. Always give a concrete fix. Preserve voice in every fix. Report only — the writer chooses which fixes land. AI patterns only — don't cut for length. If clean, say clean.
