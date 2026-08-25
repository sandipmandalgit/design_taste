# Mobile

A phone screen is a different medium: one hand, thumb reach, glanceable attention, interruptions, and no hover. Mobile design is re-prioritization, not reduction. Everything in the other references still applies; this file covers what changes.

## Structure

- **One primary action per screen, in the thumb zone** (bottom third). Navigation and destructive actions can live at the top; the thing people do most lives at the bottom.
- **Reading order = priority order.** Reflow so the most important content is first, even if the desktop layout had it in a sidebar. Don't just stack the desktop DOM.
- **Progressive disclosure.** Show the essentials; put detail behind a tap, a sheet, or an expand. Fewer things per screen than you think.
- **Top-level nav in a tab bar** (3–5 items, icon + label). Hamburger menus hide navigation; use them only for secondary destinations.
- **Sheets over modals.** Bottom sheets keep context and are reachable; full-screen modals for flows that need focus; center dialogs only for confirmations.
- **Design the back path.** Every screen answers "where am I" and "how do I go back" without losing state.

## Touch

- Minimum target 44×44pt (48dp Android), 8px+ between targets. Small icons need big invisible hit areas.
- No hover states. Use pressed states (100 ms tint change) and explicit affordances (chevrons, underlines, button shapes).
- Gestures are shortcuts, not the only way. Swipe-to-delete needs a visible alternative.
- Keep frequently used controls away from the screen edges where system gestures live; respect safe areas (notch, home indicator).
- Prefer selection over typing: chips, segmented controls, pickers, autocomplete. Text input is expensive on glass; reserve it for search and precise data.
- Right input type for the field (`email`, `tel`, `numeric`, `url`) so the correct keyboard appears.

## Layout and type

- Baseline viewport 360–390px wide. Design there first; larger phones inherit.
- Horizontal padding 16–20px; card padding 16px; section gaps 24–32px. Same spacing scale as desktop, smaller steps.
- Body 16px minimum (iOS zooms inputs under 16px). Display sizes ~65–75% of desktop. Line-height stays generous; line length is naturally short.
- Single-column by default. Two columns only for small equal units (a grid of tiles); never for text.
- Key figures and status get the top of the screen at a glance — a header that shows the one number that matters.
- Sticky bottom action bar for the primary CTA on long screens (with safe-area inset). Avoid sticky headers that eat 20% of the viewport.
- Images: fixed aspect ratios, lazy-loaded, sized for the device. A hero image should not push the primary action below the fold.

## Personality on a small screen

- Rounded corners read larger on phones; a 12px radius on a 360px screen is already soft. Scale radii down slightly from desktop.
- Shadows are less visible on small screens and cost battery on blur-heavy pages; prefer surface color shifts and hairlines.
- Color surfaces (a tinted header, a card block) work well for structure since there is little room for whitespace.
- Motion: shorter (100–250 ms), fewer, and never on scroll. Pull-to-refresh, sheet slides, and tab crossfades are the whole vocabulary most apps need.

## States on mobile

- Offline and slow-network are normal, not edge cases. Cache the last state, show it with a "last updated" note, and queue actions.
- Loading skeletons matching the layout; never a blank screen with a spinner for more than a moment.
- Empty states include the primary action; on mobile they are often the onboarding.
- Errors inline near the field, and the keyboard must not cover them.

## Platform conventions

Follow the platform for core mechanics (navigation patterns, sheet behavior, back gesture, system pickers, share sheets). Spend distinctiveness on type, color, content, and the one signature interaction — not on reinventing the tab bar. Users switch between dozens of apps a day; the ones that feel native are the ones they trust.

- iOS: large title that collapses, tab bar, swipe-back from the left edge, `.sheet` presentation, SF Symbols weight matching text.
- Android: Material 3 navigation bar, predictive back, FAB only for a single creation action, elevation via tonal surfaces.
- Cross-platform frameworks (React Native, Flutter): still honor each platform's navigation and controls; share visual identity, not mechanics.

## Quick checks
- Primary action in the thumb zone?
- Reading order equals priority order?
- Every target ≥ 44pt, with spacing between?
- Body ≥ 16px, single column for text?
- Input replaced by selection wherever possible?
- Offline/slow state designed?
- Does it follow platform mechanics and spend novelty on identity?
