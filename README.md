# Reviewer activation: Web3 participation loop (Quest submission)

Candidate: Akinbile Funsho
Role: Web3 Product Owner / Crypto Business Ops Manager, MUST Company

This repository holds my Quest submission. It uses the supplied fictional case and synthetic data only. No real users, rewards, mainnet transactions or live campaigns were involved.

## Start here

| Item | Link |
|---|---|
| Loom walk-through | https://www.loom.com/share/0d67c230f9034e618aed57f49585a1b8 |
| Why this problem | [intent.md](intent.md) |
| Final directive, with the results and handoff appendix | [directive.md](directive.md) |
| Working prototype | https://funsho-ops.github.io/must-quest-funsho/reviewer-activation-prototype.html |

`directive.md` links every artifact, the checks I ran, the AI contribution and the limitations.

## The problem I chose

Reviewer activation: the step from an invited waitlist member to a first qualified review of a public project disclosure. Wallet connection is optional, and declining it costs a participant nothing.

## Files

| File | What it is |
|---|---|
| [intent.md](intent.md) | Four bottlenecks compared, scores, sensitivity check, hypothesis, non-goals |
| [journey-and-participation-rules.md](journey-and-participation-rules.md) | Journey stages, eligibility, incentive logic, exclusions, duplicate and bot handling, optional testnet acknowledgement |
| [reviewer-activation-prototype.html](reviewer-activation-prototype.html) | Interactive prototype with 12 labelled synthetic records and live formulas |
| [prd.md](prd.md) | PRD, qualified review definition, funnel, baseline and target, stop rules, five-item backlog, event schema |
| [experiment-brief.md](experiment-brief.md) | One channel experiment: deep-linked section prompt in the invitation email |
| [decision-memo.md](decision-memo.md) | Weekly decision memo based on the simulation |
| [directive.md](directive.md) | Objective, scope, requirements, completion criteria, results and handoff appendix |
| [Evidence](Evidence) | Screenshots of the prototype checks, linked from section A4 of `directive.md` |
| `index.html` | Redirects the site address to the prototype |

## How to view the prototype

1. Open the prototype link above. It runs in the browser with no wallet and no sign-in.
2. Read section 5 of the page: 12 labelled synthetic records, P01 to P12.
3. Press the buttons under "Add a participant" to add a decliner, a duplicate or a failed acknowledgement, and watch the funnel recalculate.
4. Change the five rule thresholds to test the rules. Press "Reset to 12 records" to restore the starting data.

## Starting-state results (all synthetic)

| Metric | Result |
|---|---|
| Qualified conversion (qualified / invited) | 5 of 12, 41.7% |
| Quality rate (qualified / submitted) | 5 of 7, 71.4% |
| Wallets connected (side metric) | 4 of 12 |
| Qualified reviews from participants without a wallet | 2 of 5 |
| Credit earned by acknowledgement | 0 |

These figures show the measurement method. They are not forecasts.

## AI use

Claude drafted the files and the prototype. The thresholds and credit amounts are AI-proposed assumptions that I accepted for testing, and they are untested. Four corrections found during review are listed in section A5 of [directive.md](directive.md).

## Limitations

- All data is synthetic.
- The thresholds and the 20% lift target are assumptions.
- The 200-invite pilot is underpowered and gives direction only.
- The acknowledgement is simulated and does not call a testnet.
- Duplicate detection reads a stored similarity value and does not compute it.
- The rubric has no rater agreement check yet.

The full list is in section A6 of [directive.md](directive.md).
