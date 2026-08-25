# Typography

Typography carries most of the hierarchy and most of the personality. Two interfaces with the same layout and colors but different type decisions will read as two different products.

## Choosing typefaces

### One is enough
A single family with a good weight range covers 90% of interfaces. Add a second only with a clear job split:
- display (headlines) vs text (body)
- serif (editorial warmth, authority) vs sans (utility)
- mono (code, tabular numbers, technical voice) vs sans

Never three.

### Match the adjectives
Type has a voice. Map the personality words from the intent step to type qualities:

| Personality | Type qualities | Example directions |
|---|---|---|
| Precise, quiet, technical | Neutral grotesque, medium weights, tabular figures | Inter, IBM Plex Sans, Geist, Söhne-style |
| Warm, human, editorial | Humanist sans or a text serif, generous x-height | Source Serif, Fraunces, Newsreader, Nunito Sans |
| Bold, confident, modern | Tight display grotesque for headings, plain sans for body | Space Grotesk, Manrope, General Sans |
| Playful, friendly | Rounded or geometric sans, heavier weights | Outfit, DM Sans, Quicksand-style |
| Serious, institutional | Classic serif headings + restrained sans | Merriweather, Lora, Tiempos-style |
| Dense, fast, data | Compact sans with clear numerals, mono for values | Inter with `tabular-nums`, JetBrains Mono |

Inter/Roboto are not the problem; using them at defaults with no scale is. If the personality is anything other than "neutral utility", consider a face with character for headings.

### Practical filters
- Wide weight range (at least 400 / 500 / 600 / 700).
- Distinguishable `I l 1` and `O 0` for UI.
- Tabular figures available for data.
- Good rendering at small sizes (avoid thin weights below 16px).

## Scale

### Define it once
Pick 5–7 sizes and use only those. A workable default:

| Role | Size | Weight | Line-height | Tracking |
|---|---|---|---|---|
| Display | 48–64 | 600–700 | 1.05–1.15 | −0.02em |
| H1 | 32–40 | 600 | 1.15–1.2 | −0.015em |
| H2 | 24–28 | 600 | 1.25 | −0.01em |
| H3 | 18–20 | 600 | 1.35 | 0 |
| Body | 16 (15–18) | 400 | 1.5–1.65 | 0 |
| Small | 14 | 400–500 | 1.45 | 0 |
| Caption / label | 12–13 | 500 | 1.4 | 0 to +0.02em |

Avoid mathematically "pure" ratios that produce awkward sizes (e.g. 1.333 → 21.3px). Round to whole pixels and hand-tune.

### Hierarchy uses four levers together
Size, weight, color, spacing. Two adjacent levels should differ in at least two of these. H2 at 24/600/dark vs body at 16/400/mid is clear; 18/400 vs 16/400 is not.

## Setting text

### Line length
45–75 characters, ~65 ideal. Enforce with a max-width on prose containers (`max-width: 65ch`). Wider than this and the eye loses the return path; narrower and it stutters.

### Line-height is proportional
Big text wants tight leading; small text wants loose leading. Long lines want more leading than short ones. Rule of thumb: display 1.1, headings 1.2–1.3, body 1.5–1.65, small text 1.4–1.5.

### Letter-spacing
- Tighten large headings slightly (−1% to −2.5%). The gaps between letters look bigger at scale.
- Never track out lowercase body text.
- Tracking out *small caps / uppercase labels* (+4% to +8%) is correct — uppercase letters need the air.

### Alignment
- Left-align. Rag-right is the most readable for Latin scripts.
- Center only single lines or very short blocks.
- Never justify on the web (rivers, no hyphenation control).
- Align by baseline when mixing sizes on a line; vertical-center looks off.

### Text color
Three levels are enough: primary (near-black, ~90% contrast), secondary (~60–65%), tertiary/placeholder (~40–45%, must still pass 3:1 for large text and 4.5:1 for body). Use lightness or opacity of the same hue family, not a different gray.

On colored backgrounds, do not use gray for secondary text — it looks dirty. Use a lighter tint of the background hue or white at reduced opacity.

### Links
Inside prose, links need a visible cue (underline or clearly distinct color). Inside navigation and UI, links do not need underlines or a special color; treat them as UI text with hover/focus states.

### Numbers
Use `font-variant-numeric: tabular-nums` in tables, timers, and anything that updates. Large key figures can be a size or two above H2 and lighter in weight than expected — big numbers at 700 weight look heavy.

## Headings and copy structure

- One H1 per page. Do not skip levels (H2 → H4).
- Section headings left-aligned above their content, with more space above than below (the heading belongs to what follows).
- A heading + one-sentence intro is a fine pattern; a heading + generic subtitle on every section is a tell. Some sections need no intro.
- Sentence case for UI text (buttons, labels, headings) unless brand voice says otherwise. Title Case Everywhere Reads As Stiff.

## Responsive type
Scale display and H1 down 25–35% on small screens; body stays 16px minimum. Fluid sizing (`clamp()`) is good for display; keep body fixed for predictability.

## Quick checks
- One or two families, with a stated job for each?
- Every size used comes from the scale?
- Display/headings tight, body loose?
- Prose ≤ 75ch?
- Three text colors, all passing contrast?
- No gray text on colored backgrounds?
- Left-aligned multi-line text?
- Tabular figures where numbers align?
