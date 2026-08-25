# Components, surfaces and states

Components are where a system either holds or falls apart. Every decision here should be made once, written down as a token or a rule, and then applied without exception. Inconsistency is the fastest way to look generated; consistency is the cheapest way to look designed.

## Surfaces: radius, shadow, border

### Radius is a voice
| Radius | Reads as |
|---|---|
| 0–2px | Precise, editorial, technical, serious |
| 4–6px | Neutral, professional, most product UI |
| 8–12px | Friendly, modern, approachable |
| 16px+ | Playful, consumer, soft |
| Full pill | Casual; fine for tags/badges, a whole-system choice for buttons |

Pick a scale of 2–3 values tied to the personality and apply by element size: small controls get the smallest, cards the middle, only very large containers the largest. Nested radii: inner radius = outer radius − padding, so corners stay concentric.

`rounded-2xl` on inputs, buttons, cards, badges, and images alike is the single strongest generated-UI marker. If the personality is not "soft and playful", it is wrong.

### Elevation with one light source
Imagine light from above. Higher elements cast longer, softer shadows; lower ones barely any. Define 3–4 levels:
- Flat (most things): no shadow, maybe a hairline border
- Raised (cards that are interactive, dropdowns): `0 1px 2px rgba(0,0,0,.06), 0 1px 3px rgba(0,0,0,.08)`
- Floating (popovers, menus): `0 4px 12px rgba(0,0,0,.08), 0 1px 3px rgba(0,0,0,.06)`
- Overlay (modals): `0 16px 40px rgba(0,0,0,.16)`

Two-part shadows (a tight dark one + a wide soft one) look more natural than one big blur. Tint the shadow toward the surface/accent hue on colored backgrounds; pure black shadow on a blue surface looks dirty. On dark mode, prefer surface lightness over shadows.

### Fewer borders
A border is the loudest way to separate. Try in this order: space → background shift → hairline → border with shadow. A card with border + shadow + hover ring is over-specified. Tables and forms often need only horizontal hairlines.

### Backgrounds as structure
Alternating section backgrounds (white / warm-gray / white) give rhythm without lines. Keep the shift subtle (2–4% lightness). A tinted accent background (accent-50) for one key section is a good single emphasis.

## Buttons

- **One** primary (filled accent) per view. Secondary is outline or accent-tint; tertiary is text-only. Destructive is danger-colored and never the default.
- Fixed heights per size (e.g. 32 / 40 / 48), consistent horizontal padding (~1.5× vertical), font size and weight from the type scale, one radius.
- Label = the action ("Save changes", "Send invite", "Delete project"), not "Submit" / "OK" / "Get Started".
- States: default, hover (slight darken or lift, not both), active/pressed, focus-visible (ring), disabled (reduced opacity + no pointer), loading (spinner replaces label, width preserved).
- Icons in buttons: leading, 16–20px, aligned to the text's optical center; never icon-only without an accessible label.

## Forms

- Label above the field, left-aligned, small but clearly readable. Placeholder is a hint, never the label.
- Field height matches button height so rows align. Border 1px neutral; focus adds accent border + ring.
- Group related fields with spacing, not boxes. Between-field gap ≥ 2× label-to-field gap.
- Inline validation on blur, error in danger color with an icon and a fix ("Email needs an @"). Never only red border.
- Helper text below the field in tertiary color, only when it prevents an error.
- One clear submit; secondary actions quieter and to the left or below.
- Choose the right control: radio (2–5 exclusive), select (6+), checkbox (multiple), switch (immediate effect), segmented control (2–4 view modes), slider (approximate value only).

## Cards

Cards are for repeatable, comparable units (products, projects, people). Not for wrapping every paragraph.
- Consistent internal padding from the spacing scale (16 / 20 / 24 by size).
- Internal hierarchy: one primary line, one secondary line, metadata tertiary. Not four equal lines.
- Whole card is the click target if it navigates; otherwise a clear action inside.
- Image aspect ratios fixed (16:9, 4:3, 1:1) and cropped with `object-fit: cover`.

## Navigation

- Primary nav: 4–7 items, left-aligned logo, one primary CTA at the right end.
- Current location is always visible (active state).
- Sidebar apps: collapsible, icons + labels, grouped with small section headers, active item with tint background + accent text (not a filled accent block).
- Mobile: tab bar (3–5 items) for top-level destinations; hamburger only for secondary.

## Tables and data

- Left-align text, right-align numbers, tabular figures, header row slightly heavier and muted.
- Horizontal hairlines only; no vertical rules. Row hover tint for scanning.
- Row height 40–48px; dense mode 32px for expert tools.
- Sort indicator on the active column only. Truncate with ellipsis + tooltip, never wrap to three lines.
- Empty and loading states inside the table body, not replacing the whole component.

## Icons and imagery

- One icon set, one stroke weight, one size per context (16 for inline, 20 for buttons/nav, 24 for standalone). Mixing outline and filled sets is a tell.
- Icons accompany labels; icon-only needs a tooltip and an `aria-label`.
- Illustrations: one style across the product. Generic 3D blob illustrations and "people holding giant pencils" are as recognizable as gradients.
- Photos: consistent treatment (same crop, same tone). Text over images needs a scrim or a solid panel, not a hope.

## States (design all of them)

| State | Must include |
|---|---|
| Empty | What this area is for, why it's empty, one action to fill it. Optional small illustration. Never just "No data". |
| Loading | Skeleton that matches the final layout for pages/lists; inline spinner for actions; progress bar for known-duration tasks. Keep layout stable (no jump when content arrives). |
| Error | What happened, in plain words; how to fix or retry; keep the user's input. Inline near the cause for fields; banner for page-level. |
| Success | Confirm what was done, show the result, offer the next step. Toast for minor, inline or full-state for major. |
| Partial / offline | Show what is available, mark what isn't, don't block everything. |
| Disabled | Visibly reduced (opacity ~50%), cursor not-allowed, ideally a hint why. |
| Focus | Always visible ring; matches accent; 2px with offset. |
| Hover | One subtle change (bg, border, or color) — not scale + lift + shadow + color together. |

## Feedback and microcopy

- Confirm destructive actions with the specific consequence ("Delete 'Q3 report' and its 14 comments?"), and make the safe option the default.
- Toasts: short, top-right or bottom-center, auto-dismiss 4–6s, with undo when possible.
- Errors talk like a person: "We couldn't save your changes — check your connection and try again."

## Tokens: write the system down

Before building components, declare the tokens (CSS variables or theme object):

```
spacing: 4 8 12 16 24 32 48 64 96
radius: sm 4, md 8, lg 12 (adjust to personality)
shadow: raised, floating, overlay
font: family, sizes (display…caption), weights, line-heights
color: bg, surface, surface-raised, border, text, text-muted, text-subtle,
       accent(-hover, -subtle, -text), success/warning/danger/info(-bg, -fg)
control heights: sm 32, md 40, lg 48
```

Then every component references tokens. If a value appears that isn't a token, either add it deliberately or fix the component.

## Quick checks
- One radius scale, applied by size?
- Shadows from a defined elevation set, tinted, mostly absent?
- Each card/panel uses one separation method?
- One primary button per view; all buttons share heights/padding?
- Forms: labels above, inline validation, one submit?
- Single icon set and weight?
- All eight states present for every dynamic component?
