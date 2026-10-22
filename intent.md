# intent.md

## Decision

Bottleneck selected: **reviewer activation**. This is the step from an invited waitlist member to a first qualified review.

## Why this problem

The platform has one job. It must turn a public disclosure into useful questions and reviews that lead to qualified follow-up. Every stage upstream feeds that output. Every stage downstream depends on it. If few qualified reviews exist, follow-up has nothing to convert, and more waitlist volume only adds cost.

## Bottlenecks compared

Scores run from 1 to 5. For effort, 5 means low effort.

| Bottleneck | What breaks | User value | Business conversion | Effort | Confidence | Weighted score |
|---|---|---|---|---|---|---|
| Waitlist | Signups grow, nothing downstream improves | 2 | 2 | 4 | 4 | 2.7 |
| Disclosure reading | People open the document and leave | 3 | 3 | 3 | 3 | 3.0 |
| Reviewer activation | Readers do not submit a useful review | 4 | 5 | 3 | 4 | 4.2 |
| Qualified follow-up | Reviews do not become inquiries | 3 | 5 | 2 | 2 | 3.35 |

Weights: user value 30%, business conversion 35%, effort 15%, confidence 20%.

Example, reviewer activation: (0.30 x 4) + (0.35 x 5) + (0.15 x 3) + (0.20 x 4) = 4.2.

Confidence measures how well I understand the mechanism and can measure it. It does not measure how sure I am of the result.

## Sensitivity check

With equal weights of 25% each, the scores become: waitlist 3.0, disclosure reading 3.0, reviewer activation 4.0, qualified follow-up 3.0. Reviewer activation leads under both weightings, so the choice does not depend on my weights.

## Why I rejected the others

- **Waitlist.** It adds volume to a funnel that has not been shown to convert. Signups and wallet connections would rise and tell us nothing about qualified outcomes.
- **Disclosure reading.** The leak is real, but reading time is a weak proxy. A person can read for four minutes and submit nothing useful. I treat it as an input metric inside the chosen problem.
- **Qualified follow-up.** It has the highest value per unit and the lowest confidence. It cannot be tested until enough qualified reviews exist. It is the next problem after this one.

## Hypothesis

Invited participants who finish a meaningful read stall at the blank page. Three changes should raise the share of invited participants who submit a qualified review:

1. A structured prompt tied to one disclosure section.
2. A stated time cost for the task.
3. Credit awarded for quality, not for volume.

Wallet connection plays no part in this lever.

## What I could be wrong about

- The scores are judgement calls, not measurements. The case gives no real funnel data, so the prototype uses synthetic records and labels every rate as an assumption.
- I assume the main loss sits between meaningful read and submission. If the simulation shows a larger loss before the read, I move to disclosure reading.
- Credit can attract low-effort submissions. The participation rules add a quality gate, duplicate checks and a cap before any credit is awarded.

## How I prioritise from here

Rank work by expected qualified reviews per unit of effort. End any test when its stop rule fires, even if the headline number looks good.
