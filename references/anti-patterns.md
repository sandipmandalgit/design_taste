# Anti-patterns: the vibe-coded tells

This is the list of things that make an interface read as "generated". Each entry has the tell, why it happens, and the fix. Run through it before delivering any UI. Aim to fail none of these; if a pattern is kept on purpose, be able to say why in one sentence.

## Layout and structure

| Tell | Why it happens | Fix |
|---|---|---|
| Centered hero → 3-column feature grid → testimonial row → CTA band, every time | Pattern-matching "what landing pages have" | Design from the product's actual argument. Vary composition: split layouts, asymmetric grids, a single wide image, a text-only section, a table of real numbers. |
| Every section is heading + one-line subtitle + card grid | No content hierarchy beyond "section" | Let sections differ in density and width. One section can be a single sentence; another a dense comparison. |
| Everything centered | Centering feels "safe" | Left-align body content and lists. Center only short symmetrical things. |
| Cards for everything, including a single paragraph | Card = "designed" in the training set | Use cards only for repeatable, comparable units. Otherwise use space and typography. |
| Uniform full-width containers with `max-w-7xl` and edge-to-edge sparse content | Not deciding a measure | Set content widths per section: prose ~65ch, forms ~480px, dashboards wide. |
| Equal visual weight on everything | No ranking done | Rank primary/secondary/tertiary and make the difference obvious. |
| Icon-in-a-colored-circle above each feature heading | Cheapest way to look "designed" | Remove unless the icon carries meaning; if kept, drop the circle and align icon with the text baseline. |
| Placeholder content: lorem ipsum, "Feature One", "John Doe", "Lorem Corp" | Layout designed before content | Write real or realistic content first; the layout follows. |
| Stats row of "10K+ users · 99% uptime · 24/7 support" | Template reflex | Only show numbers that are true and specific. Otherwise delete the row. |

## Color

| Tell | Why it happens | Fix |
|---|---|---|
| Purple/indigo → blue or pink gradient (on text, buttons, backgrounds) | The 2021–2024 default | Pick one accent that matches the personality. If a gradient is used, use it once, with two neighboring hues, never on body-level text. |
| Gradient text on headlines | Looks "premium" in isolation | Solid color headline. Emphasis comes from size, weight, and space. |
| Glow / blur blobs behind hero or cards | Fills empty space without deciding anything | Decide what the space is for. Use a subtle background shift, an image, or leave it empty on purpose. |
| Glassmorphism (`backdrop-blur` + translucent white) on cards, nav, modals | Trend layering | Reserve for overlays that genuinely sit above rich content. Opaque surfaces elsewhere. |
| Pure gray text (`#9CA3AF`, `#6B7280`) with no relationship to the accent | Default Tailwind grays | Tint neutrals toward the accent hue or a chosen temperature. |
| Gray text on colored backgrounds | Trying to de-emphasize on a colored surface | Use a lighter tint of the background color, or reduce opacity of white, not gray. |
| Dark mode as inverted grays with neon accents | "Dark = techy" | Dark surfaces are layered (bg < surface < raised), text is off-white, accents are desaturated slightly. |
| Semantic colors missing or improvised per component | No system defined | Define success/warning/danger/info shade ranges once. |

## Typography

| Tell | Why it happens | Fix |
|---|---|---|
| Inter/Roboto at default weights everywhere | Safe default | Inter is fine; the problem is no scale and no contrast. Define a scale, use weight ranges (e.g. 400/500/600) with intent, or choose a typeface with character that matches the adjectives. |
| Giant hero text with `font-extrabold tracking-tight` on every heading | Copying one look | Tighten only large display text; body and subheads use normal tracking and medium weight. |
| Hierarchy by bold alone | Easiest lever | Use size + weight + color + spacing together. |
| Long paragraphs at full container width | No measure set | 45–75 characters per line. |
| All-caps labels with wide tracking on everything | Looks "designed" | Use sparingly for tiny labels/eyebrows; never for body or multi-line text. |
| Same line-height for headings and body | One `leading` value | Headings tight, body loose. |
| Text centered over multiple lines | Centered hero habit | Left-align multi-line text. |

## Components and surfaces

| Tell | Why it happens | Fix |
|---|---|---|
| `rounded-2xl` / `rounded-3xl` on every element | The single strongest tell | Choose a radius scale tied to the personality and apply it by element size: small controls 4–6px, cards 8–12px, only very large surfaces larger. Sharp corners are a legitimate choice. |
| Card = border + shadow + ring + hover lift + gradient border | Stacking every affordance | One surface treatment. Either a hairline border or a soft shadow, not both. |
| Shadows that are big, black, and identical on every element | Default `shadow-lg` | Small, tinted, elevation-based. Most elements need none. |
| Buttons with different heights/paddings across the page | Ad-hoc styling | One button system: fixed heights, padding, font size, radius. |
| Multiple primary buttons in view | No single action decided | One filled primary; the rest are outline/ghost/text. |
| Pill-shaped everything (badges, buttons, inputs, tabs) | Rounded reflex | Pills for tags/badges only, or as a consistent whole-system choice. |
| Emoji as icons in production UI | Fast "personality" | Use an icon set with one stroke weight. Emoji only for consumer/playful products, consistently. |
| Empty state = nothing or "No data" | Never designed | Guidance + one action. |
| Generic avatar circles with initials for fake people | Placeholder habit | Real content or none. |

## Motion

| Tell | Why it happens | Fix |
|---|---|---|
| Every section fades/slides up on scroll | Framer Motion default | Reveal at most the hero and one key moment. Static is fine. |
| Hover lift + scale + shadow on every card | Copied micro-interaction | Subtle state change (background/border shift) unless the card is genuinely a big tappable object. |
| Smooth-scroll hijacking (lerp/Lenis) on a normal product site | "Premium agency feel" | Native scroll. Reserve hijacking for narrative/portfolio sites and always honor reduced-motion. |
| Animated gradient backgrounds, floating blobs, particle fields | Filling space | Remove. |
| Spinner for every loading state | Default | Skeletons for layout, inline progress for actions, optimistic UI where safe. |

## Copy

| Tell | Why it happens | Fix |
|---|---|---|
| "Unlock the power of…", "Seamless", "Elevate", "Next-generation", "Supercharge" | Marketing-token averaging | Say what it does, for whom, in plain words. One concrete claim beats three abstract ones. |
| Feature titles that are adjectives ("Fast. Secure. Scalable.") | Same | Titles that are outcomes or verbs. |
| Buttons that say "Get Started" / "Learn More" everywhere | No decided action | Label the actual action: "Create a workspace", "See pricing", "Download the report". |
| Error text: "Something went wrong" | Never designed | What happened + how to fix it + what to do next. |

## The two-second test

Look at the output as a thumbnail. If, at thumbnail size, it could be any of a thousand SaaS sites — it is not done yet. Something should be specific: the type, the composition, the color world, the way content is arranged. Pick one of those to be distinctive and keep the rest disciplined.
