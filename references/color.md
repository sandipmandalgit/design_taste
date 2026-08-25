# Color

Color is a system with a small number of roles. Most generated UIs fail here not by picking ugly colors but by never defining roles: the accent appears in ten shades chosen ad hoc, grays come from a default palette that has no relationship to the brand, and gradients paper over the gap.

## Order of operations

1. **Neutrals first.** Background, one or two surface levels, borders, and three text levels. This is 80–90% of what users see.
2. **One accent.** It carries personality and marks interactive/primary elements.
3. **Semantic colors.** Success, warning, danger, info — each with its own tint range.
4. **Effects last, if ever.** Gradients, glows, blur.

## Neutrals

### Tint them
Pure gray reads as inert. Shift neutrals a few degrees toward the accent hue or toward a temperature that matches the personality (warm: slightly yellow/red; cool: slightly blue). In HSL this is a hue set to the accent's hue with saturation 3–10% across the gray ramp. In OKLCH, a small chroma (0.005–0.02) at the accent's hue.

### Levels
Light mode:
- Background (page): near-white, not pure white if the personality is warm (`#FAFAF9`-style)
- Surface (cards, panels): white or one step lighter than background
- Raised (popovers, modals): white + shadow
- Border: ~10–15% darker than surface; a hairline, not a frame
- Text: primary ~L 15%, secondary ~L 45%, tertiary ~L 60%

Dark mode is not inverted light mode. Use layered dark surfaces (background darkest, surfaces progressively lighter: e.g. L 8% → 12% → 16%), off-white text (not pure white, ~L 90%), and slightly desaturated accents so they don't vibrate. Shadows barely work on dark; use surface lightness to show elevation.

## Accent

### Choose by personality, then by category
| Wants to feel | Typical hue families | Notes |
|---|---|---|
| Trustworthy, stable | Blue, deep teal, navy | Finance/health convention; differentiate through the neutral warmth and type instead |
| Energetic, bold | Orange, red-orange, saturated green | Use sparingly at full strength; lots of tint |
| Calm, premium | Muted green, slate, deep plum, warm black | Low saturation, high contrast through lightness |
| Playful, friendly | Yellow, coral, bright green, sky blue | Pair with rounder shapes and heavier type |
| Editorial, serious | Near-black accent, oxblood, forest | Let type do the work; accent is a single rule or link color |

Purple-to-blue gradients are not a personality; they are the absence of one.

### Define the full ramp
For the accent and each semantic color, define ~9–10 steps from very light tint to very dark shade (50 → 900 in the common naming). You will need:
- 50–100: tinted backgrounds, hover on ghost buttons, selected rows
- 200–300: borders, subtle badges
- 500–600: primary buttons, links, icons
- 700–800: text on light tints, pressed states
- 900: dark text on the lightest tints

Do not let lightness kill saturation: as a color gets lighter or darker, nudge saturation up so mid-tones don't look washed out. Rotate hue slightly toward yellow when lightening and toward blue/red when darkening for more natural ramps.

### Where the accent goes
Primary action, links, focus rings, selected/active states, key data marks, and *maybe* one brand moment (logo, a hero treatment). Not headings, not borders on every card, not icon backgrounds on every feature. If more than ~10% of the screen is accent, it has stopped being an accent.

## Semantic colors
Define once: success (green), warning (amber), danger (red), info (blue or the accent). Each gets a light tint for backgrounds, a mid for icons/borders, and a dark for text on tint. Do not reinvent them per component. Danger should be reserved for destructive/irreversible actions and errors — overuse trains users to ignore it.

Never rely on color alone: pair with an icon, a label, or a shape.

## Contrast and accessibility
- Body text ≥ 4.5:1; large text (≥ 24px or ≥ 19px bold) and UI components ≥ 3:1.
- Accessible does not mean flat: dark accent text on a light accent tint often passes where white-on-mid-accent fails, and it looks richer.
- Focus rings: visible, 2px, offset, using the accent or a high-contrast color — never removed.
- Check the *tertiary* text; it is the one that usually fails.

## Effects

### Gradients
A gradient is a choice about light and mood. Rules if used:
- Two hues that are neighbors on the wheel (blue → teal, orange → pink), not opposites.
- Adjust the midpoint so the middle doesn't go muddy.
- One instance on the page — a hero background, a single brand element. Never on body text, never on every button.

### Glow and blur
Glow implies a light source and luxury. It only works with a dark surface, a single subject, and restraint. Glowing blobs behind a light-mode SaaS hero are the most common vibe-coded marker after `rounded-2xl`.

### Glassmorphism
Translucent blur belongs on elements that float above rich, moving content (a nav over a photo hero, a media overlay). On a white page over white cards it is invisible cost.

## Working method
- Author in HSL or OKLCH, not hex, so ramps and tints are reasoned rather than eyedropped.
- Store as tokens: `--bg`, `--surface`, `--border`, `--text`, `--text-muted`, `--accent`, `--accent-hover`, `--accent-subtle`, `--success`… and reference tokens in components, never raw values.
- Test the palette on a real screen with real content before committing. A palette that looks good as swatches can fail in context.

## Quick checks
- Neutrals tinted, not pure gray?
- One accent, with a defined ramp?
- Accent covers ≤ ~10% of the screen and appears only on meaningful elements?
- Semantic colors defined once?
- All three text levels pass contrast?
- Every gradient/glow/blur justified by the personality and used once?
- Dark mode layered, not inverted?
