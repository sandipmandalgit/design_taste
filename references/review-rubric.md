# Review rubric

Use this to critique an existing UI or to self-check before delivering. It combines a five-dimension lens (adapted from the Terra design system framework described in Tewari, 2025) with concrete pass/fail checks drawn from the other reference files.

Score each dimension 1–5. Anything under 4 gets a specific fix, not a comment. Report the three highest-impact fixes first.

## 1. Clear — can they understand it?

Reduces cognitive burden through information presentation and interface simplification.

- [ ] A first-time user can state the screen's purpose in 3 seconds
- [ ] One obvious primary action; secondary actions visibly quieter
- [ ] Three-tier hierarchy visible (primary / secondary / tertiary)
- [ ] Language matches the user's mental model; consistent terms throughout (one word per concept)
- [ ] Ambiguity handled in place: tooltips, helper text, links to detail — not a manual
- [ ] Nothing on screen that doesn't serve the current task
- [ ] Contrast, keyboard navigation, screen-reader semantics, focus visibility all pass
- [ ] Values are more prominent than their labels

*Measure with:* Customer Effort Score, System Usability Scale, think-aloud testing on the hierarchy, confusion/hesitation points in behavioral data.

## 2. Efficient — can they do it quickly?

Optimizes workflows by removing unnecessary interaction steps.

- [ ] Steps to complete the core task counted and minimized
- [ ] Intelligent defaults pre-fill what the system can know
- [ ] Shortcuts and bulk actions for repeated tasks; keyboard support on desktop
- [ ] Forms grouped logically, minimal required fields, inline validation, autocomplete
- [ ] No dead ends: every state offers a next action
- [ ] Nothing important hidden behind extra taps or banners
- [ ] Feedback under 100 ms; transitions under ~300 ms; waits masked with progress

*Measure with:* task time, completion rate, drop-off per step, CES on the flow.

## 3. Smart — does it help proactively?

Integrates contextual assistance without taking control away.

- [ ] Suggestions and recommendations based on context (recent, popular, relevant), never a blank search or empty picker
- [ ] Predictive input where it reduces typing (autocomplete, format tolerance)
- [ ] Adapts to user stage: new → guided, returning → their stuff first, expert → dense and fast
- [ ] Proactive error prevention: constrained inputs, disabled impossible options, warnings before irreversible actions
- [ ] User stays in control: automation is visible, reversible, and explainable

*Measure with:* adoption of smart features, error rate before/after, CES on assisted tasks.

## 4. Connected — does it hold together?

Unified design language and consistent interaction patterns across the product.

- [ ] One spacing scale, one radius scale, one shadow set, one type scale, one icon set — used without exception
- [ ] Buttons, inputs, cards, and nav behave and look the same on every screen
- [ ] Same component for the same job everywhere (no three kinds of dropdown)
- [ ] Brand identity (type, color, tone) consistent across web, mobile, email, and empty states
- [ ] Transitions between features feel like one product, not a collection of pages
- [ ] Data and state consistent across surfaces (what I did on mobile shows on web)

*Measure with:* heuristic audit of pattern consistency, cross-surface usability testing, CES across platforms.

## 5. Polished — does it feel finished?

Meticulous attention to visual detail, micro-interaction refinement, and craft.

- [ ] Every dynamic component has empty, loading, error, success, disabled, focus, hover states
- [ ] Micro-interactions purposeful and fast; no decorative motion
- [ ] Optical alignment corrected; nothing off by a pixel
- [ ] Imagery and icons professional, single style, correctly sized and cropped
- [ ] Error messages say what happened and how to fix it
- [ ] Copy is specific, sentence-case, free of marketing filler
- [ ] Passes the vibe-coded tell list in `anti-patterns.md`

*Measure with:* SUS satisfaction items, CSAT on visual quality, expert review, engagement with polished flows.

## The tell list (fast version)

Fail any of these → not done:

1. Purple/blue gradient, gradient text, or glow blobs without a personality reason
2. `rounded-2xl`+ on everything
3. Icon-in-a-colored-circle feature grid
4. Centered multi-line text or all-centered page
5. Every section = heading + subtitle + 3 cards
6. Placeholder content (lorem ipsum, Feature One, John Doe, 10K+ users)
7. Pure default grays unrelated to the accent
8. Multiple filled primary buttons in view
9. Card = border + shadow + ring + hover lift
10. Every section animates on scroll / scroll hijacking on a product site
11. Body text wider than ~75 characters
12. Hierarchy by bold alone; same line-height everywhere
13. Missing empty/loading/error states
14. "Get Started" / "Learn More" / "Unlock the power of…"
15. Mixed icon sets or emoji as icons in a serious product

## Reporting format

When reviewing for a user, use this shape:

```
Verdict: [one sentence — what it is now and what it should become]

Top 3 fixes
1. [specific change] — [why, in one line]
2. …
3. …

By dimension
Clear 3/5 — …
Efficient 4/5 — …
Smart 2/5 — …
Connected 3/5 — …
Polished 2/5 — …

Keep
- [things that are working and should not be touched]
```

Be specific: name the element, the current value, the target value. "Secondary text `#9CA3AF` on white is 2.5:1 → use `#6B7280` (4.6:1)" is useful; "improve contrast" is not.
