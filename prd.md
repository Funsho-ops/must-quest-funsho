# PRD: Reviewer activation

Companion files: `intent.md`, `journey-and-participation-rules.md`, `reviewer-activation-prototype.html`. All figures marked synthetic come from the 12-record simulation and are illustrations of the method, not forecasts.

## 1. Problem and objective

Invited waitlist members read a public project disclosure and then stall before submitting a useful question or review. The objective is to raise the share of invited participants who submit a qualified review, without rewarding volume or wallet connection.

**In scope:** invite to qualified review, optional testnet acknowledgement, reviewer credit, measurement.
**Out of scope:** waitlist growth, real rewards, mainnet transactions, any claim about asset ownership, reserves or returns.

## 2. Definitions

**Qualified review.** A submission that meets all six conditions in `journey-and-participation-rules.md`: section tag, minimum length, adds something new, under 80% similarity, passes duplicate and bot checks, rubric score of 3 or higher.

**Qualified follow-up (the business conversion).** A qualified reviewer requests a meeting, a data answer or a project-team response, or accepts what the team offers, within 7 days of the review.

**Rubric (1 to 5).**
- 1: off-topic, or restates the disclosure.
- 2: generic comment with no section reference.
- 3: specific, references a section, adds one new point.
- 4: specific question or concern with reasoning the project team can answer.
- 5: identifies a gap or risk with evidence the team can act on.

Two raters score a 10% sample. If agreement within one point falls below 80%, revise the rubric before trusting the pass rate.

## 3. Funnel and formulas

S1 Invited, S2 Opened, S3 Meaningful read, S4 Submitted, S5 Qualified, S6 Qualified follow-up.

| Metric | Formula | Synthetic value |
|---|---|---|
| Qualified conversion (primary) | S5 / S1 | 5 / 12 = 41.7% |
| Quality rate | S5 / S4 | 5 / 7 = 71.4% |
| Follow-up rate | S6 / S5 | 3 / 5 = 60.0% |
| Duplicate rate | duplicates / S4 | 1 / 7 = 14.3% |
| Wallet connect rate (side metric) | wallets / S1 | 4 / 12 = 33.3% |
| Decliner parity | qualified rate of no-wallet submitters / qualified rate of wallet submitters | (2 / 3) / (3 / 4) = 0.89 |

Wallet counts, acknowledgements and raw transactions are reported in a separate panel and never enter the funnel.

## 4. Baseline and target

- **Baseline:** 41.7% is synthetic. The real baseline is measured on the first 200 invites, with no new prompt shown.
- **Target:** a 20% relative lift over the measured baseline. On the synthetic number, 41.7% becomes 50.0%.
- **Pilot:** 14 days or 200 invites per arm, whichever comes first. At a 41.7% baseline, 200 per arm gives about 39% power to detect the 50.0% target, so the pilot is directional only.
- **Decision test:** about 560 invites per arm gives 80% power at a 5% two-sided level for the same lift. Recompute with the real baseline before sizing. (Correction made after review: the first draft treated 200 per arm as a decision-grade sample.)

## 5. Stop rules

| Rule | Trigger | Action |
|---|---|---|
| Quality drop | Quality rate below 60% | Pause credit, tighten the gate, re-score a sample |
| Abuse | Duplicate rate above 20% of submissions | Pause the arm, review device and similarity flags |
| Decliner parity | Parity below 0.80 | Stop the acknowledgement prompt and review its placement |
| Acknowledgement health | Failure rate above 30% of attempts | Pause the prompt only. Reviews and credit continue |
| No effect | Pilot lift under 5% relative after 200 invites per arm | End the test and move to disclosure reading |
| Wrong bottleneck | Control step conversion S2 to S3 is below S3 to S4 | Re-run the bottleneck scoring before scaling |

## 6. Backlog (prioritised)

Ranked by expected qualified reviews per unit of effort. Tasks 1 and 2 ship together, because a lever with no measurement cannot be read.

**1. Section-tagged review prompt.**
Why first: it is the lever in the hypothesis.
Acceptance criteria:
- Each disclosure section shows a prompt and a stated time cost.
- The submit button stays disabled until the meaningful-read threshold is met.
- Every submission carries a section ID.
- The page works with no wallet present.

**2. Event tracking and funnel dashboard.**
Why second: it makes the test readable.
Acceptance criteria:
- All events in section 7 fire with the common fields.
- The dashboard shows the funnel and the side-metrics panel separately.
- Qualified conversion, quality rate, duplicate rate and decliner parity update daily.

**3. Quality gate and duplicate check.**
Why third: it protects the metric from abuse.
Acceptance criteria:
- Similarity above 80% against any earlier submission is flagged and receives no credit.
- Email normalisation, a device-cluster hold above three participants and a honeypot field are active.
- The rubric queue returns a score before credit is awarded.

**4. Reviewer credit ledger.**
Why fourth: it pays for outcomes once the gate exists.
Acceptance criteria:
- Credit posts only after a qualified result.
- The cap of three credited reviews per participant per disclosure is enforced.
- Acknowledgement credit is zero in the ledger.

**5. Optional testnet acknowledgement.**
Why last: it adds no conversion, and the case requires it to stay optional.
Acceptance criteria:
- A visible skip option, with identical credit and access for decliners.
- The disclaimer on ownership, reserves and returns shows before signing.
- A failed signature retries once, then logs `ack_failed` with a reason code, and the review stays valid.

## 7. Event schema

Common fields on every event: `event_id`, `participant_id` (pseudonymous), `timestamp`, `disclosure_id`, `disclosure_version_hash`, `arm`.

| Event | Extra fields |
|---|---|
| `waitlist_joined` | `source_channel` |
| `invite_sent` | `batch_id` |
| `disclosure_opened` | none |
| `meaningful_read_reached` | `active_seconds`, `scroll_pct` |
| `review_submitted` | `section_id`, `type`, `word_count`, `text_hash` |
| `review_checked` | `similarity_pct`, `duplicate_flag`, `rubric_score`, `qualified` |
| `credit_awarded` | `amount`, `reason` |
| `followup_requested` | `topic` |
| `followup_accepted` | `days_to_accept` |
| `wallet_prompt_shown`, `wallet_connected`, `wallet_declined` | `wallet_type` on connect |
| `ack_attempted`, `ack_succeeded` | `tx_hash` on success |
| `ack_failed` | `reason_code` (`rejected`, `no_gas`, `rpc_timeout`) |

## 8. Incentive abuse risks

- **Duplicate accounts.** Mitigated by email normalisation, device clustering and the credit cap.
- **Copied or generated text.** Mitigated by the similarity check, the section-tag requirement and the "adds something new" test.
- **Quantity farming.** Mitigated by paying for qualified results only, with a daily submission limit.
- **Wallet pressure.** Acknowledgement earns zero credit, and decliner parity is monitored.
- **Misreading the acknowledgement.** The disclaimer shows before signing, and reviews that claim ownership are excluded.

## 9. Next validation step

Run the 14-day pilot with a control arm (no prompt) and a treatment arm (section prompt plus credit). Details are in the experiment brief. The weekly decision memo reads the result against the stop rules above.
