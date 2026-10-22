# Weekly decision memo: week 1, simulation read-out

Data: 12 synthetic records in `reviewer-activation-prototype.html`. Every number below is synthetic and shows the method only.

## Decision

Run the 14-day pilot with step-level events live. Do not scale the section prompt yet. Do not claim the simulation supports the bottleneck choice.

## What the simulation shows

| Step | Reached | Step conversion | Lost |
|---|---|---|---|
| S1 Invited | 12 | n/a | n/a |
| S2 Opened | 11 | 91.7% | 1 |
| S3 Meaningful read | 8 | 72.7% | 3 |
| S4 Submitted | 7 | 87.5% | 1 |
| S5 Qualified | 5 | 71.4% | 2 |
| S6 Qualified follow-up | 3 | 60.0% | 2 |

Primary metric: 5 of 12 invited participants produced a qualified review (41.7%).

Side metrics, kept apart: 4 of 12 wallets connected (33.3%), 3 acknowledgements recorded, 1 failed. Two of the five qualified reviewers had no wallet, so declining cost them nothing.

## What the simulation cannot show

The largest loss sits at S2 to S3 (3 participants), not at S3 to S4 (1 participant). That contradicts the hypothesis in `intent.md`.

I wrote the 12 records to exercise every path (a decliner, a duplicate, a failed acknowledgement), not to estimate where participants leave. They cannot confirm or reject the bottleneck. The pilot must.

The treatment may also move S2 to S3, because it points the invitee at one bounded section. The pilot measures both steps, so the lever stays worth testing either way. The problem label may change.

## Actions

**Engineering**
- Ship tasks 1 and 2 of the backlog together: the section prompt and the event tracking.
- Confirm that `meaningful_read_reached` and `review_checked` fire with the common fields.

**Operations**
- Recruit two raters and score a 10% sample against the rubric. Check agreement within one point is at least 80%.
- Prepare the control and treatment invite emails and single-use links.

**Growth lead (me)**
- Own the weekly read-out. Report control step conversions first.

## Risks

- Credit may attract low-effort submissions. Watch the quality rate against the 60% stop rule.
- Duplicates sit at 14.3% of submissions on synthetic data. The stop rule is 20%, so there is little headroom.
- The pilot is underpowered. Treat a lift as a signal and not as proof.

## What would change this decision

- Control S2 to S3 conversion below control S3 to S4 conversion: move to disclosure reading and re-score.
- Quality rate below 60%: pause credit and tighten the gate.
- Decliner parity below 0.80: stop the acknowledgement prompt and review its placement.

## Next review

Day 7 of the pilot, using real step conversions.
