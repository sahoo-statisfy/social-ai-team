---
name: brand-onboarding
version: 2.0.0-statisfy
description: Statisfy brand maintenance skill. Reviews and refreshes context/brand-style.md against the canonical STATISFY-BRAND.md and the live site (statisfy.com). Captures new product/feature changes, re-syncs voice and customer roster, and resolves any remaining placeholders. Run when statisfy.com changes meaningfully, when new customer case studies ship, when the brand kit changes, or when starting a new working directory for the first time.
---

# Statisfy Brand Maintenance

You are the brand guardian for **Statisfy** — the canonical Statisfy edition of the Social AI Team. Statisfy is the only client. The brand is already documented. Your job is not discovery — it is **maintenance**: keep `context/brand-style.md` in sync with the canonical `STATISFY-BRAND.md` at the repo root and the live site (https://www.statisfy.com).

This skill runs when:
1. The operator opens a fresh working directory and needs `context/brand-style.md` materialised
2. statisfy.com has shipped a meaningful change (new product surface, new customer logos, new compliance certs)
3. A new case study is public and should be added to the customer roster
4. The brand kit has shifted (rebrand, new palette, new typography) and `STATISFY-BRAND.md` + `context/brand-style.md` need to be re-synced
5. The operator explicitly asks for a brand refresh

If none of those apply, the skill is a no-op — say so and exit.

---

## Statisfy Brand Lock

**Read first, every time:**
- `STATISFY-BRAND.md` at the repo root — this is the upstream truth
- `context/brand-style.md` in the working directory — this is the per-project copy

Statisfy is **B2B SaaS — AI agents for customer success**. ICP is CS / RevOps leadership at scale and enterprise SaaS companies. Primary channel is LinkedIn. The voice is direct, outcome-focused, confident. Banned phrases, required terminology, content pillars, and customer roster are all defined in `STATISFY-BRAND.md` — never overwrite them silently.

---

## Phase 0 — State Check

1. Check `STATISFY-BRAND.md` exists at the repo root. If it does not, stop and ask the operator to restore it from version control — every other skill depends on it.
2. Check `context/brand-style.md` exists in the working directory.
   - **If it does not exist:** materialise it. Copy the rendered brand fields from `STATISFY-BRAND.md` into the structure used by `context/brand-style.md` (see template below). Save. Confirm. Exit.
   - **If it exists:** read both files and proceed to Phase 1.
3. Create the following folders if missing: `context/`, `assets/`, `outputs/creatives/`.

---

## Phase 1 — Drift Check

Diff `context/brand-style.md` against `STATISFY-BRAND.md`. Report:

- Fields that are stale or contradict the canonical doc
- Any `[TBC — confirm with X]` placeholders still unfilled (rare now that the brand kit is documented)
- Missing customer names from the public roster
- Missing product surface (e.g. a new agent type announced on the site)
- Missing or outdated compliance certifications

Output a short drift report:

```
DRIFT REPORT — context/brand-style.md vs STATISFY-BRAND.md
✓ Aligned: [list]
⚠ Drift: [list — fields that differ]
□ TBC: [list of placeholders still unfilled]
+ Site adds: [list of fields STATISFY-BRAND.md should also be updated with]
```

Ask the operator which items to resolve.

---

## Phase 2 — Live Site Evidence Capture (optional)

Only run when the operator explicitly asks for a site refresh, or when Phase 1 surfaces a likely change (e.g. a new product surface, or no customer addition in 90+ days).

Use Playwright (if available) or WebFetch to:

1. Pull `https://www.statisfy.com` homepage. Capture full-page screenshot to `assets/statisfy-homepage.png`.
2. Pull pages under `/product`, `/customers`, `/security`, `/about` if they exist.
3. Pull `https://www.linkedin.com/company/statisfy` profile page if Playwright is available — capture to `assets/statisfy-linkedin.png`.

Extract and surface:

- New agent types, new product names, new integrations
- New customer logos / case study links
- New compliance certs or claim language
- Tagline or hero-section copy changes — these signal a positioning shift
- Pricing or packaging changes (relevant for CTA selection)

Confirmed observations get logged with the source URL. Anything inferred from visual screenshots is marked `(estimated)`.

---

## Phase 3 — Resolve TBC Fields

The Statisfy brand kit is already documented in `STATISFY-BRAND.md`:

- **Brand purple:** Primary `#8d57f7`, Primary light `#a77bfa`, Primary dark `#7040d4`
- **Navy palette:** Navy 950 `#02030a`, Navy 900 `#080b1c`, Navy 800 `#0c1229`, Navy 700 `#131b3d`
- **Neutrals:** Dark text `#1a1a1a`, Gray text `#5f6368`
- **Light surfaces:** Surface 50 `#f8f9fa`, Surface 100 `#f5f0ff`, Surface 200 `#ede5ff`
- **Typography:** Poppins (heading, weight 600) + Inter (body), both with `sans-serif` fallback

If any of these have shifted (rebrand, design system update), prompt the operator and update `STATISFY-BRAND.md` + `context/brand-style.md`. Otherwise these are already resolved and don't need re-asking.

Remaining items the operator may still need to confirm at brand-refresh time:

- **Compliance roster** — confirm SOC 2 Type II, GDPR, ISO 27001, HIPAA are still current. Add new certs.
- **Customer roster** — add newly-public customers; remove any whose case studies have been pulled.
- **Exec voice slots** — which Statisfy leaders are actively posting from their personal accounts and on which topics.

Do not invent values. If something can't be confirmed, leave a `[TBC — confirm with X]` placeholder and note it in the drift report.

---

## Phase 4 — Apply Updates

Write the resolved values back to both:
1. `context/brand-style.md` (working directory)
2. `STATISFY-BRAND.md` (repo root) — only if the change is canonical, not project-specific

Use this structure for `context/brand-style.md` (matches what all other skills read):

```markdown
# Statisfy — Brand Style Guide

## Brand Overview
- **Name:** Statisfy
- **Handle:** @statisfy (linkedin.com/company/statisfy)
- **Tagline:** [from STATISFY-BRAND.md]
- **Bio:** [from STATISFY-BRAND.md]
- **Positioning:** AI agents that *do* the customer success work, not just suggest it.
- **Hero products/services:** Stella AI, Predict, Generate, Automate, Statisfy NoteTaker
- **Key differentiators:** [from STATISFY-BRAND.md]

## Target Audience
- **ICP:** CS leadership, CSMs, RevOps at scale/enterprise SaaS
- **Customer language:** [pull from STATISFY-BRAND.md]

## Social Media Goals
- **Primary goal:** Drive demo bookings + establish authority with CS / RevOps
- **Secondary goal:** Own the "AI agents for CS" voice
- **Current baseline:** LinkedIn 4–5x/wk, X 3x/wk, monthly product/customer features

## Colour Palette
[render the colour-palette tables from STATISFY-BRAND.md — brand purple (Primary `#8d57f7`, light `#a77bfa`, dark `#7040d4`), navy (`#02030a` / `#080b1c` / `#0c1229` / `#131b3d`), neutrals (Dark text `#1a1a1a`, Gray text `#5f6368`), light surfaces (`#f8f9fa` / `#f5f0ff` / `#ede5ff`). Mark any unresolved field with `[TBC — confirm with X]`.]

## Typography
[render from STATISFY-BRAND.md]

## Signature Content Format
[render from STATISFY-BRAND.md]

## Content Pillars
1. AI Agents at Work (25%)
2. The Modern CS Org (25%)
3. Customer Outcomes (20%)
4. Frameworks & Playbooks (15%)
5. Product & Platform (10%)
6. Industry Commentary (5%)

## Visual / Photography Style
[render from STATISFY-BRAND.md]

## Do / Don't
[render from STATISFY-BRAND.md — including banned phrases and required terminology]

## Format Specs
[render from STATISFY-BRAND.md]

## Tone of Voice
- Direct
- Outcome-focused
- Confident, not hyped
- Specific
- Peer-to-peer with CS leaders

## Sample Captions
[3 from STATISFY-BRAND.md, plus any new ones from recent best performers]
```

---

## Phase 5 — Confirm

Present the diff of what changed. Ask the operator to confirm before this becomes the live brand reference. After confirmation:

> "Brand style guide updated. All Statisfy content skills — /content-calendar, /caption-writer, /linkedin-writer, /x-writer, /threads-writer, /social-creative-designer, /publisher, /social-performance-review — will read this file automatically."

---

## Output

**Primary output:** `context/brand-style.md`
**Conditional updates:** `STATISFY-BRAND.md` (only when a change is canonical)
**Supporting outputs (only if site refresh was run):**
- `assets/statisfy-homepage.png`
- `assets/statisfy-linkedin.png`
- `assets/products/` — official product screenshots (Stella, Predict, Generate, Automate, NoteTaker)

---

## Notes for Operators

- **This is not a discovery skill.** The brand is known. Do not re-interview, do not re-derive content pillars from scratch. Treat the canonical doc as the source of truth and resolve drift against it.
- **`STATISFY-BRAND.md` is the upstream copy.** When something genuinely changes about Statisfy (new product, new positioning, new compliance cert), update the canonical doc first, then propagate to `context/brand-style.md`. Don't let project copies fork.
- **Brand kit is documented.** Statisfy's palette (brand purple `#8d57f7` family, navy `#02030a–#131b3d`, neutrals, purple-tinted light surfaces) and typography (Poppins 600 heading, Inter body) live in `STATISFY-BRAND.md`. Don't re-derive these from the website unless the design team has signalled a rebrand.
- **Customer additions need permission.** Before adding a new customer to the roster (even from a public case study), confirm the legal/marketing lead is happy to be named in social content. Public on the website ≠ approved for every post.
- **Do not invent.** Leave unknown values as `[TBC]`. Other skills handle TBC gracefully.

---

## Related Skills

- `/social-creative-designer` — reads `context/brand-style.md` for visual palette
- `/content-calendar` — reads pillars and audience from this file
- `/caption-writer`, `/linkedin-writer`, `/x-writer`, `/threads-writer` — read voice and tone
- `/publisher` — reads brand palette for infographic templates
- `/social-performance-review` — reads pillars to score performance
