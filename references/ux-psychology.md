# UX psychology: why the rules work

Rules without reasons get applied mechanically and then broken at the wrong moment. This file is the "why" layer, distilled from the cognitive-psychology and usability literature (Norman, Krug, Johnson, Weinschenk, Yablonski, Lidwell et al.). Use it when designing flows, onboarding, decisions, forms, and errors — and when deciding whether a visual rule can be bent.

## How people actually use interfaces

- **They scan, they don't read.** Users look for the thing that matches what they want and click the first plausible candidate. Design for scanning: strong headings, front-loaded sentences, visible hierarchy, obvious clickables.
- **They satisfice.** They don't look for the best option, they take the first that seems good enough. So the primary path must be the most obvious thing on the screen, not merely present.
- **They muddle through.** People rarely form an accurate model of how a product works; they form a "good enough" story. Consistency makes their story keep working; surprises break it.
- **Attention is limited and expensive.** Every element competes. Anything that does not help the current task is a tax.
- **Perception is biased by goals and context.** Users see what they expect and what they're looking for. Put things where the mental model says they should be.

## Laws worth designing with

| Principle | What it says | Design consequence |
|---|---|---|
| Hick's law | Decision time grows with the number and complexity of options | Fewer choices per step; progressive disclosure; sensible defaults; group and rank options |
| Fitts's law | Time to hit a target depends on its size and distance | Big, close targets for primary actions; edges and corners are "infinite" targets; 44×44 minimum on touch |
| Miller / chunking | Working memory holds only a handful of items | Chunk information (phone numbers, cards, steps); keep visible what the user must compare |
| Gestalt: proximity, similarity, common region, continuity, closure | Things close together / alike / enclosed / aligned are perceived as groups | Spacing *is* grouping; consistent styling *is* categorization; alignment creates implied lines |
| Jakob's law | People expect your product to work like the ones they already use | Follow platform and category conventions for core mechanics; spend novelty on identity, not on navigation |
| Aesthetic–usability effect | Attractive things are perceived as easier to use and are forgiven more | Polish earns tolerance — but it cannot rescue a broken flow, and it makes usability problems harder to spot in testing |
| Von Restorff (isolation) effect | The one thing that differs is remembered | One accent, one emphasized element; if everything is emphasized, nothing is |
| Serial position effect | First and last items are remembered best | Put the most important nav items at the ends; end flows with a clear summary |
| Peak–end rule | Experiences are judged by their most intense moment and their end | Design one intentional high point and a deliberate ending (confirmation, summary, next step); smooth the worst moment (long form, error, wait) |
| Doherty threshold | Interaction feels fluid under ~400 ms | Keep feedback under 100 ms, transitions under 300 ms; mask longer waits with progress |
| Zeigarnik effect | Incomplete tasks stay in mind | Progress indicators and "you're 2 steps from done" pull people through |
| Goal-gradient | Effort increases as people near a goal | Show progress; front-load the hardest steps early or make them look small |
| Tesler's law (conservation of complexity) | Some complexity cannot be removed, only moved | Decide who carries it — the system (smart defaults, automation) or the user (choices). Prefer the system |
| Postel's law | Be liberal in what you accept, conservative in what you emit | Accept messy input (spaces in card numbers, any date format); output clean, consistent results |
| Occam's razor | Prefer the simplest solution with equal function | When two designs work, ship the one with fewer elements |

## Norman's vocabulary (use it when critiquing)

- **Affordance** — what an object lets you do. **Signifier** — the visible cue that tells you the affordance exists. Buttons must *look* pressable; links must *look* linked. Flat design removed signifiers and then re-invented them; keep them.
- **Mapping** — the relationship between controls and effects. Sliders that move the thing in the same direction, toggles next to what they toggle.
- **Feedback** — immediate, informative acknowledgment of every action. Silence after a click is a bug.
- **Conceptual model** — the story users build. Consistency and clear signifiers make the story accurate.
- **Constraints** — physical, logical, cultural limits that prevent errors. Disable what can't be done now; validate before submit; make destructive actions harder than safe ones.
- **Discoverability** — can users figure out what's possible and how? If the answer requires a tour, reconsider.
- **Gulf of execution / evaluation** — how hard is it to figure out what to do, and to tell whether it worked? Every screen should shrink both.

## Cognitive load

Three kinds; only one is useful:
- **Intrinsic** — the real difficulty of the task. Can't remove; can chunk and sequence.
- **Extraneous** — caused by the interface: clutter, inconsistency, unclear labels, unnecessary choices. Remove relentlessly.
- **Germane** — effort spent building understanding. Support it with clear structure and feedback.

Practical reducers: fewer elements per screen, consistent placement, plain language, defaults, showing rather than explaining, recognition over recall (show options, don't ask users to remember them), and progressive disclosure (basic first, advanced on demand).

## Emotion and trust

- Three levels of emotional response (Norman): **visceral** (first-glance look and feel), **behavioral** (does it work, does it feel competent), **reflective** (what using it says about me). Polish serves visceral; reliability and clarity serve behavioral; identity, values, and shareable moments serve reflective. A product needs all three, in that order of urgency.
- **Trust signals** are specific: real numbers, real names, clear pricing, honest error messages, visible security cues where they matter. Generic "trusted by 10,000+" rows are noise; a single named customer with a concrete result is signal.
- **Delight** is a small, well-timed surprise — a thoughtful empty state, a generous default, a moment of humor in copy. It is not confetti on every screen.

## Persuasion, and its limits

Social proof, scarcity, reciprocity, and commitment work. Use them honestly (real reviews, real stock levels, real deadlines). Dark patterns — confirmshaming, hidden costs, roach-motel cancellations, pre-checked upsells, fake urgency — damage trust and are increasingly illegal. If a pattern only works because the user didn't notice it, don't build it.

## Flows and onboarding

- Get to value fast. Ask only what is needed for the next step; collect the rest later or infer it.
- Show, don't tour. Empty states and inline hints beat modal walkthroughs.
- Adapt to stage: new users get guidance and fewer options; returning users get their stuff first; power users get density and shortcuts.
- Every multi-step flow shows where the user is, what's left, and how to go back without losing work.
- End well: confirm what happened, show the result, offer the obvious next action.

## Forms and errors

- Prevent before you detect: constrain input formats, provide defaults, disable impossible options.
- Validate inline, at the moment it helps (usually on blur), never on first keystroke.
- Error messages: what went wrong, why (if useful), how to fix it — in human language, near the problem, preserving the user's input.
- Make the safe action the default in any confirmation. Provide undo instead of "are you sure?" wherever possible.

## Measuring (from the Terra framework paper)

Good design principles are measurable. When the user can measure, suggest:
- **Customer Effort Score** — how easy was it to do X? Predicts retention better than satisfaction alone.
- **System Usability Scale** — standardized 10-item questionnaire; a benchmark you can track across versions.
- **Usability testing** — think-aloud sessions expose mental-model mismatches numbers miss.
- **Behavioral metrics** — funnels, drop-off points, time-on-task, rage clicks, error rates.
- Complementary: NPS, CSAT, expert heuristic review (e.g. PURE).

Pair each principle you claim (clear, efficient, connected…) with the metric that would show it working.

## Quick checks
- Can a first-time user tell what this screen is for in 3 seconds?
- Is the primary action the most obvious clickable thing?
- Does each screen ask for one decision at a time?
- Do controls look like what they do (signifiers present)?
- Does every action get immediate feedback?
- Is complexity on the system side wherever possible?
- Does the flow have a designed peak and a designed ending?
- Would any element only "work" if the user didn't notice it?
