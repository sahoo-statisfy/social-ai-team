# Social AI Team — Statisfy Edition

A Claude Code workspace customised for **[Statisfy](https://www.statisfy.com)** — AI agents that automate customer success work. Every skill has been retuned for Statisfy's brand voice, B2B SaaS audience (CS / RevOps leaders at scale and enterprise SaaS), and primary channels (LinkedIn first, X second).

This is a **single-client** customisation. The original generic Social AI Team was built for SMB consumer brands (food, beauty, local services). That workflow has been rewritten to fit Statisfy's category and operating model.

Built to run inside [Claude Code](https://claude.ai/code).

> **Canonical brand reference:** [STATISFY-BRAND.md](STATISFY-BRAND.md) — the single source of truth every skill reads. Update this file when something genuinely changes about Statisfy (new product, new positioning, new compliance cert).
>
> **New here?** Read [SETUP.md](SETUP.md) for the original Claude Code / install / MCP walkthrough. The Statisfy-specific notes are in this README.

---

## What's Different in the Statisfy Edition

| Area | Generic Social AI Team | Statisfy Edition |
|---|---|---|
| **Client model** | Many SMB clients per repo | Single client — Statisfy |
| **Primary channel** | Instagram | LinkedIn |
| **Secondary channel** | Facebook / LinkedIn | X |
| **Off-channel** | (none — all platforms in play) | Instagram, Facebook, Threads, TikTok (only on explicit operator request) |
| **Content pillars** | Service / Product / Local / Personal-brand / B2B templates | 6 Statisfy-specific pillars: AI Agents at Work, The Modern CS Org, Customer Outcomes, Frameworks & Playbooks, Product & Platform, Industry Commentary |
| **Voice** | Adaptive per client | Direct, outcome-focused, confident, peer-to-peer with CS leaders |
| **Visual register** | Lifestyle photography, product composites, stop-motion reels | Enterprise tech — Navy backgrounds (`#080b1c` family), Primary purple `#8d57f7` accent, Poppins 600 + Inter typography. Product UI polish, customer quote graphics, conference photos with overlay treatment. |
| **Customer naming** | Generic "client" | Statisfy's real public customer roster (Observe.ai, Sendoso, Cerby, Gremlin, Mixpanel, Illumio, Eightfold.ai, Skyflow, Milestone) — gated by per-month permission roster |
| **CTAs** | Generic ("link in bio", "DM us") | Statisfy CTAs: Book a Demo, See the Agents, Read the case study |
| **Benchmarks** | SMB consumer (Instagram-led) | B2B SaaS (LinkedIn-led, anchored on click-through and demo attribution) |

---

## How the Skills Work Together

```
/social-media-manager  ← start here (orchestrates everything)
         │
         │  LAYER 1 — FOUNDATION
         ├── /brand-onboarding ──────────→ context/brand-style.md
         │       (refresh against STATISFY-BRAND.md)
         │       Run when the brand file is missing
         │       or statisfy.com has shipped a change.
         │
         ├── /content-calendar ──────────→ context/content-calendar.md
         │       Run monthly. Builds Statisfy's
         │       LinkedIn-led, X-secondary month.
         │       Anchors customer features and
         │       reactive Industry Commentary slots.
         │
         │  LAYER 2 — CONTENT CREATION
         ├── /linkedin-writer ───────────→ outputs/linkedin/
         │       PRIMARY CHANNEL. Direct,
         │       outcome-focused posts. Brand voice
         │       + named-exec first-person.
         │
         ├── /x-writer ─────────────────→ outputs/x/
         │       Secondary channel. Sharper takes,
         │       reactive commentary, 280-char hard
         │       limit, zero hashtags.
         │
         ├── /social-creative-designer ──→ outputs/creatives/
         │       Real-photo overlay treatment
         │       (Brand mode), product UI polish
         │       (Product UI mode), rare editorial
         │       generations (Generate mode).
         │
         ├── /caption-writer ────────────→ outputs/captions/
         │       OFF-CHANNEL. Only for IG/FB
         │       one-offs (event activations,
         │       recruiting, founder moments).
         │
         ├── /threads-writer ────────────→ outputs/threads/
         │       EXPERIMENTAL. Only for X cross-posts
         │       or specific moments.
         │
         │  LAYER 3 — DISTRIBUTION & REVIEW
         ├── /publisher ─────────────────→ Blotato (LinkedIn + X scheduling)
         │       Enforces customer-permission gate
         │       and banned-phrase scan. Generates
         │       infographic visuals (stat cards,
         │       framework diagrams, 3-step,
         │       quote graphics).
         │
         └── /social-performance-review ─→ outputs/reviews/
                 Run end of month. Pillar mix,
                 author voice, customer-named lift,
                 demand-gen attribution.            │
                                                    ▼
                                         context/best-performers.md
                                         context/review-history.md
                                         (feeds next month)
```

### Skills cross-reference each other:

- **STATISFY-BRAND.md** → upstream canonical brand → mirrored to **context/brand-style.md** in each working dir
- `/content-calendar` → writes `content-calendar.md` → read by `/linkedin-writer`, `/x-writer`, `/social-creative-designer`, `/publisher`
- `/linkedin-writer`, `/x-writer` → write **BLOTATO FLAG** + **Customer permission status** → read by `/publisher`
- `/social-creative-designer` → produces real-photo overlays + product UI captures → attached at publish
- `/social-performance-review` → updates `best-performers.md` + `review-history.md` → feeds next month's `/content-calendar`

---

## What Each Skill Does

### `/social-media-manager` — Orchestrator (Statisfy edition)
Single-client mode. Reads `context/workflow-status.md` and routes to the right next step — brand refresh, monthly content production, publishing, end-of-month review, or a specific Route F task. Approval gates at every transition.

### `/brand-onboarding` — Brand maintenance
Not a discovery skill. Reviews `context/brand-style.md` against the canonical `STATISFY-BRAND.md` and the live site (statisfy.com). Resolves drift, updates the customer roster, and re-syncs the brand kit if it shifts.

### `/content-calendar` — Statisfy strategist
Builds the LinkedIn-led, X-secondary monthly calendar. 6 Statisfy pillars with default 25/25/20/15/10/5 mix. Adjusts to month goal (demo bookings, thought leadership, product launch, event activation, etc.). Anchors customer features (permission-gated), product launches, conference moments, and reactive Industry Commentary slots.

### `/linkedin-writer` — Statisfy's primary channel
LinkedIn-native posts in Statisfy's voice — direct, outcome-focused, confident, peer-to-peer with CS / RevOps leaders. Brand voice for company-handle posts; first-person for named-exec personal posts. Per-pillar recipes for hook + body + CTA. Banned-phrase enforcement. Customer-permission status on every post. BLOTATO FLAG for infographic handoff.

### `/x-writer` — Statisfy's secondary channel
Sharper than LinkedIn — contrarian takes, reactive commentary, customer-quote one-liners. 280-char hard limit with count on every post. Zero hashtags. Threading only when an idea genuinely needs the space. Per-pillar X recipes. Customer-permission status enforced.

### `/social-creative-designer` — Real-photo + product UI specialist
Three modes for Statisfy: **Brand** (overlay treatment on real photos — team, conference, customer events, headshots), **Product UI** (polish real Stella / Predict / Generate / Automate / NoteTaker screenshots), **Generate** (rare — editorial / atmospheric for thought-leadership posts when no real asset exists). Hard rules: never AI-generate UI, never use lifestyle stock, never use AI visual tropes (glow orbs, circuit boards, blue-gradient brains).

### `/publisher` — Blotato scheduling + infographic generation
Schedules to LinkedIn (company + exec personals) and X (@statisfy + exec personals). Enforces the **customer-permission gate** — any post quoting a named customer must appear in the current month's `context/customer-roster.md` or it's held. Banned-phrase scan as a backstop. Generates Statisfy-palette infographics (Navy 900 `#080b1c` background, white Poppins 600 headlines, Primary purple `#8d57f7` accent, Inter body) for posts flagged `BLOTATO FLAG: Yes`.

### `/social-performance-review` — Statisfy demand-gen analyst
Monthly review anchored on **demand-gen metrics** (clicks to statisfy.com, demos sourced from social) — not just engagement rate. Analyses pillar performance, author voice performance, customer-named lift, format effectiveness, banned-phrase slips. Ranked recommendations that feed next month's `/content-calendar` and `/publisher` permission backlog.

### `/caption-writer` — Off-channel (deprioritised)
Instagram / Facebook / multi-platform captions. **Only use for specific one-off moments** — event activations, recruiting, founder/team milestones, or cross-posts. Statisfy's audience is on LinkedIn and X; the default monthly workflow does not include this skill.

### `/threads-writer` — Experimental (deprioritised)
Threads posts. Same Statisfy voice; 500-char limit. Used for X cross-posts (slight expansion) or specific experiments with defined success metrics.

---

## Folder Structure (Statisfy workspace)

When you run these skills, they create and read from this structure automatically:

```
your-statisfy-workspace/
├── STATISFY-BRAND.md            ← canonical brand reference (repo root)
├── context/
│   ├── brand-style.md           ← per-working-dir copy of STATISFY-BRAND.md
│   ├── content-calendar.md      ← created by /content-calendar
│   ├── customer-roster.md       ← current-month approved-to-name customers
│   ├── best-performers.md       ← updated by /social-performance-review
│   ├── upcoming-events.md       ← Pulse, SaaStr, customer announcements, product launches
│   ├── review-history.md        ← month-over-month trend log
│   └── workflow-status.md       ← updated by /social-media-manager
├── assets/
│   ├── products/                ← real Stella / Predict / Generate / Automate / NoteTaker screenshots
│   ├── team/                    ← approved headshots, team photos
│   ├── events/                  ← conference photos
│   └── customers/               ← approved customer logos (permission-gated)
└── outputs/
    ├── linkedin/                ← /linkedin-writer
    ├── x/                       ← /x-writer
    ├── creatives/               ← /social-creative-designer (real-photo overlays + product UI polish)
    ├── captions/                ← /caption-writer (off-channel — only when justified)
    ├── threads/                 ← /threads-writer (experimental — only when justified)
    └── reviews/                 ← /social-performance-review
```

---

## Installation

> **New to this?** See [SETUP.md](SETUP.md) for the full beginner walkthrough — Claude Code, MCPs, and the install steps. The Statisfy-specific notes are below.

### 1. Get the files

```bash
git clone https://github.com/stevenflanagan1/social-ai-team.git
cd social-ai-team
```

(Or download ZIP via the green **Code** button.)

### 2. Run the installer

**Mac / Linux:**
```bash
bash install.sh
```

**Windows:** double-click `install.bat` (or run from the command line).

This copies all skills into `~/.claude/skills/` where Claude Code can find them.

**Important — re-run after customisation:** if you edit anything in the `skills/` folder of this repo, re-run `install.sh` to propagate the changes to `~/.claude/skills/`. Claude Code reads the installed copy, not this source.

### 3. Bootstrap a working directory

```bash
mkdir my-statisfy-month && cd my-statisfy-month
# open Claude Code in this folder
# then run /social-media-manager — it will detect no brand file in the working dir
# and run /brand-onboarding to materialise context/brand-style.md from STATISFY-BRAND.md
```

---

## MCP Requirements

| MCP | Used by | What it enables |
|---|---|---|
| **Playwright** | `/brand-onboarding` | Optional — live site evidence capture from statisfy.com when refreshing the brand file |
| **Nano Banana** | `/social-creative-designer` | AI image edit/generate for Brand mode, Product UI mode, and rare Generate mode |
| **Blotato** | `/publisher` | LinkedIn + X scheduling + infographic generation. Required for `/publisher`. |
| **Firecrawl** | `/content-calendar`, `/linkedin-writer`, `/x-writer`, `/social-performance-review` | Optional — competitor LinkedIn / X analysis (Gainsight, ChurnZero, Catalyst, Vitally, Planhat) |
| **SerpApi** | `/content-calendar` | Optional — trending topic / industry news research |
| **Tasty Content** | `/x-writer` | Optional — current X conversation research for Industry Commentary posts |

**Minimum for the Statisfy workflow:** Blotato (publishing) and Nano Banana (visuals). Firecrawl, SerpApi, and Tasty Content are optional research enhancements.

---

## How to Use

### Monthly workflow (default)
```
/social-media-manager
```
The orchestrator reads `context/workflow-status.md` and picks up where you left off. New month → builds calendar → writes LinkedIn → writes X → handles visuals → publishes → end-of-month review.

### Brand refresh
```
/brand-onboarding
```
Run when statisfy.com has changed, a new case study has shipped, the brand kit has shifted, or the customer-permission roster needs updating. Reviews drift against `STATISFY-BRAND.md` and the live site.

### Specific tasks (most common in practice)
```
/linkedin-writer       # one-off LinkedIn post (e.g. reactive Industry Commentary)
/x-writer              # one-off X post (e.g. reaction to a news event)
/social-creative-designer  # one-off visual
/publisher             # schedule whatever's been approved
/social-performance-review  # end-of-month
```

### Off-channel (rare — only when justified)
```
/caption-writer        # event activation IG post, recruiting moment
/threads-writer        # X cross-post experiment
```

---

## Customisation Inventory (this edition)

Files changed in the Statisfy edition vs the original Social AI Team:

| File | Change |
|---|---|
| `STATISFY-BRAND.md` | **New** — canonical brand reference |
| `context/brand-style.md` | **New** — Statisfy-prefilled per-working-dir copy |
| `skills/brand-onboarding/SKILL.md` | Rewritten — now a brand maintenance skill, not discovery |
| `skills/content-calendar/SKILL.md` | Rewritten — Statisfy pillars, LinkedIn-led, single-client |
| `skills/content-calendar/references/content-mix-guide.md` | Rewritten — B2B SaaS pillars only |
| `skills/linkedin-writer/SKILL.md` | Rewritten — Statisfy voice, per-pillar recipes, customer permission, banned phrases |
| `skills/x-writer/SKILL.md` | Rewritten — Statisfy voice on X, contrarian / commentary patterns |
| `skills/caption-writer/SKILL.md` | Rewritten — deprioritised as off-channel; for specific one-offs only |
| `skills/caption-writer/references/hook-library.md` | Rewritten — Statisfy-flavoured hook formulas |
| `skills/threads-writer/SKILL.md` | Rewritten — experimental / cross-post only |
| `skills/social-creative-designer/SKILL.md` | Rewritten — Brand / Product UI / Generate modes; no lifestyle, no fake UI, no AI tropes |
| `skills/publisher/SKILL.md` | Rewritten — LinkedIn + X only; customer-permission gate; banned-phrase scan |
| `skills/social-performance-review/SKILL.md` | Rewritten — B2B SaaS analysis, demand-gen anchored, author-voice and customer-named-lift analysis |
| `skills/social-performance-review/references/benchmarks.md` | Rewritten — B2B SaaS benchmarks; CTR + demos sourced as primary |
| `skills/social-media-manager/SKILL.md` | Rewritten — single-client orchestrator with Statisfy routes |
| `README.md` | This file — Statisfy edition overview |

---

## License

Original Social AI Team created by [The AI Impact](https://theaiimpact.co/). Statisfy-edition customisations applied for use within Statisfy's social workflow. Want a different brand build? See the original repo.
