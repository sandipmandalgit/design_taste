# Motion

Motion is communication. It answers three questions: *where did this come from*, *did my action work*, and *what changed*. Motion that answers none of these is decoration, and decorative motion is the fastest way to make a product feel like a template.

## Principles

1. **Purpose first.** Every animation maps to one of: orientation (spatial continuity), feedback (confirm input), attention (one change worth noticing), or personality (a single deliberate flourish per product, if the adjectives allow).
2. **Fast and small.** Interfaces are tools; users have somewhere to be. Most transitions should be barely noticeable when done well.
3. **Consistent physics.** One easing family, one duration scale, one distance scale. Elements in the same product move the same way.
4. **Reduced motion is a first-class mode.** Honor `prefers-reduced-motion: reduce` by replacing movement with fades or nothing. Never leave a user with a page that requires motion to be usable.
5. **Never block.** Motion must not delay the user's next action. Interactive elements are usable during entrance animations.

## Duration and easing

| Kind | Duration | Easing |
|---|---|---|
| Micro (hover, toggle, color, focus ring) | 100–150 ms | ease-out |
| Small element enter/exit (tooltip, menu, toast) | 150–250 ms | enter: ease-out · exit: ease-in |
| Medium (drawer, modal, expand/collapse) | 250–350 ms | ease-in-out or custom `cubic-bezier(0.2, 0, 0, 1)` |
| Large (page/route transition, layout shift) | 300–500 ms | ease-in-out |
| Ambient / celebratory (rare) | 600–1200 ms | spring or custom |

- Entering elements decelerate (ease-out). Leaving elements accelerate (ease-in) and can be faster than entering.
- Larger distances get slightly longer durations, not much — 500 ms is already slow.
- Springs (Framer Motion `type: "spring"`, `stiffness 300–500, damping 30–40`) feel physical for drag, reorder, and toggles; avoid bouncy springs on serious products.
- Use `transform` and `opacity` only; animating `width`, `height`, `top`, `box-shadow` jank. For expand/collapse use a measured height with `overflow: hidden` or a grid-rows trick.

## What to animate, and how

### Feedback
- Button press: 1–2% scale down or a slight darken, 100 ms. Not both scale-up and shadow and color.
- Toggle/checkbox: state change 150 ms with the thumb sliding.
- Form success: a check icon fading in; the field border easing to success color.

### Orientation
- Menus and popovers originate from their trigger (transform-origin at the anchor) and travel 4–8px.
- Modals: fade + scale from 0.98 → 1; backdrop fades. Exit faster than enter.
- Drawers slide from their edge. Tabs: content crossfades or slides in the direction of the tab change.
- Route change: short crossfade (150–250 ms) or shared-element continuity where the framework supports it. A three-layer colored curtain wipe is a stylistic statement — use only for a portfolio/agency personality, never as a default.

### Attention
- One element at a time. A new item appears with a fade + 4px rise; a changed value flashes its background once and fades over 600 ms.
- Skeleton shimmer: slow (1.5–2 s), subtle, low contrast.
- Never pulse or bounce continuously to attract attention; it becomes noise within seconds.

### Lists
- Stagger children by 20–40 ms, capped at ~8 items, total under 400 ms. Staggering fifty rows is a wait, not a delight.

### Scroll
- Reveal-on-scroll: at most the hero and one or two key sections, one time, short distance (8–16px), fade in. Not every heading, card, and paragraph.
- Parallax: only for image-led storytelling; keep the offset small and disable on mobile and reduced-motion.
- Scroll hijacking / lerp smoothing (Lenis, Locomotive, custom RAF loops): changes how the user's own input behaves. Appropriate for narrative sites, long-form portfolios, and campaign pages where the scroll *is* the experience. Inappropriate for product UI, docs, dashboards, e-commerce — anywhere people are trying to get somewhere. If used: lerp ~0.08–0.12, native scroll for touch, respect reduced motion, keep anchor navigation working.
- Sticky headers: shrink or gain a hairline/shadow after scrolling, 150 ms, and get out of the way.

### Loading
- Under ~300 ms: show nothing (avoid flashes).
- 300 ms – 2 s: skeleton in the final layout.
- Longer or unknown: progress indicator with text ("Generating report…"), and let the rest of the UI stay interactive.
- Optimistic updates where the action is safe and reversible.

### Personality flourish
If the product's adjectives allow *one* signature motion — a logo mark that draws itself, a confetti burst on a milestone, a card that flips — do it once, well, and nowhere else. A single deliberate flourish reads as craft; the same flourish everywhere reads as a plugin.

## Tokens
Declare durations and easings as variables and reuse them:

```
--dur-fast: 120ms; --dur-base: 200ms; --dur-slow: 320ms;
--ease-out: cubic-bezier(0.16, 1, 0.3, 1);
--ease-in: cubic-bezier(0.7, 0, 0.84, 0);
--ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
```

## Quick checks
- Can I say which of orientation / feedback / attention / personality each animation serves?
- Are all durations from the scale and under ~350 ms except deliberate large transitions?
- Only `transform`/`opacity` animated?
- Is anything looping, bouncing, or floating without purpose?
- Does every section fade up on scroll? (If yes, cut most of them.)
- Does the page work with `prefers-reduced-motion`?
- Is scroll behavior native unless the site is explicitly narrative?
