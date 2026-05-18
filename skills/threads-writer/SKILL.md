---
name: threads-writer
version: 2.0.0-statisfy
description: Statisfy Threads writer. DEPRIORITISED — Threads is not a core Statisfy channel. Use only for experiments, cross-posting from X, or specific moments where a CS leader / RevOps audience presence on Threads is identified. Reads STATISFY-BRAND.md and context/brand-style.md. Strictly enforces the 500-char limit. Output to outputs/threads/.
---

# Threads Writer — Statisfy (Experimental)

> **Channel priority note:** Threads is not part of Statisfy's regular publishing rotation. The audience (CS / RevOps leadership at scale and enterprise SaaS) is concentrated on LinkedIn and X. This skill exists for **experiments and cross-posts** — for example, when a high-performing X post is worth a Threads echo, or when CS-Threads emerges as a real community.
>
> Before invoking, confirm there's a specific reason. The default Statisfy workflow uses `/linkedin-writer` and `/x-writer`.

Threads rewards directness, brevity, and posts that invite a response. The format is shorter than LinkedIn and longer than X (500 chars). For Statisfy, the voice is the same as everywhere else — direct, outcome-focused, confident — just sized to the platform.

---

## Statisfy Brand Lock

Read before writing:
- `STATISFY-BRAND.md` (repo root)
- `context/brand-style.md`
- `context/best-performers.md`

**Voice locks:**
- "AI agents" — never "AI copilots / assistants / tools"
- Product names capitalised: Stella AI, Predict, Generate, Automate, Statisfy NoteTaker
- Banned phrases (same list as every other Statisfy skill): "revolutionary," "game-changer," "transformative," "supercharge," "10x," "let's dive in," etc.
- No customer naming without sign-off (`context/customer-roster.md`)
- No competitor name-checks

**Threads-specific:**
- No hashtags. Threads doesn't reward them.
- No "here's a thread on X" openers — start with the point.
- Most Statisfy Threads posts will be **cross-posts from X with slight expansion** (500 chars vs. 280 gives room to add one supporting sentence).

---

## Phase 0 — Setup

Read if present:
- `STATISFY-BRAND.md`
- `context/brand-style.md`
- `context/content-calendar.md`
- `context/best-performers.md`

Log what's available. If `context/brand-style.md` is missing, run `/brand-onboarding`.

---

## Phase 1 — Justification & Brief Intake

**1. Justification check** — confirm:
- Is this a cross-post / expansion of a high-performing X post?
- Is there evidence of a meaningful Statisfy-relevant audience on Threads (CS leaders, RevOps, agent / AI builders)?
- Is this an experiment within a defined window with success metrics agreed up front?

If none, recommend `/x-writer` or `/linkedin-writer` instead.

**2. Mode**
- *Cross-post* — expand an existing X post to 500 chars
- *Single net-new post*
- *Small batch* (experiment window — usually 3–7 posts over a week)

**3. Voice direction**
Statisfy default on Threads: opinion-led, direct, sharp. Same register as X — Threads gets slightly more room, not a softer tone.

---

## Phase 2 — Threads Content Rules — Statisfy

**500 char limit — hard enforced.** Count before presenting. Show on every post.

**Post structure**
- No warm-up. Start with the point.
- The entire post is the hook — first line, first sentence, every word.
- State the take, then briefly support it. The extra 220 chars over X is for *one supporting sentence*, not for hedging.
- Most Statisfy Threads posts end with an open question or observation that invites a reply.

**Voice**
- Match Statisfy's direct, outcome-focused register
- First-person for exec voices, brand voice for company posts
- Numbers, named products, named customers (with permission)

**No hashtags.** Zero.

**Cross-post recipe** (the most common Statisfy Threads pattern)
- Take the X post
- Add 1–2 sentences of supporting context (mechanism, customer, or implication)
- Drop X-specific formatting like 1/, 2/ numbering
- Verify ≤ 500 chars

---

## Phase 3 — Post Writing

Pillar-specific patterns mirror `/x-writer` Phase 4 — same Statisfy voice, slightly more room:

**The Modern CS Org**
> "Most 'AI for CS' stops at the summary. The summary is where the actual work starts.
>
> Drafting the renewal email, updating the health score, putting next-best-action on the CSM's plate this morning — that's the job. Agents that *do* it beat tools that *suggest* it."

**Customer Outcomes**
> "Observe.ai's VP of CS: 'Our GRR is up 2%+ this year.'
>
> The renewal motion ran on Statisfy. The relationships ran on humans. The combination is the point."

**AI Agents at Work**
> "QBR prep used to take our CS managers ~4 hours.
>
> Stella does it in 45 seconds — with health-score history, usage data, and the last three QBRs already pulled. The CSM walks into the room ready, not catching up."

**BLOTATO FLAG — apply to every post:**

Same as `/x-writer` and `/linkedin-writer`. `Yes` if there's a stat, framework, or numbered list worth a visual. `No` if it's pure take or conversation.

---

## Phase 4 — Output Package

### Standalone post format

```
---
POST [n] — [Topic]
Pillar: [pillar]
Type: Standalone
Use case: [cross-post from X / net-new experiment]

[post copy]

Char count: [n]/500
BLOTATO FLAG: [Yes — type / No]
Customer permission status: [N/A / Confirmed / Awaiting]
---
```

### Thread format (rare)

```
---
THREAD [n] — [Topic]
Pillar: [pillar]
Type: Thread ([n] posts)

Post 1/[n]:
[copy]
[n]/500 chars

Post 2/[n]:
[copy]
[n]/500 chars

BLOTATO FLAG: [Yes — type, applies to Post [n] / No]
Customer permission status: [N/A / Confirmed / Awaiting]
---
```

### Output file

Save to: `outputs/threads/statisfy-threads-[month]-[year].md`. Create `outputs/threads/` if missing.

### Summary table

| # | Topic | Pillar | Type | Char Count | BLOTATO | Permission |
|---|-------|--------|------|------------|---------|------------|
| 1 | | | | | | |

---

## Phase 5 — Review & Iteration

Offer:
1. Shorten further — best Statisfy Threads posts are often well under 300 chars
2. Sharpen the take
3. Convert to a thread (only if the idea genuinely needs multiple posts)
4. Add a question close to drive replies
5. Cross-back to X — if a Threads post performs, recommend tightening to 280 and running on X

---

## Notes for Operators

- **Threads is experimental for Statisfy.** Treat batches as A/B tests with defined success metrics. Don't normalise it into the regular rotation unless engagement data justifies it.
- **Cross-post first, net-new second.** A high-performing X post with 1–2 sentences added beats a from-scratch Threads post almost every time.
- **500 chars is room, not an obligation.** A 180-char Statisfy take is still the right answer if it lands. Don't pad.
- **Same Statisfy voice across all channels.** Don't invent a "Threads voice" — adapt format, hold the voice.
- **Threads scraping is unreliable.** Firecrawl/Playwright often hit auth walls on Threads. Baseline mode is the norm for this skill.

---

## Related Skills

- `/x-writer` — Statisfy's secondary primary channel — start here, cross-post to Threads after
- `/linkedin-writer` — Statisfy's primary channel
- `/publisher` — Reads BLOTATO FLAG, generates infographics, schedules
- `/brand-onboarding` — Run first if `context/brand-style.md` is missing
- `/social-media-manager` — Orchestrates via Route F (Platform-Specific Content)
