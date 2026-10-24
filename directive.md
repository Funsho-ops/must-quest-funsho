# directive.md

Quest: Build and Measure a Meaningful Web3 Participation Loop
Candidate: Akinbile Funsho
Chosen bottleneck: reviewer activation, from invited waitlist member to first qualified review.

Everything in this submission uses the supplied fictional case and synthetic data. No real users, rewards, mainnet transactions or live campaigns were involved.

## 1. Objective

Raise the share of invited participants who submit a qualified review of a public project disclosure, and prove the gain with measures that exclude wallet counts and raw transactions.

## 2. Scope

**In scope**
- Journey from invite to qualified review and qualified follow-up.
- Participation rules: eligibility, incentive logic, exclusions, duplicate and bot handling.
- An optional testnet acknowledgement that no participant is required to use.
- A synthetic simulation, funnel formulas, one channel experiment and one weekly decision memo.

**Out of scope**
- Waitlist growth.
- Real rewards, real money and mainnet transactions.
- Any claim about asset ownership, verified reserves or guaranteed returns.
- A live campaign or production deployment.

## 3. Requirements

| ID | Requirement | Source file |  
|---|---|---|
| R1 | Compare at least three bottlenecks with stated criteria and scores, and select one | `intent.md` |
| R2 | Specify eligibility, incentives, exclusions, duplicate and bot handling and the optional acknowledgement before building | `journey-and-participation-rules.md` |
| R3 | A working prototype from registration to a meaningful off-chain action and the optional acknowledgement | `reviewer-activation-prototype.html` |
| R4 | The prototype includes a participant who declines a wallet, a duplicate and a failed acknowledgement | prototype records P02, P03, P04, P05 |
| R5 | A PRD with a qualified review definition, funnel, event schema, baseline, target and stop rules | `prd.md` |
| R6 | Five prioritised tasks with acceptance criteria | `prd.md`, section 6 |
| R7 | At least ten labelled synthetic records with visible formulas | prototype, section 5 |
| R8 | Wallet counts and raw transactions stay separate from qualified conversion | prototype side-metrics panel, `prd.md` section 3 |
| R9 | One channel experiment brief | `experiment-brief.md` |
| R10 | One weekly decision memo based on the simulation | `decision-memo.md` |
| R11 | Incentive abuse risks, the next validation step and next actions for engineering and operations | `prd.md` section 8, `experiment-brief.md`, `decision-memo.md` |

## 4. Completion criteria

The work is complete when:

1. Every requirement above maps to a file a reviewer can open without asking me.
2. The prototype's starting data reproduces the figures in section A3 below.
3. A decliner, a duplicate and a failed acknowledgement each show the stated outcome in the prototype.
4. Every link in section A1 opens for a reviewer who is not signed in as me.
5. Every figure derived from synthetic data is labelled synthetic.
6. The limitations in section A6 are stated in the Loom.

---

# Appendix: results and handoff

## A1. Artifact links

Replace each placeholder with an accessible link, then open every link while signed out.

| Artifact | Link |         
|---|---|
| Loom video (5 minutes maximum) | [add link] |
| `intent.md` | [add link] |
| Journey and participation rules | [add link to `journey-and-participation-rules.md`] |
| Operating prototype and synthetic dataset | [add shared link to `reviewer-activation-prototype.html`] |
| PRD, five-item backlog, event schema | [add link to `prd.md`] |
| Experiment brief | [add link to `experiment-brief.md`] |
| Decision memo | [add link to `decision-memo.md`] |

## A2. How to view and reproduce

1. Open the prototype link. It runs in the browser with no wallet and no sign-in.
2. Read section 5 of the page. It lists 12 labelled synthetic records, P01 to P12.
3. Check the funnel, the side-metrics panel and the headline against section A3.
4. Press "Declines wallet, asks a question", "Duplicate of P01" and "Acknowledgement fails" and watch the funnel and credit totals change.
5. Change the five rule thresholds and watch the qualified count recalculate. Press "Reset to 12 records" to return to the starting data.

## A3. Results on the starting data (all synthetic)

| Metric | Result |          
|---|---|
| Invited | 12 |
| Opened | 11 |
| Meaningful read | 8 |
| Submitted | 7 |
| Qualified | 5 |
| Qualified follow-up | 3 |
| Qualified conversion (primary) | 41.7% |
| Quality rate (qualified / submitted) | 71.4% |
| Duplicate rate | 14.3% |
| Wallets connected (side metric) | 4 of 12 |
| Qualified reviews from participants without a wallet | 2 of 5 |
| Decliner parity (submitters) | 0.89 |
| Credits awarded, all non-cash | 90 |
| Credit earned by acknowledgement | 0 |

The figures show the method. They are not forecasts.

## A4. Checks and actual results

| Check | Done by | Result | Status |
|---|---|---|---|
| Recounted funnel stages from the 12 raw records against the PRD table | Claude, by hand | Matches: 12, 11, 8, 7, 5, 3 | Done |
| Recomputed credits: P01 20, P02 10, P03 25, P05 10, P11 25 | Claude, by hand | Total 90, matches the page logic | Done |
| Recomputed sample size and power for 41.7% to 50.0% | Claude | 200 per arm gives about 39% power. About 560 per arm gives 80% | Done, led to correction C1 |
| Compared the hypothesis in `intent.md` with step conversions in the records | Claude | S2 to S3 loses more than S3 to S4, which contradicts the hypothesis | Done, led to correction C2 |
| Opened the prototype in a browser and compared the starting state with section A3 | Funsho, run locally, 23 Oct 2026 | All figures matched: funnel 12, 11, 8, 7, 5, 3; headline 41.7%; credits 90; wallets 4 of 12; 2 of 5 qualified reviewers without a wallet | Done |
| Ran the four participant scenarios (wallet user, decliner, duplicate, failed acknowledgement) | Funsho, run locally, 23 Oct 2026 | One click each, in sequence, with no reset between them, so the result is cumulative. Final state: 16 invited, 8 qualified (50.0%), quality rate 72.7%, credits 120, 7 wallets connected, 3 of 8 qualified reviewers without a wallet, acknowledgement credit 0. The figures match a hand calculation for the same sequence | Done, cumulative |
| Ran the 120-second read threshold test from the 12-record start | Funsho, run locally, 24 Oct 2026 | Matched the expected figures: 5 meaningful reads, 4 qualified (33.3%), credits 80. P04 and P05 no longer reach submission | Done |
| Screenshots of the page | Funsho | Starting state, cumulative scenario run and 120-second test, linked below the table | Done |
| Opened every link in A1 while signed out | Funsho | [record result] | Pending |
| Two-rater rubric check on a sample | Not run. It needs real submissions | Planned for the pilot | Not done |

Claude did not run the prototype in a browser. Funsho ran every check marked above locally. The figures match Claude's hand calculations.

Evidence for the prototype check (run locally, 23 and 24 Oct 2026):

- [Starting state, funnel and headline](Evidence/starting-state-1.png)
- [Starting state, side metrics and records](Evidence/starting-state-2.png)
- [Four scenarios run in sequence, cumulative result](Evidence/scenarios-cumulative.png)
- [Read threshold set to 120 seconds](Evidence/read-threshold-120s.png)

## A5. AI contribution and corrections

**What AI produced.** Claude drafted `intent.md`, the participation rules, the prototype, `prd.md`, the experiment brief, the decision memo and this file. The thresholds (90 seconds, 40 words, 80% similarity, rubric pass of 3) and the credit amounts are AI-proposed assumptions that I accepted for testing.

**My decisions**
- I chose the interactive page over a spreadsheet, on Claude's recommendation, so the decliner, duplicate and failed-acknowledgement paths can be shown live. I did not build both.
- I chose one PRD file for the backlog and event schema, on Claude's recommendation, so the reviewer finds everything in one place.
- I accepted reviewer activation as the bottleneck on Claude's scoring. I did not change the scores or the weights.
- I kept the wallet-neutral incentive design as proposed. I did not change it.
- I did not change Claude's thresholds or credit amounts. They remain untested assumptions.
- The four corrections in the table below were found by Claude during review. I checked them and kept them.

**Corrections found during review**

| ID | What was wrong | Correction |   
|---|---|---|
| C1 | `prd.md` treated 200 invites per arm as a decision-grade sample. Power is about 39% | Reclassified 200 as a directional pilot. Added the 560-per-arm decision test. Logged in `prd.md` |
| C2 | The synthetic records lose more participants at S2 to S3 than at S3 to S4, against the hypothesis | Stated in `decision-memo.md`. Added a switch rule to the PRD stop rules. The data was not altered |
| C3 | The rubric scale was undefined, which left the pass mark of 3 meaningless | Defined the 1 to 5 scale and a two-rater agreement check in `prd.md` |
| C4 | Decliner parity over all invitees would have compared 2 of 8 against 3 of 4, distorted by people who left early | Defined parity over submitters only, giving 0.89 |

## A6. Limitations

- All data is synthetic. The 12 records exercise every path and do not estimate real drop-off.
- The prototype simulates duplicate detection. Similarity is a stored input, not computed between submissions, so two identical records can both qualify. The real check is task 3 of the backlog.
- The thresholds and the 20% lift target are assumptions with no supporting data.
- The pilot is underpowered and gives direction only.
- The prototype simulates the acknowledgement. It does not call a testnet.
- The rubric has not been tested for rater agreement.
- No pre-existing work was adapted.
- Actual effort: 18 hours. 7 hours reading and correcting the AI drafts, 4hrs checking the prototype, 6 hours writing decisions, 1 hour Loom.
