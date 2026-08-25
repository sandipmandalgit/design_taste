# Hierarchy, layout and spacing

Hierarchy is the design. Layout and spacing are how hierarchy becomes visible. Most "it looks generic" complaints are hierarchy failures: nothing is clearly first, so the eye wanders and the page reads as noise.

## Hierarchy

### Rank before you style
For every screen, sort elements into three tiers:
- **Primary** — the one thing the screen exists for (the main content, the key number, the main action).
- **Secondary** — the few things that support the primary (context, filters, secondary action).
- **Tertiary** — everything else (metadata, timestamps, helper text, footers).

If the sort is hard, the screen is doing too much. Split it or cut.

### Emphasize by de-emphasizing
The instinct is to make the important thing bigger and bolder. It works once; after that everything is big and bold. The better lever is to *quiet* the supporting elements: lighter color, smaller size, regular weight, more distance. The primary then stands out without shouting.

### Levers, in order of subtlety
1. Position (top-left / first in reading order wins)
2. Space around it (isolation = importance)
3. Color contrast (dark vs mid vs light text)
4. Weight
5. Size
6. Decoration (borders, backgrounds, icons) — last resort

Use several small levers rather than one big one. Size alone forces huge headings; weight alone forces bold everywhere.

### Values over labels
Data screens: the number is the content, the label is a caption. Render the value large and dark, the label small and light. "Revenue" should never be more prominent than "$48,200".

### Visual vs document hierarchy
An `<h2>` does not have to be big. Semantic order is for the document and assistive tech; visual weight is for the reader. Style by role in the visual hierarchy, keep the DOM semantic.

### Balance weight and contrast
Heavy elements (icons, bold text, filled shapes) need lower contrast to sit at the same level as lighter text. A solid black icon next to gray text looks heavier than intended — soften the icon instead of darkening the text.

## Spacing

### One scale, used strictly
Choose a base unit (4px is the common one) and a limited progression, e.g. `4 8 12 16 24 32 48 64 96 128`. Every margin, padding, and gap comes from this list. The point is not the numbers; it is that the eye reads consistency as intention.

### Relationship-based spacing
Space communicates grouping (Gestalt proximity). The rule that makes layouts feel resolved:

> gap *between* groups ≥ 2 × gap *within* a group

A form with 8px between label and input and 24px between fields reads clearly. 12px and 16px reads as mush.

### Start with too much space
Add space generously, then reduce until it feels right. The reverse (start cramped, add space) almost never lands. Dense is a valid personality (data tools, dashboards) but density must be uniform and deliberate.

### Ambiguous spacing
If an element sits at equal distance between two things, it belongs to neither. Move it clearly toward its group.

### Larger elements need more space
Padding and gaps scale with type size. A 48px heading needs more breathing room below it than a 16px label. Card padding scales with card size — small cards ~16px, large panels ~32px.

### Optical alignment
Text with descenders, icons, and rounded shapes sit differently from their bounding boxes. Nudge by 1–2px when something looks off even though the numbers are "correct". Trust the eye over the ruler for final alignment.

## Layout

### Content width
Set widths by content type, not by the container:
- Reading text: 60–75 characters (~600–720px at 16–18px)
- Forms: 400–520px
- Cards in a grid: 280–360px each
- Data tables / dashboards: as wide as the data needs

A page can have several widths. A hero at 900px, prose at 680px, and a full-width table on the same page is fine — as long as the left edge stays consistent.

### Grids
Use a grid for alignment, not as a cage. Equal 12-column splits produce equal, boring sections. Asymmetry (7/5, 8/4, 2/3 + 1/3) with one dominant area reads as composed. Müller-Brockmann's discipline: the grid governs the *edges* elements align to; what fills them can vary in size.

### Alignment
- Left-align text. Strong left edge = fast scanning.
- Center only symmetrical, short elements: a single hero line, a single centered button, a logo.
- Align numbers right in tables; align text left; align headings with their content.
- Baseline-align mixed sizes (a big number with a small unit), not vertical-center.

### Rhythm across a page
Alternate to keep attention:
- Wide / narrow
- Dense / sparse
- Image-led / text-led
- Light surface / tinted surface

Three identical "heading + subtitle + grid" sections in a row is the template look regardless of styling.

### Don't fill the screen
Empty space is not waste; it is emphasis. A short page with three well-spaced statements is stronger than a long page with twelve sections nobody reads.

### Responsive
Layouts reflow; they do not shrink. At narrow widths: stack in priority order (not DOM order if they differ), collapse secondary content, keep the primary action reachable. Scale type down slightly (e.g. 48 → 32 for display) and increase touch targets. See `mobile.md`.

## Quick checks
- Can I name the first, second, and third thing the eye should hit? Does the layout agree?
- Are all spacing values from the scale?
- Is between-group spacing clearly larger than within-group?
- Is any text wider than ~75 characters?
- Does anything float at ambiguous distance from its neighbors?
- Do adjacent sections differ in composition, or are they the same card grid again?
