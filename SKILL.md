---
name: design-taste
description: Think like a designer before writing any UI. Use this skill whenever the user asks to build, design, redesign, restyle, review, or "make it look better/professional/modern" for ANY website, landing page, dashboard, web app, mobile app, component, or screen — including React/Next.js/Tailwind/HTML/CSS/Flutter/SwiftUI work, mockups, prototypes, and artifacts. Also trigger on words like UI, UX, layout, hierarchy, typography, color palette, spacing, polish, design system, "vibe-coded", "generic", "looks like AI made it", "looks like a template". Even when the user only asks for code, use this skill first so the result is intentional rather than the default AI/Tailwind-template look.
---

# Design Taste

This skill exists because generated interfaces converge on the same look: centered hero, gradient headline, three feature cards with icon-in-a-colored-circle, `rounded-2xl` everything, purple-to-blue gradients, glassmorphism, a glow behind the CTA. It is recognizable in one second, and people call it "vibe-coded". None of it is *wrong* on its own — the problem is that it was never chosen. Taste is the habit of choosing.

Everything below is about making choices on purpose. The process comes first; the rules in `references/` exist to inform choices, not replace them.

## The one-sentence test

Before writing any markup, be able to finish this sentence:

> "This interface is for **[who]** trying to **[do what]**, and it should feel **[two or three adjectives]**, so the first thing they notice is **[one element]**."

If any blank is empty, do not start styling. Ask, or decide and state the assumption.

## The process (in this order)

Designers do not start with colors. They start with the job and work outward. Follow the sequence; the later steps depend on the earlier ones.

### 1. Intent — decide what this is

- **Who** uses it, in what state (rushed, curious, anxious, expert)?
- **What is the primary action** on this screen? There is exactly one.
- **What personality** should it have? Pick 2–3 adjectives and commit (e.g. *calm, precise, quiet* vs *warm, playful, generous* vs *dense, fast, serious*). Every later choice — typeface, radius, color, motion — must agree with these words. A "warm, playful" product does not get sharp corners and a cold gray; a "precise, serious" tool does not get bouncing animations.
- **Which conventions does the category expect?** (Banking reads as trustworthy through restraint; a kids' learning app through color and character.) Decide whether to follow the convention or deliberately break it. Breaking it by accident is the default AI failure.

### 2. Structure — content before chrome

- List the actual content: the real headline, the real numbers, the real labels. Design around real content, not lorem ipsum and placeholder cards. Fake content produces fake layouts.
- Rank every element: primary (one), secondary (a few), tertiary (everything else). This ranking *is* the design.
- Decide the reading path. Where does the eye land first, second, third? If three things compete for "first", the hierarchy has failed.
- Cut. If a section only exists because "landing pages have that section", remove it. Start with too little and add only what is missed.
- Design the states now, not later: empty, loading, error, success, partial. A screen with only a happy path is unfinished.

### 3. Layout — space, alignment, rhythm

- Pick a spacing scale (one base unit, a limited set of steps — see `references/hierarchy-layout-spacing.md`) and use nothing else.
- Use space, not lines, to group. Related things sit close; unrelated things sit far. The gap *between* groups should be clearly larger than the gap *within* a group.
- Align to a consistent edge. Left-aligned text with a strong left edge reads faster than centered text; center only short, symmetrical things (a hero line, a single button).
- Choose a measure. Body text at 45–75 characters per line; do not stretch text across a full-width container.
- You do not have to fill the screen. Narrow, well-spaced content beats wide, sparse content.
- Vary section rhythm deliberately: not every section is "heading + paragraph + 3-column grid". Alternate density, width, and composition so the page has a pulse.

### 4. Typography — hierarchy is mostly type

- One typeface family is enough; two at most, with a clear division of labor (display vs text, or serif vs sans).
- Establish a type scale with 5–7 sizes and stick to it. Build hierarchy with size **and** weight **and** color **and** spacing together — not with "make it bold" alone.
- Set line-height in proportion: tight (1.1–1.25) for large headings, looser (1.5–1.7) for body. Tighten letter-spacing slightly on large headings; never letter-space lowercase body text.
- Use secondary text color to *de-emphasize* supporting text instead of enlarging the primary. Emphasis by subtraction.
- Labels are a last resort. "Sales: 591" is weaker than **591** with "sales" as a quiet caption.

Details: `references/typography.md`.

### 5. Color — a system, not a gradient

- Start with the neutrals. Most of any good interface is neutral: background, surfaces, borders, text at three levels. Get these right first; the accent is the last 5–10%.
- Choose one accent that expresses the personality, then define its full shade range (light tints for backgrounds, mid for interactive, dark for text on tint). Add semantic colors (success/warning/danger/info) with the same discipline.
- Tint the grays toward the accent or toward warmth/coolness so they belong to the same world. Pure `#888` next to a saturated brand color looks disconnected.
- Gradients, glows, and glassmorphism are *effects*. Use them only when the personality calls for them, and then sparingly and consistently — one hero gradient is a choice; gradients on every card, button, and heading is a tell.
- Meet contrast requirements without going flat: dark text on a light tint of the accent is often better than white text on a mid-accent.

Details: `references/color.md`.

### 6. Components and surfaces — restraint

- Radius, shadow, and border are a *voice*. Pick one radius scale (e.g. 4 / 8 / 12) and one shadow scale and apply them consistently. `rounded-2xl` on every element is the single most recognizable vibe-coded marker.
- Emulate one light source. Shadows are subtle, slightly colored, and grow with elevation; they are not decoration.
- Prefer fewer borders. Separate with space, background shifts, or a single hairline — not a border on every card plus a shadow plus a ring.
- Icons are supporting characters, not the point. An icon in a colored circle above every feature heading is a template pattern; if the icon does not add meaning, remove it.
- Buttons: one primary per view, secondary is quieter (outline or tinted), tertiary is text. Consistent height, padding, and font across all variants.
- Forms: label above field, clear affordance, inline validation, a single obvious submit.

Details: `references/components-and-states.md`.

### 7. Motion — purpose over spectacle

- Motion explains: it shows where something came from, confirms an action, or draws attention to one change. If it does none of these, it is noise.
- Small, fast, and eased. 150–250 ms for micro-interactions, 300–500 ms for layout/page transitions. Ease-out for entering, ease-in for leaving.
- Do not reveal every section on scroll, do not add parallax by default, do not hijack scroll unless the site is explicitly a narrative/portfolio experience. Respect `prefers-reduced-motion`.

Details: `references/motion.md`.

### 8. Review — audit against the rubric

Before delivering, run the check in `references/review-rubric.md` (the *Clear · Efficient · Smart · Connected · Polished* lens plus the vibe-coded tell list in `references/anti-patterns.md`). Fix what fails. Then remove one thing.

## Hard rules (the things that get skipped under time pressure)

1. **Never start from a template mental image.** Start from intent and content.
2. **One primary action per screen.** If two things are big and colorful, neither is primary.
3. **Real content only.** No lorem ipsum, no "Feature One / Feature Two", no "John Doe" avatars when real or realistic content can be written.
4. **Consistency beats novelty.** Same radius, same shadow, same spacing steps, same button heights everywhere. A single system applied strictly reads as designed; five good ideas applied inconsistently read as generated.
5. **Every effect must be justified by the personality adjectives.** If you cannot say why the gradient/glow/blur is there, delete it.
6. **All states designed.** Empty, loading, error, success, disabled, focus, hover.
7. **Accessible by default.** Contrast, focus rings, keyboard reach, 44×44 tap targets, semantic markup, color never the only signal.
8. **Mobile is a layout, not a shrink.** Reflow, reorder, and re-prioritize; see `references/mobile.md`.

## How to use the reference files

Load only what the task needs. The listing:

| File | Read when |
|---|---|
| `references/anti-patterns.md` | Always, before final output — the vibe-coded checklist |
| `references/hierarchy-layout-spacing.md` | Any layout, grid, spacing, or "it feels cluttered/empty" work |
| `references/typography.md` | Choosing fonts, scales, headings, readability problems |
| `references/color.md` | Palettes, dark mode, themes, contrast, gradients |
| `references/components-and-states.md` | Buttons, cards, forms, tables, nav, empty/error states, shadows/radius |
| `references/motion.md` | Any animation, transition, scroll effect, loading state |
| `references/ux-psychology.md` | Flows, onboarding, decisions, cognitive load, persuasion, error prevention |
| `references/mobile.md` | Anything on a phone or touch device |
| `references/review-rubric.md` | Reviewing or critiquing an existing UI, or final self-check |
| `references/sources.md` | Attribution and further reading |

## Output expectations

- When building: state the intent sentence and the 2–3 personality adjectives in one short line before the code, then deliver the code. Do not narrate the whole process.
- When reviewing: give the verdict per rubric dimension, the three highest-impact fixes first, then the rest. Prefer specific ("secondary text is `#9CA3AF` on white, 2.5:1 — raise to `#6B7280`") over general ("improve contrast").
- When the user's request would produce the template look (e.g. "add a hero with gradient text and three feature cards"), build what they asked, but make it intentional — real content, one accent, consistent system — and mention one alternative direction in a single sentence.
