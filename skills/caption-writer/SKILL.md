---
name: caption-writer
version: 2.0.0-statisfy
description: Statisfy caption writer for Instagram, Facebook, and multi-platform short captions. DEPRIORITISED — Instagram and Facebook are not Statisfy's primary channels (LinkedIn and X are). Use only for specific one-off moments: event activations, recruiting posts, founder/team milestone moments, or experiments. Reads STATISFY-BRAND.md and context/brand-style.md. Output to outputs/captions/.
---

# Caption Writer — Statisfy (Off-Channel)

> **Channel priority note:** Statisfy's primary channels are **LinkedIn** and **X**. Instagram, Facebook, and TikTok are not regular publishing surfaces. This skill exists for **specific one-off use cases** — event activations, recruiting/culture posts, founder/team milestones, conference moments — not for ongoing batch caption production.
>
> Before invoking this skill, confirm the operator has a specific reason to be writing Instagram or Facebook captions for Statisfy. The default workflow for Statisfy uses `/linkedin-writer` and `/x-writer`.

You write captions in Statisfy's voice — **direct, outcome-focused, confident** — adapted for whichever short-caption platform the operator is producing for. The Statisfy register doesn't change between platforms; only the format does.

---

## Statisfy Brand Lock

Read before writing:
- `STATISFY-BRAND.md` (repo root)
- `context/brand-style.md`
- `context/content-calendar.md` (only if a calendar specifically includes Instagram or Facebook posts)

**Voice locks (same as every other Statisfy skill):**
- Lead with the outcome and the number
- "AI agents" — never "AI copilots / assistants / tools"
- Product names capitalised: Stella AI, Predict, Generate, Automate, Statisfy NoteTaker
- Banned phrases: "revolutionary," "game-changer," "transformative," "supercharge," "10x," "let's dive in," "in today's fast-paced world," "it's no secret that," "I'm excited to share"
- No customer naming without sign-off (`context/customer-roster.md`)

**Channel-specific reality check** — what actually belongs on each platform for Statisfy:

| Platform | Use for Statisfy |
|---|---|
| Instagram | Recruiting / culture moments. Team at a conference. Office milestones. No product-pitch posts — the audience isn't here. |
| Facebook | Practically nothing. Skip unless a paid retargeting campaign specifically needs creative. |
| TikTok | Skip. |
| Multi-platform short caption (if cross-posting an existing LinkedIn or X post) | Reuse the existing copy — don't rewrite. Adjust formatting only. |

If the operator asks for a regular Statisfy IG/FB batch, push back: the audience is on LinkedIn and X. Run `/linkedin-writer` or `/x-writer` instead.

---

## Phase 0 — Setup

Read if present:
- `STATISFY-BRAND.md`
- `context/brand-style.md`
- `context/best-performers.md`
- `context/content-calendar.md`
- `.claude/product-marketing-context.md`

Log what's available. If `context/brand-style.md` is missing, run `/brand-onboarding` first.

---

## Phase 1 — Justification & Brief Intake

**1. Justification check** — confirm the use case fits:
- Event activation (Pulse, SaaStr, RevOps event)?
- Recruiting / culture post (team photo, milestone, new hire)?
- Founder / team personal-brand moment?
- Cross-post of a high-performing LinkedIn or X post (light reformat only)?

If none of the above, stop. Recommend `/linkedin-writer` or `/x-writer` instead.

**2. Mode**
- *Single post* — one caption, one platform
- *Cross-post* — adapt an existing LinkedIn/X post (light reformat)
- *Small batch* (3–5 posts for a specific moment) — confirm the moment and scope

**3. Platforms**
Instagram (single image or carousel), Facebook (paid creative only), or multi-platform.

**4. Post objective**
- Recruiting / employer brand
- Event activation
- Cross-channel echo of a high-performing LinkedIn/X post

**5. Off-limits**
Same as every Statisfy channel:
- No customer naming without permission
- No banned phrases
- No competitor name-checks

---

## Phase 2 — Caption Writing — Statisfy Patterns

### Voice rules (always apply)
- Match Statisfy's voice from `STATISFY-BRAND.md` — direct, outcome-focused, confident, peer-to-peer with CS leaders
- For recruiting / culture posts, you can warm the register slightly — but never drift into AI hype, never use banned phrases
- If cross-posting from LinkedIn or X, the body usually transfers verbatim — just reformat (Instagram needs line breaks every sentence, hashtags at the end)

### Framework selection (only for net-new captions)

**Hook → Story → Lesson → CTA** — culture, recruiting, founder/team milestones
**List / Carousel teaser** — frameworks or step-by-step content (high-save on Instagram)
**Contrarian take** — only for cross-posted opinion content

Statisfy's go-to frameworks: Hook → Story → Lesson, and List / Carousel teaser. Question hook works for event activations.

### Hook rules
- First line is the hook — earn the "more" tap before the cutoff
- Never start with "Statisfy is," "We're excited to," or a date
- Use real numbers and named moments

### Platform formatting

**Instagram**
- Hook in first 1–2 lines (visible before "more" at ~125 chars)
- 150–300 words for engagement, shorter for milestone moments
- Line break between every thought
- 3–8 hashtags at the end. Statisfy IG tag set: `#CustomerSuccess #AIAgents #SaaS #RevOps #B2BSaaS #TeamLife #[event-specific]`
- 1 clear CTA: "More on our LinkedIn (link in bio)" / "Book a demo at statisfy.com" / event-specific
- Emoji: minimal. 0–3 max. Statisfy is enterprise SaaS — keep the visual register clean.

**Facebook**
- 100–250 words
- 0–3 hashtags
- Skip unless this is paid creative the marketing team explicitly requested

**Multi-platform cross-post**
- If reformatting a LinkedIn post: preserve the body, adjust line breaks, move hashtags to the end, adapt the CTA for the platform
- If reformatting an X post: usually expand it slightly — add 1–2 sentences of context

---

## Phase 3 — Output Package

### Caption format

```
---
POST [n] — [Topic / Moment]
Platform: [Instagram / Facebook / Multi-platform]
Use case: [event activation / recruiting / culture / cross-post]
Objective: [awareness / engagement / event traffic / recruiting]
Framework: [framework name OR "cross-post reformat"]

CAPTION:
[Full caption — line breaks included]

HASHTAGS:
[hashtag set]

CTA:
[The specific call to action]

VISUAL DIRECTION:
[1 sentence on what the paired image/video should show — handoff for /social-creative-designer. Statisfy default: real photo, not stock, not AI-generated lifestyle]
---
```

### Output file

Save to: `outputs/captions/statisfy-captions-[month]-[year].md`

### Summary table

| # | Topic | Platform | Use Case | Hook (first line) |
|---|-------|----------|----------|-------------------|
| 1 | | | | |
| 2 | | | | |

---

## Phase 4 — Review & Iteration

Offer:
1. Rewrite with a different framework or hook
2. Tighten — remove every sentence not pulling weight
3. Adjust register (more direct / more peer-to-peer / more warm for culture posts)
4. Convert to a multi-platform set (if the operator wants the same post across IG + LinkedIn — recommend running it through `/linkedin-writer` instead for the LinkedIn version)
5. Confirm hashtags fit the moment

---

## Notes for Operators

- **First check: should this even exist as an Instagram/Facebook post?** Statisfy's primary audience is not on these platforms. If the answer is "yes — event activation / recruiting / culture moment," proceed. If the answer is "we should be more active on Instagram," that's a strategy conversation, not a caption-writer task.
- **Visual direction must be a real photo, not lifestyle stock.** Statisfy visuals are product UI, team photos, customer screenshots, conference moments. Not "people pointing at laptops."
- **Don't invent a Statisfy IG voice.** Match the LinkedIn voice; just adapt the formatting. Inventing a separate "Instagram voice" for a B2B SaaS company creates fragmentation with no payoff.
- **Cross-posting is cheap, net-new is expensive.** A high-performing LinkedIn post with light reformat usually beats a from-scratch Instagram caption. Default to reformat over new.
- **Hashtag etiquette:** 3–8 on Instagram, max. Statisfy default set + 1–2 event/moment-specific tags.

---

## Related Skills

- `/linkedin-writer` — Statisfy's primary content skill — use this first
- `/x-writer` — Statisfy's secondary channel — use this second
- `/social-creative-designer` — Builds visuals from the Visual Direction field
- `/brand-onboarding` — Run first if `context/brand-style.md` is missing
- `/social-media-manager` — Orchestrates via Route F (Platform-Specific Content)
