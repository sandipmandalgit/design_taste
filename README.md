# design-taste

A Claude skill that teaches Claude to think like a designer *before* writing UI — so generated websites, apps, and components come out intentional instead of "vibe-coded".

## The problem

Ask an AI for a landing page and you get the same thing every time: centered hero, gradient headline, three feature cards with icons in colored circles, `rounded-2xl` everywhere, a purple-to-blue gradient, glow blobs, every section fading in on scroll. It is recognizable in one second. The individual choices aren't wrong; the problem is that nothing was chosen.

## What this skill does

It puts a designer's decision process in front of the code:

1. **Intent** — who, doing what, feeling how, noticing what first
2. **Structure** — real content, ranked hierarchy, all states
3. **Layout** — spacing scale, grouping by space, alignment, rhythm
4. **Typography** — one or two families, a scale, hierarchy from four levers
5. **Color** — neutrals first, one accent with a ramp, effects last
6. **Components** — one radius scale, one shadow set, one button system
7. **Motion** — purpose over spectacle, reduced-motion respected
8. **Review** — a five-dimension rubric (Clear · Efficient · Smart · Connected · Polished) and a vibe-coded tell list

Each step links to a reference file with the concrete rules and the reasons behind them.

## Structure

```
design-taste/
├── SKILL.md                            # process, hard rules, file map
├── references/
│   ├── anti-patterns.md                # the vibe-coded tells and their fixes
│   ├── hierarchy-layout-spacing.md
│   ├── typography.md
│   ├── color.md
│   ├── components-and-states.md
│   ├── motion.md
│   ├── ux-psychology.md                # the "why" — Norman, Krug, Laws of UX, cognitive load
│   ├── mobile.md
│   ├── review-rubric.md                # critique format + measurement (CES, SUS, …)
│   └── sources.md                      # attribution and further reading
└── evals/
    └── evals.json                      # test prompts
```

## Install

**Claude Code**
```bash
git clone https://github.com/sandipmandalgit/design-taste ~/.claude/skills/design_taste
```
or, if you use the skills CLI:
```bash
npx skills add sandipmandalatgit/design_taste
```

**Claude.ai** — upload the packaged `design-taste.skill` file (or the folder zipped) via Settings → Skills, or paste `SKILL.md` as a project instruction.

## When it triggers

Any request to build, design, restyle, review, or "make it look better" for a website, landing page, dashboard, web app, mobile app, component, or screen — React, Next.js, Tailwind, HTML/CSS, Flutter, SwiftUI, mockups, prototypes, artifacts. Also on words like UI, UX, layout, hierarchy, typography, palette, spacing, polish, design system, "generic", "looks like a template".

## Example prompts

- "Build a landing page for a B2B invoicing tool"
- "This dashboard looks like every other SaaS — make it feel designed"
- "Review this React component's UI and tell me what's wrong"
- "Design the home screen of a meditation app"
- "Pick a color palette and type scale for a legal-tech product"

## Sources

The skill is a distillation, written in its own words, of ideas from the design literature (Refactoring UI, Practical UI, Laws of UX, Norman, Krug, Müller-Brockmann, and others) and from the Terra design-system framework described in Tewari (2025). Full list in [`references/sources.md`](references/sources.md).

## Contributing

Additions most wanted: contemporary web-aesthetic critique, motion-craft writing, web typography specifics, token conventions, and concrete before/after case studies. Keep new material in the same shape: rule → why → quick check.

## License

MIT
