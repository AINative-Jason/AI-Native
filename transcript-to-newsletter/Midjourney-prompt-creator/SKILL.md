---
name: midjourney-prompt-creator
description: Generate 2–3 Midjourney hero image prompts for the finished newsletter, in a minimalist editorial surreal-collage style. Final skill in the keynote-to-newsletter chain. Say "make the image prompts", "generate a hero image prompt", "create the Midjourney prompts", "midjourney prompt creator", or "I need a hero image for this newsletter".
user-invocable: true
---

# Midjourney Prompt Creator

Final skill in the keynote-to-newsletter chain. Reads the finished newsletter and generates 2–3 Midjourney prompts for the hero image — each a distinct visual metaphor in a consistent editorial style, so the writer can pick the one that resonates.

> Self-contained skill. The style spec and output format are inlined below.

## How to Run

- "Make the image prompts" (after the Hemingway pass)
- "Generate a hero image prompt for this newsletter"
- "Create the Midjourney prompts"

## What the Agent Does

### 1. Load the Newsletter

Read the finished piece — `final-[slug].md` from the Hemingway editor. If the user pasted text, use that. See the **Reference: Prompt Style** below for the style spec and output format.

### 2. Extract the Core Concept

From the newsletter, identify: the **central idea / argument** (1 sentence), the **emotional tone** (cautionary, optimistic, analytical, provocative), and the **key nouns or themes** that lend themselves to visual metaphor. If the writer suggested metaphor ideas, use at least one and generate alternatives for the rest.

### 3. Generate 2–3 Visual Metaphors

Each variation gets a distinct object-based metaphor that communicates the idea symbolically, not literally. Lean on: hands interacting with objects, scale contrast, implied transformation, or tension/balance. Avoid metaphors that are too abstract, too literal (no laptops for an AI piece), or too busy.

### 4. Output the Prompts

Fill the template in the **Reference** below for each variation. Present them as clean, copy-ready labeled blocks — each label includes a 3–6 word metaphor description. End with a one-line ⭐ pick. No rationale beyond that.

## Rules

- Communicate the idea through metaphor, never literal illustration (no UI screens, no laptops-for-tech).
- Hold the house style exactly: minimalist editorial surreal-collage, cream/off-white background, grayscale with #8474E2 as the only accent. Consistency is the brand.
- Generate 2–3 genuinely different metaphors — not the same idea reworded.
- Output prompts ready to paste into Midjourney. No explanation between them; just the labeled blocks and the pick.
- If the newsletter's core idea is unclear, name the ambiguity and pick the strongest reading rather than producing a generic prompt.

---

## Reference: Prompt Style & Output Format

The house visual style for the newsletter's hero images. Hold it exactly — consistency across issues is the brand. (Swap the accent color / mood words if you're adapting this skill to your own brand.)

**Metaphor selection.** Each variation uses a distinct object-based metaphor that communicates the article's core idea symbolically. Good metaphors involve: hands interacting with objects (holding, releasing, building, breaking); scale contrast (oversized objects, tiny figures); transformation/transition (before/after implied in one frame); tension or balance (stacking, tipping, threading). Avoid metaphors too abstract, too literal (a laptop for a tech piece), or too busy. If the writer suggested metaphors, include at least one and generate 1–2 original alternatives.

**Prompt template** (fill completely for each variation):

```
Create a minimalist editorial illustration in a surreal analog collage style.
Subject/concept: [CORE IDEA IN 1 SENTENCE]
Visual metaphor: [OBJECT-BASED METAPHOR]
Composition: A clean horizontal editorial hero image with one central focal point, generous negative space, and a balanced layout. Use a cream/off-white background. The image should feel like a premium Substack or magazine illustration.
Style: Black-and-white photorealistic collage mixed with vintage engraving, halftone texture, fine ink shading, and subtle paper grain. Use cutout-style realism for hands, faces, objects, and props. Add one or two bold soft-violet geometric elements, such as a large circle, square, spotlight beam, oversized letter, or background block.
Color palette: Mostly grayscale and off-white, with #8474E2 as the only strong accent color. Minimal use of black for contrast. No bright colors beyond #8474E2.
Mood: Smart, restrained, conceptual, slightly surreal, literary, modern, and editorial. The image should communicate the idea through metaphor rather than literal explanation.
Avoid: Busy backgrounds, cartoon style, glossy 3D rendering, overly polished corporate stock-photo aesthetics, neon colors, excessive detail, clutter, and literal UI screens.
```

**Output format** (copy-ready blocks):

```
---
**Variation 1 — [short metaphor description]**
[full prompt]

---
**Variation 2 — [short metaphor description]**
[full prompt]

---
**Variation 3 — [short metaphor description]**
[full prompt]

---
⭐ **My pick: Variation [N]** — [one sentence reason]
```

No rationale or explanation beyond the ⭐ pick line.
